---
title: "[SOLVED] can't connect tointernet through wireless lan"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by dmancini on 2008-12-04
Let me start by saying that i am a complete noob.  

I have installed ubuntu 8.1 on my pc.  I am also running xp.  on this pc.  my network consists of this pc and another.  I have a d-link wda 1320 wireless card and it connects to a 2-wire wireless router.  I am sure that I am doing something wrong but don't know what.  I have entered the network key but it just brings up the same pop up prompting me to enter information.  

I apologize in advance if I am posting incorrectly.  I sould also like to thankyou in advance.

---

### Post by anewguy on 2008-12-04
I ran into this problem a year ago when I had AT&T internet and a 2-WIRE wireless router/modem combination.  My problem turned out to have an easy solution - maybe it will work for you:

Be *SURE* you select the correct type (WPA/WEP/etc.) and for the correct type (password or passkey) AND be sure the password or key you enter matches exactly in case, etc., the password on the router.  Since you can connect with this same PC in Windows, it won't be a MAC filtering issue at the router.  For your wireless on your PC in Linux - did you install a driver?  Does your wireless network show in the list from network manager?  Also - if you have your router set to not broadcast the SSID I have had trouble getting Linux to connect as well - I had to manually specify a connection and get everything exactly right.  Also, if using WPA, be sure wpa-supplicant is installed and running.

Dave ;)

---

