---
title: "Lenovo B560 couldnt connect to the certain WiFi router"
date: 2014-10-14
forum: Networking &amp; Wireless
---

### Post by alex-ryabec on 2014-10-14
A few days ago have installed Ubuntu to the my Lenovo B560 notebook. Unfortunately, couldnt connect to my WiFi router. Router is ok, because my phone and tablet connect with no problems.
When I turn on WiFi hotspot on my Nexus 7 tablet and try to connect with my notebook - its ok.
When I connect network cable directly into notebook - its ok.
Earlier I ve Windows 8.1 on my notebook.

Im newbie to Ubuntu. Help please :(
Chronic reconnection of network cable from router to the notebook and return is awful :(

---

### Post by Hadaka on 2014-10-14
Hi, please post the output of..
```
lspci -nn | grep 0200
rfkil list all
lsmod | egrep 'b43|wl|brcmsmac'
uname -r
lsb_release -d
```
thanks

---

### Post by alex-ryabec on 2014-10-14
```
alex@alex-Lenovo-B560:~$ lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
alex@alex-Lenovo-B560:~$ rfkil list all
No command 'rfkil' found, did you mean:
 Command 'rfkill' from package 'rfkill' (main)
rfkil: command not found
alex@alex-Lenovo-B560:~$ lsmod | egrep 'b43|wl|brcmsmac'
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
alex@alex-Lenovo-B560:~$ uname -r
3.13.0-37-generic
alex@alex-Lenovo-B560:~$ ^Cb_release -d
alex@alex-Lenovo-B560:~$
```

---

### Post by Hadaka on 2014-10-14
Hi i also need to see
```
lspci -nn | grep 0280
rfkill list all
```
thanks

---

### Post by wildmanne39 on 2014-10-14
Please click on # and put all code between the brackets that are created, they are called code tags.

---

### Post by alex-ryabec on 2014-10-15
```
alex@alex-Lenovo-B560:~$ lspci -nn | grep 028004:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
alex@alex-Lenovo-B560:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
alex@alex-Lenovo-B560:~$ ^C
alex@alex-Lenovo-B560:~$ 



```

---

### Post by Hadaka on 2014-10-15
Hi,please open a terminal...ctrl/alt/t and attach to the internet
with your wired cable. Then COPY  and paste -one line at a time-
the following commands.
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install b43-fwcutter firmware-b43-installer
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe brcmsmac
```
thanks

---

### Post by alex-ryabec on 2014-10-15
Done. After restarting wifi connection is ok :)

Thanks!!!

---

### Post by Hadaka on 2014-10-15
Glad that worked for you.
Please mark this thread solved
How to->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

