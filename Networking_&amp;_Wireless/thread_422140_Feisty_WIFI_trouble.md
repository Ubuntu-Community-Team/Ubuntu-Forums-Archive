---
title: "Feisty WIFI trouble"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by mog27 on 2007-04-24
Hi.  I have a Netgear WAG511 PCMCIA card that connected just fine w/ Edgy Eft.  This uses the ath driver.  I simply, no matter what I do, can't get it to connect to my Linksys WRT54G using the DD-WRT firmware.  I have tried WPA2 and WPA using TKIP, AES, combinations of them, etc.  I am using a very secure password from grc.com/password.htm and cutting and pasting it into my Ubuntu and Router.  I have tried this both on the Live CD and the installed version.  I am at a complete loss.  This worked fine in Edgy; is there some issue with this in Feisty??

---

### Post by sdide on 2007-04-25
Can you connect with no encryption? 
What are you using to connect to the AP? (NetworkManager, wpa_supplicant, etc ...)

---

### Post by mog27 on 2007-04-25
I am using Network Manager.  I haven't tried yet connecting with no encryption.  I'll try that soon.

---

### Post by Scipio_Publius on 2007-04-25
I appear to be having the same problem with the same access point with Feisty (in Dapper and Edgy is it worked fine).  I have Feisty installed on an IBM thinkpad t42 and i have tried both WPA and unencrypted modes and I still cannot connect to the access point.


Oddly enough however at work I can connect to a cisco aironet unencrypted no problem but I cannot connect to the WPA encrypeted network.  The aironet syslog is telling me its because I have no KEY Management.

---

### Post by mog27 on 2007-04-25
Any fix for this besides getting another pcmcia network card?  (which I don't mind doing)

---

### Post by nab on 2007-04-25
Hi all,
I'm having the same trouble. Under edgy wlan worked without problems.

After installing and setting everything up everything worked fine with Network-Manager.

After reboot the WIFI-Adapter isn't showing any WIFI-Networks, but if I search them with "iwlist scan" I find them.

Switching to unencrypeted isn't an option I can go.

Well I better think of going back to edgy ;-)

Nikolaus

---

### Post by mog27 on 2007-04-25
> **nab said:**
> Hi all,
I'm having the same trouble. Under edgy wlan worked without problems.

After installing and setting everything up everything worked fine with Network-Manager.

After reboot the WIFI-Adapter isn't showing any WIFI-Networks, but if I search them with "iwlist scan" I find them.

Switching to unencrypeted isn't an option I can go.

Well I better think of going back to edgy ;-)

Nikolaus

Or get a new card (like a Linksys) and sell your Netgear like I will do. :)

---

### Post by H.E. Pennypacker on 2007-04-26
Apparently Feisty has a serious problem with either WPA/WPA2 wireless networks.  We are not the only ones.  It appears that some have been lucky, and are able to connect to similarly secured networks.  One guy was connected to a WPA2 network using only AES.

I have a BCM4318 card witha WPA2-AES network (worked for that guy, not me - we have the same cards too).

---

### Post by sheine on 2007-04-26
Just read the threads. Wifi just does not work as well in feisty as edgy.

---

### Post by nab on 2007-05-10
well,

I solved the problem with my wlan.

I followed [HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc.]("http://ubuntuforums.org/showthread.php?t=202834")

On the first start everything worked fine. On second start everything broke down.
It seems that the manual configuration in /etc/network/interfaces and nm-applet broke my system, because after removing all edits from /etc/network/interfaces my wlan works fine again.

So I think - at least on my system - the problem wasn't feisty but with the user  :mrgreen: 
Niko

---

