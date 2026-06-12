---
title: "Having problems with internet connectivity..."
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Razaki on 2010-08-10
Hey there guys,
 
Very, very new Linux user here. I recently picked up a relatively old desktop PC for a couple of dollars to fool around with because I have very little to do until the semester starts in a few weeks, and since it had no OS installed on the HDD, I figured I'd finally get around to *really* trying Ubuntu.
 
I'm running into all kinds of problems right off the bat with my internet, though. Since it has no wireless card, I'm just running a straight wired ethernet cable into it. Seems simple enough, no?
 
For some reason, though, the internet is intermittent at best and downright bizarre at worst. It WILL work some of the time, but even when Firefox is connecting to webpages, programs such as Empathy's IM client and Evolution's Mail client simply will **not** do their thing. All of them have network errors when they really shouldn't.
 
If this were a Windows PC, I'd know at least the right general direction to go as far as troubleshooting is concerned; with Ubuntu, however, I'm lost.
 
Anyone able to provide me some help? I've seen other people be given terminal commands and asked for the output of that - I'd be more than willing to do that, if that's what needs to be done.
 
Any help is greatly appreciated. Thanks!

---

### Post by silverglade00 on 2010-08-10
You probably want to check the little things first. Try using another network cable to make sure that's not the problem. If that doesn't fix it, try opening the case and pulling out the network card and putting it back in (assuming it is not built into the motherboard). The third thing to check for an intermittent problem is that you don't have another computer on your network with the same IP address. Try posting the output of 
```
ifconfig
```
if none of that works.

---

### Post by Razaki on 2010-08-10
Alright, so I tried all of those fixes...no dice. It's not the same IP address as my laptop, either.

I mean, I AM able to access internet occasionally through the machine - I'm currently typing on the desktop as we speak.

As for ifconfig, here you go:

> 
eth0                Link encap:Ethernet  HWaddr 00:eth0      Link encap:Ethernet  HWaddr 00:0c:f1:82:42:b2  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe82:42b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collieth0      Link encap:Ethernet  HWaddr 00:eth0      Link encap:Ethernet  HWaddr 

lo                        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
sions:0 txqueuelen:1000 
          RX bytes:50107 (50.1 KB)  TX bytes:30701 (30.7 KB)
That make any sense to you?

---

### Post by sandyd on 2010-08-10
sounds like either a clunky driver or bad network card (might have been the reason why the desktop was sold in the first place).
run ```

lspci
lsmod

```

---

### Post by Razaki on 2010-08-10
It's a possibility that it's a bad network card, but here's the weird part: when I'm not really messing with things and only want to use firefox, webpages load perfectly fine...at least the ones that I'm trying to load. If I try to use Evolution or Empathy, though, and I begin getting network errors, it takes a little bit before I can use Firefox again. It quite reasonably could simply be the way that it APPEARS, but it's been multiple times in a row now. *shrug*

Here is lspci: 
> 
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
01:01.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
And lsmod:

> Module                  Size  Used by
binfmt_misc             6587  1 
nvidia               7087672  34 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ppdev                   5259  0 
vga16fb                11385  1 
parport_pc             25962  1 
dell_wmi                1793  0 
vgastate                8961  1 vga16fb
intel_agp              24119  1 
dcdbas                  5422  0 
psmouse                63245  0 
joydev                  8708  0 
serio_raw               3978  0 
shpchp                 28820  0 
agpgart                31724  2 nvidia,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
e100                   28211  0 
mii                     4381  1 e100
usbhid                 36110  0 
hid                    67032  1 usbhid
floppy                 53016  0 


---

### Post by sandyd on 2010-08-10
> **Razaki said:**
> It's a possibility that it's a bad network card, but here's the weird part: when I'm not really messing with things and only want to use firefox, webpages load perfectly fine...at least the ones that I'm trying to load. If I try to use Evolution or Empathy, though, and I begin getting network errors, it takes a little bit before I can use Firefox again. It quite reasonably could simply be the way that it APPEARS, but it's been multiple times in a row now. *shrug*

Here is lspci: 
And lsmod:
looks ok.
the driver is loaded
```

e100                   28211  0 

```
have you checked the ethernet cable?
preferably with another computer

---

### Post by Razaki on 2010-08-10
I have checked it before, and I went ahead and checked it again...plugged it into my windows computer sitting beside of it, did a speed test, logged into Pidgin, then used Outlook to see if it could do any of those things.

Everything ran successfully on the other computer.

Just tried again, though, and Evolution is still not working for my Gmail account. It says that imap.gmail.com's "host name is not found." and it's server query into checking about supported password types times out.

It's very, very odd, and I'm not sure what could be causing it.

---

### Post by Razaki on 2010-08-10
So, after testing a couple of things, I'm inclined to say that this almost FEELS like a firewall issue or something, although that makes no sense.

Essentially, I can browse this site and certain other websites like huffingtonpost.com, but when I try to access mail.google.com or [www.youtube.com](www.youtube.com), I immediately time out. Oddly enough, that then causes everything ELSE that was working normally to time out.

Boy, am I confused.

---

### Post by sandyd on 2010-08-10
> **Razaki said:**
> I have checked it before, and I went ahead and checked it again...plugged it into my windows computer sitting beside of it, did a speed test, logged into Pidgin, then used Outlook to see if it could do any of those things.

Everything ran successfully on the other computer.

Just tried again, though, and Evolution is still not working for my Gmail account. It says that imap.gmail.com's "**host name is not found.**" and it's server query into checking about supported password types times out.

It's very, very odd, and I'm not sure what could be causing it.
oh. DNS problems I see...
see if
-> [http://openubuntu.com/index.php/topic,230.0.html](http://openubuntu.com/index.php/topic,230.0.html)
helps

---

### Post by Razaki on 2010-08-10
Ahh, well that was a lifesaver for allowing me to access normal websites. I can even access mail.google.com perfectly fine.

It fixed Empathy's chat login, so that's great, too, but I'm still not being able to access my IMAP in Evolution.

It's timing out now instead of not finding the host, but I can't figure out how to fix that. Any thoughts?

---

### Post by sandyd on 2010-08-10
> **Razaki said:**
> Ahh, well that was a lifesaver for allowing me to access normal websites. I can even access mail.google.com perfectly fine.

It fixed Empathy's chat login, so that's great, too, but I'm still not being able to access my IMAP in Evolution.

It's timing out now instead of not finding the host, but I can't figure out how to fix that. Any thoughts?
I keep my system clean of GTK apps, so I don't exactly know what evolution's functions are, but try switching fro IMAP to POP.

heres the stuff you need -> [http://mail.google.com/support/bin/answer.py?hl=en&answer=13287](http://mail.google.com/support/bin/answer.py?hl=en&answer=13287)

---

### Post by Razaki on 2010-08-10
Switching it to POP worked...I'd rather keep it IMAP, but I suppose POP will suffice. :-)

Thank you so, SO much for all of your help.

---

