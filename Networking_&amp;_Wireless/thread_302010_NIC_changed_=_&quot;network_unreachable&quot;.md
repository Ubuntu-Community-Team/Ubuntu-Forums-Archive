---
title: "NIC changed = &quot;network unreachable&quot;"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by und3rtug4 on 2006-11-18
Hi there!

I got an machine as mail server, and i had to change it's NIC.

Know, everything is ok, but i got no network connection...

I think that the problem is that he is configured for the previous NIC and them, not recognizing this one...

... so, how can i fix this whithout having to re-installing it all again and loose all the data...

thanks in advance...

regards!

---

### Post by und3rtug4 on 2006-11-19
the problem continues...](*,) 
... i had "try it all" and i still get the network unreachable...:( 

The nic was changed..

All the settings for the eth0 are made correctly but when i try to ifconfig it, it only display the lo interface!

I have list my pci devices and i get a Datacube Inc network card! I dont know if modprobing the right module will fix the problem and i dont even know what module to modprobe...

It will be a really headaque to install all from scratch just to get the new NIC detected...

... so, if anyone knows somehow, how to fix this pain in the *** problem, i will be very thankful.

Thanks in advance...

Kind regards!

---

### Post by trubblemaker on 2006-11-19
yeah I'm going to say that you need to modprobe the right driver.  try this:

```
 lspci | grep ontroller 
``` to get the actual hardware that your using. then do a google on the name of the driver and ubuntu should come up with a driver. Also take a look through 
```
 dmesg 
``` to see if there's anything worth mentioning.

(in future to make life easy put '/home' on a serperate partion, makes re-install a non-issue.  All/Most settings stay, and personal data is still there.

---

### Post by und3rtug4 on 2006-11-19
> **trubblemaker said:**
> yeah I'm going to say that you need to modprobe the right driver.  try this:

```
 lspci | grep ontroller 
``` to get the actual hardware that your using. then do a google on the name of the driver and ubuntu should come up with a driver. Also take a look through 
```
 dmesg 
``` to see if there's anything worth mentioning.

(in future to make life easy put '/home' on a serperate partion, makes re-install a non-issue.  All/Most settings stay, and personal data is still there.

Yeahh, that what i thought!
Thanks a lot **trubblemaker**, it worked just fine! Found the card, crawled the google for the mod name and after modprobing and restart the network it's working again!

Also, thanks for the advise to intall the /home dir on other partition!
It will help for future installations!

Kind regards!

---

