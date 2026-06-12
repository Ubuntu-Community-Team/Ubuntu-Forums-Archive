---
title: "HP Pavilion dv6000 - Wireless problems"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by pozqe on 2007-10-03
Hi, I've been trying Ubuntu for two days no..Just installed in on my HP Pavilion dv6000 laptop, but I can't get the wireless network to work. I use GNOME, and I have tried several guides about how to fix it. Some requires internet, which I try to get to work so that's kinda lame and the others doesn't help. I've tried with the Synaptic thingy and Ubuntu CD. I just tried a guide and now I can't even choose Wireless in the "Network Settings" window. A guide said that if I have Broadcom 43xx card it might show as "Dell Wireless 1390 WLAN" and mine showed as that, but still didn't get anything working by following the guide.

-Thanks for helping =)

---

### Post by kevdog on 2007-10-03
Follow this guide:
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

### Post by enetic on 2007-10-06
make sure that your wireless cardlamp is showing a blue light not red. that was my problem after following the guide :)

---

### Post by PRINCE1985 on 2007-10-08
I have that problem! My wireless card light is always red, and never become blue!!!
I tried so many tutorials. Now I have installed ndiswrapper with bcmwl5 and bcmwl6, but none of the two works. 
What should I do? Where the problem could be? :confused:

---

### Post by darkness_s on 2007-10-08
You could try to install ndisgtk. But first you will have to remove ndiswrapper if you compiled it. Then just open a terminal and type: sudo ndisgtk
Then click Install and select then inf file of the bcmwl5 windows drivers. The light should turn blue after that. If it works, edit /etc/modules and add the word ndiswrapper to the end of the file so the module starts every time you boot the computer. This worked fine on my computer, which is a dv6125se. Good luck.

---

### Post by kevdog on 2007-10-08
Installing ndisgtk isnt going to do anything different than installing by hand!!!

When you mean not working, can you be more specific.  Can you post the following for me

lshw -C network
ndiswrapper -l

---

