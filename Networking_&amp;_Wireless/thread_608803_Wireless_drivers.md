---
title: "Wireless drivers"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by desperateone on 2007-11-10
I have Ubuntu 7.10 on my machine, and everything is allright, except the fact the I can't connect to a wireless network. I've wasted some time, accomplishing nothing, and though I never planned asking for help, I really have nothing else left to do. The way I wanted to solve this problem was ndiswrapper. I had to extract the driver files, so I downloaded unshield. (cabextract doesn't extract the files I tried, namely data1.cab, data2.cab and setup.exe) Now this is where I get clueless. How the hell do I use unshield and in which files exactly are the drivers?  

Here's the link with the XP drivers. If explaining such basic, I presume, things is a nuisance, could anyone at least extract the files and send me them?

[http://dlsvr01.asus.com/pub/ASUS/nb/F3T/WLAN_XP_070117.zip](http://dlsvr01.asus.com/pub/ASUS/nb/F3T/WLAN_XP_070117.zip)


Thanks.

---

### Post by kevdog on 2007-11-10
I hope these are what you want:

---

### Post by kevdog on 2007-11-10
Hmm let me try again let me know if you have a problem with either of these

---

### Post by kevdog on 2007-11-10
If the above doesnt work try these:  ( I REALLY THINK THESE ARE WHAT YOU WANT  __ PLEASE Disregard previous post)

---

### Post by desperateone on 2007-11-10
Yeah, these files are allright, I installed it, but there is another problem. My computer displays the wireless settings no longer. I mean that when I clicked the network icon earlier, it displayed the available networks, but now there are only two options, manual config and something else, inactive (I don't remember). I tried manual cofig, but there are only dial-up settings, prompting for some phone numbers and prefixes or so, that I haven't seen in ten years.
Also, not knowing which file is the one I have to install, I installed two of them, but it says driver detected and device working anyway, for the correct one (and invalid driver for the other one). Can it have something to do with it?

---

### Post by kevdog on 2007-11-10
You have to remove the invalid driver or things are not going to work. Only one driver per device can be installed.

---

### Post by desperateone on 2007-11-10
Okay, thanks. One last thing, could you tell me how to uninstall drivers? I looked a bit and found no answer.

---

### Post by kevdog on 2007-11-10
Section from my guide:


4. INVALID DRIVER - Ive installed ndiswrapper but when I try to install the Windows driver Im getting a line that states:

```

root@dhcppc1 ndiswrapper-1.47]# /usr/sbin/ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
root@dhcppc1 ndiswrapper-1.47]# /usr/sbin/ndiswrapper -l
bcmwl5 : invalid driver!
driver : invalid driver!

```

This error usually means that there are duplicate or more than one driver installed with ndiswrapper.  The easiest way to resolve this message is to do the following:

```
sudo rm -R /etc/ndiswrapper *
```

You will then have to reinstall your windows driver via.
```
sudo ndiswrapper **********.inf  <-----Substitue the appropriate name of your inf file here.
```

---

### Post by desperateone on 2007-11-11
Well, I've installed the correct driver. I've done some searching and it seems that I am near the end, but there is, of course, a problem; where the hell is my wireless config? All guides show this window with three options, I only have two. 

[http://img111.imageshack.us/img111/4852/screenshotpp0.png](http://img111.imageshack.us/img111/4852/screenshotpp0.png)

---

### Post by desperateone on 2007-11-11
Never mind, I got it after some time. Yay.

---

### Post by kevdog on 2007-11-11
Great -- If you could post your solution it would probably aid others!!

---

