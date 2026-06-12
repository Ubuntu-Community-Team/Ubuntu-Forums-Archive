---
title: "Need help setting up wireless on laptop"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by Mostlyharmless42 on 2008-03-30
I just got a new HP pavilion dv6700 and I've installed ubuntu 8.04 with WUBI.  So far i've gotten no luck with the wireless on the computer.  Quite frankly i'm not sure were to get the info i need.  It gets internet thru the ethernet port easily.  However i don't even know if it sees my wi-fi card at all.  The first thing i need to know how to do is finding the hardware info on the wifi card.  After that i assume i'll need a driver, the restricted driver manager hasn't detected anything.  Hopefully someone out there can help me out.  Thanks in advanced.

---

### Post by abhilashkumar on 2008-03-31
Try this post

[http://ubuntuforums.org/showpost.php...5&postcount=36](http://ubuntuforums.org/showpost.php...5&postcount=36)

:)

---

### Post by Mostlyharmless42 on 2008-03-31
...link just sends me to forum home page...

---

### Post by jonwop on 2008-03-31
Your right once you find out the info on what wireless card you have you will need the drivers. Could it be listed in the books that came with your laptop?

---

### Post by heyho on 2008-03-31
Open up a teminal, and type lspci, this should display a list of the hardware in your system, amongst which you will hopefully find your wirless card.

---

### Post by Mostlyharmless42 on 2008-03-31
Thanks that was the command i was looking for.  This is what it gave me...

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

Now I need help figuring out why it won't work.

---

### Post by Mostlyharmless42 on 2008-03-31
I've looked around for a driver for this card and have yet to find anything.  Does anyone know where i can get the driver.  It isn't being detected by the restricted drivers manager like my card on my other computer is...:(:confused:

---

### Post by kevdog on 2008-03-31
Broadcom 4328 isnt supported by the restricted drivers package -- gotta go ndiswrapper.

---

### Post by Mostlyharmless42 on 2008-03-31
ok, tried installing ndiswrapper and got this error during make install

```
jred42@jred42-laptop:~/ndiswrapper/ndiswrapper-1.48$ sudo make install
make -C driver install
make[1]: Entering directory `/home/jred42/ndiswrapper/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.24-12-generic SUBDIRS=/home/jred42/ndiswrapper/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-12-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/jred42/ndiswrapper/ndiswrapper-1.48/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/jred42/ndiswrapper/ndiswrapper-1.48/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/jred42/ndiswrapper/ndiswrapper-1.48/driver'
make: *** [install] Error 2
jred42@jred42-laptop:~/ndiswrapper/ndiswrapper-1.48$ 

```

---

### Post by kevdog on 2008-03-31
What instructions did you follow?? Might want to try the latest ndiswrapper version which is 1.52..

---

### Post by Mostlyharmless42 on 2008-03-31
one last thing,

I'm only doing this on ubuntu because i can install it on wubi so that if it doesn't work, i won't have a partition taking up space.  When i get this to work, i'll probably install linux mint on a normal partition.  Will this be any easier to do with linux mint???

---

### Post by kevdog on 2008-03-31
Linux Mint is basically Ubuntu with a couple more features.  Wireless to the best of my knowledge should be the same, however Ive never really worked with Mint.  I have no reason to suspect it to be any different however.

---

### Post by Mostlyharmless42 on 2008-04-01
> **Mostlyharmless42 said:**
> ok, tried installing ndiswrapper and got this error during make install

```
jred42@jred42-laptop:~/ndiswrapper/ndiswrapper-1.48$ sudo make install
make -C driver install
make[1]: Entering directory `/home/jred42/ndiswrapper/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.24-12-generic SUBDIRS=/home/jred42/ndiswrapper/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-12-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/jred42/ndiswrapper/ndiswrapper-1.48/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/jred42/ndiswrapper/ndiswrapper-1.48/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/jred42/ndiswrapper/ndiswrapper-1.48/driver'
make: *** [install] Error 2
jred42@jred42-laptop:~/ndiswrapper/ndiswrapper-1.48$ 

```

Does anyone have any ideas as to what caused this error?

---

### Post by Mostlyharmless42 on 2008-04-01
> **kevdog said:**
> What instructions did you follow?? Might want to try the latest ndiswrapper version which is 1.52..

Sorry I didn't see that post.  However the problem turned out to be that i already had it installed.  I then went ahead and installed ndisgtk which is a GUI for ndis.  Now my problem is that it want's the .inf file.  I have no clue where to get it.  I got this file from the hp website. [ftp://ftp.hp.com/pub/softpaq/sp38501-39000/sp38764.exe]("ftp://ftp.hp.com/pub/softpaq/sp38501-39000/sp38764.exe")  It is the .exe for the windows driver.  Where do i get the .inf????

---

### Post by kevdog on 2008-04-01
You either need to extract it on a windows box, or you need to install the cabextract utility (need an internet connection to do this):

sudo aptitude install cabextract
cabextract ******.exe

---

### Post by Mostlyharmless42 on 2008-04-02
Ok, so i started over using your guide for installing ndiswrapper.

I think i'm having a problem.

i used ifconfig to see if my wireless was being lable wlan0, this is my output

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:34:da:1c  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe34:da1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1837 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2406282 (2.2 MB)  TX bytes:320591 (313.0 KB)
          Interrupt:20 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7700 (7.5 KB)  TX bytes:7700 (7.5 KB)

```

What concerns me is that there is no indication of my wireless card.  eth0 is my normal wired connection. 

After that i went on to the next step which was to get the lshw -C network output.  Mine was as follows.

```
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1e:68:34:da:1c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.105 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

```

Now as i understand it this step was to get the MAC code for my card so i can assign its logical name to being wlan0.  I can see the MAC code and logical name of my ethernet card, but the sections of the output for my wireless card gives me no MAC code or logical name.  I don't know if maybe this is a sign that i did something wrong in an earlier step.  My main question is...What do i do now?

---

### Post by kevdog on 2008-04-02
This is the driver you are using:

b43-pci-bridge

Are you using hardy?  Seems like this is the wrong driver.  You can confirm by typing dmesg and looking for relative sections related to the loading of your wireless driver.

---

