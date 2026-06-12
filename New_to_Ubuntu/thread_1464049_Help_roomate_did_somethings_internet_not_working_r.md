---
title: "Help roomate did somethings internet not working right"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by rhawnied on 2010-04-27
Hi,

 I have been in love with Linux since I installed ubuntu in march this year.  I haven't had many issues with it at all.  I have an older computer with some new parts.  It is an intel 915GAV motherboard, P4 2.93 GHZ, 2x1GB DDR RAM, and a 320 WD hard drive. 

When I got on here today I noticed firefox not working right.  I checked some things out and the plug ins are not in the manage plug in menu but they seem to be on the computer.  I have now changed the password so he can't do anything more but I don't know enough about ubuntu to fix everything he did and he says he can't remember.  I have tired to search the forums but I don't know what to look for exactly.

Let me know what information you might need and thanks ahead of time, I know this is a vague question.


Stressed out, Rhawnie :confused:

---

### Post by arrrghhh on 2010-04-27
Well let's establish you network connectivity.

Fire up a terminal (Alt+F2, gnome-terminal) and type "ping www.google.com" - see if you get replies back.

If that doesn't work, post what you get when you type "ifconfig" and hit enter.

If you CAN ping google, then there's something wrong with your FF config, most likely.  Either you can create a new profile and re-configure all your FF stuff, or we can look at proxy settings and the like that could hose FF's connectivity.

---

### Post by rhawnied on 2010-04-27
Okay so, when I typed the "ping www.google.com" It kept goingfor a while saying at the end of each something like 24s etc..  So if that is a reply then I got a bunch ;)

Next...
ifconfig got this

eth0      Link encap:Ethernet  HWaddr 00:13:20:39:0d:60  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe39:d60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83542075 (83.5 MB)  TX bytes:6670566 (6.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

I think that is a lot of errors but maybe I don't know...?

---

### Post by anewguy on 2010-04-27
> **rhawnied said:**
> 

I think that is a lot of errors but maybe I don't know...?

You must be looking at the receive packet count (RX) and transmit packet count (TX) as your error counts are all 0's.

Just so we know, also please post back the output from the following:

lspci

lsusb

lshw -C network


Dave ;)

---

### Post by arrrghhh on 2010-04-27
> **rhawnied said:**
> Okay so, when I typed the "ping www.google.com" It kept goingfor a while saying at the end of each something like 24s etc..  So if that is a reply then I got a bunch ;)

Next...
ifconfig got this

