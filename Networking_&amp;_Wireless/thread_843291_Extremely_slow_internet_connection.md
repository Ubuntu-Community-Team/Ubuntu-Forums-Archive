---
title: "Extremely slow internet connection"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by camel_brother on 2008-06-28
Hi,

I'm new to ubuntu.
I've installed ubuntu 8.04 (GNOME). I have Thomson TCM425 modem connected to my cables ISP and to my computer via USB (the Ethernet port of my network card is used to connect to my other computer). I'm not using a dial-up, but an always-up internet connection.
Ubuntu identified everything during installation, and immediately I had internet connection working. 
The problem is that it is very very very slow (I'm using dual-boot with WinXP, where it is more than 10 times faster). I've read many posts and tried everything they suggested (to disable ipv6) including "playing" with /etc/hosts, /etc/modprobe.d/aliases, /etc/modprobe.d/bad_list, about:config, /etc/sysctl.conf, etc.

Well, nothing helps me.
Strangely, I experienced this behavior with Ubuntu 7.10 too, and that was one of my reasons to upgrade to 8.04.

Please help me (remember I'm a newbie) !

Camel (camel_brother@hotmail.com).

---

### Post by superprash2003 on 2008-06-28
is it only slow browsing speed or even slow download speed?

---

### Post by camel_brother on 2008-06-30
Hi superprash2003,

Thanks for your reply.

The answer to you question is that it is extremely slow both when browsing and when downloading (for example update manager downloads...).

---

### Post by Leeming on 2008-06-30
This seems like the exact same problem i am having..
[http://ubuntuforums.org/showthread.php?t=844454]("http://ubuntuforums.org/showthread.php?t=844454")

Help would be very appreciated as it will be helping two people =)

~edit~ Dont put your email in a format like that.. popular forums are searched all the time using search engine bots.. and also spam bots.. and email harvesters. tip: if your ever want to give an email out, remove @ with [at] and . (dot) with [dot]

---

### Post by camel_brother on 2008-06-30
I hope someone will help us both :-)

---

### Post by Leeming on 2008-07-04
Did you ever resolve this? if so i would like to know how :)

---

### Post by Frenske on 2008-07-12
I have similar problems. I have a dual boot machine and tested the internet speed using [www.speedtest.net](www.speedtest.net). I got 5500kb/s download and about 500kb/s upload on the Windows XP. Not blistering fast but workable.
Using exactly same hardware but the Ubuntu OS I get a wide range of readings - usually in the order 1200 kb/s and 250kb/s and sometimes even lower. Often the mouse movement is choppy and when playing music it turns Bach into monotonous hardcore techno - anything running in Ubuntu comes to a halt. Odd thing testing the internet [www.speedtest.net](www.speedtest.net) after reboot gave me once 6500kb/s and 800kb/s respectively.
What is ubuntu doing with my internet???? Is it just crappy memory/cpu management. It is not FF related since downloading things with update manager turns my computer also in a turtle. Tried disabling IPv6 etc.

---

### Post by lionel47 on 2008-07-12
I got frustrated with this, too.  So I installed Mandriva because I couldn't figure out why Ubuntu was behaving this way and I really don't have the time to debug.  Well, Mandriva is doing the same thing.  Can it be a bug in the Linux kernel?:confused:

---

### Post by Sealbhach on 2008-07-12
Is it anything to do with your ISP, I wonder.

Maybe try some other DNS servers, like Open DNS?

