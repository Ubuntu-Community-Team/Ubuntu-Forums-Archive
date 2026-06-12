---
title: "Unable to connect to my wireless network in Ubuntu 8"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by magenta3604 on 2008-05-04
Okay, 
I was just able to get connected to my wireless network in Ubuntu 7.10 and then after upgrading to Ubuntu 8 I haven't had much success.  When i type "sudo iwconfig" to get the network information I noticed that the nothing is associated with the Access Point; in 7.10 my MAC Address was associated with the Access Point.  I'm getting frustrated because I truly HATE windows and would prefer to use a Linux OS for my work. Please see below for the iwconfig results:

root@patti-laptop:~# iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
eth1      IEEE 802.11g  ESSID:"NETGEAR"            
	  Mode:Managed  Channel:0  Access Point: Not-Associated             
	  Tx-Power=0 dBm             
	  Retry min limit:7   RTS thr:off   Fragment thr=2346 B             
	  Encryption key:35F1-XXXX-XXXX-XXXX-XXXX-XXXX-A8          
	  Link Quality:0  Signal level:0  Noise level:0          
	  Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          
	  Tx excessive retries:0  Invalid misc:0   Missed beacon:0

HELP!!!!:confused:

---

### Post by nixscripter on 2008-05-05
1. Does your access point use encryption? If so, make sure the encryption modules are being loaded with the command ```
lsmod | grep ieee
``` You should see something like ieee80211_crypt_wep, for example, if you are using wep.

2. Sometimes cards need to have their interfaces raised before they will do anything. See if the command ```
sudo ifconfig eth1 up
``` fixes it. It's unlikely, but worth a shot.

3. It may seem silly, but make sure the card is well seated (I assume it is or it wouldn't detect), and that the antenna is connected.

4. What kind of card are you using (**lspci** can tell you)? Sometimes driver problems show up as "link quality: 0".

---

### Post by c00ch on 2008-08-18
Has anybody found a solution for this? I am having exactly the same problems. I upgraded tu Ubuntu 8 and that killed my wireless connectivity. wicd is shownign me all the access points in the vicinity and I can connect to my WEP AP alright (or so it seems) but the Network Icon tells me that I am connected to my router ar 0 dBm%.

It's a mega drag.:(

---

