---
title: "Wireless stops working when lid is closed."
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by Lumby on 2008-11-02
I am currently running Ubuntu 8.04 on my Lenovo T61p. Whenever I close my laptop lid the wireless seems to stop working after a certain amount of time. I currently have it set to put up a blank screen and do nothing else when the lid is closed. Its also worth noting that my laptop is plugged in.

This is most frustrating when trying to upgrade to ubuntu 8.10, I will close my lid to let the update run but when I come back the wireless is broken and the update is nowhere near finished.

Any help or suggestions would be greatly appreciated.

Thanks

Matthew

---

### Post by ImSneakinAround on 2009-01-15
Bump for this. I've recently noticed the same problem. It doesn't happen every time, but it happens often enough to be annoying as it kills my connection for long enough to interrupt any programs that rely on it (Bittorrent, IM, access to my NAS, etc.)

I'm using an Asus G1 laptop running 8.10.

---

### Post by Paul Miller on 2009-01-16
I don't have a specific solution, but this sounds like a power management issue to me.  I'd try tweaking the power management settings to see if this fixes it.

---

### Post by slibuntu on 2009-05-20
I'm having this problem also. On Ubuntu 9.04 on a Dell XPS M1330.

After opening, the wifi, although it appears to be connected, isn't and I must turn it off and on again (the wifi) to connect again.

There are no power management options for this kind of behaviour

---

### Post by GonzalitoUY on 2009-06-19
Same problem with a T-1625 Gateway, and Realtek 8187b.Out of the box wireless doesn't work right, but after installing linux-backport-modules, everything seems nice, except for this issue. Using Jaunty 32 bits, on a AMD Turion X2 64, maybe that'the problem? Doesn't have any experience with 64 bits systems.

---

### Post by micdhack on 2009-07-07
same problem here

UPDATE: i disabled the screensaver when the lid closes or after a period of inactivity from power management options. Now everything works normal and there are no disconnections on the wifi so far.

---

### Post by xirox on 2009-10-27
> **micdhack said:**
> same problem here

UPDATE: i disabled the screensaver when the lid closes or after a period of inactivity from power management options. Now everything works normal and there are no disconnections on the wifi so far.

I have same problem with lid and wifi. My notebook is a HP COMPAQ F760 LA. AMD TURION 64. 2gb RAM, nvidia, wifi broadcom.
With 8.04 it worked fine, but with 9.04.

How did it do?. How to disalbed the screensaver when lid closes?.

---

### Post by xirox on 2009-11-16
I did a clean install of Kubuntu 9.10.
This problem persists.
I tried this
$ ping [www.google.com.ar](www.google.com.ar)
PING [www.l.google.com](www.l.google.com) (74.125.67.105) 56(84) bytes of data.
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=1 ttl=50 time=193 ms
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=2 ttl=50 time=190 ms
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=3 ttl=50 time=193 ms
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=4 ttl=50 time=194 ms
------- here close the lid --------
64 bytes from 74.125.67.105: icmp_seq=5 ttl=50 time=195 ms
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
.
.
.
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
From nblinux.local (192.168.1.34) icmp_seq=89 Destination Host Unreachable
From nblinux.local (192.168.1.34) icmp_seq=90 Destination Host Unreachable
From nblinux.local (192.168.1.34) icmp_seq=91 Destination Host Unreachable
------ here open the lid --------
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=93 ttl=50 time=638 ms
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=94 ttl=50 time=261 ms
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=95 ttl=50 time=375 ms
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=96 ttl=50 time=1068 ms

---

### Post by xirox on 2009-11-16
I did a clean install of Kubuntu 9.10.
This problem persists.
I tried this
$ ping [www.google.com.ar](www.google.com.ar)
PING [www.l.google.com](www.l.google.com) (74.125.67.105) 56(84) bytes of data.
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=1 ttl=50 time=193 ms
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=2 ttl=50 time=190 ms
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=3 ttl=50 time=193 ms
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=4 ttl=50 time=194 ms
------- here close the lid --------
64 bytes from 74.125.67.105: icmp_seq=5 ttl=50 time=195 ms
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
.
.
.
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
From nblinux.local (192.168.1.34) icmp_seq=89 Destination Host Unreachable
From nblinux.local (192.168.1.34) icmp_seq=90 Destination Host Unreachable
From nblinux.local (192.168.1.34) icmp_seq=91 Destination Host Unreachable
------ here open the lid --------
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=93 ttl=50 time=638 ms
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=94 ttl=50 time=261 ms
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=95 ttl=50 time=375 ms
64 bytes from gw-in-f105.1e100.net (74.125.67.105): icmp_seq=96 ttl=50 time=1068 ms

