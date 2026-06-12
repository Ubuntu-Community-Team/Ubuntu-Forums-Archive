---
title: "Ubuntu 16.04 Belkin F9L1101v1 Problems"
date: 2017-05-14
forum: Networking &amp; Wireless
---

### Post by Gwiffleez on 2017-05-14
Hi all,
I recently decided to switch from WIndows 10 to Ubuntu 16.04 on my desktop computer because I am more comfortable all around with Ubuntu. I do have a USB Network Adapter - the Belkin F9L1101v1 - and I've had some trouble getting it to work. Some things I have tried:
[LIST=1]
[*]ndiswrapper with bcmwlhigh5.inf (Windows XP Driver), and bcmwlhigh6.inf (Both the Vista and Win7 drivers).
[LIST=1]
[*]Side note, the best that has happened was with the bcmwlhigh5.inf file. I am able to get momentary internet access, but after a second or two any internet calls time out.
[/LIST]

[*]I have tried a good amount of the drivers on github, including rtl8192du. These did not work.
[/LIST]

One thing I've noticed is that I can ping my router, but if I try to ping google.com or 8.8.8.8 the requests time out. Looking at the results of the wireless-info script that was stickied here, it looks like I do not have an IPv6 gateway set (this might be the problem?). I'm not great with networking stuff but I was able to install dkms and ndiswrapper by downloading the .deb files from my laptop (which I'm posting from), putting them on a Flash Drive, and installing with dpkg on my Desktop. I've attached the .tar.gz file to the post and the output of the script is located here: [https://pastebin.com/7VC5HhT8](https://pastebin.com/7VC5HhT8) . Any help would be much appreciated!
Thanks,
Griff

[ATTACH]275118[/ATTACH]

---

### Post by Gwiffleez on 2017-05-15
I've just been trying everything here; I want to make this work, not just pass it off. I ended up downloading the firmware-b43-installer package onto a USB Stick and used dpkg to instal it. I added the noted lines to my blacklist. None of that helped anything. I have been messing around with other stuff, but I have only had those sweet few seconds of internet before everything comes crashing down and I have to reboot. Is something possibly wrong with my router? I am able to use this router on a Windows machine.

---

