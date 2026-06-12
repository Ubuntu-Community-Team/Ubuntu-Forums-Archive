---
title: "Wireless Network/WEP Problems"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by StrangeWeakness on 2008-04-09
Ok, so listen to this. I installed Ubuntu 7.10 after deciding upon a dual boot. I installed using the LiveCD perfectly. I then got to the Network part. It didn't pick up the network straight away, but after a while it came up. I clicked it to connect, and a a window asking me to enter the passphrase appeared. I have tried every type of WEP key (Hex, ascii etc), and it does not connect. It just repeatedly asks me to put it back in. I have double checked it, and put it into Windows again to make sure the key is correct. This was fine, so I went back into Ubuntu. No matter what I do, it just doesn't want to do it. 

I'll post the readings of my iwconfig later, but I'm on my Windows side.

Thanks in advance,

Beau.

---

### Post by StrangeWeakness on 2008-04-09
lo        no wireless extensions.

eth0      
no wireless extensions.

eth1   
unassociated  ESSID: off/any  
      
Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated  
Bit Rate: 0 kb/s   Tx-Power:16 dBm   
 
Retry limit:15   RTS thr: off   Fragment thr: off

Power Management: off
      
Link Quality:0  Signal level:0  Noise level:0
  
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
    
Tx excessive retries:0  Invalid misc:422   Missed beacon:0



I tried putting it into the paragraph it was set out in.

---

### Post by dstew on 2008-04-09
Try manually entering the essid:```
sudo iwconfig eth1 essid "*Your_ESSID*"
```Maybe the driver does not support scanning.

---

### Post by lswest on 2008-04-09
try this: ```
sudo iwconfig eth1 essid [your ssid for the network] key [key for the network] && sudo dhclient eth1
```
it sets the information for the connection in the terminal and then the dhclient program retrieves an IP for your computer from the dhcp server of your router.

---

### Post by StrangeWeakness on 2008-04-10
Guys thanks for your help, I'll try this, and post my results.

---

### Post by Lazy-buntu on 2008-04-10
I've got a very similar problem:

Currently I dual boot Windows Vista and Ubuntu 7.10 (Gutsy), but I'm running into a problem with my wireless.

I used ndiswrapper to install my wireless driver (broadcom chip =/ ) and the good news is I can see wireless networks when I do iwlist eth1 scan. (my wireless card is eth1--it doesn't appear as wlan0)

There's a problem though: I can see the networks, but I cannot connect to them. My network has a WEP key (hex) and a broadcasted ESSID. So, in my network tools I set my ESSID, put my WEP key in, and set my IP to DCHP.

I heard ipv6 can cause problems according to the built in help topics in ubuntu--it tells you to gedit /etc/modprobe.d/aliases and change ....... pf 10 ipv6    to      ........ pf 10 off--I did this and rebooted, no go. (I did change it back since then.)

Any ideas? (BTW: I can't get a wired connection, so I haven't been able to do any  updates)

---

### Post by Lazy-buntu on 2008-04-10
Made my own thread: [http://ubuntuforums.org/showthread.php?p=4692890#post4692890](http://ubuntuforums.org/showthread.php?p=4692890#post4692890)

please post anything regarding my problem there

---

