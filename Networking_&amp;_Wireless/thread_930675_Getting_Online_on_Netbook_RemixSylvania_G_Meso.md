---
title: "Getting Online on Netbook Remix/Sylvania G Meso"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by PhoebeG on 2008-09-26
Hi everyone,

As of yesterday, I'm a new owner of a Sylvania G Meso. I wanted to get a netbook that natively ran ubuntu, and this one was more affordable than the Dell Mini. I have linux experience--I've been using Kubuntu on my desktop for two years now--but to be honest, I usually have more success with it when things Just Work, rather than when I have to tinker in the command line. Anyway, I'm mostly happy with my purchase, except for one big problem: I can't get online.

I don't have a wireless router at home. When I first fired it up, I managed to connect to a neighbor's unsecured wireless using network manager, but it was very, very slow and dropped out pretty quickly. So I figured I would just plug in my wired connection to install some updates/software I needed.

But it wouldn't connect to the wired connection. I went online, read some forums, tried a few things, no luck. Probably stupidly, I thought it might be a software problem (I remembered having similar problems back when I first tried ubuntu a few years ago, and it was a software problem *then* :roll: ). So I decided to try another Network manager. I downloaded WICD to my SD card, popped it in, removed network manager, and installed it. Everything looked okay, but I still can't connect . . . and I haven't been able to get a wireless connection since installing WICD, either. Both wireless and wired connections hang up at "obtaining IP address."

Here's my ifconfig:

> eth1      Link encap:Ethernet  HWaddr 00:0c:6f:01:17:30  
          inet6 addr: fe80::20c:6fff:fe01:1730/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1062670 (1.0 MB)  TX bytes:12240 (11.9 KB)
          Interrupt:221 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112135 (109.5 KB)  TX bytes:112135 (109.5 KB)

wlan1     Link encap:Ethernet  HWaddr 00:0d:f0:58:fa:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0D-F0-58-FA-7D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Sometimes, randomly and unpredictably, it also shows this in ifconfig:

> eth1:avahi Link encap:Ethernet  HWaddr 00:0c:6f:01:17:30  
          inet addr:169.254.2.58  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:221 Base address:0xc000 

In fact, the only way I've managed to get it to connect via WICD is by naming the wired interface "eth1:avahi." Then, I can plug in and connect, but I still can't get firefox, etc. to connect to the internet.

Sorry so long--any advice on what could be going on here? I really want to get online with this thing.

Thanks in advance,
Phoebe

---

### Post by jetpeach on 2008-10-11
did you work out your connection issues? i am also occasionally having issues on my meo, wondering if intrepid will be better...

---

### Post by the3dman on 2008-12-02
You can try this image and see if it helps with connection issues, this is supposed to be the most updated version so far.

Here is an email I got from techincal support with a link to the Restore Image. They told me that this is not the final image, and that the final image will be uploaded to their website hopefully by the end of the month. This image works great though. To install just unzip and put all files on to a usb flash drive and then from a windows computer run makeboot.bat on the usb flash drive, and it will make it bootable. Warning: only run the makeboot file from the usb flash drive. Running from any other drive will mess up your computer.


Here is the email I got with the link:

Here is a link of the UNR you can download until the mean time if you need it instantly. You have to download it on to a flash drive and then run the “makeboot.bat” file and it should start installing once reboot.



Thank You



Sincerely,



Christy Mejia

Technical Support

Digital Gadgets

Tel: (88 571-0866

Email: [email]dgsupport@digitalgadgets.com[/email]



the latest image that has been updated to UNR 1 is available here:

[http://people.ubuntu.com/~jouston/20...ge-autousb.zip](http://people.ubuntu.com/~jouston/20...ge-autousb.zip)

---

### Post by letica4u2 on 2011-02-03
my name is lesbia and buy a sylvania netbook and i cant connect to internet can someone please help me on how to get internet.

---

