---
title: "Can't use wireless on Dell Inspiron 17R"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by card_ace on 2011-04-19
i recently got a Dell Inspiron 17R as a graduation gift with Win. 7 Home Premium.  I dual booted with ubuntu 10.10 64 bit.  Everything is working great except when I'm in ubuntu my laptop won't find any wireless networks.  When i go to the top corner to the network symbol and click on it, it only shows wired networks and VPN, not even an option for wireless.  Is there a driver I'm missing or will wireless just not work?

---

### Post by ttshivers on 2011-04-19
Your wireless card might have to use a restricted driver in order to work.  Here are some instructions on how to enable a restricted driver for your wireless card: [https://help.ubuntu.com/8.04/hardware/C/restricted-manager.html]("https://help.ubuntu.com/8.04/hardware/C/restricted-manager.html")

---

### Post by card_ace on 2011-04-20
when i try to go through the restricted drivers when I'm plugged in online it just tries to update the entire system, which i can't do because I have limited internet usage per month.  But when I access it when i'm not online it says there are no restricted drivers in use by the system.  Do i have to update before it will let me find it?

My wireless card is "Dell Wireless 1502 802.11b/g/n" from the specs of the website where it was purchased.

---

### Post by TBABill on 2011-04-20
You can install it right from the liveCD or DVD. What I normally do is tell the installer to apply restricted apps during the install. I'm not 100% sure if you have to do updates at that time or can just leave that option unchecked. I always apply them, but I understand why you would like to wait.
 
Anyway, I click the "install proprietary driver" option during the live session but I do NOT restart. Instead I just do a ```
sudo modprobe nameofdriveryoujustinstalled
``` and then install the system. Worked on 10.10 and Natty for me with a Broadcom BCM4312.
 
If you aren't sure what you need, just paste back here the output of ```
lspci
``` in a terminal.

---

### Post by card_ace on 2011-04-22
ok i got it now.  for some reason when ubuntu was running and i put the disk into the drive then it gave me 2 popups.  one was for the restricted drivers and one was for updates.  i got the wireless driver downloaded and installed and now everything is working perfectly.  thanks for the help.

---

