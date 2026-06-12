---
title: "wireless"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by zzForSaken on 2009-11-27
Yesterday I installed Ubuntu 9.10 on my computer. Then I tried to connect to my router with a wireless PCI card. I installed ndisgtk with Synaptic Package Manager. With that programm I installed the driver. After that i don`t know what to do.:-( Could anyone help me out? I have a Linksys WRT54G router.

---

### Post by blazemore on 2009-11-27
What happens when you click the wireless symbol in the notification area, in the top right hand corner? A list of networks should appear. You can click yours to connect to it.

---

### Post by zzForSaken on 2009-11-27
it says: 
wired network:
disconnected
wireless networks:
device not ready

---

### Post by Shazaam on 2009-11-27
Did you reboot?

---

### Post by zzForSaken on 2009-11-27
I think so, but to make sure I did a quick reboot again.
And now it says:
wired network:
disconnected
wireless networks:
disconnected
??

---

### Post by 3rdalbum on 2009-11-27
> **zzForSaken said:**
> it says: 
wired network:
disconnected
wireless networks:
device not ready

Try shutting down the whole way and then starting the computer up again.

You know, Ubuntu does contain drivers for many wireless cards... did you make sure yours wasn't natively supported before going down the ndiswrapper route?

Also I'll preempt other poster by asking you to post the output of this command:

```

lspci
```

So we can see what the chipset of your wireless device is.

---

### Post by zzForSaken on 2009-11-27
> **3rdalbum said:**
> Try shutting down the whole way and then starting the computer up again.

You know, Ubuntu does contain drivers for many wireless cards... did you make sure yours wasn't natively supported before going down the ndiswrapper route?

Also I'll preempt other poster by asking you to post the output of this command:

```

lspci
```

So we can see what the chipset of your wireless device is.

I don`t know if it is natively supported. 
here is the output of "lspci":

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)
05:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by Dude-PWB- on 2009-11-27
Here are a couple threads for you to look at. Looks like you will not need ndisgtk and ndiswrapper. But you will need to get yourself a connection with your hard wired ethernet going so you can get the appropriate drivers and updates completed.

[http://ubuntuforums.org/showthread.php?t=1338967&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1338967&highlight=BCM4306)

[http://ubuntuforums.org/showthread.php?t=1328969&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1328969&highlight=BCM4306)

---

### Post by bkratz on 2009-11-27
I looked for your wired network controller and found a few instances of people who had the same one and never did seen to get it work ( or at least stopped posting).

Here is a link to a gentlemen who seemed to get the Broadcom wireless card working first, I think it may be worth a try. he did it with software on the live cd.

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by zzForSaken on 2009-11-28
Thanks for all the comments. =D
I looked at the threads and decided to plug in my UTP-Cable.
I dont know how I did it but after I plugged in my UTP-Cable I had several available network connections. :D Without updating any drivers.

---

### Post by CoolDreamZ on 2009-11-28
This looks like a common problem, see here for a possible solution:

[http://ubuntuforums.org/showthread.php?t=1312603]("http://ubuntuforums.org/showthread.php?t=1312603")

---

### Post by 3rdalbum on 2009-11-28
> **zzForSaken said:**
> Thanks for all the comments. =D
I looked at the threads and decided to plug in my UTP-Cable.
I dont know how I did it but after I plugged in my UTP-Cable I had several available network connections. :D Without updating any drivers.

Broadcom wireless device? You should just need to reload the package list (go into System > Administration > Synaptic Package Manager and hit the Reload button), close Synaptic, go into System > Administration > Hardware Drivers and it should offer a download for you that will get your wireless working.

---

