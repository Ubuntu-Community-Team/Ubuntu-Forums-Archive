---
title: "System very slow"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by cjnappoly on 2009-08-02
Hi,
i loaded Ubuntu 8.04 Lts on my Celeron 1200Mhz 40Gb 512Mb SD RAM (Freq 133). But the response time for the system is very slow. the system takes time even to scroll up n dwn the mouse. My swap is 1 Gb. Even the firefox pages take time to load though i hav a broadband connection. 
the "top" command showing the running processes always shows that the CPU resources are being heavily drained and consumes around 60%. 
Synaptic package manager shows that there are 1190 installed packages out of around 25,000 packages. The "top" command in terminal shows that there are 90 sleeping processes and 2 running processes when i have only firefox and one terminal running with "top" command and the CPU shows 72% consumption.
Can anyone help me out with this prob.

Thnx 

cjnappoly

---

### Post by cariboo on 2009-08-02
Does top tell which package is using all you resources?

---

### Post by CLomax on 2009-08-02
Firefox is a hungry fox.

Is your system slow with Firefox closed? If so, it would be best to try another browser. There are quite a few in the repos like Midori and Epiphany which are rather good.

---

### Post by wpshooter on 2009-08-02
You have something running (that is probably NOT necessary) that is taking up your CPU resources.

Just go to System/Administration/System Monitor and then go to the PROCESSES tab and then sort on the CPU header, so that it shows you the process that is taking up the greatest amount of the CPU resources.  Then research what those process(s) are and see if they are something that you do NOT need to be running.

---

### Post by sydbat on 2009-08-02
If you have desktop effects enabled (compiz), try shutting them off and see if things are speedier.

---

### Post by cjnappoly on 2009-08-04
top shows around 90 applications running and the system resources being consumed by around 2 or 3 applications though i it keeps updating very frequently sometimes it shows 6 application, mainly Xorg consumes high resources. Firefox works very fine when no other applications are running but when other applications like acrobat reader9 , open office 3.0 are opened performances are affected.
Thanx

---

### Post by cjnappoly on 2009-08-04
though compiz is installed (as shown in the package manager) it is not activated.
Thnx

---

### Post by cjnappoly on 2009-08-04
though its a doubt - does ubuntu 8.04 Lts hav a i386 installation also? the type that is loaded on my PC is i686. will that affect the performance.
Thnx

---

### Post by wpshooter on 2009-08-04
> **cjnappoly said:**
> though its a doubt - does ubuntu 8.04 Lts hav a i386 installation also? the type that is loaded on my PC is i686. will that affect the performance.
Thnx

Is your computer 32bit or 64bit ?

My "guess" is 32bit.  In which case, I think that you have installed the wrong version !!!

---

### Post by halitech on 2009-08-04
> **cjnappoly said:**
> though its a doubt - does ubuntu 8.04 Lts hav a i386 installation also? the type that is loaded on my PC is i686. will that affect the performance.
Thnx

i386 is simply the class for 32bit systems. I486 (486 based computers), i586 (early P1 computers), i686 (later Pentium computers) is simply the natural progression of the systems. Basically i386 will run on any 386 computer and up. The i686 kernel was designed to take advantage of the faster processors.

