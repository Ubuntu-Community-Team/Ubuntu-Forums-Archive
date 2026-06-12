---
title: "BroadCam Wi-Fi Driver Not Recognized"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by WubiNoob on 2010-02-17
Hi Ubuntu forums,
This is my first post, and needed some help with hardware that lots of other people have, and might have problems with as well. Yesterday, I installed Ubuntu 9.10 Desktop on my HP Pavilion dv4 1123us using Wubi on a live CD. The installation was great, and everything's working, exept a Wi-Fi Driver. In case it matters, the name of this wi-fi driver is: BroadCam 4322AG 802.11a/b/g/draft-n Wi-Fi Adapter.
 
I have used the Hardware Drivers application to search for any drivers not being used, but it can't recognize it. (PS: I have had Linux Mint in the past, and even installed on my HD, it knew they were there, but it could not activate them without an internet connection)
 
I don't have easy access to the Router I use, and was wondering if I could use somthing like a terminal command to activate the driver permently. (The weird part: It works in the Live CD mode, but not installed on the computer)
 
Thanks, Help is appreciated.

---

### Post by Greenwidth on 2010-02-17
The drivers you want (STA) are on the LiveCD (it's why the wireless works when using it) and in the repos, they are not included in the installation because they are not open source. 

If you can't get access to a wired connection, see section 2 of:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by WubiNoob on 2010-02-17
Thanks, the information was exactly what I needed. :D

---

### Post by lidex on 2010-02-17
Broadcom, eh? Have a look here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless")
Ah, I see you got it working. Bookmark this site as it addresses a lot of issues with HP series notebooks with ubuntu.

---