eth0      Link encap:Ethernet  HWaddr 00:13:20:39:0d:60  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe39:d60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83542075 (83.5 MB)  TX bytes:6670566 (6.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

I think that is a lot of errors but maybe I don't know...?

Believe it or not, that's not a bunch of errors... looks like you have an IP, can you ping your gateway?

Again, from terminal ```
ping 192.168.0.1
```

IF that works, try to ping this IP - 74.125.19.103.  So far it sounds like a potential DNS problem.


FYI - This is what a successful ping looks like: ```
 ping www.google.com
PING google.navigation.opendns.com (208.69.36.231) 56(84) bytes of data.
64 bytes from 208.69.36.231: icmp_seq=1 ttl=53 time=32.9 ms
64 bytes from 208.69.36.231: icmp_seq=2 ttl=53 time=42.2 ms
64 bytes from 208.69.36.231: icmp_seq=3 ttl=53 time=45.1 ms
64 bytes from 208.69.36.231: icmp_seq=4 ttl=53 time=41.7 ms
64 bytes from 208.69.36.231: icmp_seq=5 ttl=53 time=36.2 ms
```

Obviously yours will vary from mine, for several reasons.  But basically you should get a reply back every half second or so.  The "64 bytes from ..." means that the ICMP packet came back ok.

---

### Post by 2hot6ft2 on 2010-04-27
> **rhawnied said:**
> 
When I got on here today I noticed firefox not working right.  I checked some things out and the plug ins are not in the manage plug in menu but they seem to be on the computer.
For that part of your problems this may help
[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

To be more specific this under troubleshooting
[Addons page is blank - [FOT002]]("http://lovinglinux.megabyet.net/?page_id=220#Addons-page-is-blank--2")

---

### Post by rhawnied on 2010-04-27
Okay Dave:

lspci:

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)

Then lsusb:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Then lshw -C network:

 WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 01
       serial: 00:13:20:39:0d:60
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.0.10 latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:ff500000-ff500fff ioport:bc00(size=64)


Okay arrrghhh:

ping 192.168.0.1:

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.717 ms
64 bytes from 192.168.0.1: icmp_seq=14 ttl=64 time=0.720 ms
64 bytes from 192.168.0.1: icmp_seq=15 ttl=64 time=0.700 ms
64 bytes from 192.168.0.1: icmp_seq=16 ttl=64 time=0.651 ms
64 bytes from 192.168.0.1: icmp_seq=17 ttl=64 time=0.656 ms
64 bytes from 192.168.0.1: icmp_seq=18 ttl=64 time=0.664 ms
64 bytes from 192.168.0.1: icmp_seq=19 ttl=64 time=0.672 ms
64 bytes from 192.168.0.1: icmp_seq=20 ttl=64 time=0.673 ms
64 bytes from 192.168.0.1: icmp_seq=21 ttl=64 time=0.658 ms
64 bytes from 192.168.0.1: icmp_seq=22 ttl=64 time=0.706 ms
64 bytes from 192.168.0.1: icmp_seq=23 ttl=64 time=0.660 ms
64 bytes from 192.168.0.1: icmp_seq=24 ttl=64 time=0.667 ms
64 bytes from 192.168.0.1: icmp_seq=25 ttl=64 time=0.665 ms
64 bytes from 192.168.0.1: icmp_seq=26 ttl=64 time=0.678 ms
64 bytes from 192.168.0.1: icmp_seq=27 ttl=64 time=0.674 ms
64 bytes from 192.168.0.1: icmp_seq=44 ttl=64 time=0.706 ms
64 bytes from 192.168.0.1: icmp_seq=45 ttl=64 time=3.12 ms
64 bytes from 192.168.0.1: icmp_seq=46 ttl=64 time=0.654 ms
64 bytes from 192.168.0.1: icmp_seq=49 ttl=64 time=0.709 ms
64 bytes from 192.168.0.1: icmp_seq=50 ttl=64 time=0.656 ms
64 bytes from 192.168.0.1: icmp_seq=54 ttl=64 time=0.704 ms
64 bytes from 192.168.0.1: icmp_seq=55 ttl=64 time=0.652 ms
64 bytes from 192.168.0.1: icmp_seq=56 ttl=64 time=0.652 ms
64 bytes from 192.168.0.1: icmp_seq=57 ttl=64 time=0.656 ms
64 bytes from 192.168.0.1: icmp_seq=59 ttl=64 time=0.702 ms
64 bytes from 192.168.0.1: icmp_seq=60 ttl=64 time=0.674 ms
64 bytes from 192.168.0.1: icmp_seq=76 ttl=64 time=0.721 ms
64 bytes from 192.168.0.1: icmp_seq=77 ttl=64 time=0.650 ms
64 bytes from 192.168.0.1: icmp_seq=78 ttl=64 time=0.653 ms
64 bytes from 192.168.0.1: icmp_seq=79 ttl=64 time=0.658 ms
64 bytes from 192.168.0.1: icmp_seq=80 ttl=64 time=0.662 ms
64 bytes from 192.168.0.1: icmp_seq=81 ttl=64 time=0.670 ms
64 bytes from 192.168.0.1: icmp_seq=82 ttl=64 time=0.663 ms

And it kept going from there.  Hopefully I did those right I wasn't sure if I was suppose to sudo first.

Thanks

---

### Post by 2hot6ft2 on 2010-04-27
> **rhawnied said:**
> 
When I got on here today I noticed firefox not working right.  I checked some things out and the plug ins are not in the manage plug in menu but they seem to be on the computer.
> **rhawnied said:**
> Okay so, when I typed the "ping www.google.com" It kept goingfor a while saying at the end of each something like 24s etc..  So if that is a reply then I got a bunch ;)

