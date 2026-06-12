---
title: "Will I ever be able to smoothly play x264 720p on Ubuntu?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by wesleyb82 on 2010-02-14
I have an Acer 3100 with 1.8Ghz single core, and ATI 1100/1200 mobile (no driver support- only open as I understand). I have installed what seems all the players, codecs, etc. My best result have been with VLC but results are choppy and CPU is at 100%. 

Has anyone with these specs been able to play x264/mkv 720p or should I just give up and stick to 480p mpg LD on this old machine?

I just got into Ubuntu and I'm loving it. Thanks for any help.

---

### Post by Satoru-san on 2010-02-14
My laptop specs are around the same I can play doom3 (on the lowest setting) but also cannot play [s]720p[/s] these computers cant handle that.

EDIT:Just checked it tuns out I have matrix 1080p

---

### Post by wesleyb82 on 2010-02-14
You just tested the system with 1080p? 
I know it has a lot to do with the under powered CPU but I wonder what the results would be if I had non-generic drivers for the GPU. Can the windows drivers be used somehow?

Thanks!

---

### Post by Julita on 2010-02-14
I have been able to play .mkv (720p)flawlessly with VLC on my ASUS netbook (Intel Atom n270 1.6GZ; 1GB RAM.)

---

### Post by lidex on 2010-02-14
There is a ppa version of mplayer that works best for me. Probably the easiest way for you to get is using ubuntu-tweak. Click [here]("http://launchpad.net/ubuntu-tweak/0.5.x/0.5.0/+download/ubuntu-tweak_0.5.0-1~karmic1_all.deb") to download if you're on karmic (9.10). Double-click on the file to install with gdebi. Go [here]("http://ubuntu-tweak.com/downloads/") if not on karmic or for alternate install options.

Once installed open at "Applications>System Tools>Ubuntu Tweak". Go to "Applications>Third-Party-Sources" and place a checkmark next to Mplayer. Click "Refresh". Go to the "Add/Remove" section and select "Mplayer Movie Player" then click "apply".

If you right-click on the movie file in nautilus and select "properties" you can choose mplayer as default for those file types on "open with" tab.

---

### Post by clhsharky on 2010-02-14
HI

