---
title: "Fluctuating WI-Fi signal on Broadcom limited bcm 43142 [14e4:4365] (rev 01)"
date: 2018-01-16
forum: Networking &amp; Wireless
---

### Post by drmz2 on 2018-01-16
Just installed Ubuntu 17.10 and my wi-fi signal is fluctuating constantly although I'm right next to the router.
Is there an alternate driver i can install and/or options to tweak to fix this ?

Link to wireless info script results: [https://paste.ubuntu.com/26399725/](https://paste.ubuntu.com/26399725/)

---

### Post by Hadaka on 2018-01-17
Hi, with a working wired connection please Copy and paste..
```
sudo apt-get update
sudo apt-get install --reinstall bcmwl-kernel-source 
```
Then do..
```
sudo iw reg set RO
sudo sed -i 's/=.*/=RO/' /etc/default/crda
```
Then..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/DIGI-TG62PJ
systemctl restart network-manager.service
```
Remove wired connection...reboot and test wireless
Thanks.

---

### Post by drmz2 on 2018-01-17
Thank you for taking the time to reply, but it didn't work, it's still fluctuating. 
I did install the driver with a wired connection after updating my repositories right after installing Ubuntu so I don't think it's that.
I think it may be a problem with the driver for my card itself as it was working fine on Windows 10 after installing an obscure driver with the HP support app.
Without it I had exactly the same problem on Windows with the prepackaged driver.
Should I buy an external Wi-Fi adapter ? Otherwise it's pretty impossible  to use any Wi-Fi that I'm not right next to.

---

### Post by Hadaka on 2018-01-17
Hi, first please go into bios and verify secure boot/UEFI...is disabled.

Then please provide a diagnostic report of your system by..
    opening a terminal...ctrl/alt/t then Copy and Paste .
    ```
 wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./ wireless-info
```
    Then do..
```
cat wireless-info.txt | nc termbin.com 9999
```
    This will have an output that looks this...
    [http://termbin.com/xxyy](http://termbin.com/xxyy) <- It wont say 'xxyy' it will be something else
    copy and paste to your reply.
    Thank you

---

### Post by drmz2 on 2018-01-17
Hey, secure boot was disabled.

Link to wireless info: [http://termbin.com/5yy0](http://termbin.com/5yy0)
Thanks

---

### Post by Hadaka on 2018-01-17
Hi from the diagnostic wireless report all of the items are unchanged.
The commands given in post # 2, were to help with the wireless connection.
Please copy and paste them..one at a time and if you still have issues
with your wireless connection, post a new wireless report.
Thanks.

---

### Post by drmz2 on 2018-01-18
My bad, forgot to delete the old results from when i first ran the script, that's why you saw it unchanged.
 When i ran it the 2nd time as instructed in post #4 it just posted the old results.

Results after rerunning post #2 instructions anyway:  [http://termbin.com/tgeo](http://termbin.com/tgeo)
Thanks.

---

### Post by Hadaka on 2018-01-18
Hi, from the report , the network control has been handed over to
/etc/netplan/01-network-manager-all.yaml...network manager.
I have no exprince or knowledge of this method. I found a few
posts from ubuntu users with symptoms like yours by google search
of...ubuntu /etc/netplan/01-network-manager-all.yaml...perhaps
you can find an answer by doing the same or someone who knows this
method. sorry i am unable to help you.

---

### Post by drmz2 on 2018-01-18
Thanks a lot for taking your time to help, I'll try to look into that.

---

