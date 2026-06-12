---
title: "Wireless firmware."
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by ivaylo.tanev on 2014-03-10
Hi to all. In my previous thread ([http://ubuntuforums.org/showthread.p...0#post12901240]("http://ubuntuforums.org/showthread.php?t=2199727&p=12901240#post12901240") ) I explained my problem with the wifi firmware. I sorted it out at the time but what happens now is that every time I attempt a kernel update the same thing keeps happening and I need to go through the process all over. Additionally when I try to install the updated kernel firmware it fails and this is what it says in the details 
```
installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 290077 files and directories currently installed.) 
Preparing to replace linux-firmware 1.79.7 (using .../linux-firmware_1.79.10_all.deb) ... 
Unpacking replacement linux-firmware ... 
dpkg: error processing /var/cache/apt/archives/linux-firmware_1.79.10_all.deb (--unpack): 
 trying to overwrite '/lib/firmware/ar3k/ramps_0x31010000_40.dfu', which is also in package bt-dw1705-firmware 0.1 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-firmware_1.79.10_all.deb 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
```
I am wondering how can I avoid having to install the kernel wifi driver manually every time and also what is the problem with the instalation of the drivers.
Thank you for your help.

---

### Post by chili555 on 2014-03-10
I'm corn-fused. In the thread you linked, you said:> [http://ubuntuforums.org/showthread.php?t=2190930](http://ubuntuforums.org/showthread.php?t=2190930) POST 4 this one worked. Thank you so much. And in post #4 in the link you gave, it says:> cd Desktop/backports-3.13-rc2-1
make defconfig-ath9k
make
sudo make install...which is nothing about foirmware at all. The driver for your device, ath9k, doesn't require any firmware:```
$ modinfo ath9k
filename:       /lib/modules/3.13.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     B263A0867EA2F23AA22F163
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
<snip>
```There is no mention of firmware at all here.

Please clarify your question. On a side note, I strongly suspect that first, if you upgrade to 13.10, your troubles will be over and, second, no, there is no way currently to add a new driver to an old kernel than the backports process. It's really not so onerous to re-compile, is it?  We only get newer kernels rather infrequently.

---

### Post by ivaylo.tanev on 2014-03-11
No luck with upgrade. now I am stuck in a login loop. I made a terrible mistake with this as I have lots of work to do. nevermind lesson learned next time will stick to the path of least resistance or at least read more before attempting an upgrade. I did do a backup beforehand but no luck when I cant login . I hope I find a way to sort it out soon. thanks for the reply.

---

### Post by chili555 on 2014-03-11
I am sorry to hear about your trouble. I recommend you re-install 13.10; your wireless device will be recognized with no need to compile. Post back if you need more help.

---

### Post by ivaylo.tanev on 2014-03-11
can I do it without live boot cd? can I do it straight through terminal? thanks for the support. and sorry for the stupid questions.

---

### Post by chili555 on 2014-03-11
Now I may be confused. If you can get to the terminal, what is login looping? Logging in to the Ubuntu desktop or to...what?? Tell me exactly what's going on or going wrong. 

:confused: :confused:

---

### Post by ivaylo.tanev on 2014-03-11
I am sorry I am new to Ubuntu and I am bad with terminology. By terminal I mean Ctrl+Alt+F1 at the login screen. What happens is when I try to log in to the Ubuntu desktop, as soon as I put in my login details it flashes the black screen with coding for a fraction of a second and goes back to login screen. Currently I am putting Ubuntu 13.10 on a bootable pen drive.

---

### Post by chili555 on 2014-03-11
>  I did do a backup beforehandSince you have a backup, I'd just install from the USB and have a fresh start.

---

