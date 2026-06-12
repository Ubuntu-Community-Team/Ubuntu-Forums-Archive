---
title: "wired Internet but No wireless"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by Augie1944 on 2010-06-15
I am a newbie and need help with making wireless connection to Internet.  In Windows Vista I have no problem with wireless to my network using my notebook.  I have a Dell notebook and a Linksys router WRT160N. After reading some threads, I used the Terminal to get:

ecil@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:ce:7d:cc  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:9bff:fece:7dcc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46347336 (46.3 MB)  TX bytes:1677118 (1.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1904 (1.9 KB)  TX bytes:1904 (1.9 KB)

and
cecil@ubuntu:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:ce:7d:cc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 03
       serial: 00:1e:4c:c7:58:cf
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:fe7fc000-fe7fffff memory:f0000000-f00fffff(prefetchable)

Does anyone have any suggestions on what I should do?
Thanks so much

---

### Post by ieee488 on 2010-06-15
you had it working 3 months ago
[http://ubuntuforums.org/showthread.php?t=1437176&highlight=BCM4328](http://ubuntuforums.org/showthread.php?t=1437176&highlight=BCM4328)

what happened???

---

### Post by Augie1944 on 2010-06-16
Yes, I did, but I had to reinstall my C drive image due to problems with Win Vista.  when I reinstalled Ubuntu, I download the 10 vs and found that I couldn't connect with wireless.  I had not made notes on what happened 3 months ago to make the connection then.  I am 87 yrs. old and am forgetting things.  I have no trouble connecting wireless in Win Vista. Please help.  Thanks.

---

### Post by Augie1944 on 2010-06-16
[SIZE=3]I did not know how to find my old post, but after trying to activate the Broadcom driver, it failed.  I uninstalled and then reinstalled Ubuntu before trying to activate the driver again.  The error message was: 
failed to fetch from archive the file:  ................/patch_2.6-2ubuntu/_amd64.deb.  and could not resolve  us.archive.ubuntu.com

I thought perhaps reinstalling Ubuntu might help resolve the error.  Any suggestions?   I had been using the 9.10 vs, but now had to download the new 10.04 vs. 
Thanks so much for any help.
[/SIZE]

---

### Post by Augie1944 on 2010-06-16
[SIZE=3]I tried to get the Broadcom device activated after several hrs. and succeeded this time.   But, there are no wireless networks shown.  With Win Vista I can see three networks available including my own.[/SIZE]  [SIZE=3]Network Manager shows wireless is disabled.  What does "disabled" mean here?
Thanks for any help.
[/SIZE]

---

### Post by lkraemer on 2010-06-16
This might help:
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=Broadcom+files](http://ubuntuforums.org/showthread.php?t=1470146&highlight=Broadcom+files)

lk

---

### Post by Shazzam6999 on 2010-06-16
I don't know if this will help but you may try running these commands:
iwconfig eth1 power on
ifconfig eth1 up (ifconfig not iwconfig)
iwconfig eth1 essid networkname key networkpasswd (just fill in your name/passwd in the appropriate areas).
dhcpcd eth1 

That's what I have to do to connect with my wireless. Just replace eth1 with whatever your wireless interface is (ie: wlan0). It sounds like your wireless is working but you're just having issues connecting. I had had the same exact problem trying to use the GUI in 10.04, but in 9.10 I had no issues. I hope that helps.

---

### Post by Augie1944 on 2010-06-16
I appreciate your two suggestions.  I looked at the linked page and was mystified by the instructions.  Then, I tried each one of the Terminal commands and was denied in each one. Surely, there is some commands which would help find the network.
Thanks again.

---

