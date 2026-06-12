---
title: "Wireless on FS Amilo M7400"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by bosco6 on 2007-01-25
Hi,

I am running dapper on a FS Amilo M7400 (centrino CPU), but the wireless does not work.

Does anyone know how to fix this problem? I've looked on these fourms, but to no avail.

I'm a ubuntu virgin, so please be gentle!

---

### Post by Metaljaz on 2007-01-25
tell us about your wireless.
What brand card are you using or is it built in? What happens when you try to get on-line?

---

### Post by bosco6 on 2007-01-26
It's a centrino, so inbuilt.

Wifi radar and wireless assistant will not see the Wireless connection. Networking tells me that the card is active.

Also, I've tried using the fsam7400 module, but nothing will happen when trying to "make".

---

### Post by Metaljaz on 2007-01-26
is your router or access point using WPA or WEP? If not  
try:
System>Administration>Networking

click on the wireless connection that is active and select properties.
set connection settings to DHCP.

post the results of this command:
lshw
scroll down to *network and cut and paste the product and vendor.
The product should be the name of your card and the vendor
should be the chipset.

You may have to get the drivers for your chipset and install them using 
ndiswrapper.

---

### Post by bosco6 on 2007-01-26
Using WEP on a DHCP router (Linksys wrt54g running ddwrt)


                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation


Surely Dapper (I'm running Edgy now) would have the drivers for such a popular chipset inbuilt.

---

### Post by Metaljaz on 2007-01-26
ok sounds like this could be an issue with WEP. I can't help much with that but
have you tried disabling WEP and then seeing if you can get connected. If you
then get connected you have located the issue.
From some of the reads it sounds like your drivers should have been installed
when you installed the OS. 
Helpful links below.

[http://www.ubuntuforums.org/showthread.php?t=328803&highlight=wireless+2200bg](http://www.ubuntuforums.org/showthread.php?t=328803&highlight=wireless+2200bg)
[http://tuxmobil.org/centrino.html](http://tuxmobil.org/centrino.html)

---

### Post by bosco6 on 2007-01-27
No luck with turning off WEP on both my router and laptop.

Is there a program out there that will act like the Windows Wireless window, as in it will tell me what connections are in range? Because I think that the card is not even working properly.

I have it turned on in the BIOS, but having it on or off doesn't seem to matter, same results (nothing) each time.

---

### Post by philc on 2007-01-31
I used the following tutorial to get wireless working on my Amilo (different model to yours though):

[http://ubuntuforums.org/showthread.php?t=332857&highlight=AMilo](http://ubuntuforums.org/showthread.php?t=332857&highlight=AMilo)

The tutorial didn't work perfectly for me, but with a bit of creative thinking I got things to go. Essentially the problem I had was that the drivers associated with my wireless device were incorrect - and these were the drivers Edgy installed/detected by default. Removing these drivers and using ndiswrapper for the windows driver pretty much fixed the problem.

Read the above tutorial and see how you go.

I haven't got my connection working with WPA1 yet, only over a clear connection. Fixing that is a job for this weekend.........

---

### Post by timohnani on 2007-08-02
Hi,

Try the instructions at:

[http://ubuntuforums.org/showthread.php?t=189540&page=7](http://ubuntuforums.org/showthread.php?t=189540&page=7)

Read post #61. 


Timo

---

### Post by batchy on 2008-07-11
I also have an Amilo M7400. I am running windows XP and have a Intel(R) PRO/Wireless 2200BG Network Card and none of the solutions seem to work( i think cause im on Windows)

My wireless was working till i had to restore my computer and it lost the WButton.exe file that used to activate the wireless switch.

Is there any fixes that work for windows that are not too technical. I will really apreciate any help you can give.

Batchy

---

