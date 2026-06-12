---
title: "getting my PCMCIA networkcard working"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by groundler on 2006-09-26
If I run my computer from the live cd my ethernetcard (10/100M PCMCIA ethernet card from wisecom)works but if I try to run this card on my normal installation it doesn't. How can I install my driver from the cd or how can I activate my networkcard?? 
My LED's are all working so maybe the problem is not the driver but the activation.

---

### Post by Henry Rayker on 2006-09-26
post the results of an ifconfig

god, I hope that's the command

---

### Post by brc64 on 2006-09-28
I'm having this same problem.  When I booted from the Live CD, everything worked fine.  So I proceeded to install, and now it's telling me that I've got no eth0.

ifconfig results:
```

lo     Link encap:Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING  MTU:16436  Metric:1
       RX packets:3 errors:0 dropped:0 overruns:0 frame:0
       TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

```

When I try to "sudo ifup eth0", I get:
```

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

```

The lights on the card are on.  Also interesting is that if I go into Applications->System->Networking, the DNS tab has the correct DNS server and Search Domain.  I'm not terribly familiar with Linux, so I don't really know what to try next.  Any suggestions would be helpful.

---

### Post by mips on 2006-09-28
Try turning **acpi** off

---

### Post by brc64 on 2006-09-28
> **mips said:**
> Try turning **acpi** off

I checked the BIOS settings, but it's very old laptop and there was no option for acpi specifically.  I turned off all of the individual power management options, but that didn't have any noticeable effect on the issue.  If you're talking about disabling acpi in the OS, I don't know how to go about doing that.

Also, I'm running xubuntu 6.06.1 if it makes a difference.

---

### Post by brc64 on 2006-09-28
Upon further searching, I found a post on [linuxquestions.org](http://www.linuxquestions.org/questions/showthread.php?t=454810) that outlined my problem almost exactly (the hardware was different, but the symptoms were the same).  The fix listed worked for me!

> 
I had a similar problem and what it came down to is "/etc/pcmcia/config.opts". If you copy the one that existed when you booted up the install cd to your drive after everythings setup then it'll fix the problem. One way of doing this would be;

(If your main linux drive is hda1)

sudo mkdir /mnt/hda1
sudo mount /dev/hda1 /mnt/hda1
sudo cp /etc/pcmcia/config.opts /mnt/hda1/etc/pcmcia/
sudo umount /mnt/hda1
reboot

Sure enough, I had no config.opts file in my /etc/pcmcia directory.  Once I copied the one from the live CD and rebooted, all was well.

---

### Post by groundler on 2006-09-29
I couldn't enter the internet for some time because of this problem, but I just tried to copy the file and everything works perfect thanks!

---