[http://en.wikipedia.org/wiki/Intel_80386](http://en.wikipedia.org/wiki/Intel_80386)

[http://en.wikipedia.org/wiki/I686](http://en.wikipedia.org/wiki/I686)

---

### Post by cjnappoly on 2009-08-05
as i said earlier my system has a Celeron processor 1200 Mhz and is a 32 bit system and i hav installed the ubuntu 8.04 Lts which is i686.........in which case kindly tell me whether is there a ubuntu 8.04 Lts for i386 installation?
the celeron system that i hav is some equivalent to Pentium III.....i dont know quite... may be i am wrong.
Further i made the ubuntu CD from the official site which had a link for 9.04 version and another link for 8.04LTS,,,having downloaded the iso from that site i installed ubuntu on my PC which loaded the i686 version automatically. the site did not specify that the download is for i686,,,,maybe ubuntu thinks that whoever downloads has a up-to-date system!!!!
So...Should i remove the ubuntu 8.04 LTS i686 installation from my system and try and download ubuntu 8.04 lts i386(if such a download exists for i386???)
Pls advice
 
Thnx

---

### Post by halitech on 2009-08-05
the Celeron processor you have would be in the i686 class so when you downloaded and installed the x86 version, it detected your processor and installed the best kernel to operate on your system so no need to wipe out your current install and install anything else.

Instead it would be better to figure out what processes are running and see if we can help you trim down the usage to get you a better running system.

Open a terminal and post the results of the following commands.

```
free -m
```
```
mount
```
```
top
```
after running top, press CTRL + Z to exit it so you can copy and paste the results.

---

### Post by 3rdalbum on 2009-08-05
> **cjnappoly said:**
> as i said earlier my system has a Celeron processor 1200 Mhz and is a 32 bit system and i hav installed the ubuntu 8.04 Lts which is i686.........in which case kindly tell me whether is there a ubuntu 8.04 Lts for i386 installation?

So...Should i remove the ubuntu 8.04 LTS i686 installation from my system and try and download ubuntu 8.04 lts i386(if such a download exists for i386???)
Pls advice
 
Thnx

No, there's only Ubuntu 32-bit and Ubuntu 64-bit. The 32-bit disc is the correct one for you.

What graphics card, or integrated graphics, do you have? Have you looked in the Hardware Drivers program to see if you can install a graphics driver? If Xorg stayed near the top of the "top" list that's the first thing I'd check.

---

### Post by Tux118 on 2009-08-05
> **cjnappoly said:**
> top shows around 90 applications running and the system resources being consumed by around 2 or 3 applications though i it keeps updating very frequently sometimes it shows 6 application, mainly Xorg consumes high resources. Firefox works very fine when no other applications are running but when other applications like acrobat reader9 , open office 3.0 are opened performances are affected.
Thanx

Firefox, Open Office, and acrobat readers are RAM hogs. Sorry but your computer has no choice but to be slow when you have them all running.

---

### Post by cjnappoly on 2009-08-05
when the Hardware Drivers program is opened it shows a blank ---- no non proprietary drivers loaded.
Maybe that opening multiple windows slows down my system----no idea.
As far as top is concerned Xorg does not stay on top always,,,,the processes keep refreshing sometimes Xorg consumes 3% CPU and the next refresh cycle i see that Xorg is hogging 40% CPU.
yes 32 bit is the right one for me,,,,but when i open Ubuntu tweak the system shows that Ubuntu i686 is installed.
i will try n post the results of the commands soon,,,,,.
thanx

---

### Post by LunaticHiatus on 2009-08-05
If you want the maximum in speed, why not do a minimal install? It will get you up to command line. in which case all you have to do is type in sudo aptitude install x lxde synaptic firefox abiword htop and WICD (for wireless) (anything else you want you can get from synaptic) and you will have absolutely the lightest and fastest desktop around. thats what I use anyhow...

oh yeah, you also need to install gtk (what gnome uses) for WICD to show a gui for WICD. No big deal.

---

### Post by halitech on 2009-08-05
ok, if nothing shows in hardware drivers then there are no proprietary drivers for your video. Doesn't tell us what card you have though. Open a terminal and post the results of ```
lshw -C video
```

the more programs you have running the more CPU cycles it is going to take and the more ram you are going to use.

32bit is the generic term for any version of the x86 family (ie, i386, i486, etc)

---

### Post by cjnappoly on 2009-08-17
> **halitech said:**
> ok, if nothing shows in hardware drivers then there are no proprietary drivers for your video. Doesn't tell us what card you have though. Open a terminal and post the results of ```
lshw -C video
```the more programs you have running the more CPU cycles it is going to take and the more ram you are going to use.

32bit is the generic term for any version of the x86 family (ie, i386, i486, etc)

hi,
as you said the results of the code is 
cjnappoly@Ubuntu8:~/Desktop$ lshw -C video
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade/i1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 6a
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=32
cjnappoly@Ubuntu8:~/Desktop$ 

sorry for the late response as i was traveling (onboard my ship internet facility is a bit bad)
Thnx

---

### Post by cjnappoly on 2009-08-17
> **halitech said:**
> the Celeron processor you have would be in the i686 class so when you downloaded and installed the x86 version, it detected your processor and installed the best kernel to operate on your system so no need to wipe out your current install and install anything else.

Instead it would be better to figure out what processes are running and see if we can help you trim down the usage to get you a better running system.

Open a terminal and post the results of the following commands.

```
free -m
``````
mount
``````
top
```after running top, press CTRL + Z to exit it so you can copy and paste the results.

hello,
as you had asked - the results of the codes are pasted below:

cjnappoly@Ubuntu8:~/Desktop$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        486          8          0         12        146
-/+ buffers/cache:        327        167
Swap:         1029         40        988
cjnappoly@Ubuntu8:~/Desktop$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/cjnappoly/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cjnappoly)
cjnappoly@Ubuntu8:~/Desktop$ top

top - 08:26:11 up 36 min,  3 users,  load average: 2.28, 1.57, 1.11
Tasks:  96 total,   2 running,  93 sleeping,   1 stopped,   0 zombie
Cpu(s): 94.4%us,  5.3%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    507448k total,   500820k used,     6628k free,    12120k buffers
Swap:  1054116k total,    41760k used,  1012356k free,   157924k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5191 cjnappol  20   0  224m 101m  24m S 49.5 20.5   6:21.35 firefox            
 4668 root      20   0 36116  18m 8536 R 33.9  3.7   7:01.84 Xorg               
 5289 root      20   0 51680  38m  22m S 12.3  7.8   3:36.10 synaptic           
 5181 cjnappol  20   0 91836  68m  12m S  1.0 13.7   0:28.98 update-manager     
 5032 cjnappol  20   0 26300  13m 9260 S  0.7  2.8   0:12.64 update-notifier    
 5359 root      20   0  5100 1852 1592 S  0.7  0.4   0:06.24 http               
 5360 root      20   0  5100 1856 1592 S  0.7  0.4   0:03.52 http               
 5452 cjnappol  20   0 75640  20m  10m S  0.7  4.2   0:11.26 gnome-terminal     
    1 root      20   0  2844 1688  544 S  0.0  0.3   0:02.10 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.26 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             

[2]+  Stopped                 top
cjnappoly@Ubuntu8:~/Desktop$ 


Thnx

---

### Post by halitech on 2009-08-18
this may help for the video

```
gksudo gedit /etc/X11/xorg.conf
```

and make it look like this
[http://ubuntuforums.org/showpost.php?p=7742459&postcount=3](http://ubuntuforums.org/showpost.php?p=7742459&postcount=3)

I have almost the same setup with my laptop (Toshiba Satellite 1800) and I've only got 256meg of ram. Its showing you have 495 (512 - your onboard video). As thought before, firefix is killing you with using almost half your ram when it is running. You could try a lighter browser (Opera seems to be pretty good) and as well, Xorg is using a fair bit. Making the change in the Xorg conf file may help with that some as well.

the other option would be to install a lighter DE or distro of linux. Since you have 8.04 installed, you could try
```
sudo apt-get install xubuntu-desktop
```
and use the XFCE DE instead. It was still fairly light back in 8.04 and may run better. I know right now with you being on a ship it may not be the best time to try and download alot so for now you may want to live with the slowness and change when you get back to shore.

If you want something lighter still, you could try the instructions here to install Debian with the XFCE DE
[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by cjnappoly on 2009-08-21
hi
am back on land now!!
hav been reading thru the internet regarding this issue of mine....and in fact there has been lot of **unhappiness over the graphics drivers that ubuntu 9,04 and 8.04 has been shipped with**...dont know if that could be a problem with my PC.
Can be found here
[http://www.h-online.com/open/Updated-graphics-drivers-for-Ubuntu-9-04--/news/113261](http://www.h-online.com/open/Updated-graphics-drivers-for-Ubuntu-9-04--/news/113261)
i tried loading the visual effects (Normal) as well (Extra) which i believe runs Comfiz package???
But i could not activate the visual effects as it said "**Searching for Drivers**" and then the **screen flickered for sometime** and then the message said "**Desktop effects could not be enabled"**
further there are **no proprietory drivers loaded in my system**...
By the way i did a fresh installation of Ubuntu 9.04 also on my system wiping out completely Ubuntu 8.04 and also converting the file system to ext4!!!!!!!!
But nothing seems to be working,,,,am still confident that some help would come my way.
The **page scrolling in Firefox and acrobat seems to take ages but the booting is extreemly fast...**

Finally could it be the video graphics problem???

I did post the results of the code 
**lshw -C video**

which is as below:::::


cjnappoly@Ubuntu8:~/Desktop$ lshw -C video
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade/i1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 6a
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=32
cjnappoly@Ubuntu8:~/Desktop$ 

Hope i get a solution...

Thnx

---

### Post by halitech on 2009-08-21
if you had an ATI or Intel video card, then maybe but you don't, you have a Trident video card. Did you try using the settings from my post on the previous page to configure xorg.conf?

As far as compiz goes, check out here to see if ti will run compiz
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

