---
title: "I've got my infamous Netgear WNA3100 working - but it's flakey, and slow."
date: 2013-12-22
forum: Networking &amp; Wireless
---

### Post by harlenhatter on 2013-12-22
Hi all I decided to make the switch to Ubuntu from Windows on my main PC as it's only used for the internet, office work and music. It's a beefy self built gaming PC but having taken ownership of an Xbox One I won't be doing much gaming on it anymore.

Anyway I've finally got everything running, including spending about 5 hours getting this blasted wifi dongle working. Only issue is it takes about a minute to connect to my modem after the Ubuntu has loaded up and occasionally experiences random disconnects which take a further minute to connect again. In addition, I'm running BT infinity fibre optic in my home. Wired, I'm getting a 55mb connection through Ubuntu, wireless, I'm getting a 5mb connection.

I'm using the Broadcom 43xx64 drivers for it installed through the Wireless Network Drivers program. Is this really the best I'm going to get out of it? Or am I doing something majorly wrong? As people who are using this method seem pretty happy with it whereas I'm having a terrible experience.

I don't want to just give in and go back to Windows, that's not like me, I want to use Ubuntu. So please please, any suggestions let me know. If you need info from me just ask. I don't want to let this beat me.

---

### Post by praseodym on 2013-12-31
Please show
```

lsusb
lsmod
dmesg | grep ndis
cat /etc/resolv.conf
iwconfig
sudo iwlist scan
ndiswrapper -l
```

---

