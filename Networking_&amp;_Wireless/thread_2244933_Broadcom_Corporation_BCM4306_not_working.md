---
title: "Broadcom Corporation BCM4306 not working"
date: 2014-09-19
forum: Networking &amp; Wireless
---

### Post by rob-5star on 2014-09-19
since upgraded to 14.04.1 haven't been able to use wireless tried several things but still no go.

---

### Post by jeremy31 on 2014-09-19
Well you can start with ```
sudo apt-get install [COLOR=#000000][FONT=Ubuntu Mono]firmware-b43-installer
``` and reboot.  Hopefully it works after a reboot[/FONT][/COLOR]

---

### Post by rob-5star on 2014-09-19
will try that brb

---

### Post by rob-5star on 2014-09-19
Preparing to unpack .../firmware-b43-installer_1%3a018-2_all.deb ...
Unpacking firmware-b43-installer (1:018-2) ...
Setting up firmware-b43-installer (1:018-2) ...
No chroot environment found. Starting normal installation
--2014-09-19 14:00:07--  [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)
Resolving   ( )... failed: Name or service not known.
wget: unable to resolve host address ‘ ’
dpkg: error processing package firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
pegamoose@pegamoose-Pavilion-zd7000-DS487U-ABA:~$

---

### Post by rob-5star on 2014-09-19
still not working

---

### Post by jeremy31 on 2014-09-19
Do you have any internet access from the Ubuntu pc?

---

### Post by rob-5star on 2014-09-19
yes wire

---

### Post by jeremy31 on 2014-09-19
So what happens when you ```
ping lwfinger.com
```

---

### Post by rob-5star on 2014-09-19
64 bytes from just119.justhost.com (173.254.28.119): icmp_seq=33 ttl=55 time=69.8 ms
64 bytes from just119.justhost.com (173.254.28.119): icmp_seq=34 ttl=55 time=68.9 ms
64 bytes from just119.justhost.com (173.254.28.119): icmp_seq=35 ttl=55 time=67.9 ms
64 bytes from just119.justhost.com (173.254.28.119): icmp_seq=36 ttl=55 time=66.9 ms
64 bytes from just119.justhost.com (173.254.28.119): icmp_seq=37 ttl=55 time=56.0 ms
64 bytes from just119.justhost.com (173.254.28.119): icmp_seq=38 ttl=55 time=74.8 ms
64 bytes from just119.justhost.com (173.254.28.119): icmp_seq=39 ttl=55 time=62.8 ms

---

### Post by jeremy31 on 2014-09-19
Strange, try the command again ```
sudo apt-get install firmware-b43-installer
```

If nothing else I think praseodym or chilli555 has the firmware uploaded to a dropbox account already

---

### Post by rob-5star on 2014-09-19
Setting up firmware-b43-installer (1:018-2) ...
No chroot environment found. Starting normal installation
--2014-09-19 15:43:43--  [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)
Resolving   ( )... failed: Name or service not known.
wget: unable to resolve host address ‘ ’
dpkg: error processing package firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
pegamoose@pegamoose-Pavilion-zd7000-DS487U-ABA:~$

---

### Post by jeremy31 on 2014-09-20
Time to see if Praseodym's method will work for you
```
[COLOR=#000000][FONT=Ubuntu Mono]wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz
```
```
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]and reboot [/FONT][/COLOR]

---

### Post by varunendra on 2014-09-20
Or a completely offline alternative : [http://ubuntuforums.org/showpost.php?p=13119224](http://ubuntuforums.org/showpost.php?p=13119224)

---

### Post by sheldon-corey on 2014-09-20
if that fails download firmware from another pc and copy / paste to ~/Downloads and run 


sudo dpkg -i ~/Downloads/firmware-*

---

### Post by rob-5star on 2014-09-21
that solved it ! thankyou

---

### Post by varunendra on 2014-09-23
Hey rob-5star!

Although all the suggested solutions lead to the same solution - installing/copying the required firmware, yet it would have been more helpful to the future readers if you also mentioned which one worked.

And please mark the thread as [SOLVED] using "Thread Tools" link above the top post. Thanks! :)

---

