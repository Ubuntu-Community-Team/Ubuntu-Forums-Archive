---
title: "(Help!) Monitoring activities on the router"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by sh_son on 2008-10-06
Hi,

I have a wireless router DI-524UP, setup with highest security measures I can configure: Hidden SSID, WPA-PSK AES-CCMP (random 63char) and MAC Address filtering and static IP. I have 6 individuals connected to the router through wireless connection. The problem is that the internet speed is extremely slow;

In Australia, you have limitation on your bandwidth usage if you use more than certain amount of data, the UP/DN speed will decrease down to about 4 kB/s which is very, very painful. It was too painful so I cracked neighbor's wireless which was using WEP key but it was 'illegal' and stealing so I'not using.

So I want to find who is using most of bandwidth, or what uses so much bandwidth. Is there any other way I can monitor my router how much traffic is going out/in and how much data it has transferred. Like Conky, it displays amount of data in Mbyte;

aircrack-ng, kismet, wireshark, airsnare, tcpdump such tools do not provide a bandwidth measure.

Yes I have logging feature in the router but I do not really prefer using it. Either in XP or Ubuntu is fine.

I appreciate your help and please understand my bad English.
Thank you in Advance.

     - Eric

---

### Post by ajgreeny on 2008-10-06
Right click in an empty area of your panel and choose "Add to panel".Add the network monitor from the list and when you click on that it tells you kb or mb in and out at that particular moment.  I suspect there are other utilities available but have always found that to be the simplest.

---

### Post by jrasmussen0 on 2008-10-06
Look at ntop, etherape, and iftop.  Etherape is a gnome based application whereas ntop and iftop are curses based which help when ssh'ing into boxes.

---

### Post by sh_son on 2008-10-07
> **jrasmussen0 said:**
> Look at ntop, etherape, and iftop.  Etherape is a gnome based application whereas ntop and iftop are curses based which help when ssh'ing into boxes.

Thanks for your recommendations, I will give those a try when I reinstall ubuntu;

---

### Post by medya on 2008-10-08
to see your internet speed in real time use [netspeed]("http://blog.shevin.info/2008/10/see-your-internet-speed-in-moment-just.html") gnome applet.

---

### Post by rocksockdoc on 2011-07-19
> **medya said:**
> to see your internet speed in real time use [netspeed]("http://blog.shevin.info/2008/10/see-your-internet-speed-in-moment-just.html") gnome applet.

I installed "netspeed" from the "Ubuntu Software Center" but I can't find where it installed.

It does not seem to be on the menus; and it's not in my path.

An "sudo updatedb" and "locate netspeed" doesn't seem to locate a binary.

Once installed, HOW do you execute netspeed?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197846&stc=1&d=1311130201[/IMG]

---

