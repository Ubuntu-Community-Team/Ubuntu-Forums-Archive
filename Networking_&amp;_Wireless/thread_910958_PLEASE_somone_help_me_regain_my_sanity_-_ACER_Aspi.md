---
title: "PLEASE somone help me regain my sanity - ACER Aspire ONE problem"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by dumpyloser on 2008-09-05
I have noticed that everyone has been having problems with the wireless cards. I just installed ubuntu today and I've never really "used" linux more that just piddling with it in the past. I've learned a lot by trying to get this darn wireless card working! I've tried every madwifi tutuorial I can find and every NDISWRAPPER tutorial I can find. I'm struggling for ideas! I've tried everything I can think of. 

My status as of now:

1.) is showing up in the system>administration>hardware drivers program
At first, there was 2 of them and they were enabled. now, after all I've done I can't get them to come back. (and I'm not sure if i even need to)

2.)Iwconfig reads: 
lo        no wireless extensions.

eth0      no wireless extensions.

3.) when using NDISWRAPPER the hardware present has always read no. I have tried 2-3 different windows drivers.

4.) I have the AR5BXB63 card.

that's about all I can think to include right now. 

if any info will help you folks pinpoint the problem, let me know and I'll get it.... I just may need some help finding it haha.


thanks in advance for your help folks!

---

### Post by dumpyloser on 2008-09-05
and btw, I'm using 8.04

---

### Post by dumpyloser on 2008-09-05
the results of lshw -C network are:

ryan@ryan-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:b8:1f:90
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.6 latency=0 module=r8169 multicast=yes



2 things of interest for me are there is only an ether net interface listed and no wireless, AND the width is 64 bits instead of 32 and i have a 32 bit system

---

### Post by Crafty Kisses on 2008-09-05
Also post results of this command: ```
iwconfig

```

---

### Post by dumpyloser on 2008-09-05
I posted the results of iwconfig in my original post, but here they are again!


ryan@ryan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ryan@ryan-laptop:~$ 




I now have a yes on 2 different drivers in windows wireless drivers. Still no radio broadcasting out and kwifimanager reads: Not Connected

system>admin> hardware drivers now lists two wireless drivers but I have them uninstalled

ifconfig now reads:
ryan@ryan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:b8:1f:90  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:feb8:1f90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:407 errors:0 dropped:1961118890 overruns:0 frame:0
          TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:476538 (465.3 KB)  TX bytes:57349 (56.0 KB)
          Interrupt:219 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74700 (72.9 KB)  TX bytes:74700 (72.9 KB)

ryan@ryan-laptop:~$ 

lshw -C Network now reads:

ryan@ryan-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:b8:1f:90
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.6 latency=0 module=r8169 multicast=yes
  *-network
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
ryan@ryan-laptop:~$ 
ryan@ryan-laptop:~$ 


I've made some progress ( i think), but I'm still stuck!

---

### Post by dumpyloser on 2008-09-05
sudo ifconfig returns:

ryan@ryan-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:b8:1f:90  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:feb8:1f90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1574 errors:0 dropped:4286350064 overruns:0 frame:0
          TX packets:1347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1925679 (1.8 MB)  TX bytes:187701 (183.3 KB)
          Interrupt:219 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74700 (72.9 KB)  TX bytes:74700 (72.9 KB)

ryan@ryan-laptop:~$

---

### Post by dumpyloser on 2008-09-05
bump for anyone who can help.


I just can't figure this out :(:confused:

---

### Post by 9krpmrx8 on 2008-09-05
Reinstall XP.

---

### Post by dumpyloser on 2008-09-05
what will that solve?

---

### Post by 9krpmrx8 on 2008-09-05
Your computer would work and you would regain your sanity.  I tried Ubuntu and I think its great but i could never get it to work on my laptop.

---

### Post by dumpyloser on 2008-09-06
oh. lol. I still have xp lol... dual boot.


I just like ubuntu better! the only thing that I can't figure out is the wireless deal AND now with beryl I can't figure out how to get emerald themes to work, but that is a non-issue right now.



any advice folks?

---

### Post by dumpyloser on 2008-09-06
bump for good advice

---

### Post by mikespug on 2008-09-06
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

