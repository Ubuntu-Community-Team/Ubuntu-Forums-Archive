---
title: "Network Manager missing some resources"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by mightyh on 2009-05-22
I recently booted my PC from Ubuntu 9.04 CD. Since this is the first time I'm getting in the Linux system I choose the option of running it from the cd to try Ubuntu instead of installing it to my hard drive. I'm a newbie with absolutely no knowledge of this system but very willing to learn. Ubuntu started real slow but I already expected that since I was running it from the cd. I was greeted with a notice that "The Network Manager could not find some required resources. It cannot continue." I presume that I cannot connect to the internet because of this problem. I use two system in my PC to connect, wired and wireless. The wired part is built-in my motherboard and the wireless is a PCI card that I added. How do I go about solving this problem to make Ubuntu work? I really want to learn Linux because I always believed that it is a good system. It is just a question of getting familiar with it to enjoy it. I have just made my first step, can somebody guide me to the next? Another question I have in my mind is that is it neccessary to install Ubuntu in my hard drive to make my first problem go away? Or is it neccessary install the drivers for Linux to make it work in my PC? Any guidance will be very much appreciated. Thanks.

---

### Post by spiderbatdad on 2009-05-22
This error is usually associated with nm-applet unable to find the icon cache. Try the command:```
gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

---

### Post by mightyh on 2009-05-23
Where in Ubuntu do I go and how do I execute that command. I am very new to Linux and this is still a virgin territory for me. Thanks.:)

---

### Post by Tibuda on 2009-05-23
> **mightyh said:**
> Where in Ubuntu do I go and how do I execute that command. I am very new to Linux and this is still a virgin territory for me. Thanks.:)

Applications > Accessories > Terminal

---

### Post by mightyh on 2009-05-23
I booted my PC with Ubuntu 8.10 by mistake instead of Ubuntu 9.10 and the system seemed to have no problems after it started. I was able to connect with the internet through Firefox and I even downloaded some missing plug-ins for my mp3 files without a hitch. Things seem to work beautifully with that version. Why doesn't it work with the latest version in my PC? Is it a bug in the system, or is the problem local within my CD? Not everything went perfect though. I tried installing it in my PC (not realizing I had an older version) and it crashed during the installation somewhere in the partitioning stage according to the notice that I got. I tried one of the options to repeat the partitioning process but the system just hung-up for a long time that I was forced to hit my PC restart button. I want to install the latest version in my PC but I need some answers to my question first. I need some help from the experts out there for this little boy lost.

---

### Post by mightyh on 2009-05-30
I finally got Ubuntu 9.10 installed in my PC using the Wubi installer. I am now finally learning more about the Linux system. I know I still have a lot to learn. One of my problem with Ubuntu is my wireless connection. I cannot connect to the internet wirelessly. I have a wireless PCI adapter in my PC and it appears that my Ubuntu does not have the proper driver for it. Ubuntu has identified it as: Texas Instruments ACX 111 54Mbps Wireless Interface. Can anybody help me get the driver for this and guide me on how to install it? At this stage, my knowledge of installation for any applications in Ubuntu is still very questionable but I hope it will improve in time. I do have the means of connecting to the internet with my wired connection and Ubuntu never had a problem with that. I had to go to the Network Manager and uncheck the wireless connection to make it work every time I boot. Any help out there is greatly appreciated. Thanks.;)

---

