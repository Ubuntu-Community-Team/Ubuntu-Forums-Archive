---
title: "Folding@home SMP and BOINC Don't See GPU"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by AvoidedRider on 2011-01-28
I started using Ubuntu about 2 years ago. Beginning of the month I decided to install it on my main computer because well my main computer was starting to collect dust. My computer has a graphics card that I had been using with folding@home(FAH) and I would like to continue that in Ubuntu. What I am trying to do is let BOINC use the CPU and FAH to the GPU primarily with little crossover. The BOINC projects I use don't support GPU anyways.

When I open BOINC it gives me a message of

Thu 27 Jan 2011 07:57:27 PM EST        No usable GPUs found

When I installed Linux (x86) and BSD *combined uniprocessor (CPU) and SMP2 client* (64-bit build) I ended up with a FAH process using 200 percent of a single core and then running 
                     ```
nvidia-smi -a  
 
```> 
GPU 0:
    Product Name        : GeForce 9800 GT
    PCI Device/Vendor ID    : 60510de
    PCI Location ID        : 0:2:0
    Display            : Connected
    Temperature        : 50 C
    Fan Speed        : 35%
    Utilization
        GPU            : 0%
        Memory        : 7%
GPU 1:
    Product Name        : GeForce 7150 / nForce 630i
    PCI Device/Vendor ID    : 7e010de
    PCI Location ID        : 0:0:10
    Display            : Not connected
    Utilization
        GPU            : 0%
        Memory        : 0%
So as an experiment I allowed a project on BOINC that should have used the GPU to try and it didn't change GPU Usage. So I did some research and was sure I had the answer. Everywhere I looked it seemed like the answer was installed CUDA and your problems will be solved. Yeah about that. I used this Howto [http://ubuntuforums.org/showthread.php?t=1625433&highlight=cuda+10.10](http://ubuntuforums.org/showthread.php?t=1625433&highlight=cuda+10.10) I installed > "GPU Computing SDK" and compile of the examples to verify that your installation works with the result of. 
> 
CUDA sample DCT/IDCT implementation
===================================
Loading test image: barbara.bmp... [512 x 512]... Success
Running Gold 1 (CPU) version... Success
Running Gold 2 (CPU) version... Success
Running CUDA 1 (GPU) version... Success
Running CUDA 2 (GPU) version... 4140.641464 MPix/s //0.063310 ms
Success
Running CUDA short (GPU) version... Success
Dumping result to barbara_gold1.bmp... Success
Dumping result to barbara_gold2.bmp... Success
Dumping result to barbara_cuda1.bmp... Success
Dumping result to barbara_cuda2.bmp... Success
Dumping result to barbara_cuda_short.bmp... Success
Processing time (CUDA 1)    : 0.278300 ms 
Processing time (CUDA 2)    : 0.063310 ms 
Processing time (CUDA short): 0.093000 ms 
PSNR Original    <---> CPU(Gold 1)    : 32.777073
PSNR Original    <---> CPU(Gold 2)    : 32.777050
PSNR Original    <---> GPU(CUDA 1)    : 32.777000
PSNR Original    <---> GPU(CUDA 2)    : 32.777039
PSNR Original    <---> GPU(CUDA short): 32.749447
PSNR CPU(Gold 1) <---> GPU(CUDA 1)    : 58.249779
PSNR CPU(Gold 2) <---> GPU(CUDA 2)    : 64.753647
PSNR CPU(Gold 2) <---> GPU(CUDA short): 42.258053

PASSED
and
> ./deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

There is 1 device supporting CUDA

Device 0: "GeForce 9800 GT"
  CUDA Driver Version:                           3.20
  CUDA Runtime Version:                          3.20
  CUDA Capability Major/Minor version number:    1.1
  Total amount of global memory:                 536150016 bytes
  Multiprocessors x Cores/MP = Cores:            14 (MP) x 8 (Cores/MP) = 112 (Cores)
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       16384 bytes
  Total number of registers available per block: 8192
  Warp size:                                     32
  Maximum number of threads per block:           512
  Maximum sizes of each dimension of a block:    512 x 512 x 64
  Maximum sizes of each dimension of a grid:     65535 x 65535 x 1
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             256 bytes
  Clock rate:                                    1.62 GHz
  Concurrent copy and execution:                 Yes
  Run time limit on kernels:                     Yes
  Integrated:                                    No
  Support host page-locked memory mapping:       Yes
  Compute mode:                                  Default (multiple host threads can use this device simultaneously)
  Concurrent kernel execution:                   No
  Device has ECC support enabled:                No
  Device is using TCC driver mode:               No

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 3.20, CUDA Runtime Version = 3.20, NumDevs = 1, Device = GeForce 9800 GT


