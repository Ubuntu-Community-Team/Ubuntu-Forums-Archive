---
title: "50% CPU Usage on Desktop on 2.7ghz processor"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by ALoneWolves on 2009-02-15
Hey, I'm getting around 50% cpu usage on my desktop, not sure what is using it all.

Is there some command I type in the terminal so I can get a log and post here so you can all help diagnose it?

Also entirely unrelated, I'm using both Pidgin and Steam (through Wine) for my IM conversations. How do I get the minimised window in the panel to flash if someone is talking to me? Also is this possible in Avant Window Manager?

Finally how do I delete all the install packages I've download, and check free disk space?

Thanks.

---

### Post by betterhands on 2009-02-15
> **ALoneWolves said:**
> Hey, I'm getting around 50% cpu usage on my desktop, not sure what is using it all.

Is there some command I type in the terminal so I can get a log and post here so you can all help diagnose it?

Also entirely unrelated, I'm using both Pidgin and Steam (through Wine) for my IM conversations. How do I get the minimised window in the panel to flash if someone is talking to me? Also is this possible in Avant Window Manager?

Finally how do I delete all the install packages I've download, and check free disk space?

Thanks.

open the system monitor and take a look: System--> Administration--> System Monitor.  sort by cpu and see what's up.

btw--pidgin runs great native in ubuntu without wine.

---

### Post by ALoneWolves on 2009-02-15
I think it is Gnome system monitor using it all up, it averages around 10% but when I change windows or tabs it spikes up to over 30%.

Also using my mouse scroll wheel seems to take it up into the 90%, or just scrolling a website normally using the arrows. Any quick actions seem to cause major spikes.

---

### Post by betterhands on 2009-02-15
> **ALoneWolves said:**
> I think it is Gnome system monitor using it all up, it averages around 10% but when I change windows or tabs it spikes up to over 30%.

Gnome System Monitor is the app you just opened to take a peek--it's not using cpu when you close it.  when it first opens it's likely hitting the cpu a little, but it should settle down after a bit.  after sorting by cpu, what are your other top offenders other than the system monitor?

---

### Post by ALoneWolves on 2009-02-15
It's really weird, while I'm just idling in any program it goes right down, but the moment I move my mouse, change songs, open tabs, open windows or anything like that it spikes right up.

I just sat their with the monitor open, it was on around 8% but I just started moving my mouse quickly in circles and it jumped up to over 30%.

All the other offenders seem to be using reasonable amounts, music player/steam are using around 5% each.

---

### Post by Pollox on 2009-02-15
In regards to checking free disk space, go to Applications >> Accessories >> Disk Usage Analyzer.

---

### Post by betterhands on 2009-02-15
not sure why it would be around 30%--perhaps someone more familiar with desktop issues will contribute.

---

### Post by ALoneWolves on 2009-02-15
Gahh, my computer just changed songs and it spikes up to over 90% for less than half a second, this is getting annoying.

---

### Post by sdennie on 2009-02-16
> **ALoneWolves said:**
> Gahh, my computer just changed songs and it spikes up to over 90% for less than half a second, this is getting annoying.

Why is this annoying?  Spiking to 90% usage for half a second seems fairly normal to me for an older CPU.  A newer CPU spikes to 100% too.  Just for a shorter period of time.  Having your CPU/Core spike to 100% is normal, expected and makes your machine more responsive.  Having said that, if you are seeing something that looks like a performance problem, that's a different matter but, high CPU usage isn't inherently bad.

As for gnome-system-monitor taking a lot of CPU, that's a bug that has existed in gnome-system-monitor since beta releases of Hardy (so, over a year).  It's gotten better but, it's still a bug.  Don't rely on any information in gnome-system-monitor.  Use htop in a terminal instead.

To clean out your cached packages use:

```

sudo apt-get autoremove

```

---

### Post by betterhands on 2009-02-16
i agree--those spikes are normal--you *want* your software to use the resources available to it...as long as you're not taking unreasonable performance hits in terms of application response.

---

### Post by Sealbhach on 2009-02-16
I agree, my CPU spikes up over 90% when opening applicayions, but it's only for a second or two so that's fine. 


.

---

### Post by durand on 2009-02-16
I've had that scrolling problem before when ubuntu wasn't using my graphics card properly. Try installing the graphics drivers for your card. If you're in any doubt, type lspci in a terminal (Applications/Accessories/Terminal) and post the output here.

I can't say I have the same problem with songs changing. I've never seen spikes like that and I have a fairly old computer as well.

---

### Post by van_002 on 2009-05-04
I have that scrolling issue.

That applies to all the system.    I just don't know how to fix this grphic issue.

The lspci output for my pc is:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)


Hope you can help me.

Thanks in advance.

---

