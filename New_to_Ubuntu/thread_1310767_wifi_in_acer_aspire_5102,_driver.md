---
title: "wifi in acer aspire 5102, driver"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by johnyjj2 on 2009-11-02
Hello :-)!

I've got Ubuntu and I cannot use wireless network (even if it works in Windows). I've got Acer Aspire 5102. I tried to install this compat-wireless-2.6.tar.bz2 from the tutorial here [http://www.downloadatoz.com/driver/a...untu-8-10.html]("http://www.downloadatoz.com/driver/articles/how-to-make-atheros-ar5007eg-wireless-cards-work-on-ubuntu-8-10.html") (How to make Atheros AR5007EG Wireless cards work on Ubuntu 8.10 - Driver Download) but it didn't help.

I include results of some commands in txt file. (My network is listed as third of those four). Simply Mozilla Firefox says that server cannot be found.

Thanks in advance for your help :-)!
Greetings :-)!

---

### Post by pastalavista on 2009-11-02
According to your lspci, the correct driver (ath5k) is installed (a kernel module) but "access denied". Have you turned the switch off? Look for a wireless switch on the machiine.

---

### Post by johnyjj2 on 2009-11-02
Thanks for your answer :-)!
The switch is turned on, wireless network works in Windows.
Greetings :-)!

---

### Post by johnyjj2 on 2009-11-02
However, it still doesn't work in Ubuntu. Can anybody help me, please? It is Acer Aspire 5102.

---

### Post by moster on 2009-11-02
I have acer aspire too and ubuntu did not recognize my wlan until I do this.
Open terminal and enter:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
add line and save:
```
blacklist acer_wmi
```

After restart your wlan will mysteriously start working :D
(mark that for later installations)

---

