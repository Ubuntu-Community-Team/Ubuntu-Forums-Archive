---
title: "Realtek 8187b -  I've tried everything"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by pounditflat on 2008-09-16
I've had lots of different people try to help get my laptop online with the Realtek 8187b wireless adapter. I just can't seem to make it work. Maybe the one that I downloaded is the problem, maybe I should download a different one and maybe it will have the device manager with it. I could really use that. Can someone help a newbie get Ubuntu working with my wireless card? I would really appreciate it. I don't want to use anything Micro$oft if I can work around it. Thanks.       
                 
                Pound

---

### Post by pounditflat on 2008-09-16
Is there anything better than ubuntu that I can use? I need something that my laptop online with. Is there any?
My laptop is a toshiba s205 and it uses a realtek 8187b wireless adapter. Does anything work with this wireless card?

---

### Post by niccholaspage on 2008-09-16
I have the same card as you. Here is how I got mine working.
If you have an ethernet cable to use the internet wired, Than plug it in.
If you don't, than get a Ubuntu Live CD. Insert it and go to System>Administration>Software Sources And check the cdrom place at the bottom.
Now open Synaptic Manager(System>Administration>Synaptic Package Manager)
And search for ndisgtk. Install the ndisgtk package.
Now you may need a USB drive for this next step if you aren't connected to a wired ethernet connection.
Go to host-a.net/niccholaspage/
Download the fileshare.ro_rtl_drivers.tar.gz from there.
Extract the file.
Now open ndisgtk(System>Administration>Windows Wireless Drivers) And click Install New Driver. Now open the .inf file in the extracted directory. Now try to connect with the network manager in the top upper hand corner.


Tell me if you need some more help.

---

### Post by niccholaspage on 2008-09-16
I have the same card as you. Here is how I got mine working.
If you have an ethernet cable to use the internet wired, Than plug it in.
If you don't, than get a Ubuntu Live CD. Insert it and go to System>Administration>Software Sources And check the cdrom place at the bottom.
Now open Synaptic Manager(System>Administration>Synaptic Package Manager)
And search for ndisgtk. Install the ndisgtk package.
Now you may need a USB drive for this next step if you aren't connected to a wired ethernet connection.
Go to host-a.net/niccholaspage/
Download the fileshare.ro_rtl_drivers.tar.gz from there.
Extract the file.
Now open ndisgtk(System>Administration>Windows Wireless Drivers) And click Install New Driver. Now open the .inf file in the extracted directory. Now try to connect with the network manager in the top upper hand corner.


Tell me if you need some more help.

---

### Post by pounditflat on 2008-09-16
Now open ndisgtk(System>Administration>Windows Wireless Drivers) And click Install New Driver. Now open the .inf file in the extracted directory.

When I do this, it doesn't appear to understand what I'm trying to do

---

### Post by dmizer on 2008-09-16
Merged your two posts, and edited for consistency. Please give the people in this forum some time to respond to your problems. If you need immediate help, you're more likely to get it in the Ubuntu IRC channel.

It is very difficult to provide support if you make multiple threads for the same or similar problems.

Please try to have a little bit of patience while working through the learning process. According to niccholaspage, this card does work in Ubuntu. So, if you post your problems, we will be more than happy to help you out.

Also, if you're having problems getting the card to work in Ubuntu, it's very likely that you will have problems making the card work in another distribution. Obviously this is not always true and if you like, you're welcome to try any other distribution you like.

> **pounditflat said:**
> When I do this, it doesn't appear to understand what I'm trying to do
Are there any error messages? What does it do exactly? Where exactly did you save fileshare.ro_rtl_drivers.tar.gz? Where is the net8187b.inf file located on your computer?

---

### Post by pounditflat on 2008-09-17
It doesn't give an error message, but it says that the .inf file that I'm pointing it to does not contain the .inf file that it needs. It also does not recognize the card is installed and for some reason I can't find hardware manager in systems.

Thank you all for trying to help. I'm not going to give up, but I may buy another internal card or maybe a usb wireless adapter.

Pound

---

### Post by pounditflat on 2008-09-17
it says the drivers are installed but the card is not. That's what's stopping me. it doesn't recognize that the card is there. HELP  !

---

### Post by dmizer on 2008-09-17
Okay, let's work through this a step at a time.

First of all, where exactly did you save the fileshare.ro_rtl_drivers.tar.gz?

---

### Post by pounditflat on 2008-09-18
I reformatted and re installed Ubuntu and now it can recognize  that the card is there. It thinks it can go online, but no. Then it says address not found.

---

### Post by dmizer on 2008-09-18
What is the output of:
```
sudo ifconfig
```

---

### Post by pounditflat on 2008-09-20
dad@dad-laptop:~$ sudo ifconfig
sudo: unable to resolve host dad-laptop
[sudo] password for dad: 
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:95:61:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81088 (79.1 KB)  TX bytes:81088 (79.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:8f:cb:30  
          inet addr:192.168.200.249  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fe8f:cb30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2396590 (2.2 MB)  TX bytes:246341 (240.5 KB)

---

### Post by dmizer on 2008-09-20
Well, you have an IP address, so you should be able to browse.

Try disabiling IPv6 according to the directions here: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

You may also have success by using opendns DNS servers as well: [https://www.opendns.com/smb/start/device/ubuntu](https://www.opendns.com/smb/start/device/ubuntu)

---

### Post by pounditflat on 2008-09-20
I am able to browse. I am online wireless right now. Thank you so very much for helping me. I want Ubuntu to be my OS. I want to learn every thing about it. I look forward to the day when I am able to help others.

---

