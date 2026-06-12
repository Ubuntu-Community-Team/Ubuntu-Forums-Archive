---
title: "Lenovo G505"
date: 2015-01-21
forum: Networking &amp; Wireless
---

### Post by spi_ on 2015-01-21
hello, apology from my English, I have one portable Lenovo G505, with Windows 8.1 appears WiFi network(without hardware) but with Ubuntu Linux last version 64bit, only Ethernet(WLAN - cable), how I resolved this? I wait for your answer, thanks a lot...

---

### Post by slickymaster on 2015-01-21
*Moved to the ***Networking & Wireless*** sub-forum*

Please download and run the [wireless script]("http://dl.dropboxusercontent.com/u/57264241/wireless_script"), which will diagnose your system. It can be ran by copying and pasting the command below in the terminal (ctrl+alt+t opens the terminal):```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
The command will download a script and create a file named (wireless-info.txt or wireless-info.txt.tar.gz) which you must post here in the thread.

---

### Post by spi_ on 2015-01-24
hello again apology from my English , this :"wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_scriptPlease download and run the wireless script, which will diagnose your system. It can be ran by copying and pasting the command below in the terminal (ctrl+alt+t opens the terminal):"do not correct this problem: I have one portable Lenovo G505, with Windows 8.1 appears WiFi network(without hardware) but with Ubuntu Linux last version 64bit only Ethernet(WLAN - cable), how I resolved this? I wait for your answer, thanks a lot again...

---

### Post by mörgæs on 2015-01-24
Thread merged. Please keep all posts about a problem in the same thread.

---

### Post by jeremy31 on 2015-01-24
> **spi_ said:**
> hello again apology from my English , this :"wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_scriptPlease download and run the wireless script, which will diagnose your system. It can be ran by copying and pasting the command below in the terminal (ctrl+alt+t opens the terminal):"do not correct this problem: I have one portable Lenovo G505, with Windows 8.1 appears WiFi network(without hardware) but with Ubuntu Linux last version 64bit only Ethernet(WLAN - cable), how I resolved this? I wait for your answer, thanks a lot again...
Can you post what is in the wireless-info.txt file you find in your /home directory?  Or copy the contents to paste.ubuntu.com and post the URL that you are given

---

