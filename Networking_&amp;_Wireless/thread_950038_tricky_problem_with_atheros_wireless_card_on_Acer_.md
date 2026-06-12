---
title: "tricky problem with atheros wireless card on Acer 4520"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by xchronox on 2008-10-16
So here's one for those not faint of heart. 

I have a acer 4250 with an atheros card. The long short of it is I had it working perfectly with the madwifi driver... that is until the latest kernel update, 2.6.24-21, scrapped my wireless... or so i thought

I used 2 commands:

```
sudo modprobe ath_pci
```
and
```
sudo modprobe wlan_scan_sta
```

which again activated my ability to search, detect and connect to wireless networks.

The primary issue I'm having with this is that it doesn't stick after a reboot. I have to execute those commands each time I boot up and I can not for the life of me figure out how to add them a boot log or startup process (sorry for not using proper names) 

I would greatly appreciate any help that could be offered here. 
Also if any log files or command output is needed let me know.

---

### Post by Ayuthia on 2008-10-16
> **xchronox said:**
> So here's one for those not faint of heart. 

I have a acer 4250 with an atheros card. The long short of it is I had it working perfectly with the madwifi driver... that is until the latest kernel update, 2.6.24-21, scrapped my wireless... or so i thought

I used 2 commands:

```
sudo modprobe ath_pci
```
and
```
sudo modprobe wlan_scan_sta
```

which again activated my ability to search, detect and connect to wireless networks.

The primary issue I'm having with this is that it doesn't stick after a reboot. I have to execute those commands each time I boot up and I can not for the life of me figure out how to add them a boot log or startup process (sorry for not using proper names) 

I would greatly appreciate any help that could be offered here. 
Also if any log files or command output is needed let me know.

You can try the following:
```
echo ath_pci | sudo tee -a /etc/modules
echo wlan_scan_sta | sudo tee -a /etc/modules
```
This will add the two modules to /etc/modules.  This is one of the files that is read when booting and will load all the modules that are in the file.

EDIT: It doesn't help in explaining why this is happening, but it is a workaround so that you don't have to load it every time.

---

### Post by xchronox on 2008-10-16
Worked like a charm!
Thank you!

I can only image it has to do with the inner workings of the driver/hardware relationship. Do you think this could be localized to my system after the update, or would others with the same chip experience this?

---

### Post by Ayuthia on 2008-10-16
> **xchronox said:**
> Worked like a charm!
Thank you!

I can only image it has to do with the inner workings of the driver/hardware relationship. Do you think this could be localized to my system after the update, or would others with the same chip experience this?

That is the part I am not for sure about.  I am trying to keep my eye on the Atheros cards right now because a lot seems to be happening to them.

---

### Post by xchronox on 2008-10-17
Ah, tricky things these wireless cards. Well I'll do my best to document any happenings with mine and my sisters atheros. 
On the bright side though, they still work better then the Broadcom in my experience.

---

