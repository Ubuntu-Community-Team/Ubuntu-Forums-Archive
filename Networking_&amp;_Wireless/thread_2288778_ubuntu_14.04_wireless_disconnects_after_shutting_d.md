---
title: "ubuntu 14.04 wireless disconnects after shutting down the laptop"
date: 2015-07-29
forum: Networking &amp; Wireless
---

### Post by nur4 on 2015-07-29
I recently installed ubuntu 14.04 LTS along side Win8.1 on my new laptop. Wireless connection worked well for a day and then it started disconnecting whenever I downloaded something or restarted/shut down the pc. The connection can only be brought back again if I switched the router on and off.

I tried this:

[http://askubuntu.com/a/537375/433874](http://askubuntu.com/a/537375/433874)

It connected me to network but whenever I restart the pc the Power Management is on again and I have to switch the router on and off all over again.
I don't think its a problem with my router cuz my old laptop had ubuntu 12.04 with win7 and there was no problem.

When I run this for buggy N:
```
modprobe -r iwlwifi && modprobe iwlwifi 11n_disable=1
```

It gives the following: 
```
rmmod: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'iwlmvm': Operation not permitted
rmmod: ERROR: could not remove module iwlmvm: Operation not permitted
rmmod: ERROR: Module iwlwifi is in use by: iwlmvm
modprobe: FATAL: Error running remove command for iwlwifi
```

Any help?

---

### Post by Hadaka on 2015-07-29
Hi,give this a try..
```
sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```
wlan0 should come right back up; check:iwconfig

---

### Post by nur4 on 2015-07-29
> Hi,give this a try..
 	Code:
 	sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1 
wlan0 should come right back up; check:iwconfig

I tried it. It worked for 3 reboots then the same problem emerged again..

---

### Post by Hadaka on 2015-07-29
ok. lets make it permanent so it doesnt go away on a boot.
please copy and paste to avoid error,
```
sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf

```
thanks.

---

### Post by nur4 on 2015-07-29
> **Hadaka said:**
> ok. lets make it permanent so it doesnt go away on a boot.
please copy and paste to avoid error,
```
sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf

```
thanks.

Did not work too. it displayed:

```
options iwlwifi 11n_disable=1
```

When running iwconfig :

```
eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.
```

I run iwconfig on my old *network-working* laptop it showed that Power Management is off. I think that may be it but no commands are working for *permanently* turning Power Mangement off.

---

### Post by Hadaka on 2015-07-29
open a terminal  ctrl/alt/t
and do
```
sudo gedit /etc/rc.local
```

enter these lines  in the editor
```
iwconfig wlan0 power off
exit0
```
proofread..save and close gedit

then redo this..
*note THIS IS AN ENTIRE COMMAND, COPY AND PASTE...
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```

sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```

---

### Post by nur4 on 2015-07-29
THANX! It worked!

---

### Post by Hadaka on 2015-07-29
Glad that worked for you !
please take the time to use thread tools and
mark this thread SOLVED
thanks

---

