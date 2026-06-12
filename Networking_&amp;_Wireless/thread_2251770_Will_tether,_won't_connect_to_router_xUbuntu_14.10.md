---
title: "Will tether, won't connect to router x/Ubuntu 14.10 + 14.04.1 LTS / Broadcom BCM4313"
date: 2014-11-06
forum: Networking &amp; Wireless
---

### Post by superchar42 on 2014-11-06
**[SIZE=3]EDIT: a re-install of xubuntu 14.04.1 solved this issue, unknown reason[/SIZE]**

(I went through the broadcom thread and the networking threads stickied) [http://paste.ubuntu.com/8855032/](http://paste.ubuntu.com/8855032/)

I'm currently on a live usb of xubuntu 14.04.1, but this is the same on Linux Mint 17 (Cinnamon and Mate/Debian), and Ubuntu Mate. (installs and live)

I also did this: 

```
xubuntu@xubuntu:~$ lspci -nn -d 14e4:
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
xubuntu@xubuntu:~$ sudo -i
root@xubuntu:~# echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
root@xubuntu:~# echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
root@xubuntu:~# exit
logout
```


I didn't anticipate problems because I had an upgraded 14.10 Ubuntu + XFCE (added to Unity) that was running it fine. So of course, I wiped my old install and reinstalled without thinking about work in the morning. 

I'm connected via tether to my phone, which works fine. I can also make my phone a wifi hotspot and I can connect fine. Every other computer on the network can connect just fine. 

What's weird is that it says I am connected to it but I get no signal, or I'll start with a tiny bit and it leaves. It's not "not-connecting" but it's more just not coming through. Does that make sense?

---

### Post by Hadaka on 2014-11-06
Hi, let's take a look at some stuff, Please
post the output of..
```
uname -r
cat /etc/issue
lspci -n | grep -v 8086
lsmod | egrep 'wl|b43'
rfkill list all
```
thanks

---

### Post by superchar42 on 2014-11-06
Thanks! 

This is from live usb, running tethered. 

```
uname -r
3.13.0-32-generic
________________

cat /etc/issue
Ubuntu 14.04.1 LTS \n \l

_____________________

lspci -n | grep -v 8086
00:00.0 0600: 1022:1410
00:01.0 0300: 1002:990a
00:01.1 0403: 1002:9902
00:04.0 0604: 1022:1414
00:05.0 0604: 1022:1415
00:10.0 0c03: 1022:7812 (rev 03)
00:11.0 0106: 1022:7804
00:12.0 0c03: 1022:7807 (rev 11)
00:12.2 0c03: 1022:7808 (rev 11)
00:13.0 0c03: 1022:7807 (rev 11)
00:13.2 0c03: 1022:7808 (rev 11)
00:14.0 0c05: 1022:780b (rev 14)
00:14.2 0403: 1022:780d (rev 01)
00:14.3 0601: 1022:780e (rev 11)
00:14.4 0604: 1022:780f (rev 40)
00:18.0 0600: 1022:1400
00:18.1 0600: 1022:1401
00:18.2 0600: 1022:1402
00:18.3 0600: 1022:1403
00:18.4 0600: 1022:1404
00:18.5 0600: 1022:1405
01:00.0 ff00: 10ec:5289 (rev 01)
01:00.2 0200: 10ec:8168 (rev 0a)
02:00.0 0280: 14e4:4727 (rev 01)

________________________________________

lsmod | egrep 'wl|b43'
b43                   387371  0 
mac80211              630653  2 b43,brcmsmac
cfg80211              484040  3 b43,brcmsmac,mac80211
ssb                    62379  1 b43
bcma                   52096  3 b43,brcmsmac

____________________________________

rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
__________________________
```

---

### Post by Hadaka on 2014-11-06
Hi,please do..
```
sudo modprobe -rf b43
sudo modprobe -rf ssb
sudo modprobe brcmsmac 
```
 thanks

---

### Post by superchar42 on 2014-11-06
I'm not getting any output. I'll reboot into my installation and repeat.

---

### Post by superchar42 on 2014-11-06
Output from Ubuntu Mate installation: (no output from modprobe either)

```

$ uname -r
3.16.0-23-generic
_____________
cat /etc/issue
Ubuntu 14.10 \n \l
_____________________

 lspci -n | grep -v 8086
00:00.0 0600: 1022:1410
00:01.0 0300: 1002:990a
00:01.1 0403: 1002:9902
00:04.0 0604: 1022:1414
00:05.0 0604: 1022:1415
00:10.0 0c03: 1022:7812 (rev 03)
00:11.0 0106: 1022:7804
00:12.0 0c03: 1022:7807 (rev 11)
00:12.2 0c03: 1022:7808 (rev 11)
00:13.0 0c03: 1022:7807 (rev 11)
00:13.2 0c03: 1022:7808 (rev 11)
00:14.0 0c05: 1022:780b (rev 14)
00:14.2 0403: 1022:780d (rev 01)
00:14.3 0601: 1022:780e (rev 11)
00:14.4 0604: 1022:780f (rev 40)
00:18.0 0600: 1022:1400
00:18.1 0600: 1022:1401
00:18.2 0600: 1022:1402
00:18.3 0600: 1022:1403
00:18.4 0600: 1022:1404
00:18.5 0600: 1022:1405
01:00.0 ff00: 10ec:5289 (rev 01)
01:00.2 0200: 10ec:8168 (rev 0a)
02:00.0 0280: 14e4:4727 (rev 01)

_______________________

lsmod | egrep 'wl|b43'
[nothing]

________________________

 rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no 
```

---

### Post by Hadaka on 2014-11-06
You are changing kernels on me, how am i suppose to know
what you have loaded, please stick with one..and wired if possible
thanks.

---

### Post by superchar42 on 2014-11-06
Sorry about that! I'll be able to plug in later. 

The same problem exists in both places. I'll just stick with the xubuntu in that case.

---

### Post by Bucky Ball on 2014-11-06
> **superchar42 said:**
> I'll just stick with the xubuntu in that case.

Please do! ;)

Also, please use [code] tags for code. See the last link in my signature.

---

### Post by Hadaka on 2014-11-06
great ! ok , lets get some usable date,,please go here

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
then do.
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
post the **Wireless-info.txt **file here,,as an attachment,,or lots of copy and paste,,but most importantly is to use **code tags **See how in
bucky's list of stuff there.

---

### Post by superchar42 on 2014-11-07
Oh, looks like I just forgot to close the [ code] tag there. 

So I did a re-install of xubuntu 14.04.1 and it's working perfectly. Is there a way to figure out why?

---

### Post by Hadaka on 2014-11-07
Hi,probably not. Between bouncing between kernals and having to
hack the driver, then completely over writeing everything in the
now functional mode, not likely.
BCM4313 802.11bgn Wireless Network Adapter [14e4:4727]
always has been a problem to get going, hence the hack.
may as well mark this one solved by good fortune and post the
next issue that shows up.
good luck.

---

### Post by superchar42 on 2014-11-07
Thanks Hadaka :) will do

---

