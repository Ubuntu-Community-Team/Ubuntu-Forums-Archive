---
title: "Inno3d Graphics Card (G72 [GeForce 7300 SE]) Randomly Freezing"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by oookkkooo on 2009-02-28
Hi,

I built up a machine from spare parts and I wasnt satisfied with onboard video so I bought a Inno3d card (cheapie).  When I finally found drivers that work (V 177 proprietary Nvidia) it causes the system to freeze.  No Num lock no mouse nothing and the sound that was playing at the time, repeats for +/-0.2 seconds.

I have no idea what to look for in the logs (not that I even know which logs to look at).  I really hope it's not hardware because I dont really want to spend money.  When I disable the driver the PC works fine but with no 3d :-( 

So it may not be the hardware.  I dont know anything about compiling the kernel and I dont even know where to start.  I try to read up on it but I get so confused.  A good starting point will be nice.  Sort of a learning path.

Anyway, my ubuntu knowledge aside, does anyone have this card and this problem?  I am running 8.10 and I love it!!

---

### Post by oookkkooo on 2009-03-02
I have the same card and I have enabled the restricted drivers but this causes my machine to completely freeze at random.  No numlock, no mouse, nada.

I have the enhanced desktop effects enabled and it looks great.  until it freezes :-(

---

### Post by overdrank on 2009-03-02
Hi and I have moved your recent post back to your thread and will try and assist. 
If I understand your first post correctly, your are having freezing issues on your system when you activate the nvidia drivers. I had a similar issue and I had to update the nvidia driver.
Could you tell us some system specs, and have you tried the recent nvidia drivers via manual install?

---

### Post by oookkkooo on 2009-03-02
Hi,

Thanks.  Would you like an lshw?  I'll do that when I get home.  

I downloaded and ran the  NVIDIA-Linux-x86-xxx.xx.xxx.run file but when it came to compiling the kernel (I dont know how to do that) the script said could not find kernel headers (if I remember correctly).  After wich I battled to get any sort of decent resolution beause this machine is connected to my TV.

I must admit I havent tried the updated driver release 11.02.2009.  I'll also do this tonight and post results.

---

### Post by oookkkooo on 2009-03-02
I just tried to install NVIDIA-Linux-x86-180.29-pkg1.run with no success. The install returned to error it seemed to compile but when I started gdm it switched to low-graphics and now I cant enable Extra visual effects.

Attached is the xorg.log file renamed to .txt so that I could upload it and the results from lshw and I am running 8.10 which is GREAT!!

I hope someone can help me.  I have just rebuilt all my machines with Ubuntu except one and I am trying to convert my girlfriend (hence the only win^*&^* left) and this performance isn't helping.

---

### Post by oookkkooo on 2009-03-07
Quick reply to say the new driver didnt solve the problem. Now I'm setting with ordinary graphics

---

### Post by iamkrazee on 2009-03-07
Give outputs of the following plz:

```
lspci | grep nv
```
```
uname -mr
```

---

### Post by iamkrazee on 2009-03-07
In my opinion, you´d want to upgrade your kernel first, and then use the modalias 177.

---

### Post by oookkkooo on 2009-03-08
lspci|grep nv returns nothing but lspci|grep nV returns 02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)


uname -mr returns 2.6.27-11-generic i686

Thanks for the advice.   I'll give your recommendations a try and post the results.

---

### Post by oookkkooo on 2009-03-25
I guess this means no one can help me.  :-(

---

### Post by orethrius on 2009-03-26
> **oookkkooo said:**
> Hi,

Thanks.  Would you like an lshw?  I'll do that when I get home.  

I downloaded and ran the  NVIDIA-Linux-x86-xxx.xx.xxx.run file but when it came to compiling the kernel (I dont know how to do that) **the script said could not find kernel headers** (if I remember correctly).  After wich I battled to get any sort of decent resolution beause this machine is connected to my TV.

I must admit I havent tried the updated driver release 11.02.2009.  I'll also do this tonight and post results.

I thought someone would notice the emphasized part, but apparently it went unnoticed.  Try this (the 'quotation mark' is a backtick, achieved on a QWERTY layout by pressing the ~ key without holding shift), then run that NVIDIA-*blahblah*.run file again:

```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by oookkkooo on 2009-04-17
Thanks,

This sudo apt-get install linux-headers-`uname -r`
gives me 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I rerean NVIDIA bla bla bla everything went fine but it keeps starting in low graphics mode.

---

### Post by oookkkooo on 2009-06-23
So now running with restricted drivers but still freezes.  I have noticed that the system only freezes when the card is propper use (e.g. playing movies or serious browsing) so I suspected it may have been the GPU overheating so I wrote a perl script to insert the output of nvidia-settings -q GPUCoreTemp into a SQLite database to examine the next time it freezes.  This is not the case.  I have removed all other cards from my machine and it still happens. 

Still in the dark

---

### Post by Meow27 on 2009-06-28
ok im having the same problem here. here are my specs

nvidia 7300 LE 

my system is a dell e521 (ubuntu jaunty)

-AMD athalon 3800+ X2
-(crashes in both ext4 and reiserfs)(ive been reinstalling jaunty a bunch of times >.>)

3GB RAM
and i cant think of anything else :/


so id like to point out that with the current graphics drivers, ubuntu will freeze completely within a matter of 2-15 minutes, depending on the usage, but usually just crashes because the system doesn't like the driver. (need *some* sort of excuse :P)

```
lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:08.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

``` ```
uname -mr
2.6.28-13-generic i686
```

help would be VERY much appreciated :3

---

### Post by Meow27 on 2009-06-28
lo and behold, i downloaded the latest driver directly from the nvidia site, followed this guide and im not crashing anymore :D

[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

---

