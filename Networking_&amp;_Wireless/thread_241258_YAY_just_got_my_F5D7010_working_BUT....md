---
title: "YAY just got my F5D7010 working BUT..."
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2006-08-22
Only with encryption disabled on the router. I only see an option for wep, not WPA-PSK which i understand is the better one.

Also, whats the hex/ascii option all about.

---

### Post by lupine_nickt on 2006-08-22
hex/ascii refers to the format that it gives you the key in. For one of the formats (I forget which one), you have to proceed the key (in Linux) with "s:" (or select the appropriate option - hex/ascii - in whatever GUI program you use).

WPA is firmware dependent, so if your router says it doesn't have it, there's nothing you can do.

xF,

...Nick

---

### Post by dgrafix on 2006-08-22
WPA works fine on my router, and all my windows pcs. What im saying is theres no option in ubuntu for it, just wep.

In windows its simple, select WPA-PSK and choose a sentence. 

I tried using wep, and now ubuntu crashes horribly with a black screen full of numbers, then nothing will load.

Works fine with no protection, but im not happy to leave my wireless network open.


Something else that confusing me to bits is the main ethernet card under network settings is disabled. But when i plug in my cable, it stays 'not configured'  but i can connect to my network just fine. a little thingy in the top right spins round and i get wired network.

But its not cnnected according to network settings,

---

### Post by lupine_nickt on 2006-08-22
Have you installed and configured wpasupplicant correctly?

xF,

...Nick

---

### Post by dgrafix on 2006-08-22
i didnt install it, synaptic says its already there.

I downloaded wifiradar and when i choose wpa its asking for a driver???? shouldnt it be asking for a passphrase

I dont understand why the network settings thing in gnome doesnt seem to do anything, network manager seems to take over, but i cant seem to find any options for it.

---

### Post by dgrafix on 2006-08-22
heres what ive got and done so far. (may be helpful :) )

Followed this [http://ubuntuforums.org/showthread.php?t=187004](http://ubuntuforums.org/showthread.php?t=187004)

ndiswrapper -l shows hardware installed

card is recognised by network settings and allows config with WEP only no WPK
No lights on card. Also disabled normal lan adaptor

Turn of WPK on router
Wi fi connected for 1 reboot and then didnt work (lights flashing)

Tried to switch router to wep, inserted key in network settings. Ubuntu crashes with black screen. Then reboots the X server

Put everything back to normal and disabled wless-network card. 

Notice network manager is connected to LAN via cable, even though lan adaptor is disabled in network settings (which to me is weird)

Downloaded wifi radar, which (although wireless is disabled in network settings) tells me its connected to wireless network with ip 127.0.0.1 without the lights on(?). Its asking for a driver?? in the wPA box.

I assume the lights only come on when the router actually talks to it (like it did with no security)

---

