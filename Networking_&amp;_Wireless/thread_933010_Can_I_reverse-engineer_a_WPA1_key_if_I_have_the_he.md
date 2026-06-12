---
title: "Can I reverse-engineer a WPA1 key if I have the hex key?"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by shaggy999 on 2008-09-29
Ok, so here's what happened. We were using an unsecured wireless router at our place for a long time and things were going great. Then the cable company decided to put a bandwidth cap on our line (100 GB) and it turned out that almost everybody in the neighborhood was using our router. So we were pretty suprised when we got a $300 bill in the mail for our cable (they charge an extra $1.50/GB for each GB over the 100 limit). So the guy that owns the router switched the router over to WPA1 and set up hidden essid. The guy gave me the password and the essid and then left to go visit family for the next 3 weeks and I don't have a number to contact him.

Anyway, I typed the key in at the time and manually created the hex key from that at the command line. The system now connects to the internet perfectly but I just got a new system in today and wanted to set up the wireless.

Unfortunately it looks like I deleted the original file that had the wpa key in it! All I have is my /etc/network/interfaces file with a reference to the hex key that was produced from the key + essid.

The new machine I'm using is not a server but using ubuntu desktop and I tried copying over the /etc/network/interfaces file to it and making appropriate changes, but it doesn't seem to work. The only way I can seem to connect is by clicking on the wireless network in Network Manager and typing in the password.... but I can't remember the password!

So to make a long story short, is there a way to reverse-engineer what the original key was from the hex key?

---

### Post by tangibleorange on 2008-09-29
> **shaggy999 said:**
> Ok, so here's what happened. We were using an unsecured wireless router at our place for a long time and things were going great. Then the cable company decided to put a bandwidth cap on our line (100 GB) and it turned out that almost everybody in the neighborhood was using our router. So we were pretty suprised when we got a $300 bill in the mail for our cable (they charge an extra $1.50/GB for each GB over the 100 limit). So the guy that owns the router switched the router over to WPA1 and set up hidden essid. The guy gave me the password and the essid and then left to go visit family for the next 3 weeks and I don't have a number to contact him.

Anyway, I typed the key in at the time and manually created the hex key from that at the command line. The system now connects to the internet perfectly but I just got a new system in today and wanted to set up the wireless.

Unfortunately it looks like I deleted the original file that had the wpa key in it! All I have is my /etc/network/interfaces file with a reference to the hex key that was produced from the key + essid.

The new machine I'm using is not a server but using ubuntu desktop and I tried copying over the /etc/network/interfaces file to it and making appropriate changes, but it doesn't seem to work. The only way I can seem to connect is by clicking on the wireless network in Network Manager and typing in the password.... but I can't remember the password!

So to make a long story short, is there a way to reverse-engineer what the original key was from the hex key?

hmm. i'm gonna be be annoying here and say that i don't know how to do what you're asking, but wouldn't it be easier just to set a new WPA key on the router? you can usually plug into the router and do it from there, or if it has no wired ports, hold down the reset button for about 15 seconds to restore it to factory settings.

---

### Post by shaggy999 on 2008-09-29
From a technical point of view, yeah I could do that. But from a social point of view not really. The guy is really anal about other people touching his stuff.

---

### Post by digitalvectorz on 2008-09-29
I'm not sure about the WPA1 reverse engineering, but one thought i'd like to point out...

> 
So the guy that owns the router switched the router over to WPA1 and set up hidden essid. The guy gave me the password and the essid and then left to go visit family for the next 3 weeks and I don't have a number to contact him.


If he's truly anal about other people getting into his stuff, then he wouldn't want to hide the essid.  With a hidden essid, someone with a little bit of experience and or knowhow could pick up the essid (with kismet for example) and (if they have malicious intent) force the systems in your network to deauth(enticate) and make itself out to appear as a rogue access point, broadcasting the essid.  Windows systems seem especially vulnerable to this.

In other words, just because the essid is hidden, doesn't make it more secure.  In fact, it tends to make a network less secure.

Just food for thought.

---

### Post by techstop on 2008-09-29
I agree that a hidden SSID is as useless as t*ts on a bull (or a tootbrush made of ants?).

Anyway, this page explains how the hex key is calculated from the SSID and the passphrase;

[http://www.xs4all.nl/~rjoris/wpapsk.html](http://www.xs4all.nl/~rjoris/wpapsk.html)

It contains a link to the RFC which explains the calculation in more detail. In summary;

> For WPA-PSK encryption, the binary key is derived from the passphrase according to the following formula:

  Key = PBKDF2(passphrase, ssid, 4096, 256)

To summarize, the key derivation process involves iterating a HMAC-SHA1 function 4096 times, and then doing that again to produce more key bits.

Because the process involves an HMAC function, then it should be computationally infeasible to reverse the hash and obtain the passphrase. Sorry.

---

