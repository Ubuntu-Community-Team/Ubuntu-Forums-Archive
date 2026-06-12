---
title: "Unable to connect to wireless internet in ubuntu"
date: 2014-08-23
forum: Networking &amp; Wireless
---

### Post by user_linux on 2014-08-23
Hello there,
 I am trying to access wireless internet. I don't see the detected  connections in top right. I tried to find any hardware driver updates  but nothing. 
 Thank  you.

---

### Post by chili555 on 2014-08-23
Please tell us about your wireless device. If it is an internal, PCI, please open a terminal and run and post:```
lspci -nn | grep 0280
```And if it is a USB:```
lsusb
```Thanks.

---

### Post by user_linux on 2014-08-23
Thank you so much for replying to my post. Just a bit of background, I am using Acer Travelmate laptop p243m, windows 7 pro, 64 bit OS, i5. Here are the outputs:
```
travelmate@ubuntu:~$ lspci -nn | grep 0280
09:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0034] (rev 01)
```

USB:
```
travelmate@ubuntu:~$ lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04ca:3006 Lite-On Technology Corp. 
Bus 001 Device 003: ID 1bcf:2c18 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

thanks again!

---

### Post by chili555 on 2014-08-23
> Atheros Communications Inc. Device [168c:0034] (rev 01)Your device uses the driver ath9k. I am surprised that it didn't load and connect immediately. Please run and post:```
sudo modprobe ath9k
dmesg | grep ath9k
rfkill list all
lsb_release -d
```Thanks.

---

### Post by user_linux on 2014-08-23
```
travelmate@ubuntu:~$ sudo modprobe ath9k
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
travelmate@ubuntu:~$ dmesg | grep ath9k
travelmate@ubuntu:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
travelmate@ubuntu:~$ lsb_release -d
Description:    Ubuntu 12.04.4 LTS
```

Thank you.

---

### Post by chili555 on 2014-08-23
It's interesting what you find when you look beneath the rug! ndiswrapper, eh?? Let's see if the current driver actually covers your device; then, we'll do some clean-up.```
modinfo ath9k | grep 0034
cat /etc/modprobe.d/blacklist.conf | tail -n5
uname -r
```Fun!

---

### Post by user_linux on 2014-08-23
```
travelmate@ubuntu:~$ modinfo ath9k | grep 0034
travelmate@ubuntu:~$ cat /etc/modprobe.d/blacklist.conf | tail -n5
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2x00usb
blacklist rt2800usb
travelmate@ubuntu:~$ uname -r
3.2-64-generic
```
thanks.

---

### Post by chili555 on 2014-08-23
Ah, ha!! Your earlier kernel is too old to include the device ID in the driver ath9k. Let's install backports. With a working internet connection, open a terminal and do:```
sudo apt-get update
sudo apt-get install linux-backports-modules-cw-3.10-precise-generic 
sudo modprobe -r ath9k && sudo modprobe ath9k
```Your wireless should now be working.

We will still need to do some clean-up.> travelmate@ubuntu:~$ uname -r
3.2-64-genericOld Chili is a bit suspicious, but let's see how this all works out.

---

### Post by user_linux on 2014-08-23
```
travelmate@ubuntu:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US       
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release         
Hit http://us.archive.ubuntu.com lucid-updates Release                         
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://security.ubuntu.com lucid-security Release
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Reading package lists... Done
travelmate@ubuntu:~$ sudo apt-get install linux-backports-modules-cw-3.10-precise-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-cw-3.10-precise-generic
travelmate@ubuntu:~$ sudo modprobe -r ath9k && sudo modprobe ath9k
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```

Still not working sorry! WHat to do next?
thank you.

---

### Post by chili555 on 2014-08-23
Old Chili gets more confused every moment! > Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) [COLOR="#FF0000"]lucid[/COLOR]-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted SourcesLucid corresponds to Ubuntu 10.04 which is badly out of date since it is beyond its end of life and security updates are no longer provided. I would download and install 12.04.5 LTS if it were me. [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/) I'm reasonably certain your wireless will work perfectly.

---

### Post by user_linux on 2014-08-23
Problem in installing 12.04 is that the system gets frozen every so often. I had that installed but it was so bad I had to downgrade.

---

### Post by chili555 on 2014-08-23
Did you try xubuntu or kubuntu? You can try the live DVD or USB.

---

### Post by user_linux on 2014-08-24
After I have installed Ubuntu 12.04 LTS, I see that the mousepad doesn't work at the login screen, I have to press Fn+F7 to enable that everytime at the login screen. Is there a way around that?

---

### Post by chili555 on 2014-08-24
> **user_linux said:**
> After I have installed Ubuntu 12.04 LTS, I see that the mousepad doesn't work at the login screen, I have to press Fn+F7 to enable that everytime at the login screen. Is there a way around that?Please open:```
tail -f /var/log/syslog 
```Press Fn+F7. What appears on the log? 

Get out of tail with Ctrl+c.

---

### Post by user_linux on 2014-08-24
Here is what I get:
```
travelmate@ubuntu:~$ tail -f /var/log/syslog
Aug 24 16:13:36 ubuntu avahi-daemon[1933]: New relevant interface wlan0.IPv6 for mDNS.
Aug 24 16:13:36 ubuntu avahi-daemon[1933]: Registering new address record for fe80::466d:57ff:fe15:436f on wlan0.*.
Aug 24 16:13:45 ubuntu ntpdate[3913]: step time server 91.189.94.4 offset 0.852325 sec
Aug 24 16:13:55 ubuntu NetworkManager[2148]: <info> (wlan0): IP6 addrconf timed out or failed.
Aug 24 16:13:55 ubuntu NetworkManager[2148]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Aug 24 16:13:55 ubuntu NetworkManager[2148]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Aug 24 16:13:55 ubuntu NetworkManager[2148]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Aug 24 16:16:02 ubuntu anacron[2215]: Job `cron.daily' started
Aug 24 16:16:02 ubuntu anacron[4171]: Updated timestamp for job `cron.daily' to 2014-08-24
Aug 24 16:17:01 ubuntu CRON[4257]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 24 16:18:39 ubuntu kernel: [  502.046579] psmouse serio2: TouchPad at isa0060/serio2/input0 lost sync at byte 1
```

---

### Post by varunendra on 2014-08-25
How about trying a Live DVD/USB of 14.04.1? I haven't tested it myself yet (whereas dr. chili555 is 'using' it), but have seen many posts that claim that it is much lighter and faster than 12.04. Of course that also depends on how well your hardware is supported by the newer kernel.

In any case, 10.04 is a dead end unless you have VERY limited use of this laptop, and have absolutely no worries about security.

---

### Post by chili555 on 2014-08-25
> **varunendra said:**
> In any case, 10.04 is a dead end unless you have VERY limited use of this laptop, and have absolutely no worries about security.And if you are connected to the internet, the whole purpose of installing a wireless card, then you *should* be worried about security.

I see nothing in your log that shows any sign of a crash.

I would certainly recommend 14.04.1 and if you are looking for a lightweight version that demands little in the way of RAM and graphics, look into xubuntu or lubuntu. 

[http://xubuntu.org/](http://xubuntu.org/)

[http://lubuntu.net/](http://lubuntu.net/)

---