PASSED

Press <Enter> to Quit...
-----------------------------------------------------------So nothing is any different at this point. Other than I no longer have a list of additional drivers when I go to that menu item. So I have to have goofed up the installation. Right? So I went to [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome) Well I wish I could say nothing changed. After trying all options I now have 4 FAH CPU based single process threads (one per core) that I haven't managed to remove. I can't find any evidence of them in synaptic or Ubuntu software center and apt-get doesn't seem to do anything to remove them. I tried to kill the process with system monitor but they didn't die. I restarted the computer they came back. I am sure that if I try hard enough with top or htop I have to be able to kill them but they will just come back. 

About my computer:
Q6600 overclocked by me 2.86 GHz
9800GT super clocked by EVGA
Ubuntu 10.10 (maverick) Used Natty off and on December to early January but it got buggy.
I think that is everything Hopefully Everything is okay about this post first time I have posted anything. Hopefully I can find this again. I tried to post in the [Threads in Forum : x86 64-bit Users]("http://ubuntuforums.org/forumdisplay.php?f=343") but it didn't let me. The button that I used to start a thread here didn't appear. Any ideas on any of it please let me know . Thank you for any and all help.[URL="http://ubuntuforums.org/forumdisplay.php?f=343"]
[/URL]

---

### Post by 3rdalbum on 2011-01-28
GPU work units are different to CPU work units. When your current CPU unit is finished, you'll probably get a GPU unit.

---

### Post by AvoidedRider on 2011-01-28
I used a project that allowed for the computing with the GPU after I had tried everything else and forced that to run by suspending my normal project. I reinstalled Folding@home after deleting everything. Should have been all new projects. If that wasn't enough its been a few days. I am picking at this when I have time.

I forgot to point out that BOINC specifically says still that i don't have a usable GPU. Just to add weight to the fact something seems still wrong.

---

### Post by AvoidedRider on 2011-01-29
While attempting to get rid of the 4 extra CPU versions of Folding@home I installed FahMon Hoping to get more information on them. I also let the computer update itself and then I let it restart to finish. It stops trying to boot at the tty1 terminal screen. If I press ctrl + alt + f7 I get Fah core1 starting and that it was successfully message repeats for other 3. Then it just sits there.

I am currently using the computer by using recovery options and loading failsafe x. Of course no grid computing here.

Is there any way to restore Ubuntu to an earlier state? Anyway to recove the computer? Right now I am thinking about reinstalling the OS and starting over again. I seem to have gotten in over my head somewhere. 

This is proving to be much harder than installing raid.

---

### Post by AvoidedRider on 2011-01-29
Well I got the computer back to a an acceptable state. Ended up remembering that the computer stoped at that terminal screen before when I removed the graphics drivers. So I completely reinstalled the CUDA and Nvidia graphics drivers. I don't understand why they disappeared though. Fahmon isn't quite what I had hoped for it doesn't just automatically scan for fah applications. 

Does anyone know how to find something like the msconfig options in Ubnutu? If I can find a list of all the Daemons that are being started before I log in even if i have to go through it line by line until I can find the CPU version to remove. 

As far as the FAH GPU version I am ready to admit that it isn't adequately supported yet.

---

### Post by AvoidedRider on 2011-01-29
In answer to my questions I found a [website]("http://askubuntu.com/questions/15844/stopping-daemons-from-loading-at-boot-time") from which I extracted the following code.
```
sudo apt-get install chkconfig
```
```
chkconfig --list
```
This showed that Origami was a lot harder to remove than I had anticipated. I attempted to remove it again with this in mind and doing some more research. I no longer have rouge FAH CPU clients on my computer. Cool. But [origami]("https://help.ubuntu.com/community/FoldingAtHome/origami") still show up in that list, but it shows that it isn't trying to start so I guess it can be left like that. 

