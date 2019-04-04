# gpuminer

### windows

1、下载 [gpuminer](https://github.com/simplechain-org/gpuminer/releases/download/v1.0.3/gpuminer-windows-1.0.4-amd64.zip)压缩文件。

2、解压所下载的文件。

3、修改start.bat文件，将-server设置为即将加入的矿池地址 ，-name设置为即将加入的矿池的矿工的名称,-gpuplatform 设置为对应的显卡的数字（A卡设置为1，N卡设置为2，混合设置为3，默认为1）。

4、双击start.bat文件开始挖矿。

### mac
1、下载 [gpuminer](https://github.com/simplechain-org/gpuminer/releases/download/v1.0.2/gpuminer-darwin-1.0.4-amd64.zip)压缩文件。

2、解压所下载的文件。

3、修改start.sh文件，将-server设置为即将加入的矿池地址 ，-name设置为即将加入的矿池的矿工的名称,-gpuplatform 设置为对应的显卡的数字（A卡设置为1，N卡设置为2，混合设置为3，默认为1）。

4、打开terminal,将目录切换到解压文件所在的目录，输入命令bash start.sh ，按下enter键开始挖矿。

### linux

1、下载 [gpuminer](https://github.com/simplechain-org/gpuminer/releases/download/v1.0.2/gpuminer-linux-1.0.4-amd64.zip)压缩文件。

2、解压所下载的文件。

3、修改start.sh文件，将-server设置为即将加入的矿池地址 ，-name设置为即将加入的矿池的矿工的名称,-gpuplatform 设置为对应的显卡的数字（A卡设置为1，N卡设置为2，混合设置为3，默认为1）。

4、打开terminal,将目录切换到解压文件所在的目录，输入命令bash start.sh ，按下enter键开始挖矿。

### 可调节的参数

```
Usage of ./gpuminer:
  -globalworksize int
    	Number of GPU threads to use for mining (default 8000)
  -gpuplatform int
    	gpu platform:1=AMD,2=NVIDIA,3=ALL (default: 1) (default 1)
  -localworksize int
    	group work size (default 64)
  -lookupgap int
    	This tunes a compromise between ram usage and performance. Setting (1/2/4/8) overrides the default of 2  (default 2)
  -memsize uint
    	filter gpu memory MB size (default: 2048) (default 2048)
  -name string
    	miner name registered to the stratum server (default "localhost")
  -password string
    	stratum protocol password, default: no password
  -server string
    	stratum server address,(host:port) (default "127.0.0.1:8801")
  -verbosity int
    	Logging verbosity: 0=silent, 1=error, 2=warn, 3=info, 4=debug, 5=detail (default: 3) (default 3)
```     
### 额外说明
当你看到以下信息时，不用惊慌，请稍等，根据各个机器配置不同，可能等待的时间从6秒到3分钟不等。

```
$ ./gpuminer.exe -server simpool.vip:8801 -name test007
INFO [03-01|07:57:33.423] miner name                               using=test007
INFO [03-01|07:57:33.431] CPU                                      number=4
INFO [03-01|07:57:33.431] NewRunPlatform                           device=Ellesmere memory=8192
INFO [03-01|07:57:33.432] kernel program build start,please wait...
```
当你看到类似以下信息时，表明你的机器已经能够正常挖矿了：
```
INFO [03-01|07:57:46.488] kernel program build success             Spend time=13.0558359s
INFO [03-01|07:57:46.506] opencl                                   version="OpenCL C 2.0 "
INFO [03-01|07:57:46.506] device Ellesmere max workgroup size is 256 and 36 compute units Advanced Micro Devices, Inc.
INFO [03-01|07:57:46.506] Client start connection
INFO [03-01|07:57:46.523] Client connected
INFO [03-01|07:57:46.531] ReceivedTask                             id=4300001807 diff=90439322116 nonceBegin=0 nonceEnd=18446744073709551615
INFO [03-01|07:57:47.349] ReceivedTask                             id=4300001807 diff=45219661058 nonceBegin=5397499323976304299 nonceEnd=6049961561462966664
INFO [03-01|07:57:49.265] ReceivedTask                             id=4400001807 diff=22609830529 nonceBegin=12062582175333332482 nonceEnd=12518593739503062420
INFO [03-01|07:57:49.743] ReceivedTask                             id=4500001807 diff=11304915264 nonceBegin=6194643657107765039  nonceEnd=7069793686865035508
INFO [03-01|07:57:50.866] ReceivedTask                             id=4600001807 diff=5652457632  nonceBegin=7709151493183826777  nonceEnd=8476122391792807122
INFO [03-01|07:58:01.524] Calculating                              hashRate=632503 count=9488000000000000 time difference=15000718100
```
注意:windows下的如果想要看到实时运行日志，可以下载安装一个git,然后利用git bash来查看 tail -f gpuminer.log

支持多显卡进行挖矿。支持gpu过滤，也就是你可以根据你自己机器的情况：
1. -gpuplatform 1 选择A卡进行挖矿。
2. -gpuplatform 2 选择N卡进行挖矿
3. -gpuplatform 3 选择混合多卡挖矿。

可以通过添加参数-memsize来过滤显存小的卡不进行挖矿（默认为2048MB）。这样，你就可以通过这个参数来设置集成显卡不参与挖矿。

备注：simpool.vip:8801 为矿池地址，访问 https://simpool.vip/ 注册帐户
