---
title: "Lost connection every restart for wlan0, workaround script but still need pemissions"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by darkborg on 2007-04-02
Folks,

Good morning, I am a newbie, Linux brought me a lot of challenges, which ones I am willing to try let me explain a
little bit in the past few days I was able to install my zydas adapter usb wireless I can make it work but after you restart it goes away with the ip address so next boot I got to restart it manually, I know there are a lot of of workarounds but I found one
that seems to be effective so you do not need to do a dhcp wlan0 every time you restart.

Script

1) Open up a terminal and go to /etc/init.d


Code:
cd /etc/init.d/2) make a new file called start-netorking as root


Code:
sudo vi start-networkingsubstitute vi with gedit or whatever if you wish

3) Make it a script that just starts your interfaces. Use this as an example:


Code:
#!/bin/bash

ifup wlan0
ifup eth1I have 2 interfaces called eth0 and eth1. You will probably only need the eth0 part if you only have 1 NIC.

4) change mode of script

Code:
sudo chmod 755 start-networking

5) Code:
cd ../rc2.d/7) make a link to your script in this dir


Code:
sudo ln -s ../init.d/start-networking S90start-networking


Now the ONLY problem is that when reboots it will ask you for
sudo for that script, remember I am a NEWBIE, so if asks for sudo will ask for a password and if you don't type it will skip the script "sudo ln -s ../init.d/start-networking S90start-networking" , how do I do in order to execute this script without being sudo? I know it might be risky but I found it's an efective workaround...how do I change permissions for this script and all
the scripts behind this in order to make ANY user able to run it at the boot time?


Thanks!

---

### Post by chili555 on 2007-04-02
I admire your skill and resourcefulness. However, I am a bit puzzled. Do you have two wireless interfaces you are trying to start?> ifup wlan0
ifup eth1This will probably never work.
If you are just trying to get wlan0 to start on boot, it will usually do so with this addtion to /etc/network/interfaces:```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

**auto wlan0**
iface wlan0 inet dhcp
wireless-essid myrouter1
wireless-key 096cxxxxxxxxxxxxxxxxafe restricted

```If I have misunderstood, please correct me.

---

### Post by darkborg on 2007-04-02
> **chili555 said:**
> I admire your skill and resourcefulness. However, I am a bit puzzled. Do you have two wireless interfaces you are trying to start?This will probably never work.
If you are just trying to get wlan0 to start on boot, it will usually do so with this addtion to /etc/network/interfaces:```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

**auto wlan0**
iface wlan0 inet dhcp
wireless-essid myrouter1
wireless-key 096cxxxxxxxxxxxxxxxxafe restricted

```If I have misunderstood, please correct me.

Hey!
Thanks for the quick reply
Indeed my /etc/network/interfaces looks pretty much the same like the one you described just add the psk key and it's the same :)  now when it reboots and you do a ifconfig
or iwcondif you can see that there is no ip, I tried wpagui since network adming does not support wpa, every
single time you need to do dhcp wlan0 if I had a script that I can load and execute at the boot process that will be great but as I said before it requires certain permissions to run dhclient like sudo need to modify that script!
And I know it works because first time I installed I played with chmod and sudo and I "disabled" sudo, for my surpise that same script worked fine! but there was no sudo
since I was no able to restore sudo and my root password got lost? Nothing else to do wipe out and start from zero.

Any ideas?

Thanks!

---

### Post by sica07 on 2007-04-05
Hello, I don't know if I'm right, but can this problem be solved  controling the run level? I found this: [http://tldp.org/HOWTO/HighQuality-Apps-HOWTO/boot.html](http://tldp.org/HOWTO/HighQuality-Apps-HOWTO/boot.html). I hope it helps.

---

