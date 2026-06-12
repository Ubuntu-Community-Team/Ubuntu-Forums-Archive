---
title: "Rosewill RNX-EasyN1 driver dead link (Ralink RT3070)"
date: 2015-07-19
forum: Networking &amp; Wireless
---

### Post by N3X15 on 2015-07-19
I have an old Lenovo IdeaPad U550 that I'm trying to bring up to snuff for use as a mobile workstation.  Unfortunately, it's got a burnt-out internal wireless device (confirmed by the manufacturer), so I'm trying to make do with a Rosewill RNX-EasyN1 USB dongle.  This little device works fine on Windows 7, but ole Kubuntu just doesn't like it,  doesn't even come up in ifconfig, not to mention the Network Manager.  I've already blacklisted the rt2800usb kernel module, which hasn't improved matters.  In addition, the drivers provided from Rosewill are from 2009 and don't even compile.  Ralink, the chipset manufacturer, has gone kaput and a domain squatter has obtained their website, which puts a damper on obtaining their driver tarball.

Any ideas?  I can get on with a wired connection, but I can't see wandering around the house with a humongous CAT5e cable being very optimal.  I also suspect there are more than a few people out there with the same issue.

wireless info script dump: (Ignore the IdeaPad adapter on wlan0, it's toast)
[http://paste.ubuntu.com/11902194/](http://paste.ubuntu.com/11902194/)

Compile errors on the Rosewill driver tarball (2009_0525_RT3070_Linux_STA_v2.1.1.0), capturing both stdout and stderr:
[http://paste.ubuntu.com/11902276/](http://paste.ubuntu.com/11902276/)

It's probably something extremely obvious I've forgotten to do, but any help with this is greatly appreciated.

---

### Post by Vladlenin5000 on 2015-07-19
Ralink was acquired by Mediatek a long time ago...
Here are the newest drivers: [http://www.mediatek.com/en/downloads1/downloads/?sort=os](http://www.mediatek.com/en/downloads1/downloads/?sort=os)

---

### Post by praseodym on 2015-07-19
Hi,

the wireless is turned off. Button, key or key combo? Tried to reset the BIOS to default? The driver for the internal card is loaded.

Edit:

```
modprobe -c | grep -i "148f.*3070"
alias usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*in* [COLOR="#FF0000"]rt2800usb[/COLOR]
```

---

### Post by N3X15 on 2015-07-19
> **Vladlenin5000 said:**
> Ralink was acquired by Mediatek a long time ago... Here are the newest drivers: [http://www.mediatek.com/en/downloads1/downloads/?sort=os](http://www.mediatek.com/en/downloads1/downloads/?sort=os) Thank you, I'll give those a shot.  > **praseodym said:**
> Hi,  the wireless is turned off. Button, key or key combo? Tried to reset the BIOS to default? The driver for the internal card is loaded.  Edit:  ```
modprobe -c | grep -i "148f.*3070" alias usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*in* [COLOR="#FF0000"]rt2800usb[/COLOR]
``` Yes, I know that, and Windows also recognizes it and tries to activate it.  However, it's the classic "lights are on, nobody's home" issue, where any action to activate the device fails to register.  It's like trying to talk to a brick wall.  I've even taken it to a guy I know in town, in case it was something stupid on my part, but he confirmed the internal device is nonresponsive, even with the function-key sequence to turn it on.  BIOS is at factory settings, too, so it's not that.

---

### Post by praseodym on 2015-07-20
Try it with the Intel driver unloaded:
```

sudo modprobe -rfv iwlwifi rt2800usb
sudo rfkill unblock all
sudo modprobe -v rt2800usb
```
Check
```

rfkill list
iwconfig
dmesg | grep rt2
```
Maybe unloading this module helps:
```

sudo rmmod ideapad_laptop
```

---

### Post by N3X15 on 2015-07-20
> **praseodym said:**
> Try it with the Intel driver unloaded: ```
 sudo modprobe -rfv iwlwifi rt2800usb sudo rfkill unblock all sudo modprobe -v rt2800usb
``` Check ```
 rfkill list iwconfig dmesg | grep rt2
``` Maybe unloading this module helps: ```
 sudo rmmod ideapad_laptop
```  Thanks, the first block got it working.  For anyone reading this thread via Google, I also had to restart the network-manager service to get KDE to acknowledge that device existed: ```
 sudo service network-manager restart 
```  I did not need to remove ideapad_laptop.

---

### Post by praseodym on 2015-07-21
Blacklist the Intel driver:
```

echo "blacklist iwlwifi" | sudo tee /etc/modprobe.d/blacklist-iwlwifi.conf
```
if it is loaded again after rebooting

---

