---
title: "No internet connection on wireless network at school"
date: 2016-11-30
forum: Networking &amp; Wireless
---

### Post by njckfletcher on 2016-11-30
I'm not entirely network savvy, so bare with me.  My issue is that I am not able to get online here at school.  I am connected to the school's network, no problem at all.  But when I try loading a webpage on a browser, it says DNS access not found.  A friend told me to ping Google's public DNS (8.8.8.8), but I'm getting 0% packet loss which leads me to believe there is a connection...  I have been able to connect in the past.  The issue started when we returned from break.  Not sure if this is relevant, but I am running Ubuntu Gnome 16.10.  Any help would be greatly appreciated :)

---

### Post by QIII on 2016-11-30
Hello!

Have you spoken to the appropriate authorities at your school?  It's their network.

Our policy here is "Their network, their rules."

---

### Post by njckfletcher on 2016-11-30
I did try talking to the front office (I'm a senior in high school) but none of them really know anything about how their network is setup.  I asked of there was maybe an IT guy I could talk to but they said he kinda just bounces around the schools in the system and isn't really available for questions.  Ultimately though, I was wondering if the problem was something on my part, rather than their network.  I guess if their network is blocking me for some reason, there isn't really anything I can do about it.  But if the issue was tied to my system, then getting help on that doesn't violate policy here, right?  Thought that maybe someone here would at least be able to help diagnose the problem

---

### Post by wildmanne39 on 2016-11-30
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by njckfletcher on 2016-11-30
I ran the script.  This is what I got:
[ATTACH]272469[/ATTACH]

---

### Post by wildmanne39 on 2016-11-30
Let's turn power management off:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Your resolv.conf shows:
```
nameserver 209.222.18.222
nameserver 209.222.18.218
```
unless you changed this for a reason it should be:
```
nameserver 127.0.1.1
```
You can reconfigure it by running:
```
sudo dpkg-reconfigure resolvconf
```
the information says capable speed is 325 Mb/s and yours is set to 433.3 Mb/s
do:
```
sudo iwconfig wlp6s0 power off
sudo iwconfig wlp6s0 rate auto
sudo  systemctl restart NetworkManager.service
```
go into network manager settings and set your settings to match the screenshots.
Reboot
[ATTACH=CONFIG]272473[/ATTACH][ATTACH=CONFIG]272474[/ATTACH]

---

### Post by njckfletcher on 2016-11-30
Okay, I have applied those changes exactly.  I do believe that my vpn is the culprit for having those settings in the resolv.conf file.  I will post again tomorrow with an update on whether I can get online on the schools network.  Either way, thanks a bunch for helping!

---

### Post by wildmanne39 on 2016-11-30
I have a vpn but my resolv conf  is normal it has not been changed because of the vpn, I suggest you turn it off until you are able to connect normally.

---

### Post by njckfletcher on 2016-12-01
Yea, I turned my vpn off right when I realized I couldn't get online.  But anyways, THANKS A TON!!!  I'm now able to get online on the school's network!  This is a huge relief

---

### Post by wildmanne39 on 2016-12-01
I am pretty sure the cause was more then the vpn, because  first your signal strength was 44 and if it get below 50 ubuntu just will not connect that low usually, that is why we changed the power settings, and with the speed set above what your card was able to do it would not connect.

I am glad it is working and I hope it continues to work with the vpn turned on it was hard getting my to connect with the vpn but I finally.

---

### Post by njckfletcher on 2016-12-05
Not a huge issue because the commands that you gave me fix it, but turning my VPN on does cause the problem to return.  My VPN will work, and I'll have internet.  But when I restart the computer, the internet no longer works and I have to run those commands again.  I'm using PIA.  Perhaps the kill switch or dns leak setting is causing this?

---

### Post by wildmanne39 on 2016-12-05
I am not sure,please tell me which commands you run again, not all of them right?

---

