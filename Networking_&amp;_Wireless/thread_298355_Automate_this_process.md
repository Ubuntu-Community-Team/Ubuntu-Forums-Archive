---
title: "Automate this process"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by kewldude606 on 2006-11-12
Sorry, I couldn't come up with a good title for this.  To get my wireless to work, I have to run this script every time I boot up:
```
`sudo modprobe -r islsm_usb`
`sudo modprobe -r ndiswrapper`
`sudo modprobe ndiswrapper`

for ETH in eth1 eth2 eth3
do
`sudo iwconfig $ETH ESSID Finnie`
done

echo "Operation complete"
`ping -c 1 google.com`
```Now, I know that I can make the script run automatically at boot, but I know that there must be a better way because before I reinstalled Ubuntu it worked right on boot without a script (it didn't work out of the box, tho).

To make it work out of the box, I deleted the driver that is removed in the above script: islsm_usb (/lib/modules/2.6.15-27-386/kernel/drivers/net/wireless/prism54_softmac/islsm_usb.ko) from the filesystem.  I have tried to delete it on this installation, but it seems to get replaced on every boot.  Also, I put it in /etc/modprobe.d/blacklist but that didn't do anything either.

Thanks in advance for any help!  BTW, I am moderately competent with Ubuntu, so you don't have to write any instructions in baby-steps.  Oh, and I'm using Dapper.

---

### Post by kosmic on 2006-11-12
ok, instead of typing this :

> 
sudo modprobe -r islsm_usb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper


Just edit you /etc/modules files and add ndiswrapper, also comment out the module islsm_usb

Just one question why do you remove the module ndiswrapper and the load it again ??

---

### Post by kewldude606 on 2006-11-12
Removing and adding it back in was just the way it worked.  I think that the islsm_usb and it were conflicting and it didn't resolve itself until after it was readded.

My /etc/modules file doesn't have islsm_usb in it.  It only has 4 lines, actually:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod

```
Is it supposed to be like that?

Thanks for your help.

---

### Post by FrodoB on 2006-11-12
Edit /etc/modprobe.d/blacklist and add the modules that you are removing to the end of the file and reboot:

blacklist islsm_usb

then when it comes up it may just work.

---

### Post by kewldude606 on 2006-11-12
> **FrodoB said:**
> Edit /etc/modprobe.d/blacklist and add the modules that you are removing to the end of the file and reboot:

blacklist islsm_usb

then when it comes up it may just work.

I tried that, nothing changed and modprobe -l | grep islsm_usb still returned islsm_usb.

---

