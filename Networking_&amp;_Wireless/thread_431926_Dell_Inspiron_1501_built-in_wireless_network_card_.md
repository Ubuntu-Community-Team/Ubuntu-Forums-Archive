---
title: "Dell Inspiron 1501 built-in wireless network card won't work"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by koldrakan on 2007-05-03
Hi!

got an issue with my wireless card, it just can't find any networks:P (YES, I'm sure there is one avaliable where I've tried:P)

can anyone help me with this rather unspecified problem?

I run 7.04 Feisty

---

### Post by Praill on 2007-05-03
There could be a bunch of problems here. Is the card detected? Is their a driver installed that supports it?
I always try this first when troubleshooting wireless in linux.

Disable ANY encryption on the signal.. open it up.

Go to a terminal and type iwconfig
if you see a device then youre good to go.. if not.. good luck.. i cant help you :)

manually assign the essid:  sudo iwconfig <device name> essid <network name>

if this gets your wirelss working then its a problem with your network manager.. which is not uncommon.

---

### Post by koldrakan on 2007-05-03
This is what I got:



lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

koldrakan@koldrakan-laptop:~$

---

### Post by whayong on 2007-05-03
Sorry, I'm not familiar with your wireless card.  I do however recall seeing a bunch of posts about it.  Did you try the search function?

---

### Post by dbott67 on 2007-05-03
You could try [this way]("http://ubuntuforums.org/showthread.php?t=405990") (easy) or use the method I did ([using ndiswrapper]("http://ubuntuforums.org/showthread.php?t=274915") - a little harder, but works well if you follow the directions carefully).

-Dave

---

### Post by Praill on 2007-05-07
The problem here looks relatively simple. The card is detected.. which is 95% of the battle... so thank god for that. The computer is just not connected to a network. 
I know feisty has a good wirless manager that auto-detects netowrks and uses wpa-supplicant by default out of the box (Kubuntu did for me at least). This is not true for edgy however.

To get your card working for now you can manually connect it to your network by typing
```
sudo iwconfig eth1 essid <network name>
```
replace <network name> with the name of your wireless network. If you dont know it you'll have to use a windows machine to see what it is, or use a wired connection to see what it is set to in your router configuration. There might be an easier way in ubuntu to scan for signals that are broadcasting SSID's but I dont know it.

Once you are connected to the wireless network you can look for ways to make your life easier everytime you boot. I remember when I got it working in edgy I had to sudo apt-get install wpa-supplicant gnome-network-manager
then edit some config file and comment out all devices but "lo". Id look this up for you but im at work right now. If you cant figure it out perhaps I could get your distro information (feisty, edgy, dapper.. either using gnome or KDE) and could look it up for you later.

---

### Post by golfing22 on 2007-05-07
[http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)

Try that, I have the same system as you and that guide worked for me.

---

### Post by pyros on 2007-05-12
> **golfing22 said:**
> [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)

Try that, I have the same system as you and that guide worked for me.

I second that. Although I used the post here on the forums for the 1505, (it uses the same wireless card and the works with the same dell driver.) the instructions are the same.

---