[http://www.opendns.com/](http://www.opendns.com/)


.

---

### Post by Frenske on 2008-07-12
> **lionel47 said:**
> I got frustrated with this, too.  So I installed Mandriva because I couldn't figure out why Ubuntu was behaving this way and I really don't have the time to debug.  Well, Mandriva is doing the same thing.  Can it be a bug in the Linux kernel?:confused:

Well I thought everything was working fine in 7.10 at least if there was a problem I did not noticed it. Perhaps there are indeed issues with the latest kernels.

---

### Post by Frenske on 2008-07-13
> **Sealbhach said:**
> Is it anything to do with your ISP, I wonder.

Maybe try some other DNS servers, like Open DNS?

[http://www.opendns.com/](http://www.opendns.com/)


.

What I gather is that Ubuntu itself becomes slow and not really the internet. The slow internet is a result of ubuntu not handling the data quick or correctly. You would think that a 2.66GHz processor would handle a 5Mb/s data stream easily.

---

### Post by HarmonicaGoldfish on 2008-07-13
I had this issue with earlier versions of ubuntu and it had to do with ipv6. Now, I disable ipv6 from the getgo each time I install a new version and don't have any problems.

To configure ipv6 for your browser (firefox):

open up firefox
type about:config

in the 'filter' area type ipv6

double click on it to make sure the value is set to true.

To configure it system-wide:

Check out this thread:
[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

Hope this helps

---

### Post by lionel47 on 2008-07-13
OK, I am back on Ubuntu.  Here is the deal: it appears that Ralink drivers are causing trouble for Ubuntu 8.04 users.  My guess is that it is a kernel thing because the same thing occurred on Mandriva on the same machine for me.

After a bit of Googling, I found [this thread]("http://ubuntuforums.org/showthread.php?t=400236") which talks about using the Serialmonkey Ralink drivers instead of the out of the box kernel drivers.  In fact, it shows you how to blacklist the OTB drivers.

I tried it and lo and behold, I have my fast network connection again.  Hope this helps.:)

---

### Post by Sealbhach on 2008-07-13
> **lionel47 said:**
> 
I tried it and lo and behold, I have my fast network connection again.  Hope this helps.:)

Yay! Well done. I wonder has it been reported as a bug on launchpad?


.

---

### Post by Vishal Agarwal on 2008-07-13
This is not related to your problem exactly. But this can help you analyzing the problem. just install one package iftop. This is a command prompt package and it will show you the bandwidth utilization.

So you will exactly be knowing what speed u are getting from your ISP.

---

### Post by Frenske on 2008-07-14
Aaaah ... now I don't have internet at all!!!! Well at least it is not slow, but not really what I wanted. 

The 'sudo dhclient wlan0' returns nothing (well an error actually), but 'iwlist wlan0 scan' shows there is a connection. Perhaps it has to do with the WPA/WEP code.

---

### Post by lionel47 on 2008-07-14
Yeah, you might want to consider editing the /etc/network/interfaces file with your settings.  Here's mine as an example:

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid hiddentiger
pre-up iwconfig wlan0 key restricted 9687654321c657f7cac0c0puffaad
```

Good luck.

---

### Post by Frenske on 2008-07-14
Pfff ... I got it finally working. The code I needed was as follows:

```
auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 mode managed
	pre-up iwpriv wlan0 set EncrypType=TKIP
	pre-up iwpriv wlan0 set AuthMode=WPAPSK
	pre-up iwconfig wlan0 essid WIRELESSNAME
	pre-up iwpriv wlan0 set WPAPSK="12345678101112"
	pre-up iwconfig wlan0 essid WIRELESSNAME
```

Now the test with [www.speedtest.net](www.speedtest.net). Remember I got 5500kb/s for download speeds on Windows XP. Taadaa, I got now 6618kb/s, a whopping increase of 20%. Bill Gates can eat my internet dust!!!

I think I am falling in love with ubuntu again! :)

---

### Post by Sealbhach on 2008-07-15
> **Frenske said:**
> Pfff ... I got it finally working. The code I needed was as follows:

```
auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 mode managed
	pre-up iwpriv wlan0 set EncrypType=TKIP
	pre-up iwpriv wlan0 set AuthMode=WPAPSK
	pre-up iwconfig wlan0 essid WIRELESSNAME
	pre-up iwpriv wlan0 set WPAPSK="12345678101112"
	pre-up iwconfig wlan0 essid WIRELESSNAME
```

Now the test with [www.speedtest.net](www.speedtest.net). Remember I got 5500kb/s for download speeds on Windows XP. Taadaa, I got now 6618kb/s, a whopping increase of 20%. Bill Gates can eat my internet dust!!!

I think I am falling in love with ubuntu again! :)

Awesome!!! :guitar:


.

---

