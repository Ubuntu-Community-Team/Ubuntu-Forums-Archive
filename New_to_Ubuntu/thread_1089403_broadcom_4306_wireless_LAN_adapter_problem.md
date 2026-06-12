---
title: "broadcom 4306 wireless LAN adapter problem"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by lewis595959 on 2009-03-07
Ok, here's my story:

I live in a university dorm, and I just installed ubuntu 8.10 - keep in mind that i'm a complete newbie.

I'm using a broadcom 4306 WLAN adapter, but I have no idea how to make it work. When i click on the icon on the taskbar, it doesn't show any networks to connect to, and I ran a command in the terminal that showed me that the device was disabled. Unfortunately, I don't know how to enable it. I tried going to  System > Administration > Hardware Drivers, but It's not being any help. When that window opens up, It tells me that first, there are no proprietary drivers in use on my system. Second, it tells me that I need to install an ATI/AMD FGLRX driver. Obviously this is for my GPU, but when I click the activate button a window pops up for less than a second saying "downloading and installing driver" (with a progress bar of 0%). 

I am currently wired through my laptop which runs windows XP, using that for an internet connection. In case it matters, my dorm wireless network uses PEAP for authentication.

I know I have zero clue what i'm doing, but i'm interested in staying with ubuntu. Any help is much appreciated :)



(i am quite knowledgable when it comes to windows computing, but - like i said - i'm a complete newbie to linux. I'm also quite drunk while posting this, so feel free to post any questions for me to clarify in the morning when i sober up :D)

---

### Post by iamkrazee on 2009-03-07
So that is actually two problems in one post. 

The jockey part for fglrx.. it will get you through, just have patience. It is approximately a 30mb download, so do the math according to your bandwidth.

As for the wireless adapter part, could you tell us what driver is it that you see in your jockey(Proprietary hardware drivers thing)? There is an issue with certain models, that once the driver is enabled, it works and goes away on reboot. Examine which of these exactly is your problem and report back.

Also, run iwconfig and post output here.

---

### Post by iamkrazee on 2009-03-07
run following codes and give outputs here.

1. ```
iwconfig
```

2. ```
jockey-gtk -l
```

3. ```
cat /etc/modules
```

---

### Post by lewis595959 on 2009-03-08
Hey, thanks for the reply. I managed to work out the problems on my own, but I have a new problem.. my university has a downloadable installer to connect to the wireless network on campus. The network uses PEAP, but I can't manage to authenticate without installing the wireless app. However, my problem is this: the app is a .exe file, and i can't find a way for it to work through wine.. ideas?

---

### Post by Lostin60's on 2009-03-09
> **lewis595959 said:**
> Hey, thanks for the reply. I managed to work out the problems on my own, but I have a new problem.. my university has a downloadable installer to connect to the wireless network on campus. The network uses PEAP, but I can't manage to authenticate without installing the wireless app. However, my problem is this: the app is a .exe file, and i can't find a way for it to work through wine.. ideas?

check out this post

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

if ndiswrapper will see your .exe file as a driver this post will get you going.
[COLOR="White"]aa[/COLOR]

---

