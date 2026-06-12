---
title: "jaunty will not let me activate wireless driver"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by cwrann on 2009-05-18
Just upgraded my laptop to jaunty, I have no ethernet connection only a wireless card.

When I go to restricted drivers I am tole that there is an inactive broadcom b43 wireless driver but I am not able to activate it.

any suggestions?

---

### Post by Oblivion.Wielder on 2009-05-19
have you tried bringing up the module with 
sudo ifconfig <your module name here, probably eth1 or eth0> up

---

### Post by cwrann on 2009-05-19
I don't have an ethernet connection on this laptop only the wireless card. The card is a Linksys wpc54g. Any Idea what the module would be named?

---

### Post by lkraemer on 2009-05-20
Open a Terminal Window and use these commands to get 
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted.
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist     OR for 9.04 use cat /etc/modprobe.d/blacklist.conf
iwconfig 

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.

Once you have the Manuf & Hardware info, use Search or Google for
"HOWTO: & 4318" or whatever your Broadcom model is to find a good guide.
 
lkraemer

---

