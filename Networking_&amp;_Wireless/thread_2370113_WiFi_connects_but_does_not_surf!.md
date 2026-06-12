---
title: "WiFi connects but does not surf!"
date: 2017-08-30
forum: Networking &amp; Wireless
---

### Post by thiagosieben1 on 2017-08-30
First of all I apologize for English, I'm Brazilian!
So I've been having a lot of trouble installing any distro on my Acer ES1-1533, it has UEFI, and it makes it impossible for me to install any other OS than Windows, absolutely all locked, I was able to install the refind By windows and installed ubuntu by My girlfriend's notebook, so far so good, I could use it on my notebook.
NOW THE PROBLEM COMES!
I can not use the wifi, only by cable, the Wifi comes to connect after a while, but it does not surf, I tried several methods but without success!
NOTE: I am a beginner!

---

### Post by johndough2 on 2017-09-01
Hi

Usually for an Acer the method is to set a simple SUPERVISOR password and then to choose Secure Boot.  
Why the need for a supervisor password escapes me.  I then installed openSuse on mine.

If you have a working wifi card, and a simple command could show this, for example in my case I have a wlan0 as my wifi and therefore type a command

sudo iwlist wlan0 channel

and it displays a channel number.  So thn I would go on to the "network manager" which may be called network manger or wicd and setup the WiFi routing etc.

---

### Post by praseodym on 2017-09-02
Please open a terminal with CTRL+ALT+T and show these outputs:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
ifconfig -a
iwconfig
sudo iwlist scan
```

---