So there was a reply.
You're getting ping responses from both google and your router.
Did I miss something?
Because other than saying firefox is messed up I don't see anything about not being connected to the Internet.
So can you bring up firefox and go to google.com?

---

### Post by cgroza on 2010-04-27
Let him try another browser like opera or epiphany and see if it works. If hose work then is a FF problem.

---

### Post by 2hot6ft2 on 2010-04-27
> **cgroza said:**
> Let him try another browser like opera or epiphany and see if it works. If hose work then is a FF problem.
We don't even know if firefox works at this point. It could just be a matter of backing up the bookmarks and re-installing it or just fixing what is wrong with it.
No need for another browser at this point.

---

### Post by arrrghhh on 2010-04-28
Stop jumping to conclusions.

OP, it looks like you could ping your router (192.168.0.1) - which is good, you have local access at least.

That is also a great example of when a ping works.  In Linux, it will ping continuously, so you have to break the process - you did that perfectly.

However, I don't see your pings to google.  Assuming you can ping google.com, let's dig at your Firefox settings.

I'd like to either blow away your profile and start with a fresh FF profile (shotgun approach, easiest for me but may be a pain for you if you have a lot of custom stuff in FF).  The other option is going thru proxy settings and checking the common things for errors.  We can start FF with a fresh profile just to see, do Alt-F2 and put "firefox -P" in there - note the P is capitalized.

Let me know what all of that results in...

---

### Post by rhawnied on 2010-04-28
Firefox opens and works a bit but there are no plugins in it and at times it will slow down like crazy or not go through proporly.

---

### Post by 2hot6ft2 on 2010-04-28
> **arrrghhh said:**
> Stop jumping to conclusions.

Who are you talking to? I made no conclusions other than restating what was already said and asking questions.

Then that brings you back to post #6 as shown below.
Have you tried the fix for the plugins not showing up linked to at the bottom?
Have you looked at the troubleshooting section of the guide?
It would help to know if you have tried the solutions already offered.
> **2hot6ft2 said:**
> For that part of your problems this may help
[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

To be more specific this under troubleshooting
[Addons page is blank - [FOT002]]("http://lovinglinux.megabyet.net/?page_id=220#Addons-page-is-blank--2")

---

### Post by rhawnied on 2010-04-28
Oh, sorry I must have missed that one... So I did what I it said. I deleted the profile and then I thought I would start from the top.  I got to Database Optimization.  Started to do it by script and got to 2) extract firefox-optimize.sh  into your home directory and first it said that I don't have the right permission to extract to the home file and when I pressed the help button this came up in the terminal I had left open:

** (gnome-help:5624): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (gnome-help:5624): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(gnome-help:5624): Yelp-WARNING **: Yelper initialization failed for 0x8acb310


??

---

### Post by rhawnied on 2010-04-28
I tried to do it the other way and got this:

Unable to open database "/home/rhawnie/.mozilla/0icohkm.DeafaultUser/places.sqlitevacuum": unable to open database file

---

### Post by anewguy on 2010-04-29
I bowed out of trying to help on this thread because of a common problem that needs mentioning:

- we are all here voluntarily, so let's quit the p*****g contest and try to focus on helping the user - this side tracking only confuses people looking for help

- when answering a post, try to keep in mind the flow.  Too often anymore we get posters bringing in opposing or at least different ideas (which is the idea here) but doing so in a way that is disruptive to the flow of the thread.

These aren't rules or anything - just my observations.  I've seen more posts getting sidetracked by people arguing with each other, or in some way going away from an apparent flow in the thread, and in general confusing the new user who was the original poster.  They came here seeking help.

