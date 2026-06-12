---
title: "Networking Disabled on reboot"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by kc5hwb on 2010-09-22
Whenever I reboot my Ubuntu laptop, which connects wirelessly to my home internet, the Networking connection always comes up as disabled.  I have to manually enable it, and then manually connect to my wireless network, which has a hidden SSID but is also saved in my connections on this laptop.

How do I set the wireless to enable upon startup and connect to my home network?

---

### Post by spiky001 on 2010-09-22
if you right click network manager then edit wireless connection there is an option to connect automatically make sure it,s ticked

---

### Post by kc5hwb on 2010-09-22
It is checked.  I guess I should have said that.  I've had it checked since I freshly installed this OS on this laptop, but it still won't auto-connect and it always comes up as disabled.  I am guessing that if I can figure out why its always disabled, and change it to be enabled on boot, then maybe the auto-connect will work.... ?

---

### Post by spiky001 on 2010-09-22
I googled this [http://ubuntuforums.org/showthread.php?t=75544](http://ubuntuforums.org/showthread.php?t=75544)  it is old it sayes in network interfaces (auto eth0),mine has got that, I,m no expert on this just trying to help

---

### Post by drorata on 2010-10-04
I have more or less the same problem for the last 2 days though... For me it maybe related to some update or something as the suspend option is broken as well for 2 days.

---

### Post by NightwishFan on 2010-10-04
Press Alt+F2 and type:
```
gconf-editor
```

Navigate to Apps -> nm-applet, and check the settings there.

---

### Post by ehsanotaku on 2010-10-04
> **NightwishFan said:**
> Press Alt+F2 and type:
```
gconf-editor
```Navigate to Apps -> nm-applet, and check the settings there.

Hi there ^;^
Still doesn't solve the problem ,, I only could disable a couple of notification upon detecting wireless SSID ,,
NO option has been given for making it enable from the beginning,, ( using Eee pc Asus 1005px ) ,, which comes with the  Atheros  AR2427 Wireless Network Adapter ,, PCID : 168c:002c , ath9k 

Above information was provided after installing the device manager . However it failed to report back the exact details of my pci card ,, just it mentioned it belongs to atheros under the network controller .

I also used the terminal to observe and make sure I have it enabled , but to my surprise the wireless marked as disabled ! ( Do we have some option in the Bios or some special config to resolve ? )

```
Lshw -class network 
```more technical info : using dual-boot system , Win7 starter with netbook version of  Ubuntu ( latest ver . Kernel upgraded through update manager )

and last question is , Do I need to do it via NdisWrapper and launch some winxp driver , after extracting .info , .sys which is related to the appropriate driver or there is an obvious solution for it ?

Thx in advance guys ^;^


**EDIT :  **Finally managed to enable my wireless card by clicking Fn+F2 ^.^  yeh just figure it out when i did a 
```
rfkill list 
```  ,, ,, just one problem now guys ,, despite having a dozen of access points available , it didn't detect any SSIDs ! Guess need to reboot ,, report back ASAP,,

-----------------------------

Nope didn't show any live router/modems in my area !!,, I think ,, I might need an expert assistance to get it work ,,,

---

