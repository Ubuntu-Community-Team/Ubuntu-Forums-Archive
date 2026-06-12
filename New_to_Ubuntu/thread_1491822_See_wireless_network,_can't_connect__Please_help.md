---
title: "See wireless network, can't connect???  Please help"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by family_man2 on 2010-05-24
Okay, I am brand new to Ubuntu and I am trying a dual boot on toshiba laptop.  I have the OS installed and updated.  But I can't connect to wireless.  I can SEE all the wireless systems in my neighborhood, but when I enter the key, it rejects it.  I can connect with the Toshiba using the Windows XP Wifi and the exact same key.

Am I missing something obvious?

Please help.

---

### Post by MC_Sketch on 2010-05-24
what type of wireless router are you trying to connect to? because i use a Cisco Linksys and it works fine, but my friend up the road has a Belkin that i just cant seem to connect to.

---

### Post by anewguy on 2010-05-24
I also have to ask - is it asking for the network key, or is it asking for the keyring key for the network?

Dave ;)

---

### Post by family_man2 on 2010-05-24
MCSketch - 
Its a 2wire dsl modem / wireless router.  Don't know the model off hand.
 
Anewguy - 
Its asking for the network key.  I don't know what you mean by "keyring key."

---

### Post by family_man2 on 2010-05-24
Okay some more info.  I  can connect wirelessly with Ubuntu if I remove the security on the wireless router.  But once I put on a WEP key, Ubuntu won't let me through.  Since I can get through to the internet wireless without secuity, can I assume my driver is okay?

---

### Post by louieb on 2010-05-24
Is it a 2 wire from ATT? Believe the default encryption is WPA / WPA personal - anyway yes it sounds like your talking to the wireless card - since you can see wireless networks - and connect unsecured too.  

Have one of those "2 wire modem routers" also - not a problem - after entering the pass-phrase - connects right up.  

BTW: you'll know if its asking for the key-ring password - the dialog box  will let you know - and yes it would be different from your wireless network pass-phrase.

---

### Post by anarchywolf46 on 2010-05-24
Double check if it uses WPA or WEP to make sure you are sending what it needs.

---

### Post by family_man2 on 2010-05-24
I can confirm that I am using WEP-Open.  The key is the same on the modem and Ubuntu.  

The integrated wireless card is RTL-8139/8139C/8139C+

Other thoughts?

---

### Post by BandD on 2010-05-24
can you paste the result of ```
lspci |grep -i Network
``` run in a terminal (go to Applications --> Accessories --> Terminal). To copy from the terminal, highlight the text and press ctrl+shift+c.

Thanks.

---

### Post by family_man2 on 2010-05-25
BandD,

I didn't produce a response.  See below:

mark@Laptop:~$ lspci |grep -i Network
mark@Laptop:~$

---

### Post by ima5k on 2010-05-25
better try
```
lspci | grep -i Ethernet
```

---

### Post by family_man2 on 2010-05-26
Same result, no response.

mark@Laptop:~$ lspci | grep -i Network
mark@Laptop:~$

---

### Post by bkratz on 2010-05-26
I used one of the AT&T 2wire ( model 2701 ) for my wireless at one point. I was never able to get the wep function to work and had to go to wpa2--aes only to finally make contact.  Of course it was limitations of my particular wireless card ( not the modem/AP) but that was the final solution. WEP is really not good anyway!

---

### Post by family_man2 on 2010-05-26
BKratz,

Thanks for the idea.  I tried switching over to WPA but to no avail; I still can't access the internet.  I tried to plug in the modem (2701 HG-B) address into firefox (192.168.1.254), but I can't see the modem settings.

Should I be concerned that lspci | grep -i Network doesn't return anything?

---

### Post by anewguy on 2010-05-26
I'd try doing a hard reset on the 2Wire modem/router, then hardwire to it.  I had one of those a few years ago with AT&T DSL service, and I seem to remember the default password is actually either all of or part of a string printed on the modem itself.  I could get WEP working, but never could get flavors of WPA working.

If you haven't already, I'd do that hard reset (so it's set back to the way it was delivered) and try connecting to it.  Once you are able to, add the encryption back in and do nothing more until you get that working.  I have found, at least, that it's easiest to remove all obstacles (the hard reset) and get it working on a wide-open network, then move on to encryption, MAC filtering, etc..

As far as seeing the network adapters, I would:

lshw -C network

That way we can also see the driver module being used.

Dave ;)

---

### Post by bkratz on 2010-05-27
> **family_man2 said:**
> BKratz,

Thanks for the idea.  I tried switching over to WPA but to no avail; I still can't access the internet.  I tried to plug in the modem (2701 HG-B) address into firefox (192.168.1.254), but I can't see the modem settings.

Should I be concerned that lspci | grep -i Network doesn't return anything?

The address you wanted (from the manual) is 
"
• Open a Web browser and access the 2Wire gateway user interface by entering (from a wired connection!)
  [http://gateway.2Wire.net](http://gateway.2Wire.net)
"

Yours is the same model as mine. I still have the manuals I downloaded ( 2 -3meg files) and would be happy to send them to you if you PM me. Will probably need an email address due to the size. Than command above may not return anything unless the word "Network" is actually in the description of the device. I've seen where it wasn't. If still interested try just 

```
lspci -nn
```

and look at the listing--it will be longer, but should still be there.

---

### Post by anewguy on 2010-05-27
> **bkratz said:**
> 
```
lspci -nn
```

and look at the listing--it will be longer, but should still be there.


Not necessarily true - some laptops use an internal USB connection for the built-in wireless.  I noticed the user mentioned a Toshiba laptop - hence why I recommended lshw -C network, as it will list the hardware with network in the name, not just pci devices.  In order to get the best picture if you want to use lspci, you must also include lsusb on laptops just in case.  This Toshiba laptop may be one such case.

Dave :

---

### Post by BandD on 2010-05-27
+1 for Dave's suggestion.  This is a much better way to go and I stand corrected.  I will certainly remember lshw in the future for this type of troubleshooting!  Thanks Dave.

---

### Post by anewguy on 2010-05-28
> **BandD said:**
> +1 for Dave's suggestion.  This is a much better way to go and I stand corrected.  I will certainly remember lshw in the future for this type of troubleshooting!  Thanks Dave.

Not a problem - I learned this myself when trying to help someone with wireless on their notebook last year.  Couldn't see it with lspci, asked if it was PCMCIA or external USB and they said no, so I had them do a lsusb anyway.  That's when I found out - not something I would have expected but it turns out that several notebooks end up being that way.

Dave ;)

---