The main problem is Adobe flash player. Adobe does not support hardware acceleration on Linux. There minimum hardware configurations is to much for low power systems.
[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

Most just download the flash file and play it in there favorite player. 

Sharky

---

### Post by Julita on 2010-02-14
As to online HD videos, one can always choose earlier version of Adobe Flash Player that is less resourse-consuming...

---

### Post by lovinglinux on 2010-02-14
> **clhsharky said:**
> HI

The main problem is Adobe flash player. Adobe does not support hardware acceleration on Linux. There minimum hardware configurations is to much for low power systems.
[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

Most just download the flash file and play it in there favorite player. 

Sharky

+1 

I have a Core2 Duo 2.9Ghz and can play 1080p fine, but locally, not on YouTube. See discussion [here](http://ubuntuforums.org/showthread.php?t=1403387).

---

### Post by lidex on 2010-02-14
I think the OP was referring to mkv video, not flv.

---

### Post by wesleyb82 on 2010-02-14
Many thanks for responses. 

First, I am looking to stream MKV movies and shows from my media center and play 720 MOV files from my pocket cam. Regardless of whether the file is on the LAN server or local machine the file is choppy.

The tweaks app is cool, thanks for that tip, but I already have mPlayer installed. I have used VLC, Mplayer, Movie Player, gnome Mplayer, installed ffshow, and all other plug-ins/codecs I could find. I have noticed the video output options and ive been playing with those and have not seen any differences. I do know how much the codec can make from my media center experiences with HD content. 

So there is someone out there with a netbook running 720p mkv. But I think the difference here is that you probably have a supported GPU, while I have a GPU (ATI xpress 1100/1200) that is not supported (I think) and I am using the open driver. 

Thanks guys! I'll be so stoked if I can get this going.

---

### Post by wesleyb82 on 2010-02-14
Oh yeah, and my CPU usage seems really high. With just System Monitor open the usage ranges between 30-40% .... That doesn't seem right.

---

### Post by NightwishFan on 2010-02-14
Open a terminal (Application -> Accessories -> Terminal) and type this and push enter:
```
top
```

That should show the top apps using CPU. Please list the top few here. Press Q to quit top.

You should also make sure your Ubuntu install CD is correct. Insert it in your drive, and run this command in the terminal as well:
```
cd /media/cdrom0 && md5sum -c md5sum.txt
```

The command will check the CD for errors. If it does not say "ERROR" at the end, then the CD is fine.

---

### Post by 3rdalbum on 2010-02-14
Your CPU use at idle is definitely too high. Investigate this.

If you have Compiz (visual effects) turned on, then try turning them off while playing video.

---

### Post by lidex on 2010-02-14
> **wesleyb82 said:**
> Many thanks for responses. 

First, I am looking to stream MKV movies and shows from my media center and play 720 MOV files from my pocket cam. Regardless of whether the file is on the LAN server or local machine the file is choppy.

The tweaks app is cool, thanks for that tip, but I already have mPlayer installed. I have used VLC, Mplayer, Movie Player, gnome Mplayer, installed ffshow, and all other plug-ins/codecs I could find. I have noticed the video output options and ive been playing with those and have not seen any differences. I do know how much the codec can make from my media center experiences with HD content. 

So there is someone out there with a netbook running 720p mkv. But I think the difference here is that you probably have a supported GPU, while I have a GPU (ATI xpress 1100/1200) that is not supported (I think) and I am using the open driver. 

Thanks guys! I'll be so stoked if I can get this going.

I feel you but the reason I recommended mplayer from that ppa is that it worked extremely well on some mkv 264 files I downloaded when everything else I tried choked on them, including mplayer from the ubuntu repository. So clearly something better going on there. And with any video player you'll want to go into preferences and configure the video drivers, etc, for best performance.

Having said that, you would probably benefit more from some xorg tweaks and possibly a different driver. What is your terminal output from this command:
```
lspci -nn | grep VGA
```

---

### Post by wesleyb82 on 2010-02-14
> **NightwishFan said:**
> Open a terminal (Application -> Accessories -> Terminal) and type this and push enter:
```
top
```That should show the top apps using CPU. Please list the top few here. Press Q to quit top.

You should also make sure your Ubuntu install CD is correct. Insert it in your drive, and run this command in the terminal as well:
```
cd /media/cdrom0 && md5sum -c md5sum.txt
```The command will check the CD for errors. If it does not say "ERROR" at the end, then the CD is fine.
wesley@wesley-ubuntu:~$ top

top - 23:48:18 up  1:08,  2 users,  load average: 0.86, 0.83, 0.53
Tasks: 147 total,   3 running, 142 sleeping,   1 stopped,   1 zombie
Cpu(s):  8.6%us,  5.3%sy,  0.0%ni, 85.8%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1413400k total,   715464k used,   697936k free,    54284k buffers
Swap:   923696k total,        0k used,   923696k free,   378208k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7159 wesley    20   0  290m  84m  29m S  5.0  6.1   0:57.22 firefox            
  688 root      15  -5     0    0    0 R  3.6  0.0   0:53.34 ntos_wq            
  940 root      20   0  170m  34m 7704 S  3.3  2.5   6:15.35 Xorg               
 7350 wesley    20   0 38352  12m 9568 S  1.0  0.9   0:01.00 gnome-terminal     
 7374 wesley    20   0  2472 1176  884 R  0.7  0.1   0:00.16 top                
    6 root      15  -5     0    0    0 S  0.3  0.0   0:01.39 events/0           
 1688 wesley    20   0  103m  13m  10m S  0.3  1.0   0:06.10 metacity           
    1 root      20   0  2532 1524 1128 S  0.0  0.1   0:00.86 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:01.30 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 async/mgr          
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      

This is with mail/firefox, but with system monitor (graphical) it jumps to 30-40%

---

### Post by wesleyb82 on 2010-02-14
> **lidex said:**
> I feel you but the reason I recommended mplayer from that ppa is that it worked extremely well on some mkv 264 files I downloaded when everything else I tried choked on them, including mplayer from the ubuntu repository. So clearly something better going on there. And with any video player you'll want to go into preferences and configure the video drivers, etc, for best performance.

Having said that, you would probably benefit more from some xorg tweaks and possibly a different driver. What is your terminal output from this command:
```
lspci -nn | grep VGA
```

wesley@wesley-ubuntu:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975

According to the Acer website this 3100 should have a 1100/1200 xpress GPU. 200M must be the generic driver?

I also could not follow your instructions for ppa install. When I ran tweaks your instrucions did not make sense- it intalled version 0.5.0- maybe you have an older version?

Clearer instructions so that I could try this would be awesome.

---

### Post by lavinog on 2010-02-14
200M is the gpu chipset.  The driver is the open source radeon driver since ATI dropped proprietary support for older cards as of jaunty (9-3).

You can try the latest open source radeon driver, or wait until lucid is released in april which will come with the more recent driver.

I don't think that acer was ever advertised as being able to play hi-def video, so you may have some issues even on windows.

---

### Post by lidex on 2010-02-15
> **wesleyb82 said:**
> wesley@wesley-ubuntu:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975

According to the Acer website this 3100 should have a 1100/1200 xpress GPU. 200M must be the generic driver?

I also could not follow your instructions for ppa install. When I ran tweaks your instrucions did not make sense- it intalled version 0.5.0- maybe you have an older version?

Clearer instructions so that I could try this would be awesome.

Yes i have older version but I'm on jaunty. The idea is to use ubuntu-tweak to add the ppa for mplayer. That ppa upgrades mplayer through regular means (synaptic, apt, etc).

---

### Post by lidex on 2010-02-15
Radeon Driver info:
> This guide will show you how to use the Free, Open Source driver for many ATI graphics cards called "radeon" or "ati". It will provide 2D and 3D acceleration in your video hardware. This driver is not as fast as the closed-source, proprietary "fglrx" driver from AMD/ATI Inc. for some cards, but has better dual-head support, and supports some older chipsets that fglrx does not. 
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver") Definitely worth a look - has xorg tweaks.

The latest flgrx driver supporting your chip is 9.3:
[http://support.amd.com/us/gpudownload/linux/9-3/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/9-3/Pages/radeon_linux.aspx")
However there is a bug:
[http://ati.cchtml.com/show_bug.cgi?id=183]("http://ati.cchtml.com/show_bug.cgi?id=183")

---

### Post by wesleyb82 on 2010-02-15
> **lidex said:**
> Radeon Driver info:
 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) Definitely worth a look - has xorg tweaks.
 
The latest flgrx driver supporting your chip is 9.3:
[http://support.amd.com/us/gpudownload/linux/9-3/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/9-3/Pages/radeon_linux.aspx)
However there is a bug:
[http://ati.cchtml.com/show_bug.cgi?id=183](http://ati.cchtml.com/show_bug.cgi?id=183)
 
Wow, you guys are great.
I currently have 9.10 installed, what version of Ubuntu is this driver compatible with? I read somewhere that 8.10 is the latest version which supports the card I think. If so I'm going to burn a 8.10 and boot from disk and try to get these drivers from AMD going, see if it makes a difference. Am I on the right track?

---

### Post by Julita on 2010-02-15
In order to lower your CPU usage, you have to define parameters by installing programs cpufreqd and cpufrequtils. Once installed, you will be able to see your configuration of CPU frequency via command cpufreq-info and set your own parameters via sudo cpufreq-set. Type in the terminal man cpufreq-set for usage. Type sudo cpufreqd to launch useful demon (via sudo cpufreqd-set you can define the way demon works.)

---

### Post by lidex on 2010-02-15
> **wesleyb82 said:**
> Wow, you guys are great.
I currently have 9.10 installed, what version of Ubuntu is this driver compatible with? I read somewhere that 8.10 is the latest version which supports the card I think. If so I'm going to burn a 8.10 and boot from disk and try to get these drivers from AMD going, see if it makes a difference. Am I on the right track?

A cautious yes here...you may want to try installing 8.10 to another partition and then test the driver. Don't think a live session will do it for you. If you're not married to Karmic and this works, then go for it. A lot of users are still running 8.04

---

### Post by wesleyb82 on 2010-02-15
i uninstalled all video apps and codec packages, then following the previous suggestion by [lidex]("http://ubuntuforums.org/member.php?u=577099") i started the open source ATI drive instrutions, ran 
$ sudo apt-get remove --purge xorg-driver-fglrx

choose y, restarted

then opened a MKV and all is well!

i do not understand this whole process yet but i just know 720p is running at 100% in VLC.

ah, my 8 hour plane trip is going to be mint! Thank you!

---

