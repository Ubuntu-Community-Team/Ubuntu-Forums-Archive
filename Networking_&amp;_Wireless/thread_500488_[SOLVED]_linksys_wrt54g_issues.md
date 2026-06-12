---
title: "[SOLVED] linksys wrt54g issues"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by funfanatic91 on 2007-07-13
im completely new to ubuntu, and reading a book to start.
the book is a little out of date, and im having trouble with the wireless network.

the computer im using is an acer aspire 3000 laptop.

i've read other forums concerning the linksys wrt54g router, but none helped me.

i have tried typing in 'iwconfig' and it looks "normal" compared to other people who have posted it.


help of where to go next would be greatly appreciated :confused:

---

### Post by dfego on 2007-07-13
Well what exactly is the problem you're having?

---

### Post by funfanatic91 on 2007-07-13
well.
it wont connect to my wireless network.
i dont really know where to start.

---

### Post by dfego on 2007-07-13
Well since iwconfig seems "normal," it's more likely a problem with your computer than the access point.  Can you  show me the output of:

$ sudo ifconfig <YOUR-WIRELESS-INTERFACE>

---

### Post by t4thfavor on 2007-07-13
You will have to post some info to help us help you, first start out with your wireless card make and model. Next the wireless setup of your LAN (WEP WPA? DHCP server?)

Then we can assist you with diagnosing and fixing the actual problem.

---

### Post by funfanatic91 on 2007-07-14
alright. i attached the iwconfig and sudo ifconfig results

---

### Post by funfanatic91 on 2007-07-14
sorry i have to attach files.

im on a mac right now.

---

### Post by dfego on 2007-07-14
It would be a lot easier if you saved it in a plaintext file. ;-)

Try this and see if that "Access Point: Invalid" in your iwconfig response goes away, then report back.

$ sudo iwconfig eth1 essid "Broadcom 4318"

---

### Post by t4thfavor on 2007-07-14
Try typing this on the commandline

```
sudo iwconfig eth1 essid "your SSID" key "Your Key if you have one";
sudo dhclient eth1
```

---

### Post by macogw on 2007-07-14
It's not the router you've got to worry about.  It's your wireless card.  Unless, of course, you're modifying and reinstalling the Linux that's already on the wrt54g to make it behave like a much more expensive router.

---

