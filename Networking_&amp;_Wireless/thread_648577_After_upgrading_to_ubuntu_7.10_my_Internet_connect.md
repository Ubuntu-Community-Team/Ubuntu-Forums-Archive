---
title: "After upgrading to ubuntu 7.10 my Internet connection is slow"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by devinWhalen on 2007-12-23
Hey,

I recently moved from a dual boot with WinXP and ubuntu 5 to just ubuntu 7.10.  After I did this my internet speed is quite a bit slower.  I have seen other people with this issue but I have not been able to fix it the way they did (such as disabling ip6).  I have a high speed dsl connection.

What configuration program should I be using:
pppoeconf or pppoe-setup

Here is some info on my machine:
2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
00:0a.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP


Thanks for any help.

---

### Post by csat on 2007-12-23
Try disabling IPv6 setup from your browser (firefox).  It is simple and you can do it fast.  Just type  about:config  at the URL field.  A full list is gone be shown.  At the filter field type IPv6 

A single line is going to be shown, like this below:

network.dns.disableIPv6

Highlight it with your cursor and click it twice changing its value to "true".  Shutdown firefox and call it back again.

---

### Post by devinWhalen on 2007-12-23
Thanks for your help.  Unfortunately, I found this same 'fix' while searching the web and it didn't change anything.

Any other ideas?

Thanks

---

### Post by Quiane on 2007-12-23
you could try following this guide to speeding up firefox...it worked well for me, but i'm still having a lot of trouble with my bittorrent d/ls.......
but this sped up my browsing very nicely...
(and yes, it does talk about the ipv6 stuff..but there are a lot of other things in the guide)

[http://ubuntuforums.org/showthread.php?t=107370&highlight=speed+firefox](http://ubuntuforums.org/showthread.php?t=107370&highlight=speed+firefox)

---

### Post by samol on 2007-12-23
I just spend the better part of 2 days reading the boards trying
to find a fix for my slow ethernet connection on Gutsy 7.10. I tried pretty
well everything suggested by various posters but nothing helped. My main machine was ok..  

I kind of gave up and then thought i'd try a different browser so I downloaded
and installed Opera 9.125 and this really speeded things up. Problem solved. 
My internet is now pretty fast and this on a Pentium2. Works great for an old
machine. Ubuntu rocks. Looks like Firefox 2 was the problem so I installed Opera
on my other (P4) machine and that one is now browsing faster as well.

Hope this helps some of you.
Dave

---

### Post by BrianElliott0218 on 2007-12-24
I have read through the posts on this and have still not found a solid solution.  I have not yet used torrent downloads and uploads, but I did use [www.speedtest.net](www.speedtest.net) to checkout the download speed on this machine...  I have to say I am surprised.

[[IMG]http://www.speedtest.net/result/214994090.png[/IMG]](http://www.speedtest.net)

My uploads were almost 2X as fast as dls.  What is up with that?!?

I really love ubuntu and have only been playing around with different flavors of it for a few weeks, but this is not conducive to my being able to sell other users on it.  I really think this problem should be addressed.

For me it has been not only Firefox (mine is still slow after squelching IPV6), but also when downloading packages in apt.

Solutions please?
brian-newubuntu:confused:

---

### Post by Kobalt on 2007-12-24
> **BrianElliott0218 said:**
> I have read through the posts on this and have still not found a solid solution.  I have not yet used torrent downloads and uploads, but I did use [www.speedtest.net](www.speedtest.net) to checkout the download speed on this machine...  I have to say I am surprised.


My uploads were almost 2X as fast as dls.  What is up with that?!?

I really love ubuntu and have only been playing around with different flavors of it for a few weeks, but this is not conducive to my being able to sell other users on it.  I really think this problem should be addressed.

For me it has been not only Firefox (mine is still slow after squelching IPV6), but also when downloading packages in apt.

Solutions please?
brian-newubuntu:confused:
How do you connect to the Internet? How did you set up your connection? (drivers, security, etc...)

---

### Post by guyvertoon on 2007-12-24
I had a similar issue when I switched to FIOS and posted the fix that worked for me...

[http://ubuntuforums.org/showthread.php?t=640720](http://ubuntuforums.org/showthread.php?t=640720)

HTH

---

### Post by devinWhalen on 2007-12-24
Well, I am glad I am not the only one having these problems.

I don't think that this is a browser issue, it is fine to tweak the browser speed (which I did) but this needs to be solved at a lower level.  However, I will try Opera when I get home from work today just to make sure.

I configured my dsl with ppoeconf from the command line, is that the right program to use?  I am hoping that this is just a settings issue so that it can be fixed with some minor conf editing.

---

### Post by gfuggs on 2008-01-03
After switching over to Ubuntu from Windows XP last week, I was having a slow internet connection problem.  I read a bunch of mumbo-jumbo about ipv6 and did all that, but it didn't do anything.

I just figured out a fix for my problem-
Open your network settings, and go to the DNS tab.  Is your router on the top of the list of DNS servers?  If so, click on it, delete it, and then add it back so it's on the bottom of the list.

---

