---
title: "Wifi not working on Inspiron E1505, new install of Lubuntu 12.04"
date: 2015-06-21
forum: Networking &amp; Wireless
---

### Post by woomonkey on 2015-06-21
This Inspiron was previously running XP. I upgraded the RAM and swapped the HDD for a SSD to boost its responsiveness and decided to go with Lubuntu 12.04, because it's 32-bit (unless I am mistaken), as is this computer. I just want this computer as basically a web browser

Here is what I have tried so far (with Ethernet cable connected):

1) [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR]
which completed without problem.

2) [COLOR=#000000][FONT=Ubuntu Mono]lspci -nn -d 14e4:[/FONT][/COLOR]
to find the wireless controller. which was [COLOR=#000000][FONT=Ubuntu Mono]14e4:4311[/FONT][/COLOR]

3) So I installed 
[COLOR=#000000][FONT=Ubuntu Mono]firmware-b43-installer [/FONT][/COLOR]
and it seemed to complete.

4) Went into Network Connections and have set up the Wireless network with the proper SSID, Mode set to Infrastructure, MTU to automatic and the other fields blank.
IPv4 and v6 have Automatic (DHCP)
Wireless Security set to WPA and 2 Personal, with the right password.

5) Rebooted.

6) The computer gives no indication that it recognises I have a wireless network. When I unplug the Ethernet cable, the wifi symbol in the system tray says "No network devices available".

Thank you so much for any assistance you can render.

---

### Post by wildmanne39 on 2015-06-21
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by woomonkey on 2015-06-21
Well, I did that and now the wired connection isn't working either despite multiple reboot and double-checking the cable's seating.

---

### Post by wildmanne39 on 2015-06-21
The wired connection did not stop working because you tried the wireless script I assure you of that! Most likely when you tried to install firmware it blacklisted a module that you need so please post the output of these commands and put it between code tags by clicking on #.
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
cat /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by wildmanne39 on 2015-06-21
Only guessing without the information, but pretty sure if you do:
```
sudo apt-get purge bcmwl-kernel-source
```
then reboot your wired connection should be working and possibly your wireless.
Thanks

---

### Post by praseodym on 2015-06-21
Install the missing firmware from here:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot.

---

### Post by woomonkey on 2015-06-21
@praseodym
EDITED:
Your firmware worked! 

Y'all, thank you very much! I really appreciate your responsiveness and your substantive answers.

---

### Post by woomonkey on 2015-06-21
@Wild Man
EDITED:
Also that purge command cleared up the wired connection! :-)

---

### Post by wildmanne39 on 2015-06-21
Was wired working when you tried to install the firmware by praseyodym?

---

### Post by wildmanne39 on 2015-06-21
It would be better to run the wireless script and post the file.
Thanks

---

