---
title: "Wpc11 wireless"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by Heresy on 2007-10-20
I am really in need of help here
I have a WPC 11 ver 3 on Fiesty 

it works in wep IF i use hexidecimal. 
it doesnt allow WPA. or Wep ascii. 

I have tried NDISwrapper...   it always says wrong driver
I did some stuff from the forum..  nothing ever helps so far.  
Went to these links over the past week in the forum  

linksys wpc11 wireless setup, Linksys Wireless-B WPC11 v4, and the wireless how to...  

Any help would be appreciated...

---

### Post by sbennettgso on 2007-10-21
Has anyone gotten this card (v3 or v4) to work under Gutsy?

It worked out-of-the-box for me under Dapper and Edgy.  It worked almost out-of-the-box for Feisty (I had to remove Network Manager to get it to work).

I've tried all these tricks under Gutsy, with/without Network Manager, with/without native drivers, ndiswrapper, secured/unsecured.

When attempting to connect to a secured network, it hangs up and I have to power down.  When attempting to connect to an unsecured network, it simply never connects.  It appears to associate with the AP, but it never seems to connect to the rest of the network (when using DHCP it never is able to lease an IP address, when using static IP I can't ping anything else on the network).

I have read of several issues similar to these with this card.  This might be to the point where it needs to be elevated as a bug.

Thanks,
Scott

---

### Post by bluebaby on 2008-03-06
> **Heresy said:**
> I am really in need of help here
I have a WPC 11 ver 3 on Fiesty 

it works in wep IF i use hexidecimal. 
it doesnt allow WPA. or Wep ascii. 

I have tried NDISwrapper...   it always says wrong driver
I did some stuff from the forum..  nothing ever helps so far.  
Went to these links over the past week in the forum  

linksys wpc11 wireless setup, Linksys Wireless-B WPC11 v4, and the wireless how to...  

Any help would be appreciated...


hi. i'm having the same problem. when i try to connect to the wpa network im being prompted for a wep passphrase instead. were you able to get wpc11 to work with wpa?

---

### Post by Sam Lars on 2008-03-23
Try the guide [here]("http://ubuntuforums.org/showthread.php?t=202834").

---

