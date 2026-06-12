---
title: "Oh, what did I miss?  WEP"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by The Tronyx on 2007-12-13
I feel like I have read almost every piece WEP related info and I **still** cannot connect to a WEP protected network.

I am on a fresh install of gutsy, Toshiba Satellite (A215), Realtek RTL8187 Wi-Fi Card...that's about all I can think of.  The problem is that I can connect to open and unsecured networks but if they hey any encryption/authentication, I cannot connect.  I have tried using both Wicd and the Network-Manager and it just hangs when it tries to get an IP address. 

Thanks a lot for your help!

EDIT:  I have also checked the settings on my router and I can assure you(99.99%) that it is not a problem at the router.

And these were the drivers used [http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/](http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/)

---

### Post by foolsh on 2007-12-13
Is you router offering dhcp services or were they turned off?
I've had no troubles connecting to either unsecured, or WEP secured networks as long a I have the wep passphase or key with gusty 7.10
are you using a passphase or WEP key?

edit: so its not the router hmmm?
what kind a wireless router is it?

---

### Post by The Tronyx on 2007-12-13
I'll check on the DHCP when I get home but I am useing a passphrase.

---

### Post by The Tronyx on 2007-12-13
Ok, I just looked, DHCP is active on my router, to answer your question it is a Wuffalo Wireless G WHR-HP-G54.  I still cannot connect to any encrypted networks with the right passphrase and my router is currently using 128 bit WEP.

/sigh

Ok, so I ditched Wicd and got Wi-Fi Radar at the advice of a friend.  Below is a screenshot of what I am describing
[IMG]http://i24.photobucket.com/albums/c45/sigplace/Screenshot-4.png[/IMG]
My SSID is Abrooks
There is only one SSID in that screenshot that I can edit, which is the one with the SSID "ssid."  That is also the only one bolded.  If I try to edit the Abrooks SSID nothing happens.  I also noticed there is no indicator of signal strength.  I'm at a complete loss.  If anyone thinks of anything remotely close to assistance don't hesitate to let me know.

P.S.  I am also using the WIN98 driver with ndiswrapper -a

---

### Post by madking on 2007-12-13
I am having the exact same problem, but i have a laptop, so i cant replace the card easyily. My card is a broadcom (not on it right now, so i do not know which one [i believe it is a 43XX]) WiCD hangs on obtaining a ip. Any suggestions?

---

### Post by johnc4510 on 2007-12-14
2point0, i just bought that laptop and am going to be installing gutsy shortly. Can you point me to a way to get the Realtek RTL8187 wireless working? It looks like it's a little tricky and there are several conflicting post. Thx in advance. :)

---

