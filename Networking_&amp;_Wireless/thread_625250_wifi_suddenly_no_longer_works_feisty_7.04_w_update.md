---
title: "wifi suddenly no longer works: feisty 7.04 w/ updates"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by old_vaio on 2007-11-27
I have a vaio pcg-f560 laptop paired with a SL2511CD plus wifi card. 
Cardinfo reports this card as an "Intersil PRISM2 Reference Design," and
not only did this card work well on Redhat 7, but also Ubuntu 7.04 Feisty.

Now, I've had pretty reliable trouble with the default tool
NetworkManager, and eventually found wifi-radar to work best for me.

[B]Lately, the card cannot establish a connection with wep.  I seem to be
able to connect only with unsecured, open networks.
[/B]    
Examining wifi-radar and trying to mimic it, I find that the iwconfig
command fails.

When I insert the card, it first grabs any address from anyone's network
(though it isn't a functional connection).  The light on the card is
solid.  If I do:

~> sudo iwconfig eth0 essid aaa nick aaa key restricted 12345 mode Master channel auto
Error for wireless request "Set Mode" (8B06) :
   SET failed on device eth0 ; Operation not permitted.

and the light blinks.  If, instead, I do:
~> sudo iwconfig eth0 essid aaa nick aaa key restricted 12345

(omitting the mode and channel, both of which it will similarly complain  
about), no error will be shown although the light will again be on the   
blink.

I have observed that the card used to usually succeed when the light
remained solid, so I suspect the problem to be here.  I have no idea what
started it, though.  The last update before this happened was for three
samba packages I have yet to use for the first time, so I don't see a
relation.

Wireless-Tools version 28 is installed, compatible with wireless extension
v11-v20, and the kernel is compiled with wireless extension v21, although
it has been this way for some time.

The card itself is using the orinoco, orinoco_cs, and hermes modules.  It
also loads several hostap modules and an ieee80211 module, although I
can't verify that I use them for anything.  At no point have I needed the ndiswrapper drivers.

The card is currently operating on an older linux machine, so I know that
the card itself operates well, and it suggests that the router also is fine.

I have no idea why it just up and quit, but I can't figure it out at all.
As far as I can tell, the card is well supported and has been for some
years. If anyone can help shed some light on this I would really appreciate it.

---

### Post by old_vaio on 2007-12-05
I eventually determined the problem.  If a router is configured to use wep, and has multiple keys set, then iwconfig must be invoked specifying which key. for example:
*~> iwconfig eth0 -key [2] 123abc*
The man pages left me to infer that [2] would only be needed if iwconfig was given several keys.  **However, even if iwconfig is given only one key, this [2] index is still necessary. ** 
Apparently this matters only if you are using any key but the first one, which is why the problem developed in the first place.
By extention, when setting keys in a utility such as wifi-radar, one should mimic the iwconfig syntax ( [2] 123abc ) since that utility probably actually calls iwconfig.
Since making this change a week ago I have had no further problems, so I consider the issue resolved. :)

---