Now as to the original, real objective, still can't get the FAH SMP client to use my GPU and BOINC still says that I don't have a usable GPU. I did find mention of a program ([cpulimit]("http://cpulimit.sourceforge.net/") to limit the CPU usage of the FAH once I get it to use the GPU.

Any suggestions, I am open. I am also not as worried as I probably should be about grenading my OS. I think the coolest thing about computers is that if you ruin everything the worst case scenario is that you start over from scratch with a clean install.

---

### Post by AvoidedRider on 2011-01-30
Finally some progress. I ran code that I found [here]("https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/587426") ```
sudo /etc/init.d/boinc-client restart
```
and now BOINC can now see my GPU > Sun 30 Jan 2011 12:31:43 AM EST        NVIDIA GPU 0: GeForce 9800 GT (driver version unknown, CUDA version 3020, compute capability 1.1, 511MB, 364 GFLOPS peak)
 Apparently has something to do with when the driver and BOINC start in relation to each other.Now if only folding at home was that easy.

---

### Post by AvoidedRider on 2011-01-31
I guess I should say thank you for not calling me an idiot. SMP and GPU are two separate things. So I really only had one program misbehaving. Thank you for all the help.

---

### Post by hiacynt on 2011-02-08
I'm having exactly the same issue, man. Couldn't find a way to get F@H to use my GPU, no matter which version I used, it just crashed. I did manually reinstall the drivers, CUDA etc., to no avail. Hopefully someone will have an answer or they eventually make a native linux port *sighs*.

---

### Post by AvoidedRider on 2011-02-08
Hey sorry I left this thread the way I did. I became frustrated and irritable. My system has been working for about a week and is now getting about 4261 PPD on the GPU. It all came back to my last post for me. I didn't understand the difference between the SMP and the GPU clients. 

Its a shame I didn't see this yesterday. I just closed down my browser with all the forums I used on this. Looking through my history I realize just how reliant I am on the Internet.

Personally I had no success with the zip files. After trying like 7 different ways of installing the program, I used wine to install the [GPU Client]("http://www.stanford.edu/group/pandegroup/folding/release/Folding@home-Win32-GPU-systray-623.msi") with the windows MSI. Now it needed a wrapper. The links that I found with twomurs or GPU3 in the address were outdated they might pull a file and seem like they worked but they weren't any good. I think this is the [website]("http://www.fold4life.com/forum/viewtopic.php?f=3&t=2011") I finally got my last few pieces from. ```
wget http://www.fold4life.com/ffiles/wrapper2ndgen/cudart.dll.so -O ~/.wine/drive_c/windows/system32/cudart.dll
``` I think that is all it took, but I was all over the map looking for a solution and in the last week I've been fighting with FAH monitoring programs which are every bit as difficult. ```
wine Folding @home-Win32-GPU.exe -configonly -forcegpu nvidia_g80
``` and ```
wine Folding @home-Win32-GPU.exe -forcegpu nvidia_g80
``` helped me find errors that I was looking up online.  When it finally started working I was able to just click on Applications->Wine->Programs->Folding@Home-GPU->Folding@Home and that got me into the configuration and got the program running.

If you wouldn't mind telling me the reason that F@H says it is failing I'll try to figure out what is going on. If you can't or don't want to use the above code to see what is causing F@H to crash you can look at the log files. You can use ```
sudo find / -iname FAHlog.txt
``` to find those log files. It came in handy trying to set up the monitor after I got the client installed.

---

### Post by rklapp on 2011-05-06
I get the following error message. Any suggestion? TIA

[01:42:46] Decompressed FahCore_11.exe (1908736 bytes) successfully 
[01:42:51] + Core successfully engaged 
[01:42:56]  
[01:42:56] + Processing work unit 
[01:42:56] Core required: FahCore_11.exe 
[01:42:56] Core found. 
[01:42:56] Working on queue slot 01 [May 7 01:42:56 UTC] 
[01:42:56] + Working ... 
[01:43:00] CoreStatus = C0000135 (-1073741515) 
[01:43:00] Client-core communications error: ERROR 0xc0000135 
[01:43:00] This is a sign of more serious problems, shutting down.

---

