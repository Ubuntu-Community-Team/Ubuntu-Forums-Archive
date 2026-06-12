---
title: "wireless setup error"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by clayburn88 on 2006-09-21
I am trying to get my wireless card setup from the instructions [here]("http://ubuntuforums.org/showthread.php?t=201902").  Unfortunately, when I input ndiswrapper -l it gives me this: ```
bcmw15  invalid driver!
```

Any suggestions on what to do?  I have gotten stuck.

---

### Post by wieman01 on 2006-09-21
When you install the driver (*.inf) make sure all other driver files such as *.cat are in the same directory as *.inf. All files need to be present in order for the system to recognize the new (Windows) driver.

---

### Post by haxx on 2006-09-21
Dapper provides a native driver for the BCM 43xx series driver i fought and fought with this plague but am know flawless with my own.

I could use a little info.
Your essentials mostly 
MoBo, CPU, Exact Distro, Exact wifi card (which is what we will get from the terminal command)

In terminal please type-
    lspci
you may need to add "sudo"(without "")depending on the distro

---

### Post by Melcar on 2006-09-21
If using a Broadcom device make sure you blacklist the Dapper-provided driver first before doing anything with ndiswrapper.

---

### Post by haxx on 2006-09-22
The NDIS WinXP driver setup is less potent than that of the native linux driver.

The NDIS I have gotten going in the past as well and every time I have it lost the connection more often and used more battery power. Aswell I performed range tests and at ideal times I got an extra 20-40 feet of effective range.

Native is the way to go.

We need to determine if you have update to the new kernel and than go about updating the native bcm43xx firmware from a reository to get you online.

Please post back the info I previously requested.

---

