---
title: "USB Link Cable help?"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by mameshiba on 2010-09-06
Hello

I have a desktop PC and I need to transfer some of the files on it to my laptop. Someone told me I could do this if I had a USB link cable, so I have bought one, kind of thinking it would plug and play but nothing happens when both machines are switched on and the cable is plugged in at both ends. (Please excuse my naïveté.)

Can someone talk me through what I have to do to make the two PCs talk to one another or link me to somewhere it has already been explained?

Thank you! (^-^)

---

### Post by jtarin on 2010-09-06
Run the command ```
ifconfig
``` in a terminal and post results.
[Link to USB connections]("http://www.linux-usb.org/usbnet/")

---

### Post by mameshiba on 2010-09-07
This is what I got:

> carrie@carrie-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:98:02:5f  
          inet addr:86.0.168.143  Bcast:86.0.171.255  Mask:255.255.252.0
          inet6 addr: fe80::290:f5ff:fe98:25f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7887 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8303528 (8.3 MB)  TX bytes:1533691 (1.5 MB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:96:a5:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Apologies for the late response- in the middle of moving house at the moment!! (>_<)

---

### Post by jtarin on 2010-09-07
Is this what you have?

---

### Post by mameshiba on 2010-09-08
Yes, that's it.

---

### Post by bredman on 2010-09-08
I have never seen a solution where you can just connect the two computers with a USB cable. Normally, a computer is a USB host and expects a USB device at the other end of the cable. In your case, you have two USB hosts and no USB devices.

It is interesting that the Ethernet connection on your laptop seems to be working perfectly. Is the other PC also connected to the same Ethernet network? I ask because the standard way for PCs to talk to each other is via an Ethernet network.

---

### Post by mameshiba on 2010-09-08
No, only the laptop is connected. I don't have the means to connect the desktop as well.

---

### Post by TNT1 on 2010-09-08
> **mameshiba said:**
>  I don't have the means to connect the desktop as well.

Why? What interfaces does the desktop have? What network is it?

---

### Post by mameshiba on 2010-09-08
It's also on Unbuntu (Karmic rather than Lucid). It's *capable* of being connected to the internet (it always was before I got my laptop), I just don't have a hub so I can't have both of them connected at the same time.

---

### Post by mameshiba on 2010-09-08
I think I should clarify: the reason I want the files off the PC is because I want to get rid of it. I don't need both the laptop and the desktop, I bought a laptop to downsize (in terms of actual physical size) because I'm going away to university, which will include a year abroad, and I wanted something that wasn't a palaver to move or take on a plane.

---

### Post by TNT1 on 2010-09-08
> **mameshiba said:**
> It's also on Unbuntu (Karmic rather than Lucid). It's *capable* of being connected to the internet (it always was before I got my laptop), I just don't have a hub so I can't have both of them connected at the same time.

Lot of docs? Dropbox/ubuntu One could work?

---

### Post by mcduck on 2010-09-08
Most likely the usbnet module used for this isn't loaded by default, as it's rarely used.

I just checked and it is present on the standard Ubuntu installation, so simply loading it with "sudo modprobe usbnet" and then plugging in the host-to-host USB cable should get the cable recognized as a network interface.

Honestly, I would have simply bought a crosswired Ethernet cable instead, and used that for direct connection between the machines. Or a Firewire cable, if both machines have a Firewire connector.

Actually if you are lucky both your computer's network interfaces support Auto-MDIX and a normal Ethernet cable works for direct connection between the machines. Most gigabit Ethernet interfaces support this.

---

### Post by mameshiba on 2010-09-08
Not many documents - that could probably work for those. (How do I access it again?...)

It's more my photos (not as important as they're backed up online) and music library (not currently backed up anywhere) I'm concerned about; I fully intend on backing them up externally fairly soon but can't afford an external hard drive big enough *right now*.

---

### Post by TNT1 on 2010-09-08
> **mcduck said:**
> 

Honestly, I would have simply bought a crosswired Ethernet cable instead, and used that for direct connection between the machines. Or a Firewire cable, if both machines have a Firewire connector.

Actually if you are lucky both your computer's network interfaces support Auto-MDIX and a normal Ethernet cable works for direct connection between the machines. Most gigabit Ethernet interfaces support this.

1st Prize.

---

### Post by jtarin on 2010-09-08
OK...[here ya go]("http://www.linux-usb.org/usbnet/#t-host")...basically what you will have to do is load the right driver for your cable to act as a bridge between the two machines.This is why I asked you to issue the command "ifconfig" to see if it has a network address. The page I directed you to gives you a way to do that.Look for your driver in the list and it will give you the name of the driver you need to load. then you will have to configure it.

---

### Post by bredman on 2010-09-08
Please ignore my earlier post.

I have just learned from jtarin that Ubuntu does support USB host-to-host connection. This looks like your best bet for success.

This just shows that old dogs can learn new tricks by hanging out at the Absolute Beginners forum.

---

### Post by mameshiba on 2010-09-13
Thanks for all your help, guys. I'm settled in at my new home now so I'll sit down and sort this all out and let you know if I have any difficulties.:KS

---

### Post by migs73 on 2010-09-13
> **mameshiba said:**
> I think I should clarify: the reason I want the files off the PC is because I want to get rid of it. I don't need both the laptop and the desktop, I bought a laptop to downsize (in terms of actual physical size) because I'm going away to university, which will include a year abroad, and I wanted something that wasn't a palaver to move or take on a plane.
You also say you don't have enough money to by a HDD big enough for all your files yet you are going to get rid of one from your PC?? Just buy a suitable caddy and fit the one from your PC into it!! Then you don't have to get them tranferred and once you wipe of the other OS you'll have extra space on it):P

---

