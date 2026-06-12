---
title: "Lubuntu fresh install with no wireless. I'm connecting via an ethernet cable"
date: 2014-11-14
forum: Networking &amp; Wireless
---

### Post by allyson2 on 2014-11-14
I don't know any fancy code talk, I don't even know WHERE to enter the code, I installed LUBUNTU over WINXP which used my wireless card somewhere within my computer, but it doesn't work now, and I"M CONNECTED VIA ETHERNET CORD to my wireless box! I've been working all day and night and am getting frustrated with all ya'll that know how to code this operating system.  I need help before one of us kills themselves tripping on this cord.  tell me step by step how to fix this.  I need someone to say, "now go to the little blue icon on the toolbar at the bottom of your screen...". Please.  Mommie needs this computer cause all the kids stole all the other ones that WORK!  
Thanks in advance,
Allyson

---

### Post by slickymaster on 2014-11-14
Hi allyson2, welcome to the forums.

I moved your thread to the **Networking & Wireless** sub-forum, a more suitable venue for your problem.

Please [follow this instructions]("http://ubuntuforums.org/showthread.php?p=13024222#post13024222") to download and run the wireless_script to gather the information necessary for troubleshooting your wireless connection.

---

### Post by allyson2 on 2014-11-14
wow! thanks for doing that for me!

---

### Post by Hadaka on 2014-11-14
Hi, please open a terminal...ctrl/alt/t... 
then COPY  and paste one line at a time
```
lspci -nn | grep 0280
rfkill list all
lsmod | egrep 'b43|wl'
```
copy and post the results.
thanks

---

### Post by allyson2 on 2014-11-14
it didn't work. really. i thought it would. what to do now?

---

### Post by Hadaka on 2014-11-14
Re-read the simple instructions i requested..
"Post the results"   the output from the commands.
thanks.

---

### Post by allyson2 on 2014-11-15
allyson@allyson-Latitude-D630:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
allyson@allyson-Latitude-D630:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
allyson@allyson-Latitude-D630:~$ lsmod | egrep 'b43|wl'
wl                   6148792  0 
cfg80211              430618  2 wl,mac80211
allyson@allyson-Latitude-D630:~$

---

### Post by chili555 on 2014-11-15
My friend Hadaka may be away for a bit. In his behalf, please hook up the ethernet, open a terminal Ctrl+Alt+t and run:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install firmware-b43-installer
```After it finishes, detach the ethernet, reboot and tell us how its going.

---

### Post by allyson2 on 2014-11-21
Guess WHAT. WIRELESSSSSS!!! You people are geniuses.  Thank you so much! (I'm happy I have wireless again! Merry Christmas to me eh?  I have my own computer finally!) :-D

---

### Post by mörgæs on 2014-11-21
Congratulations.
Please read the signature in post #2.

---

