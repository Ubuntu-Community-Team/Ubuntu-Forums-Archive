---
title: "700wx as USB Modem on Feisty Fawn"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by elephant007 on 2007-09-12
the quick

700wx Sprint running Mobile-Stream USB Modem software
Edgy results, works
Device /dev/ttyAMC0
```
sudo pppd /dev/ttyAMC0 call ppp-script-evdo
```
PPP-SCRIPT-EVDO consists of
```
921600
connect '/usr/sbin/chat -s -v  "" "AT&F0E0V1S0=0"  OK ATD#777  CONNECT'
debug
updetach
crtscts
noipdefault
novj
lcp-echo-failure 0
nobsdcomp
novjccomp
nopcomp
noaccomp
noauth
user USERNAME
modem
usepeerdns
defaultroute
connect-delay 5000
```

 Feisty Fawn results, does not work
Device attaches as /dev/ttyUSB1
```
sudo pppd /dev/ttyUSB1 call ppp-script-evdo
```
ppp-script-evdo is the same as above

My question is this, does this line here ```
connect '/usr/sbin/chat -s -v  "" "AT&F0E0V1S0=0"  OK ATD#777  CONNECT'
``` need to be changed to something else since the device is now attached at ttyUSB1?
I have tried various howtos here, none were successful although I was able to get gnome-ppp to recognize my device as a modem.  Query modem found the modem, posted all blanks for the AT strings.

I have found a resolve for this issue
[http://ubuntuforums.org/showthread.php?t=550133]("http://ubuntuforums.org/showthread.php?t=550133")

---

### Post by elephant007 on 2007-09-13
I was able to follow a howto on how to get an A900 to connect, I applied this to my Razr and was able to get it working.  I tried the same steps to my Treo 700wx and still was unable to get it connected to the internet.
Any direction would be much appreciated.
anything.

---

### Post by elephant007 on 2007-09-13
I found how to make this work and will be posting a howto in the very near future

---

### Post by richter on 2007-12-11
Any update would be appreciated, I'm having the exact same problem. Thanks in advance.

---