This website is updated regularly as new fixes/tweaks are discovered for the ONE.  There is a solution listed for the wireless card.  You should also know that the next distro of ubuntu uses the 2.6.27 kernel which has the wireless drivers built and will negate the need for any modifications.

Onelinux.org is working on a "custom" ubuntu distro with all tweaks/modifications built in.  Check there in the near future.

---

### Post by twoflatfish on 2008-09-06
I have successfully installed ubuntu on my Aspire-1. Go to this site for full instructions. I have read that Ubuntu 8.10.1 is necessary so that may be your problem. 
Cheers
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)



> **dumpyloser said:**
> I have noticed that everyone has been having problems with the wireless cards. I just installed ubuntu today and I've never really "used" linux more that just piddling with it in the past. I've learned a lot by trying to get this darn wireless card working! I've tried every madwifi tutuorial I can find and every NDISWRAPPER tutorial I can find. I'm struggling for ideas! I've tried everything I can think of. 

My status as of now:

1.) is showing up in the system>administration>hardware drivers program
At first, there was 2 of them and they were enabled. now, after all I've done I can't get them to come back. (and I'm not sure if i even need to)

2.)Iwconfig reads: 
lo        no wireless extensions.

eth0      no wireless extensions.

3.) when using NDISWRAPPER the hardware present has always read no. I have tried 2-3 different windows drivers.

4.) I have the AR5BXB63 card.

that's about all I can think to include right now. 

if any info will help you folks pinpoint the problem, let me know and I'll get it.... I just may need some help finding it haha.


thanks in advance for your help folks!

---

### Post by khourianya on 2008-09-07
I had the same issues as you are having and finally decided to just reinstall Linpus again and wait the month for 8.10.  I figured that the Aspire One is still pretty new and it will take some some time for the support to be in place so rather than fighting it, I can wait a month and have a much easier time of it.

It's not that long...and, while sure i had wired connection - what's the point of having a netbook if it isn't wireless.

now...if only I could get my resolving dependencies issue on linpus solved...

(and it is 8.04.1 that has the atom support in it - I don't think there is an 8.10.1 yet)

---

### Post by twoflatfish on 2008-09-07
Ubuntu V 8.04.1 works on Aspire-1... but wireless network card drivers have to be installed. Newer version due out very soon will have the drivers built in I believe.

---

### Post by thinkpadx60 on 2008-09-26
I Installed Ubuntu 8.10.1 alpha 6 on My aspire one last night (Using Unetbootin ,I created a Bootable flash drive)  , I then hooked a Network cable to it and downloaded over 300 MB of updates.. after installing ALL the Updayes I disconected the Cable and rebooted ... WiFi Works Great (No Additional Drivers Needed), Touchpad works great, Video Works Super..  I'll check out the Mike & Camera This weekend after I install a 60 GB PATA drive to replace the SSD .

---

### Post by poldie on 2008-09-30
> **mikespug said:**
> [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

This website is updated regularly as new fixes/tweaks are discovered for the ONE.  There is a solution listed for the wireless card.  You should also know that the next distro of ubuntu uses the 2.6.27 kernel which has the wireless drivers built and will negate the need for any modifications.

Onelinux.org is working on a "custom" ubuntu distro with all tweaks/modifications built in.  Check there in the near future.

That link suggests getting 8.4.1, which I got, but that doesn't solve the wifi problem - my connection is very sporadic and when I do get it working (by manually attempting to connect loads of times and fiddling around with options and the switch on the front) it only works for a while and doesn't survive a reboot.  Say what you like about Linpus, but the wifi there is solid.  I prefer Ubuntu, but this inability to get online (using wifi) is driving me crazy!

---

### Post by Davsdu on 2008-10-09
> **poldie said:**
> That link suggests getting 8.4.1, which I got, but that doesn't solve the wifi problem...

Did you try with the Ubuntu 8.10 beta version? Apparantly, as stated above, sufficient drivers are included with Intrepid Ibex and so your wi-fi should work without too much (if any) hassle. I´m asking since I´ve just purchased my own Aspire One A150 and am eager to know whether the wi-fi works out of the box with the latest Ubuntu release. Thank you.

---

