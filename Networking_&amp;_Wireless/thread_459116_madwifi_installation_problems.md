---
title: "madwifi installation problems"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by xGutsAndGloryx on 2007-05-30
I am having troubles installing the madwifi wireless driver. my notebook has a built in wireless adapter... i am not getting any error messages. i am just having troubles configure, building & installing it. Can anyone point me in the right direction?

---

### Post by chili555 on 2007-05-30
Let's start by telling us which step has you stopped. Did you get any error messages at any point in the process? Are you building the madwifi modules from a tar.gz? Which one?

---

### Post by stchman on 2007-05-30
> **xGutsAndGloryx said:**
> I am having troubles installing the madwifi wireless driver. my notebook has a built in wireless adapter... i am not getting any error messages. i am just having troubles configure, building & installing it. Can anyone point me in the right direction?


You have (2) choices:

1.  Go to my website and follow this procedure:  [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

2.  Upgrade to Feisty as it supports nearly all the Atheros wireless cards out of the box.

Festy is far better with wireless than Edgy.

---

### Post by xGutsAndGloryx on 2007-05-30
> **chili555 said:**
> Let's start by telling us which step has you stopped. Did you get any error messages at any point in the process? Are you building the madwifi modules from a tar.gz? Which one?

i received no error messages
i download madwifi modules and extract them to my desktop

typed in the directory it was located and typed make 
followed by make install

i followed by restarting a checking to see if the wireless was detected.

---

### Post by xGutsAndGloryx on 2007-05-30
i went home during lunch to give installing the madwifi driver another try to find out... last night i must have screwed up my pc during trying.... its saying its connecting to the internet but when i click on my browser... it just times out?  is there anyway to perform a repair or system restore like in windows?

---

### Post by spd106 on 2007-05-30
Two things that might help

1) Check that you have disabled the restricted modules driver included in Edgy as directed on this page [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)
If you run **dmesg | grep ath**, it will tell you which version of madwifi you is being used.

2) Sometimes I find that it connects better if I reload the driver. To do this run these commands
```
sudo modprobe -r ath_pci
```
```
sudo modprobe ath_pci
```
If network manager fails, then restart it with
```
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

Probably best to copy/paste these commands, I only remember them through tab completion.

---

### Post by tturrisi on 2007-05-30
To build the madwifi driver from sources you need additional packages and as well need to be root to make & install.  If you have installed the linux-restricted-modules then uninstall the madwifi driver.

then do:
```

application > accessories > root terminal

apt-get install build-essential
apt-get install linux-headers-`uname -r`
ifconfig ath0 down
ifconfig wifi0 down
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng
wget http://patches.aircrack-ng.org/madwifi-ng-r2277.patch
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
make install
depmod -ae
modprobe ath_pci

```

---