In the case of this thread, one proposed doing things to Firefox, another suggested trying another browser.  Here's my take:

- if the suggestion has the possibility of being destructive of part of the user's information, such as deleting a profile from Firefox, then why not try a non-destructive test first - like loading another browser.  If the other browser doesn't work, you know you have other problems,  If the other browser does work, then you can work your way into what may be wrong in the config, etc., of Firefox.

I'm not trying to argue here, and I know I'm doing the very thing I hate - adding something slightly off topic.  My point is that even if it may seem like more work to just install another browser (in this case) via Synaptic, instead of the path of least resistance sometimes it's smarter for the Original Poster, the guy with the problem, if you take the path of least chance of screwing things up and confusing the user.  It's only a little extra time, and you don't end up with "now I can't do anything with...." posts back from the OP.

Just me throwing in my 2 cents worth because to me at least this has been getting aggravating - I'm sure that when one of you reports my post I'll be given a warning, but it's worth it to me if a point is made.

Dave 

To the OP - rhawnied - I'm sorry to jump in here again, but sometimes something needs to be said.  Maybe I picked the wrong time in place.

---

### Post by jetsam on 2010-04-29
Now the thread is threatening to implode in some kind of irony vortex.  

OP, you mentioned stress...  Are you still stressed?

Take a break?  Maybe five minutes or half an hour or a movie's worth or a night of rest?  It's up to you really.  In the end, all we can do is try to help you over the hurdles.

---

### Post by lovinglinux on 2010-04-29
> **anewguy said:**
> - if the suggestion has the possibility of being destructive of part of the user's information, such as deleting a profile from Firefox, then why not try a non-destructive test first - like loading another browser.  If the other browser doesn't work, you know you have other problems,  If the other browser does work, then you can work your way into what may be wrong in the config, etc., of Firefox.

I agree. I only recommend deleting FF profile if you can't find the culprit and only if you know the problem resides in the profile. But I also don't recommend installing another browser, unless the user can't troubleshoot Firefox itself. My recommendation is to follow the [General Troubleshooting](http://lovinglinux.megabyet.net/?page_id=220#Troubleshooting-1) steps first.

> **rhawnied said:**
> I tried to do it the other way and got this:

Unable to open database "/home/rhawnie/.mozilla/0icohkm.DeafaultUser/places.sqlitevacuum": unable to open database file

Looks like you missed the quotes or spaces, because instead of trying to "vacuum" the file *places.sqlite* it is trying to open the file *places.sqlitevacuum*. Did you install sqlite3?

---

### Post by rhawnied on 2010-04-30
Okay sorry I hadn't been back yet, busy day.

Anewguy I totally get your point and I don't mind it so much.  I think it can be hard to give advice in group form when everybody may not know each other.  But don't back down because of it, your idea may be the one that would make a difference.  

I was mostly stressed over my roommate messing with things when I told him to talk to me first and I would show how him or find out first.

Thanks lovinglinux for joining. I have spent much time reading your information on this and other topics.  I guess I missed that first " that time. But I tried to do it the first way you said in and I have it in archive manager but I can't save it to the home folder that is when I get

> ** (gnome-help:5624): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

Then I tried to do help and got

> (gnome-help:5624): Yelp-WARNING **: Yelper initialization failed for 0x8acb310

---

### Post by rhawnied on 2010-04-30
I also should say that I did delete FF profile (no big deal about that I had most of the info backed up) and I still have no plug ins in the manage content plug ins when there use to be and some web sites say that I don't have adobe when it is on the computer.  In add-ons/plug ins it says I have DivX 1.4.0.233, Helix DNA Realplayer G2 0.4.-, Shockwave 10.0 r45, and Totem 2.28.2

---

### Post by rhawnied on 2010-05-03
Well just to let you guys that tried to help me, I have upgraded Ubuntu and the problem is gone.  Thanks for trying anyway. :) Now on to the other minor issues... ;)

---

