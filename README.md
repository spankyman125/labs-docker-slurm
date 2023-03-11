# Slurm docker cluster 
## Build
```console
sudo docker-compose up --build -d
```
## Submitting jobs
Enter container
```console
sudo docker exec -it spankyman0 bash
```
Verify nodes availability
```console
root@spankyman0:/# sinfo
PARTITION AVAIL  TIMELIMIT  NODES  STATE NODELIST
debug*       up   infinite      4   idle spankyman[1-4]
```
Hostname test
```console
root@spankyman0:/# srun -n 4 hostname
spankyman3
spankyman2
spankyman4
spankyman1
```
MPI test
```console
root@spankyman0:/# salloc -n 4 sh
salloc: Granted job allocation 1
# mpirun --allow-run-as-root /home/mpi.o
Hello world from processor spankyman2, rank 1 out of 4 processors
Hello world from processor spankyman1, rank 0 out of 4 processors
Hello world from processor spankyman3, rank 2 out of 4 processors
Hello world from processor spankyman4, rank 3 out of 4 processors
```
