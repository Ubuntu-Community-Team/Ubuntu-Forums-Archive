---
title: "Installation went smoothly, modem doesn't work"
date: 2005-09-26
forum: Networking &amp; Wireless
---

### Post by eagleseye on 2005-09-26
Unbuntu seemed to install without a hitch.  I checked Device manager and saw all hardware on this PC was listed.  The modem appears to be set to string 7, with 11,17, and 8 available.  The problem accurded when going to network settings.  When I chose modem set up, Unbuntu was not able to automaticly recoginize the modem.  If I manually chose /dev/modem, when the activated ppp0 button is pressed I get an error message " check that settings are appropriate for this network and that the computer is correctlyu connected to it."  If I chose any other manual setting, ...ttyS0 to S3 it appears to activate.  However after closing the window and going back I see that ppp0 is not active.

it seems like a driver problem to me and, if need be, I have no idea how to change to a different string, I assume these are similar to Win IRQs.  I did find a site that sells Linux drivers, I believe it is called Lunixant.  I should tell you all the modem type installed, it is a Diamond HCF 56k Data/Fax.  According to device manger it use the conexant chipset.  Back to Lunixant, they have a driver developed for this chipset.   Do you think that will solve my problem?

Also, a system search for /dev/modem found nothing.

Thanks for your help.

---

### Post by occy8 on 2005-09-26
that is a winmodem, you need the driver otherwise it can't work.

---

### Post by mlomker on 2005-09-26
> According to device manger it use the conexant chipset.  Back to Lunixant, they have a driver developed for this chipset.   Do you think that will solve my problem?


The linuxant drivers work great.  They have a free one that you can try, but it only works at 14.4.  There's a driver out there called slmodem that is free and works with some of the modems and not others.  I'd recommend reading up on [Linmodems]("http://www.linmodems.org"), otherwise if you don't mind the $15 then [Linuxant]("http://www.linuxant.com") works well...I bought one for my last laptop.

---

### Post by eagleseye on 2005-09-26
Thanks, A different driver was my first thought, I'll go with the Linuxant charge then figure out how to install.

---

