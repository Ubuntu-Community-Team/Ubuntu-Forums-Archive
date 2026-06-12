---
title: "activate broadcom-STA without gui &quot;hardware drivers&quot;??"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-11-18
Hi, 
  So I have used 10.04 before, and it was easy via System>>Admin>>hardware drivers to download Broadcom-STA. However, I just did a "minimal" install of 10.04 + gnome-core.

  Since doing it this way there is no "Hardware Drivers" under Admin, how can I enable broadcom STA? I have already downloaded broadcom-sta-source and broadcom-sta-common. 
  
   I assume this is the problem because with WICD no wireless networks are found. 

   Thanks in advance!

---

### Post by cariboo on 2010-11-19
You also need build essential to install the drivers. If you have a wired internet connection, the easiest way is to enter the following command:

```
sudo apt-get install bcmwl-kernel-source
```

If you don't have a wired connection, have a look at [Keryx]("http://keryxproject.org/"), it will make things a lot easier for you.

---

### Post by UbuNoob001 on 2010-11-19
> **cariboo907 said:**
> You also need build essential to install the drivers. If you have a wired internet connection, the easiest way is to enter the following command:

```
sudo apt-get install bcmwl-kernel-source
```

If you don't have a wired connection, have a look at [Keryx]("http://keryxproject.org/"), it will make things a lot easier for you.


I do indeed have a wired connection. I will try this and report back, thanks for the help.

---

### Post by UbuNoob001 on 2010-11-19
> **cariboo907 said:**
> 

```
sudo apt-get install bcmwl-kernel-source
```



Okay so I now have: 

bcmwl-kernel-source
broadcom-sta-common
broadcom-sta-source 

all installed. However when using wicd/NWM I still unable to pick up wireless networks. I realize in doing a gnome-core install from minimal I will be a bit more on my own. Can anyone point me in a good direction though for doing some research? 

Thanks in advance.

---

### Post by UbuNoob001 on 2010-11-19
Simple solution:

running iwconfig yields ```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

however the default for wireless in WICD was wlan0. All I needed to do was to simply **change wireless interface in WICD from wlan0 to eth1.**

thanks again to cariboo907 as installing kernel-source was a necessary step.

thread marked as solved.

---

