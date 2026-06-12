---
title: "Linksys wireless card works SOMETIMES"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by nitewing98 on 2006-10-11
I have a Linksys wireless card in my Ubuntu box that works off and on.  I used ndiswrapper and got the thing working well enough to get online, but it doesn't stay up and has to be "coddled."

I've turned off WEP on the network (I know, not a good idea, but it was the only way I could get the card to work).  If you know how to use the WEP and get it to work, please reply.

The card works, but goes down frequently and then I have to either do ifup or System/Administration/Networking and reselect the settings.  

Why isn't it saving the settings?  Or is something else happening?  If you know what's going on here, please post a reply.

---

### Post by wieman01 on 2006-10-11
I have a WUSB54G V4 and a WRT54G router. Same problem using "ndiswrapper", etc. The solution in my case was to change 1 single settings in the router: **[COLOR="Red"]"beacon interval"[/COLOR]**. Took us a while to figure it out, but it turned out that I had to change the router's(!) default setting (100) to 10.

Tested the system for 14 hours & it became absolutely stable. Have not had a problem since. You might try that. Otherwise join this thread: [http://www.ubuntuforums.org/showthread.php?t=271625&highlight=wireless+timeout]("http://www.ubuntuforums.org/showthread.php?t=271625&highlight=wireless+timeout")

Hope this helps.

---

### Post by nitewing98 on 2006-10-11
My Comcast router doesn't show me anywhere to change something like "beacon interval."  However, in rooting around in the router, I did notice that it let me specify the specific MAC address of my pc, so at least I have now limited access of the wireless network, something I was worried about.  I tried changing the broadcast channel, maybe I was getting interference.

Thanks for the idea, it got me to looking some more!

---

### Post by wieman01 on 2006-10-11
There are definitely more settings available. Possibly under "wireless configuration" or similar. The problem sounds strangely familiar. This definitely a problem that points to the router.

As for MAC address filtering, that's a pretty weak security setting. If you want to make your network secure, you need to enable wireless encryption & authentication. WEP is a minimum requirememt, although I usually recommend nothing less than WPA(2) with AES. 

You can also hide the broadcast of your ESSID (network name). Using static IP rather DHCP also adds to wireless security (because people would then have to "guess" your IP range). 

Let me know if you want to do more about wireless security. It's my "particular" field of interest.

---

