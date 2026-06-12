---
title: "Wi-fi periodically drops on ubuntu 14.04 LTS"
date: 2014-05-27
forum: Networking &amp; Wireless
---

### Post by tgurbanov on 2014-05-27
Hi,
Wi-fi connection on my laptop became unstable after I've updated to ubuntu 14.04. Wi-fi periodically drops and it looks like wi-fi is going to sleep. I looked through several solutions (like disabling n-protocol, ignoring IPv6, etc.), but nothing worked for me. In ubuntu 12.04 connection was stable. Here is the output of [wifi script]("http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385"): [http://pastebin.ubuntu.com/7530945/](http://pastebin.ubuntu.com/7530945/). Can anybody help me?

```
$ lspci | grep Wireless
25:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

---

### Post by praseodym on 2014-05-27
Hi,

N-protocol is not necessary for Atheros chips, disable the hardware encryption and the power management instead:
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
sudo iwconfig wlan0 power off
```
Check
```

grep 11n /etc/modprobe.d/*
```
for "wrong" configs. How did you disable it?

---

### Post by tgurbanov on 2014-05-27
> for "wrong" configs. How did you disable it?

I added 
```
options iwlwifi 11n_disable=1
```

to /etc/modprobe.d/iwlwifi.conf

```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwldvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```

---

### Post by tgurbanov on 2014-05-27
I disabled the hardware encryption run modprobe.
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k

```

After these actions wi-fi turned off and I couldn't run it. So, I restarted ubuntu. Now wireless connection works.

I tried to run ```
sudo iwconfig wlan0 power off
```, but i got:
```

$ sudo iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

```

Any suggestions?

---

### Post by tgurbanov on 2014-05-27
Also, after several minutes of work, wi-fi connectio drops again

---

### Post by praseodym on 2014-05-28
SO:

```
sudo rm /etc/modprobe.d/iwlwifi.conf
```
Change the encryption mode to pure WPA2-AES (CCMP), check the router manual

---

### Post by tgurbanov on 2014-05-28
I found solution here: [http://ubuntuforums.org/showthread.php?t=2211168&p=12963298#post12963298](http://ubuntuforums.org/showthread.php?t=2211168&p=12963298#post12963298) 
I installed **backports **and now wi-fi working fine.

---

