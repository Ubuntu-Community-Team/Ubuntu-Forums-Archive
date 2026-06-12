---
title: "SOLVED - Lubuntu+wifi card recognized but not working"
date: 2017-03-10
forum: Networking &amp; Wireless
---

### Post by rhianb on 2017-03-10
I installed Lubuntu v16.10 & cannot get my wireless card to work. Lubuntu sees the card under system information -> PCI devices as:
 
Network controller : Broadcom Limited BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I downloaded the driver package "firmware-b43-installer" using synaptic Package manager  which shows this card as listed as supported and then installed it - the latest version 1:019-3. Still, after reboot, Lubuntu does not find any networks. I have been using a wired ethernet cable but want to use this connected to my TV as a media server of sorts. Anyhow, as I'm new to Lubuntu, I'm kinda stumped at this point. Is my wifi card broken maybe or am I not doing something right? 

What do you guys/gals think?  Thanks for any help in advance :)

---

### Post by jeremy31 on 2017-03-10
Please see the wireless script link in my signature and post your results

Welcome to the forums

---

### Post by slickymaster on 2017-03-10
*Thread moved to **Networking & Wireless**.*

---

### Post by kc1di on 2017-03-10
Hello rhianb and Welcome to Ubuntu,

Did you try using the drive manager while the machine is connected via ethernet?  If you did which drive did it recommend? 

Could you go to a terminal and copy and past the  the following command ```
lsmod | grep -e b43 -e wl
``` Then hit enter and copy and  post the results here.

---

### Post by rhianb on 2017-03-10
> **kc1di said:**
> Hello rhianb and Welcome to Ubuntu,

Did you try using the drive manager while the machine is connected via ethernet?  If you did which drive did it recommend? 

Could you go to a terminal and copy and past the  the following command ```
lsmod | grep -e b43 -e wl
``` Then hit enter and copy and  post the results here.

This came back. 

wl                                  6152192  1
cfg80211                    512000  1     wl


Also, I am unfamiliar with "drive manager". Is this a package available to me via Synaptic package manager[?] or is it something I can activate via Terminal?

---

### Post by jeremy31 on 2017-03-10
I would uninstall the wl module with
```
sudo apt-get remove bcmwl-kernel-source broadcom-sta-common broadcom-sta-dkms
```

You might see a couple warnings about 2 packages not being installed but reboot after and see if wifi works

---

### Post by rhianb on 2017-03-10
> **jeremy31 said:**
> I would uninstall the wl module with
```
sudo apt-get remove bcmwl-kernel-source broadcom-sta-common broadcom-sta-dkms
```

You might see a couple warnings about 2 packages not being installed but reboot after and see if wifi works

Wow Jeremy, works great now. What were you looking for and what did you remove? Pretty amazing. Thanks for all of your help. :)

---

### Post by jeremy31 on 2017-03-10
You had the proprietary broadcom module installed for a chipset that works better with b43 and the firmware.  Installing the proprietary module blacklists the open source modules and removing the proprietary module removes the blacklist and allows your wifi to use the b43 module with the firmware you had installed.

There is a sticky post [here](https://ubuntuforums.org/showthread.php?t=2214110) but I know it can be confusing for new users just because they are new to Ubuntu

---

### Post by rhianb on 2017-03-10
I poked around on the forums trying to find a solution but obviously did not find the noted thread. Thanks again for your help and understanding.

---

### Post by kc1di on 2017-03-10
rhianb  Glad it's working for you :)

The driver manager is found in the system control panel.  it searches for drivers for Propitiatory hardware.  
But as Jeremy said you had the wl driver install along with the b43 and they conflict.  b43 is the best for your card.

---

