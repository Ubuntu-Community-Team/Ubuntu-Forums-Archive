---
title: "Unable to use wireless."
date: 2010-04-24
forum: New to Ubuntu
---

### Post by mastermael on 2010-04-24
I recently set my computer up with Win7/9.10 dual boot, but I cannot seem to access my wireless from ubuntu. I have looked around and cannot find the answer, I am still in the extreme beginner stage but will do my best if you can help me.

---

### Post by suryaccnamcse on 2010-04-24
Are you able to see your wireless network in the network manager. Install WiFi Radar, it helps a lot...

---

### Post by xumuk37 on 2010-04-24
could you tell us, please, if it's a desktop or laptop and it uses internal or external wireless adapter? is a wifi indicator on? Are Enable Networking and Enable Wireless boxes checked?

---

### Post by mastermael on 2010-04-24
> **xumuk37 said:**
> could you tell us, please, if it's a desktop or laptop and it uses internal or external wireless adapter? is a wifi indicator on? Are Enable Networking and Enable Wireless boxes checked?

Laptop, Internal, There is no Enable wireless box, but enable networking is checked. Wifi indicator, could you be more clear?

---

### Post by xumuk37 on 2010-04-24
the light that indicates that your wifi is on...
try to put this in Terminal: ```
sudo lspci|grep -i wireless
```

---

### Post by mastermael on 2010-04-24
Wi-Fi is on, I get no reponse to that code.

---

### Post by xumuk37 on 2010-04-24
try```
sudo lspci|grep -i net
```

---

### Post by mastermael on 2010-04-24
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

---

### Post by P4man on 2010-04-24
That broadcom chipset is giving tons of problems with linux. Really hit and miss if you read all the posts about it. There are ways to get it up using native drivers, but the easiest solution is probably using ndiswrapper, which lets you load windows drivers (only for network cards).

Go to applications > ubuntu software center

Look for "ndiswrapper" (aka as "windows wireless drivers") and install it.

After installing you will have a new menu item in 

System > adminstraton > windows wireless network drivers

Use it to install your windows driver for the card (you need the .inf file, so you may need to unpack or search a bit, it doesnt take a .exe). If you use 32 bit ubuntu, use the 32 bit windows driver, and 64 bit driver for 64 bit ubuntu.

Some additional steps may be required, but lets start with that.

---

### Post by novelty on 2010-04-24
Before trying ndiswrapper check to see if you have drivers available for your card.

Assuming you have updated, try:

System>Administration>Hardware Drivers

If your broadcom driver is there select the driver and click enable.

---

### Post by mastermael on 2010-05-04
Sorry I didnt respond, I wasnt able to access much computer time this last while,Novelty idea worked, thanks all who helped :D

---

