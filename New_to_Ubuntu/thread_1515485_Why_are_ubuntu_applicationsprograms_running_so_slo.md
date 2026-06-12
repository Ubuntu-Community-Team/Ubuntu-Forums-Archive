---
title: "Why are ubuntu applications/programs running so slow? :("
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Therisis on 2010-06-22
Hi, i recently installed ubuntu linux on my PC, and then found out that must programs are soooo slow. I don't believe my specs are that bad, if i can play Crysis on windows on MAX settings, why cant i run ubuntu? Well, its not ubuntu its self, but for example, ANYTHING i run in fullscreen, is basicly a lag attack. Plus i cant run any of the 3D games i get from the application thing. My specs;
Intel Core 2 Quad Q8800 2.6 GHZ
5GB ram
1TB Solid Hard Drive
nVidia GT 220
HELPZZ?? :3

---

### Post by hackerseraph on 2010-06-22
Are you using compiz? while running games, you might want to temporarily set your window manager back to metacity.

an easy way to switch back and forth is by using the tray icon "Compiz Fusion Icon"

```
sudo apt-get install fusion-icon
```

you can run it by going to applications > system tools > compiz fusion icon



oh and congrats on your first post. welcome to ubuntuforums.org

---

### Post by Paqman on 2010-06-22
Have you got your video card drivers installed? Go to System > Admin > Hardware Drivers and install the latest Nvidia driver.

---

### Post by lkjoel on 2010-06-22
Click on LinuxEssentials in my sig.
Extract it, then in a terminal window (Applications->Accessories->Terminal)
```
chmod +x FASTGNOME.sh
./FASTGNOME.sh
```
That will speed things up. (Assuming you are using GNOME)

---

