---
title: "Need help with wireless connection"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by jml1938 on 2009-10-30
My uncle has an HP Pavillion zv6000 that has built in wireless capability.  He also has a wireless router called a Linksys 54GS.

We can not get the computer to connet to the wireless router even though we know the name of his home network and we know the password.  However, Windows XP on the other partition of the same computer, can connect to the router.

Please help walk us through gettting his laptop to connect wireless using Ubuntu.  Perhaps there is a program/package needs to be installed.  He said in Windows he needed a program to make it work with this Linksys router.

---

### Post by phillw on 2009-10-30
> **jml1938 said:**
> My uncle has an HP Pavillion zv6000 that has built in wireless capability.  He also has a wireless router called a Linksys 54GS.

We can not get the computer to connet to the wireless router even though we know the name of his home network and we know the password.  However, Windows XP on the other partition of the same computer, can connect to the router.

Please help walk us through gettting his laptop to connect wireless using Ubuntu.  Perhaps there is a program/package needs to be installed.  He said in Windows he needed a program to make it work with this Linksys router.



Can you post the model of your wireless module ...

It seems a non too difficult job - i just need to confirm your device type & model.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw)

will tell you how to find it.

Regards,

Phill.

---

### Post by Buuntu on 2009-10-30
If you do not see any wireless networks even when you go to System > Administration > Network Connections, it's likely that Ubuntu does not have support for your wireless card.  Thankfully there is a program called ndiswrapper to let you use Windows drivers to run your wireless card.  See if you can follow the instructions in [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).  

If you have any questions just ask.  I use ndiswrapper myself to load my NIC and couldn't get internet before that either.

Also, in case there are other reasons behind your problem, could you post the output of the following command when you run it in the Terminal? (Applications > Accessories > Terminal)
```
iwconfig
```

---

### Post by MrKlean on 2009-10-30
One point... make sure the drivers you use are for the archetecture your using... 32 bit drivers won't work on 64 bit linux.. I know.. I tried LOL!!  Even tho my drivers were supposed to work on 64 bit.. they wouldn't....took a few days to find it out LOL!!!

---

