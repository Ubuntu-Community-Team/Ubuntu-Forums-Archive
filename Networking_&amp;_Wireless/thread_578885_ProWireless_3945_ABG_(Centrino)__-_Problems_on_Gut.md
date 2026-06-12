---
title: "Pro/Wireless 3945 ABG (Centrino)  - Problems on Gutsy Gibbon"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by gljubej on 2007-10-17
I Have a HP 6720s Laptop with Pro/Wireless 3945 ABG (Centrino) wireless card.
I have read that this card should be supported but I just cannot get it to work so I some help.

The card seems to be recognized as hardware, but it is not enabled or installed correctly.
I have tried turning it off and on with special button for that.

Here are the listings 

lshw -C network >>

```
  *-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1a:4b:6a:76:54
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=1.1-2 latency=0 link=no module=e1000 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945


```

 lspci

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

 iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

```

Please help me.

---

### Post by strategicpause on 2007-10-17
Bump.  Having the same exact issue with Intel 2200BG on a Dell Inspiron 9300.

---

### Post by strategicpause on 2007-10-17
I actually found a fix for the problem.  try sudo apt-get install linux-restricted-modules

---

### Post by gljubej on 2007-10-18
I tried installing restricteed modules and it still doesn't work.

When I open Restricted Drivers Management I can see that driver on the list, it is enabled but status is "Not in use".

What does that mean? How can I put it in use?

Somenone please help.
Thanks

---

### Post by mb0108 on 2007-10-18
I had many problems with the 3945ABG. Then I read a post to disable the ipw3945 driver and enable the iwl3945. Since then, wlan is working very well. 

Michael

---

### Post by gljubej on 2007-10-18
Can you please explain me how to do that.?
Thanks

---

### Post by VoodooRider on 2007-10-18
Yes, if you could post some instructions...I'd be very grateful !:)

---

### Post by gljubej on 2007-10-18
Guys, my problems are solved after I have downloaded the final version and installed it again.

Now everything works just fine.

---

### Post by mb0108 on 2007-10-18
For those who can not connect with WPA encryption with the 3945 look at this thread. This solved the issue for me. 
[http://ubuntuforums.org/showthread.php?t=579742](http://ubuntuforums.org/showthread.php?t=579742)

Michael

---

### Post by JackCrowley on 2007-10-20
> **strategicpause said:**
> I actually found a fix for the problem.  try sudo apt-get install linux-restricted-modules

Thanks.

That worked for me on a Toshiba Satellite A135.

BTW, By reverting to  Linux v 2.6.20.16 at boot , I was able to use my wireless for the purpose of downloading the linux restricted modules.

After downloading and installing I rebooted into 2.6.22.14 and things look fine.

This was my first Ubuntu upgrade. I went from Edgy to Feisty with a clean install.

I needed to shut off all but the basic repositories in order for the online upgrade to successfully fetch all the files. In doing so, I lost the linux restricted modules. 

Even with just the basic upgrade from the canonical repository, the online upgrade took quite a bit of time. For the rest of my machines I believe I will use the alternate CD approach.

---

### Post by Desiree on 2007-10-21
> **strategicpause said:**
> I actually found a fix for the problem.  try sudo apt-get install linux-restricted-modules

I tried this but at the end it said "E: Couldn't find package linux-restricted-modules"

I'm using PRO/Wireless 3945ABG Network Connection

I ran sudo lshw -C network, but I won't bother hand-typing it all unless someone lets me know I must for further support.  

iwconfig returned "no wireless extensions." for both lo and eth0.

My wireless worked fine on Fiesty just before the upgrade today.  Now wireless is not an option in the network manager.  When upgrading, I disabled third-party software and check box options other than "Canonical-supported Open Source software" and "Source code" in Software Sources.  I wasn't able to upgrade before doing this.  

I have absolutely no internet connection on that computer right now.  This is bad!  
I'd be ok with going back to the old kernel, but I'm not 100% what that means (back to Fiesty??) and no clue how to do it.  I just hear it's an option of sorts.  

Please advise!  I'm very lost, and there seems to be little hope of a fix without any internet connection.

:cry:

---

### Post by Desiree on 2007-10-21
I fixed it!!!  =D

I managed to find someone kind enough to let me use their wired internet.  From that point I was able to get all the repositories up and running, linux-restricted-modules, updates as prompted, ndiswrapper, and restarted my computer.  Then wireless was good to go.  

Sorry for the hasty post just before this one...  I was panicking. 

:guitar:

Gusty Gibbon is a go!

---

### Post by jpsolares on 2007-10-24
> **Desiree said:**
> I fixed it!!!  =D

I managed to find someone kind enough to let me use their wired internet.  From that point I was able to get all the repositories up and running, linux-restricted-modules, updates as prompted, ndiswrapper, and restarted my computer.  Then wireless was good to go.  

Sorry for the hasty post just before this one...  I was panicking. 

:guitar:

Gusty Gibbon is a go!
Nop that dosent fix the problem, u have also to install ubuntu-restricted-modules 22.14 rt(for real time kernel or generic u choose) <--something like that, also after, and after i dont know why but i think is a bug .... u have to cheeck dependencies with -ae after that it work like a charm, ubuntu-modules is to work with ipw3945 module.

PD:i did not install ndiswrapper, and have xubuntu, 7.10, 22.14 rt kernel

---

