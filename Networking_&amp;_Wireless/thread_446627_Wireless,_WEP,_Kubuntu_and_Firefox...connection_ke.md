---
title: "Wireless, WEP, Kubuntu and Firefox...connection keeps dropping."
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by keith11 on 2007-05-17
This might be one of my several posts describing my wireless problems yet again. I have tried following the howto's, troubleshooting, disabling ipv6, changing channel no., uninstalling/installing several network managers, reading forum posts as well as launchpad posts, filing a bug report on launchpad, etc. BUT I have never found a solution to my problem since 6 months. I was using Ubuntu  Edgy before I installed Kubuntu Feisty from scratch and the problem just doesn't go away.I can't put the frustration in words.

The worse part is that it works sometimes and doesn't other times so one can;t tell after all what's wrong. I connect to a wireless connection (I don't know how many times I have described my problem over and over again in this as well as other forums) which uses a WEP encryption. I am using Firefox 2.0.0.3 to connect. I have tried the troubleshooting guide for Firefox which is posted on Firefox's support website but it didn't help either. Everything works fine in my university which doesn't have any encryption on the wireless connection but at home, with the WEP encryption and the above mentioned configuration, it's an unbelievable mess. I even tried using opendns servers but it doesn;t make any difference at all. The connection is established for a while and suddenly drops at any time. This is not the case with my Windows XP installation. Everytime I face the problems in Kubuntu I try booting into Windows and test whether the connection itself is problematic but I can connect fine through windows, so apparently there is some problem in Kubuntu (the config I have) but I have not been able to figure it out for 6 months now no matter how much I have tried. I  have even tried using Opera to no avail. I have a Toshiba centrino with an Intel Pro Wireless card. It's extremely (even this is an under statement) frustrating. Is anyone facing the same problems? I never got an answer from launchpad even after more than a month so I gave up on it. I would truly appreciate if I can get sincere help regarding this issue. Thanks a ton.

Keith.

---

### Post by keith11 on 2007-05-17
I wanted to add this that whenever any of the browsers get stuck on a message like "waiting for...", I can still ping a website through the console (not always, but most of the times). So I wonder why the browsers can't download webpages and also why the connection itself drops.

I just noticed that after I connect and open swiftfox, it downloads my homepage and there's a message in the status bar of swiftfox saying "waiting for www.yahoo.com" and it stays that way. When I click on a link, it doesn't open any web page and luckily if it opens a new tab it just gets stuck at the "waiting for..." message and eventually it will die down opening no page. This is happening very consistently and just after I connect and open a webpage. Again, I can ping a website, but can;t download pages after the initial homepage. I re-enabled ipv6 thinking it might be causing the problem but it's not the case. I had changed the rate of my connection through "sudo iwconfig eth1 54M" after reading a troubleshooting document on Ubuntu forums and i changed it to 24M as thats the connection strength it shows in windows. This issue is very critical for me. Any suggestions/comments are more than welcome. Thanks.


Keith.

---

### Post by mileswilliams on 2007-05-18
I get the same as you ... I only got wireless going last night so I haven't had a play around with the settings.

I'm using a compaq machine with a USB netgear WPN111 wireless dongle. 500Mb Ram and loads of drive space. I was going to try Opera but I guess I won't bother.

Next test for me is moving my machine next to my router.

Then removing WEP / channels etc.

I have noticed that when the connection drops, CPU usage hits 100 percent on the system monitor graph, it bounces along for a short while, maxing out then when the CPU usage drops it attempts a reconnection.

I'll let you know how I get on.

---

### Post by Matty2006 on 2007-05-18
Im not really and expert at this but I thought I might put in two cents :)

I have seen this kind of problem with older netgrear cards too even in Windows, but more so when there is many wireless networks in the same area. I have not figured out how to resolve it. I was working on connecting a few desktop machines wireless to linksys router trying WEP and whatnot and it would work for maybe no more than a few minutes than loose it. I ended up removing the cards and just wiring it all. Its pretty annoying because the problem teases you.. Like it wants to work then does not. Maybe the firmware and drivers.. not sure.


I am using the NdisWrapper and the native windows driver for my dell 1530 card and do not have any trouble with this.. I also did not make any special adjustments for this card. Only followed the ubuntu wireless howto. I connect fine to WEP and unsecured.

I would say try a different card. Stay away from Belkin. I have had much better experience with Cisco and intel cards as they are natively supported as well.

---

### Post by keith11 on 2007-06-05
Any suggestions anyone? I have been struggling with such issues and other wireless connection problems for 6 months now. I boot into Kubuntu 7.04 with zeal and then when the wireless starts acting and does that again and again and again, it becomes so disappointing everytime that I eventually boot into windows and stay in windows for days before daring to boot into kubuntu  and then again going back to windows.

---

### Post by keith11 on 2007-06-08
Can someone please help me figure out the problem? Thanks.

---

### Post by dardack on 2007-06-08
I'm getting the same problems man.  I'll be playing WoW and connection dies, comes back in in like 45 seconds to 1.5 minutes.  And does it over and over again.   Haven't tried disabling WEP (not that i want an unsecure Network connection).  Haven't tried disabling IP6V though.  I am at a loss.

---

### Post by krasty75 on 2007-12-11
Hi all.

I have just started in the Linux world and after reading a lot of info, I decided to start working with Ubuntu. 

I'm suffering the same problems with the wireless. I have installed EDUBUNTU 7.10. The thing I have realized is that the wireless connection works fine when connecting to an "unsecure" wireless network (thanks to my neighbour), but when I try to connect through my router (with WEP encryption) it seems to be connected, but monitoring with "ifconfig" and "netstat" I can see packets dropped.

When I use the Ubuntu Desktop 6.10 live CD to start the computer, I set up the wireless through my router with the WEP encryption and it connects really fine.

I've been searching at other linux forums and I have found this link: [http://www.fentlinux.com/web/?q=node/2462](http://www.fentlinux.com/web/?q=node/2462)          [it's in spanish]

There they suggest this other 3 links where you can find info about how to set up wireless connections in Ubuntu. I'll try to put on working this afternoon and I'll let you know if it works.

These are the links:
1.- [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)
2.- [http://ubuntuforums.org/showpost.php?p=1084114&postcount=43](http://ubuntuforums.org/showpost.php?p=1084114&postcount=43)
3.- [http://ubuntuforums.org/showpost.php?p=1105667&postcount=218](http://ubuntuforums.org/showpost.php?p=1105667&postcount=218)

I wish it'll work.

---

### Post by ghostdog2402 on 2007-12-17
> The connection is established for a while and suddenly drops at any time. 

I have the same problem with Xubuntu on my old pentium III. I have WEP Hex encrypted connection. I set my configuration in Network Manager to "Static Ip anddress" and it works fine but drops at any time later (cca 5-10 minutes).
I check the iwconfig wlan0, and ESSID seems to be fine.
 Then I change it to "Automatic Configuration (DHCP)" and it sometimes reconnects, but usualy i must restart my comp, or i set it back to Static. Its a real mess.
Can anyone point me in the right direction?
thanks
I have Level One 11g wireless USB adapter, and Belkin Router. (couldnt get the same adapter but think thats not the case).


I also followed this guide: (maybe it will help someone)
How To: Troubleshoot your Wireless Network Connection - Connecting at Command Line
[http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless]("http://ubuntuforums.org/showthread.php?t=571188&highlight=troubleshooting+wireless")

It worked for some time.

cheers!

---

