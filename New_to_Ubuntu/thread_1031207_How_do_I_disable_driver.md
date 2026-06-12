---
title: "How do I disable driver??"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by mariane_08 on 2009-01-05
How do I DISABLE the Broadcom open source driver (bc4318) for my wireless card? I have a problem with it and need to disable it before trying the ndiswrapper route. Is there a terminal command for this?

Thanks

---

### Post by Michael.Godawski on 2009-01-05
hi, 
try this
```
gksudo gedit /etc/modprobe.d/blacklist
```
and add the following line to the end of the file
```

blacklist drivername
```

change drivername to the name of the module you want to blacklist, so it is not loaded during the boot.

See also.

[LIST]
[*][https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)
[/LIST]

---

### Post by mariane_08 on 2009-01-05
> **Michael.Godawski said:**
> hi, 
try this
```
gksudo gedit /etc/modprobe.d/blacklist
```
and add the following line to the end of the file
```

blacklist drivername
```

change drivername to the name of the module you want to blacklist, so it is not loaded during the boot.

See also.

[LIST]
[*][https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)
[/LIST]

Thanks! 
OK I have a couple of questions. 

In terminal lspci gives me:

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

So do I enter "blacklist BCM4318" or "bcm43xx"?

And if later I want to remove the blacklist entry do I simply delete it manually?

Thanks

---

