---
title: "Trying to get Gutsy and D-Link wireless USB to play nice."
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by Supertonic on 2007-10-29
Hello folks.  Well I just installed gutsy on my desktop.  I am using a D-Link WUA 2340 wireless USB adapter.  I did manage to get it working, but not without a little kink that needs to be worked out.  I shall outline my steps thus far, and explain the problem as I go.

Ok, so first off I got nidswrapper installed and good to go using the command(s)

```
 sudo apt-get install ndiswrapper-common 
``` for this step you must have your distro install CD.

Next, I went to synaptic package manager and searched for "ndis", I found ndiswrapper-utils-1.9 and installed.

Ok, I am good to go with ndiswrapper.

Next, I went to my windows XP side of the Hard Drive (where the wireless adapter works) and downloaded the latest driver for the D-Link.  The name of the file is **NetA5AGU.inf**

Onwards.  I then blacklisted a few drivers that ubuntu might try and associate with the adapter (I did a similar procedure for configuring my broadcom on my laptop).

```
 gksu gedit /etc/modprobe.d/blacklist 
```
The drivers I blacklisted are as follows:
```
 blacklist ath_pci 
blacklist ath_hal 
```
Save, and close the editor.  (I am not sure this is entirely necessary?)

Next, install the driver I downloaded which is residing in *~/Desktop/Driver*

```
 ndiswrapper -i NetA5AGU.inf 
```
Next, edit the modules file so ndiswrapper will load each time ubuntu boots up.
```
 gksu gedit /etc/modules 
```
add * ndiswrapper * at the end of the file, save and exit.

Now as I understand it, after adding ndiswrapper to the modules file it should allow me to configure the wireless network device after a reboot.  This does not happen.  

** How I got it to work with a catch **

      I booted up ubuntu with the dlink *unplugged* from the USB slot.  After logging in, I plugged in the dlink and whaddayaknow, it is recognized, I can configure the wireless device via network tools, and login to my wireless network with no problem. (Sweet, time for a drink right? Wrong).  

** This is where I need Help**
So I reboot to make sure everything is good, and low and behold, the wireless configuration has disappeared from the network tools again.  Gah! I don't want to have to unplug and plug in my device everytime I boot to get it to work.  How do I get ubuntu to recognize the Dlink adapter with it plugged in upon startup?
```
 ndiswrapper -l 
``` shows:
```
 neta5agu : driver installed
           device (07D1:3A08) present
```    and still I am not able to even see a wireless connection on the network settings manager.  :confused:

Any help is much appreciated.  Thanks folks!

---

### Post by Supertonic on 2007-11-02
Bump on my birthday.  Hey anyone wanna give me a present and help me? WHee heee.

---

