---
title: "no eth0"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by dookiebowser on 2010-06-13
I have no eth0 device after trying to install gentoo. I wiped the drive and reinstalled ubuntu and still no eth0. 

All I see is loopback adapter. Did my ethernet die? It was working fine on Ubuntu LiveCD and Ubuntu installed to disk before trying to install gentoo. The wlan still surprisingly works.

Help please!!!


> $ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:8d:60:a9  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe8d:60a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12612 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22983554 (22.9 MB)  TX bytes:1406890 (1.4 MB)
> $ lspci -v
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
    Subsystem: Intel Corporation Device 0000
    Flags: fast devsel, IRQ 18
    Memory at da000000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at 4000 [size=32]
    Capabilities: <access denied>
    Kernel modules: e1000e



> $ lsmod
e1000e                119856  0 

---

### Post by coolbrook on 2010-06-13
It could be failing.  [COLOR=Silver][COLOR=Black]Did you take a peek at the BIOS for more  information? Is it consistently detecting the ethernet port?  Is it a server board with a 2nd port to test?[/COLOR]
[/COLOR]

---

### Post by dookiebowser on 2010-06-13
> **coolbrook said:**
> It could be failing.  [COLOR=Silver][COLOR=Black]Did you take a peek at the BIOS for more  information? Is it consistently detecting the ethernet port?  Is it a server board with a 2nd port to test?[/COLOR]
[/COLOR]

It's a laptop so it's the only eth port available. The BIOS is HP OEM garbage and doesn't give me any info about the adapter. I'll check again though just incase.

I noticed the hard drive gets extremely hot while not even doing anything HD intensive, so i'm worried that it has finally damaged the things around it. Since it is so strategically positined right between both the ethernet port and the micro wifi card.

I noticed my wifi is now dropping packets (5-10 feet away from router) at random too which wasn't occurring, but then again i've been wired for a long time.

---

### Post by dookiebowser on 2010-06-13
bump. please give input.

I've been trying to make a DOS 6.22 boot CD to install a default config for PXE boot (i've made 2 coasters because somehow UltraISO for windows didn't include the files even though it reflected it in the ISO). I really do not think this is the issue though.

Would just like more input before I give it to a repair shop to order the parts and install because I am too lazy to completely disassemble an HP laptop.

Thanks.

---

### Post by an0dos on 2010-06-13
> **dookiebowser said:**
> bump. please give input.

I've been trying to make a DOS 6.22 boot CD to install a default config for PXE boot (i've made 2 coasters because somehow UltraISO for windows didn't include the files even though it reflected it in the ISO). I really do not think this is the issue though.

Would just like more input before I give it to a repair shop to order the parts and install because I am too lazy to completely disassemble an HP laptop.

Thanks.

Before you start spending money on getting it repaired, boot the computer from an Ubuntu live CD and see if it works in a live session. If it works then you can be reasonably sure it's not a hardware related issue.

---

### Post by dookiebowser on 2010-06-14
> **an0dos said:**
> Before you start spending money on getting it repaired, boot the computer from an Ubuntu live CD and see if it works in a live session. If it works then you can be reasonably sure it's not a hardware related issue.

It is not working in Ubuntu LiveCD, Ubuntu 10.4 (installed), Gentoo minimal install CD, or SystemRescueCD.

I just did a fresh install of Windows 7 and it is working in windows. It is still not working on Ubuntu LiveCD, I just tried it again.

---

### Post by Peter09 on 2010-06-14
I presume you had a wire connector in the ethernet port at the time you did the config check. Also what colour are the lights on the switch and the ethernet port in the laptop.

---

### Post by dookiebowser on 2010-06-14
> **Peter09 said:**
> I presume you had a wire connector in the ethernet port at the time you did the config check. Also what colour are the lights on the switch and the ethernet port in the laptop.

Yes it's been connected nearly the whole time while troubleshooting. 

I'm partially color blind but I took pictures. It's solid green on both I think?



[IMG]http://img251.imageshack.us/img251/4197/dscn0416f.jpg[/IMG]
[IMG]http://img815.imageshack.us/img815/8113/dscn0415v.jpg[/IMG]

---

### Post by Peter09 on 2010-06-14
Here is a thread about your controller which seems to finally end up with a solution.
 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1276211](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1276211)

---

### Post by dookiebowser on 2010-06-14
> **Peter09 said:**
> Here is a thread about your controller which seems to finally end up with a solution.
 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1276211](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1276211)


Thank you so much. It looks like I have a lot of work to do and then I will get back here.

---

### Post by dookiebowser on 2010-06-14
It worked. Thank you again for pointing out the thread!!

A big thank you to rreese6 for posting the solution!!

Some things to note:

I don't think I received the same error as Flux45 in *dmesg | grep e1000e*
I received:
> 0.877337] e1000e: probe of 0000:05:00.0 failed with error -5

The code that rreese6 alters is still in the driver src as of **e1000e-1.1.19**.

I tried fixing this problem with the Intel Boot Agent utility by running *ibautil -defaultconfig *but it did not help at all. There is definitely something wrong with my EEPROM, as it never had a problem like this with Ubuntu before. I also recently started receiving PXE-E05 errors on bootup in regards to the corrupted EEPROM.

---