ScreenSaver is Off
In powermanagement "When Lid Close: do nothing"

---

### Post by kabeza on 2009-12-26
Hi ppl
I'm having the same trouble with my Toshiba Satellite Pro L300D-SP5802 laptop.
I've the latest Karmic Koala 9.10 version, with screensaver off, dark screen on lid close (power management settings) , etc. but I keep being disconnected from my wireless connection when I close the laptop lid

Any solutions yet?
Thanks,

---

### Post by danab3791 on 2010-02-22
I've nothing terribly constructive to add here, except that I have the same problem on a Thinkpad x200s. 

the computer is set to blank screen when laptop lid is closed (Karmic 9.10 x64)

---

### Post by malikons on 2010-04-17
anyone know if this is registered as problem with Ubuntu??? this is really annoying and i can't believe it is not bothering many people.

---

### Post by Gurduloo on 2010-04-20
I'm having this problem too.  I'm using a Lenovo laptop with an Intel 4965 wireless card.

---

### Post by hayhursm on 2010-07-26
[FONT=Arial][SIZE=3]Bump[/SIZE][/FONT]
[FONT=Arial][SIZE=3][/SIZE][/FONT] 
[FONT=Arial][SIZE=3]I have an Asus F3Ka laptop and the wireless drops out a few minutes after the lid is closed (laptop is plugged in and not even running on battery).  Even after I open the lid I must re-establish the wireless connection by opening a web browser.  This is annoying because I need to connect to my laptop from work via SSH and NoMachine but I cannot.  I could leave the lid open but when you have kids that’s not really an option.  This was not an issue in Windows 7 as I could RDP to my laptop even with the lid closed.  Does anyone know if some setting can be changed in Ubuntu Lucid x64 to correct this?[/SIZE][/FONT]

---

### Post by hayhursm on 2010-07-27
> **hayhursm said:**
> [font=arial][size=3]bump[/size][/font]

[font=arial][size=3]i have an asus f3ka laptop and the wireless drops out a few minutes after the lid is closed (laptop is plugged in and not even running on battery). Even after i open the lid i must re-establish the wireless connection by opening a web browser. This is annoying because i need to connect to my laptop from work via ssh and nomachine but i cannot. I could leave the lid open but when you have kids that’s not really an option. This was not an issue in windows 7 as i could rdp to my laptop even with the lid closed. Does anyone know if some setting can be changed in ubuntu lucid x64 to correct this?[/size][/font]
 
 
bump

---

### Post by DEVIL DOG on 2010-07-27
Change your settings in System>Preferences>Power Management.

---

### Post by hayhursm on 2010-08-02
> **DEVIL DOG said:**
> Change your settings in System>Preferences>Power Management.

I couldn't find a "wireless power option" in those settings.  My Power Settings right now are to leave everything on when plugged in and the laptop is plugged in always.  Any ideas?

---

### Post by Cadeyrn on 2012-09-03
Was this problem ever fixed? I have it with an HP Touchsmart tm2, Kubuntu 12.04 (also had it in 11.04).

---

### Post by hayhursm on 2012-09-04
> **Cadeyrn said:**
> Was this problem ever fixed? I have it with an HP Touchsmart tm2, Kubuntu 12.04 (also had it in 11.04).


Hello,

I have since sold my laptop so I'm not sure about this problem any more...maybe someone else can provide a solution.  I'm sorry and wish I had better news.

---

### Post by HiddenFly on 2013-03-10
Still happens with 12.10 as well. I have reported this as bug [#1153252]("http://bugs.launchpad.net/ubuntu/+bug/1153252")

---

