---
title: "System crashes randomly when using eth0 (Realtek RTL8168/8111) to connect"
date: 2014-05-29
forum: Networking &amp; Wireless
---

### Post by a.borque on 2014-05-29
Hello!
I am using Ubuntu since 10.04 and up to now I connected to my network using USB-WLAN.
I have tried to change that using gigabit ethernet (chip: [COLOR=#000000][FONT=sans-serif]Realtek RTL8168/8111) connecting to a PowerLAN- / dLAN-device (Devolo 650+). 
Unfortunately the system crashes and restarts frequently but randomly when I do so. This occurs with or without (heavy) networktraffic and sometimes even before a user is logged in.

Further information:
1) Using Windows 7 with this configuration works without any problems and the data transmitted does not contain any significant errors
2) Ubuntu works stable at once I choose to disconnect eth0 in Ubuntu (leaving the cable connected) and reconnect using my WLAN again
3) The Problem occured with 12.04LTS (Kernel 3.8) and persists after upgrading to 14.04LTS
4) I have already tried to disable IPv6 (choosing "ignore") as it is not used in my network and to set MTU-size from automatic to 1500. Both did not help.

Are there any logfiles I can post here to help you solving this? Are there any options for logging this problem I can enable?
Using google I found two threads describing similar problems but both ended without a solution.
Thanks for any help!
A.Borque[/FONT][/COLOR]

---

### Post by praseodym on 2014-05-29
Change the driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/45/14/3005217-r8168-dkms-8.038.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by a.borque on 2014-05-31
Hello!
Thanks for your reply. I have tried your solution but unfortunately it did not help.
I suspect there might be a typo in the last command and it should read "r8168" instead of "r8169" as written there?
I used the command with r8169 exactly as in the original post, so if it is indeed wrong and works only with r8168 please let me know so I can issue that last command again.
Thanks again!
A.Borque

---

### Post by praseodym on 2014-06-01
It blacklists the old driver r8169, so the command was right. Please show now
```

lsmod
ifconfig -a
route -n
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by a.borque on 2014-06-01
Hello!
Thanks for the continued help! 
I did not realize the old driver was indeed called r8169...
The output of the five commands given above is in seperate txt-files in the ZIP-attachment.
I hope this helps.
Thanks once again!
A.Borque

---

### Post by praseodym on 2014-06-01
Both drivers are loaded now:
```

sudo modprobe -rfv r8169
sudo modprobe -rfv r8168
sudo modprobe -v r8168
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo depmod -a
sudo update-initramfs -u -k all
```

---

### Post by a.borque on 2014-06-01
After executing the commands above lsmod does not list r8169 any longer, while r8168 is listed. 
But sadly the system continues to reboot randomly (only) when using Ubuntu connected via LAN (eth0)...!?

---

### Post by praseodym on 2014-06-01
Strange. Try reinstalling the current kernel. Watch, if r8168 is build again, if not reinstall it like above after the reboot:
```

sudo apt-get install --reinstall linux-image-$(uname -r)
```
Reboot.

---

### Post by a.borque on 2014-06-01
Attached is the output of the last command. I assume that r8168 was not build again!?
Should I reissue the commands of your first post (with downloading the source) or the third one (uninstalling and blacklisting r8169 again)?

---

### Post by praseodym on 2014-06-01
```
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
```
should be enough

---

### Post by a.borque on 2014-06-03
Thanks! I won't be at my desk until wednesday.  I will try then and report back.
 Thank you also for your detailed instructions. Though I am reading the man-pages and trying to learn as much as possible while you instruct me I am not quiet fluent with Linux-terminal-commands!

---

### Post by a.borque on 2014-06-06
Sorry, it became friday instead of wednesday...
The commands did not work, the errors seems to say that the driver is already installed (see below), but the crashes continue...

administrator@cherti:~$ sudo dkms add -m r8168-dkms -v 8.038.00
Password: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Error! DKMS tree already contains: r8168-dkms-8.038.00
You cannot add the same module/version combo more than once.
administrator@cherti:~$ sudo dkms build -m r8168-dkms -v 8.038.00
Module r8168-dkms/8.038.00 already built for kernel 3.13.0-27-generic/4
administrator@cherti:~$ sudo dkms install -m r8168-dkms -v 8.038.00
Module r8168-dkms/8.038.00 already installed on kernel 3.13.0-27-generic/i686
administrator@cherti:~$

---

### Post by praseodym on 2014-06-06
Now check:
```

lsmod
grep r8 /etc/modprobe.d/*
dmesg | grep r8
modinfo r8168
uname -a
```

---

### Post by a.borque on 2014-06-07
Once again the output of the commands is in the attached ZIP-file.

---

### Post by praseodym on 2014-06-07
Thats weird. Lets check
```

sudo apt-get install ethtool
sudo ethtool eth0
ifconfig -a
cat /etc/resolv.conf
route -n
```
If necessary ethtool can be found here:

64bit: [http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3.13-1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3.13-1_amd64.deb)

32bit: [http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3.13-1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_3.13-1_i386.deb)

Installation of DEB files via double-click

---

### Post by a.borque on 2014-06-08
Okay, here are the results. 
Please note that these tests were performed whiel WLAN-USB was physically disconnected and eth0 (Realtek) was used to connect to my LAN.

---

### Post by praseodym on 2014-06-08
Try to disable the auto-negotiation of the card:
```

sudo ethtool -s eth0 speed 1000 autoneg off
```

---

### Post by a.borque on 2014-06-09
I have issued the command, but there was no apparent feedback in terminal window. So I expect, it worked!?
Are the results persistent, or do I have to place it in a configfile so it is used every time the system is (re-)started?
As the error / crash appeared randomly I will test this new setting now and report back. [EDIT: see below]

---

### Post by a.borque on 2014-06-09
Sooner than expected:
Unfortunately the crashes / restarts continue!

---

