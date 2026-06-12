---
title: "&quot;Wireless is disabled by hardware switch&quot;"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by jtomczyk95 on 2014-05-01
Hello,
I am new to Ubuntu. I was very enthusiastic to finally download and burn a copy of Ubuntu 14.04
However, I cannot access any sort of wifi network whatsoever due to what I assume is a strange bug.

My wifi icon is constanly grey. My adapter is not coming up as installed hardware. 

I am on an ASUS F75V. I have no hard wifi switch, only an fn+f2 combination (which does not help). 

Has anyone else had to deal with this?

---

### Post by grahammechanical on 2014-05-01
> [COLOR=#000000]only an fn+f2 combination [/COLOR]

That is a hardware switch. It used to be, may be it still is for all I know, that if WiFi was disabled in Windows and then Windows was shutdown, then WiFi would not work in Ubuntu.

In a terminal you could try

```
rfkill unblock wifi
```

or

```
sudo ifconfig wlan0 down
```

and then

```
sudo ifconfig wlan0 up
```

Regards.

---

### Post by praseodym on 2014-05-01
Hi,

please run this command and reboot afterwards:

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
This is one line, you better copy/paste it.

---