### Post by van_002 on 2009-05-04
In my situation the cpu usage is of 20% when there is anything working (except the default things).
Every time that I perform any action the CPU 1 usage goes to 90% or +   so this K.O. everything :(

---

### Post by Kevbert on 2009-05-04
To check what's using the processor and memory you can use the command
```
top
```
in terminal. To exit press q.
How much memory do you have ? Increasing it may also help.

---

### Post by van_002 on 2009-05-04
I have 2.5Gh   and in Ubuntu 8.10 everithing works fine.   Also 1.0Gb RAM

Should work fine.........

---

### Post by van_002 on 2009-05-04
I mean,  in Ubuntu 8.10 the all systems was excelent, that's why I decide to change the OS to Ubuntu. But in 8.10 the ehternet connection was unable to connect so I update to 9.04 witha CD-Rom and now this issue....  :(
I believe that is a driver issue, but i just don't know how to configure it properly.

---

### Post by byenary on 2009-05-04
sudo apt-get install htop

and run htop
even nicer than top

---

### Post by van_002 on 2009-05-04
thanks for that.   I can se the problem clearly now.
When I scroll for example,    the CPU 1 reaches the 100% and swith to the CPU2 and then the 2 reaches 100% and changes to the 1 and so on.

Always the CPU usage (the exsessive one) is from the root with the "Command" :

/usr/X11R6/bin/X

When I do anithing the usage of that command goes up to 90% or + (sometimes a little less than 90 but is still too high)

---

### Post by van_002 on 2009-05-04
PLease if anyone can take a look at this:

horacio@horacio-desktop:~$ cat /proc/sys/vm/swappiness
60
horacio@horacio-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        896856     412844     484012          0      30276     190732
-/+ buffers/cache:     191836     705020
Swap:            0          0          0
horacio@horacio-desktop:~$ cat /proc/sys/vm/swappiness
60
horacio@horacio-desktop:~$ sudo fdisk -l

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x46a646a5

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       31870   204796620    f  W95 Ext'd (LBA)
/dev/sda3           31871       37471    44990032+  83  Linux
/dev/sda4           37472       38913    11582865   82  Linux swap / Solaris
/dev/sda5            6375       31870   204796588+   7  HPFS/NTFS


The swap disk is not working I guess, but how can I make it work????

Please if someone know ....

---

### Post by LowSky on 2009-05-04
> **van_002 said:**
> I have 2.5Gh   and in Ubuntu 8.10 everithing works fine.   Also 1.0Gb RAM

Should work fine.........

> **van_002 said:**
> PLease if anyone can take a look at this:

```
horacio@horacio-desktop:~$ cat /proc/sys/vm/swappiness
60
horacio@horacio-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        896856     412844     484012          0      30276     190732
-/+ buffers/cache:     191836     705020
Swap:            0          0          0
horacio@horacio-desktop:~$ cat /proc/sys/vm/swappiness
60
horacio@horacio-desktop:~$ sudo fdisk -l

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x46a646a5

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       31870   204796620    f  W95 Ext'd (LBA)
/dev/sda3           31871       37471    44990032+  83  Linux
/dev/sda4           37472       38913    11582865   82  Linux swap / Solaris
/dev/sda5            6375       31870   204796588+   7  HPFS/NTFS
```

The swap disk is not working I guess, but how can I make it work????

Please if someone know ....

Also your 2.7 Ghz processor means nothing. Infact clock speed means absolutly nothing these days. Maybe 5-7 years ago, but today it means nothing. Today we worry about cache, chipsize, transistors, and FSB, not GHZ.

You dont need swap as much as you might think, you have more than enough RAM, what you have is a graphics issue and because you use SiS graphics your up a creek without a paddle. 

Make sure all gaphics effects are off (system> Appearance> desktop effects).

---

### Post by van_002 on 2009-05-04
Everithing is off, as a matther of fact.  I'm not allowed to activate any effects.

---

### Post by LowSky on 2009-05-04
type top and show results, and please use CODE tags, If you go advance in the reply menu they are the option that looks like this symbol **#**

---

### Post by van_002 on 2009-05-04
Here it is the result for TOP:

```
    
 3067 horacio   20   0  216m  83m  26m S    2  9.5   0:56.54 firefox            
    1 root      20   0  1908  780  564 S    0  0.1   0:01.07 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0            
   13 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/1            
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
   16 root      15  -5     0    0    0 S    0  0.0   0:00.01 kblockd/0   
```

---

### Post by van_002 on 2009-05-04
Every time I do something the Xorg command goes up to 90% or +

The command that is displayed in the htop is us/XR11/bin/X (That will be the Xorg command displayed in the "top")

---

### Post by van_002 on 2009-05-04
This is displayed during an action in the "top":

```
       
 2502 root      20   0  163m  25m 7928 R   95  2.9   2:39.56 Xorg               
 3067 horacio   20   0  216m  83m  26m S    7  9.5   1:18.14 firefox            
 2942 horacio   20   0 19924  10m 8288 S    0  1.2   0:00.90 metacity           
 3594 horacio   20   0  2448 1184  912 R    0  0.1   0:00.18 top                
    1 root      20   0  1908  780  564 S    0  0.1   0:01.07 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.05 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0            
   13 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/1       
```


In the first line take a look at the "95" in the CPU%usage

---

