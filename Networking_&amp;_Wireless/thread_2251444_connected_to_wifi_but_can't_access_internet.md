---
title: "connected to wifi but can't access internet"
date: 2014-11-04
forum: Networking &amp; Wireless
---

### Post by K12963 on 2014-11-04
I have a wee Acer netbook running Xubuntu 14.04. Wifi claims to be connected and at full strength. I attempted with Chromium and Firefox, but they wouldn't connect to the internet.  I can't download anything from Ubuntu Software Center either.  I have an iPhone, another Xubuntu machine, and a Windows machine all of which work fine with the wifi.  The problem machine has previously connected to different wifi without a hitch.  I am very new to Linux, so please be gentle!

---

### Post by Hadaka on 2014-11-04
Hi,With a wred working connection please open a terminal and then
COPY and paste this..
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
this creates a wireless-info-text file in your home directory,post that file here so you may be helped.
more info on this process..please read.
```
http://ubuntuforums.org/showthread.php?t=370108&
```
thanks.

---

### Post by K12963 on 2014-11-06
.

---

