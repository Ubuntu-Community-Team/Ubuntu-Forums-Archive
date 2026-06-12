---
title: "lost my Wireless ability"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by clikc on 2007-09-20
ok so on my insparion 1505, i have been useing wireless for the last 3 months with no problems,it was also working just fine this morning, now i logged in to my system, with ubuntu 7.4 and the wireless function isn't available, when i go to the ikon it states that my options are wired networks, it states that my networks are set to manual config, is there a way to put this back to automatic??? it was working really well.

thanks in advance.

clikc--

---

### Post by bgr on 2007-09-20
Yes yes.... I have had the same experiance. Last night I was able to somehow link up with my wr850g wireles router using my d-link ag530, then I moved the computer to attemt a better signal, and completly lost the ability to connect to any wireles network (as there was more than on showing in the util...) I have since moved the computer back upstairs to make sure that it can sense the wireless signal, but I cannot seem to get the option for any wireless!!!

---

### Post by MrBordello on 2007-09-20
my wifi (IPW3945)  is "half-broken" here since the last update. It authenticates properly but gets a completely wrong IP.
My AP has 192.168.0.1 and gives me (mostly) the IP 192.168.0.22, but since the my last reboot it gets me IP 192.168.1.2 from 192.168.1.1... strange.
Does your wifi authenticate (can be seen on the applet-icon)? Are you using Feisty or Gutsy?

---

### Post by bgr on 2007-09-20
I am using feisty, and I am not sure if it shows up in the applet. What I do know is that I may find some sucess if I was able to install madwifi or nidiswrapper...help total noob

---

### Post by MrBordello on 2007-09-20
Oh, I think can help you!
left-click on the applet-icon -> manual configuration -> double click on your wifi adapter -> checkbox "roaming" -> ok
should work...

---

### Post by bgr on 2007-09-20
ok , I get it. yes when I enter 192.168.10.1 I can interface with the router... still no way to enable the wireless network...

---

### Post by MrBordello on 2007-09-20
enter where?

---

### Post by MrBordello on 2007-09-20
another idea:
go to your home folder, view -> show hidden files and move the folder "networking" in .gconf/system/ to another location (or delete it) log out and back in (or reboot).
could help ;)

---

### Post by bgr on 2007-09-20
sorry, iwas refering to interfacing with the wireless router via my browser. Anyway I have tried to find a way for feisty to recognize my PCI card but no matter what I try, Ie I have downloaded Madwifi and ndiswrapper, the problem is that I am not familiar enough with the process of installing software on this os. I have thje files in the download manager but the installation instructions read like romulan and even though I have followed the directions to a t I have had no sucess. Thank you for responding... I really appreciate it. Truly frustrated noob

---

### Post by bgr on 2007-09-20
ok. so I opened the hidden files and was unable to locate the folder. I can see .gconf and .gconfd ???

---

### Post by Taino on 2007-09-20
Hmm..

In a Terminal window type..

iwlist scan

And see what connections come up, i usually do this at an internet cafe and then take the ESSID from there and activate my connection at that location.

So yeah, first scan to see if you can even see the active connections, then work on connecting thru Ubuntu's WIFI config.

If you cant even see a connection you may have driver issues.

---

### Post by MrBordello on 2007-09-20
but your wifi already worked? So I don't think, that you have to install anything. Try this: Open a Terminal. Err... I'm using german language here... you should find it under Applications -> Tools? -> Terminal I. hope.
then enter this:
```

mkdir ~/OLDCONFIG
mv ~/.gconf/system/networking ~/OLDCONFIG

```
and reboot. Good Luck!

> So yeah, first scan to see if you can even see the active connections, then work on connecting thru Ubuntu's WIFI config.
sounds logical - try this first!

---

