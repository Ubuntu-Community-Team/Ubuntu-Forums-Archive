---
title: "Tomson adsl330"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by Desy on 2006-11-26
Hi all I need some help. I have a Tomson adsl usb modem and I have follwed numerous threads on how to get online with this modem. The most recent being [http://www.linux-usb.org/SpeedTouch](http://www.linux-usb.org/SpeedTouch).

I have follwed the instructions fully but when i get to the section that says Make a bootscript, I can creat the fial dial but when i try to install using the following commands:

sudo install -m744 dial/stc/init.d &&
sudo in -s ../init.d/dial/etc/rc2.d/S95dial &&
sudo in -sf ppp/resolv.conf/etc/resolv.conf

i get a message saying command not found. I presume that the second and third sudo in, the in part is the letter i and not some other command. Please help, this is now starting to annoy me. Thanks all

---

### Post by fishpie on 2006-11-26
You should be using 'ln' instead of 'in', 'ln' is a contraction of link. You are also missing a couple of spaces which are important. You should be typing the following

```
sudo install -m 744 dial /etc/init.d &&
 sudo ln -s ../init.d/dial /etc/rc2.d/S95dial &&
 sudo ln -sf ppp/resolv.conf /etc/resolv.conf
```

---

### Post by Desy on 2006-11-26
Thanks fishpie I have done that and thats gone through, however when I load and click in the firefox browser it says that i am unable to connect

---

### Post by fishpie on 2006-11-26
Try the following command
```
sudo pppd call speedtch
```
It should connect you to the Internet, but if It doesn't It will probably give a helpful error message, if you post the message I will give you further help. If this does connect you to the Internet, then we need to find out why automatic connection is failing, to diagnose this disconnect using:```
sudo killall pppd
``` and then try to reconnect using ```
/etc/init.d/dial
``` let me know if this connect you or if it doesn't what error message you get

---

### Post by Desy on 2006-11-26
Hi fishpie,
I typed in sudo pppd call speedtch and got the following message

Remote system is required to authenticate itself, but i couldn't find any suitable secret (passwords) for it to use.  (None of the available passwords would let it use an ip address)

HTH

Thanks

---

### Post by fishpie on 2006-11-27
I think that this is a problem with your /etc/ppp/peers/speedtch file. the fourth line of the file should read:```
noauth
``` You can edit the file using```
gksu gedit /etc/ppp/peers/speedtch
```

---

### Post by Desy on 2006-11-27
Thanks fishpie, I will try this tonight when i get in and let you know

Thanks again

---

### Post by Desy on 2006-11-27
Hi fishpie,

Checked /etc/ppp/peers/speedtch file and the command noauth was on the 3rd line.  I have ammended this to the 4th line and i still get the same message as above.

Thanks

---

### Post by Desy on 2006-11-27
Hi fishpie

Cancell my last message, I have managed to get on line by typing sudo pppd call speedtch, but once i log off and log on it dosn't log on automatically.  The output when i dial is as follows

plugin pppoatm.so loaded
using interface ppo
connect ppo 0,38
CHAP authentication succeeded CHAP authentication success, unit 30924
CHAP authentication succeeded
Cannot determine ethernet address for proxy ARP
local ip address 89.241.91.48
remote ip address 89.241.80.1
primary DNS address 62.24.128.18
secondary DNS address 62.24.128.17

HTH.  The only thing wrong now is that it does not connect automatically.

Thanks

---

