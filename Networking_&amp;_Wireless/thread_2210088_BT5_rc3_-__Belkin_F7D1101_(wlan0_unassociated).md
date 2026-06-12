---
title: "BT5 rc3 -  Belkin F7D1101 (wlan0 unassociated)"
date: 2014-03-08
forum: Networking &amp; Wireless
---

### Post by pedro12 on 2014-03-08
Hello,

I'm new to linux and I'm having trouble setting up my belkin f7d1101 wireless usb adapter onto BackTrack 5 rc3 which I installed on Virtual Box. I'm attempting to get a connection in order to make use of monitor mode.

I've followed the steps on this topic: [http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815) , and this is where I'm at right now:

iwconfig:
> lo
no wireless extensions.

wlan0
unassociated Nickname: ''rtl_wifi''
Mode: Auto Access Point: Not associated Sensitivity: 0/0
Retry:off RTS thr:off Fragment thr: off
Encryoption key: off
Link Quality: 0 Signal Level:0 Noise Level:0

eth0
no wireless extensions

When I try ''iwconfig wlan0 mode monitor'' I get the following error:
> Error for wireless request ''Set Mode'' (8B06) :
SET failed on device wlan0 ; Invalid argument

Here's lsusb (detecting my belkin):
> Bus 001 Device 003: ID 050d:945a Belkin Components F7D1101 Basic Wireless USB Adapter v1000 [Realtek RTL8188SU]

When I go onto Wicd Network Manager, I detect my home network but fail to connect to it due to ''Bad password'' although the password is correct..

I've done a lot of research on google and on this forums but it seems to take me nowhere and I'm feeling kinda hopeless and lost :/ 

What do I have to do to get my Wireless adapter properly detected and working, ready to be turned onto monitor mode?

Thanks :(

---

### Post by chili555 on 2014-03-11
Please see here: [https://wikidevi.com/wiki/R8712u](https://wikidevi.com/wiki/R8712u)> **Monitor mode:** unsupported So you are asking your device and driver to do what it's not designed to do. 

My friend's 400 hp BMW won't get 40 mpg, either. 

We haven't answered up to now because; first, we aren't Backtrack forum and second, we can't give you a solution because there isn't one.

---

