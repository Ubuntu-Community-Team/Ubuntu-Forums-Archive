---
title: "Wireless help please."
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by wobwill on 2007-08-25
Hi,

I am still new to ubuntu and have been trying to get wireless to work on the laptop. A previous success story is recounted in this thread. 

[http://ubuntuforums.org/showthread.php?t=525766](http://ubuntuforums.org/showthread.php?t=525766)

Since then I have reinstalled Ubunutu v7.04 following a complete loss of my /home directory and therefore being unable to login. 

Since then I have followed the advice in the wireless troubleshooting guide and also followed the advice at the following thread (apart form installing wicd - I have not done this) 

[http://ubuntuforums.org/showthread.php?t=525833](http://ubuntuforums.org/showthread.php?t=525833)

I have also attached some logs from a terminal that are the results of the commands the files are named after.

Any help or thoughts would be a great help. 

I can get a wired connection to the computer but it means my desktop has no connection (annoying :))

Will.

---

### Post by livestockPimp on 2007-08-26
how far did you follow these instructions down? at the bottom it has "modprobe rt2500" have you done this? it is not in your lsmod, and without the kernel module it will not work.

---

### Post by kevdog on 2007-08-26
Ok, your device should be fairly straightforward to get up and running, although Im not exactly sure how far along you are in the process.  To restart all the way back at the beginning I want you to read the following thread about 3 times before doing anything.  Its about installing the rt73 driver (instead of the rt2500 driver) EXCEPT everywhere rt73 is mentioned, substitute rt2500.  And use some common sense, I dont want you blacklisting the rt2500 driver since this is the one you are using.  Anyway here is the thread, post back if you need some more help, this shouldnt take you long to get up and running :)

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

---

### Post by wobwill on 2007-08-26
Thank you both for your replies to my question. 

I am currently at work and will follow the advice you have given. 

Will.

---

### Post by wobwill on 2007-08-27
Hi, 

After having read both of your thoughts and advice and having read through the thread that Kevdog pointed me to I did the following in this order

1 - opened the blacklist file and removed the entry for rt2500.

2 - followed the WifiDocs/WirelessTroubleShootingGuide and got stuck at point 3.2.5 - driver looks OK, device disbaled.

3 - followed almost to the letter (substituting rt2500 for rt73 throughout and from point 14 ra0 for wlan0) the guide that Kevdog pointed me to. 

When I have worked out how to compress the terminal output i've saved to an .odt file i'll post it here for people to review.

System/administration/network in the  connection tab shows a wireless connection. All the correct info is in properties. 

Will

---

### Post by wobwill on 2007-08-27
Hi,

have split the file into three parts, all attached, I hope that someone can tell me exactly what I am doing wrong.

Will.

---

### Post by wobwill on 2007-08-27
Just to make it clear, I am still not able to connect wirelessly.

Will

---

### Post by kevdog on 2007-08-27
Few points:

1. Can you try without WEP? --(**Note to me --  your using WEP128 with 26 hex characters)
2. Can you post the following:
lshw -C network
modinfo rt2500
/etc/iftab

Can you post your essid line exactly as you typed it?

---

### Post by wobwill on 2007-08-27
Hi Kevdog, 

Attached is some of what you asked for but I can't get access /etc/iftab as I am told either the command doesn't exist or that I don't permission to access it (have tried sudo and gksu prefixes with out success).

Also have not tried to connect without the WEP key yet as I share my wireless with housemate. (The router and connection is mine but they piggy back onto it). I don't want to alter router settings while they are connected, but will do so once they have finished with it.

Will.

---

### Post by wobwill on 2007-08-27
Hi Kevdog

Essid line as requested (lifted from terminal output part 3)

Orignial input was a copy paste from the post you pointed me to apart from changing wlan0 to ra0 and putting in the network name (in lower case).

**william@william-laptop:/usr/src/rt2500-cvs-2007082705/Module$ sudo iwconfig ra0 essid ***********

will

---

### Post by wobwill on 2007-08-28
:redface: cheeky bump to the top.

Will

---

### Post by wobwill on 2007-08-30
Hi,

Does anyone have any more thoughts on this issue?

I still cannot connect to the internet wirelessly. 

I am wondering if my laptop (fujitsu siemens amilo D 7800) has disabled the wireless card and if so how I activate this. 

Will

---

