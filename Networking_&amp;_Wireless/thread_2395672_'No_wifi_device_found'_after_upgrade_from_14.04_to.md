---
title: "'No wifi device found' after upgrade from 14.04 to 18.04"
date: 2018-07-05
forum: Networking &amp; Wireless
---

### Post by dubeysandeep on 2018-07-05
Yesterday i upgraded my OS ubuntu 14.04  to 18.04 and after the upgrade wifi device is not showing. i have gone through lots of thread regarding this issue and tried almost all solution i found but non of them worked till now.

I found [this]([https://ubuntuforums.org/showthread.php?t=2395628](https://ubuntuforums.org/showthread.php?t=2395628)) issue as the most similar to my problem and tried the provided solution, but still problem persists. 

Device log: [https://pastebin.com/qzsL029z](https://pastebin.com/qzsL029z)

---

### Post by deltamind on 2018-07-05
Hey

Have you tried this? [https://askubuntu.com/questions/1038242/no-wifi-option-on-ubuntu-18-04-and-16-04](https://askubuntu.com/questions/1038242/no-wifi-option-on-ubuntu-18-04-and-16-04)

---

### Post by Autodave on 2018-07-05
I am guessing that it was not a good idea to upgrade that far. I rarely find that an upgrade from one release to the next works, but you did an upgrade through 8 releases! Perhaps something that someone else has suggested will work, but if it were my machine, I would back up everything and do a clean install.

---

### Post by dubeysandeep on 2018-07-05
@Autodave: I was having some issue in my laptop motherboard so i reinstalled motherboard (new one) after that Ubuntu 14.04 was not booting up (although my hdd was booting well on other laptops) so the technician asked me to do a clean setup i.e, format your hdd and then do a clean install, so i made back up and installed 18.04. and now I'm having this issue :p hope you'll understand. (but wifi is working on same device for windows and i also tried 16.04 in try mode and wifi device was not working there too.)

@deltamind : I think i have gone through that as my first attempt and that didn't resolved, even i tried it right now it's not working in my case! :(
Log after running `sudo make install`: [https://pastebin.com/UqNZYuMk](https://pastebin.com/UqNZYuMk)
 
Thanks for the responses!

---

### Post by chili555 on 2018-07-05
Deleted.

---

### Post by chili555 on 2018-07-05
> **dubeysandeep said:**
> Yesterday i upgraded my OS ubuntu 14.04  to 18.04 and after the upgrade wifi device is not showing. i have gone through lots of thread regarding this issue and tried almost all solution i found but non of them worked till now.

I found [this]([https://ubuntuforums.org/showthread.php?t=2395628](https://ubuntuforums.org/showthread.php?t=2395628)) issue as the most similar to my problem and tried the provided solution, but still problem persists. 

Device log: [https://pastebin.com/qzsL029z](https://pastebin.com/qzsL029z)With a working internet connection by ethernet, tethered or whatever means possible, please try:> sudo apt install --reinstall bcmwl-kernel-source
sudo modprobe wlIf there are any errors, please post:```
uname -r
```As well as:```
cat /var/lib/dkms/bcmwl/6.30.223.271+bdcom/`uname  -r`/x86_64/log/make.log
```

---

### Post by dubeysandeep on 2018-07-05
> **chili555 said:**
> With a working internet connection by ethernet, tethered or whatever means possible, please try:If there are any errors, please post:```
uname -r
```As well as:```
cat /var/lib/dkms/bcmwl/6.30.223.271+bdcom/`uname &nbsp;-r`/x86_64/log/make.log
```

*log after running `sudo apt install --reinstall bcmwl-kernel-source`:* [https://paste.ubuntu.com/p/Vqf2rwCGnp/](https://paste.ubuntu.com/p/Vqf2rwCGnp/)

reboot
didn't worked 
[I]
log after running `uname -r`;[/I] **4.15.0-23-generic**

*log after running ` cat /var/lib/dkms/bcmwl/6.30.223.271+bdcom/4.15.0-23-generic/x86_64/log/make.log`;* [https://paste.ubuntu.com/p/YKbvcNzbT9/](https://paste.ubuntu.com/p/YKbvcNzbT9/)

logs says some warnings regarding misleading indentation.

---

### Post by jeremy31 on 2018-07-05
Try uninstalling the iwlwifi backports, then reboot

---

