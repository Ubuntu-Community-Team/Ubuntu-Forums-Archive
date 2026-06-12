---
title: "Hidden SSID"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by WhyWontThisWork on 2008-01-12
Hi, I'm having problems connecting to my wireless network ONLY when the SSID is hidden... I have looked through other posts with no luck, I have all the updates and can't understand why this is happening.  im using ubuntu 7.10 (forget the release name), and the wireless card MSI PC60G 32bit PCI2.2 Turbo G Wireless Adapter, which was recognised right out of the box... maybe I can use NDISWarpper and have better luck (its what I did on my other box)

cheers
-J

---

### Post by HermanAB on 2008-01-12
So don't hide the SSID.  The only thing hiding the SSID does, is making it difficult for you, it does nothing to the 'bad guys'.

Cheers,

Herman

---

### Post by WhyWontThisWork on 2008-01-13
I know that, but it keeps the neighbors out (had a problem with that), but I'm giving up on keeping it hidden and im moving to security, trying to use WPA and none of my linux clients can connect... so i've got something to work on now, does anybody have any ideas? i looked at a few articles and my /etc/netwroking/interfaces file looks about the same as all the ones that I've found that it should look like

any help is good

cheers,
-J

---

### Post by stchman on 2008-03-03
> **WhyWontThisWork said:**
> I know that, but it keeps the neighbors out (had a problem with that), but I'm giving up on keeping it hidden and im moving to security, trying to use WPA and none of my linux clients can connect... so i've got something to work on now, does anybody have any ideas? i looked at a few articles and my /etc/netwroking/interfaces file looks about the same as all the ones that I've found that it should look like

any help is good

cheers,
-J

Then encrypt your wireless.  Wth zero encryption and simply a hidden SSID you are a PRIME target for people looking to exploit your WAP.

---

### Post by netztier on 2008-03-03
> **WhyWontThisWork said:**
> I know that, but it keeps the neighbors out 

It doesn't. All they need is to eavesdrop passively until your wireless computer attempts a rejoin to the (hidden) SSID WLAN, and they have it in cleartext and can just walk in. Turn on broadcasting again and set up some decent encryption. WPA with pre-shared keys (WPA-PSK or "WPA-Personal") is *not* difficult to do on Linux with network-manager.

As a plus, it's difficult to configure non-overlapping (and thus non-interfering) WiFi channels in a neighborhood if you don't know which channels your neighbors are on (because they're hiding their SSIDs). So finding a reason why your WLAN just doesn't seem to fly becomes ad daunting task involving sniffing tools and spectrum analysers.

SSID broadcasting is goooooood ;-)

regards

Marc

---

### Post by grndslm on 2008-06-05
Soo, uh.... yea!  I'd still like an answer as to how I could automatically connect to a hidden SSID with network-manager.

I know hiding the SSID is not going to work against the bad guys, but it works for everybody I've been around, in college & my hometown from multiple routers.  I'd gladly let someone use my computer if they can find the SSID (but people in Mississippi are a little slow to things like this), because I know they couldn't hack all the Linux computers found behind my OpenWRT router(s).  And even if they were quick to finding the SSID, they could just as easily find the WEP/WPA password.  Hiding the SSID is good enough for me, and network-manager should automatically connect to it when it's in range.  Why wouldn't it?

Is there really no remedy for this??

---

### Post by Novega on 2008-06-05
I don't know what to tell ya, Our home wireless is a hidden SSID because we live in a townhouse complex.

My computer automatically connects to our network, I didn't do anything special? It just does it on it's own.

---

### Post by grndslm on 2008-06-05
Really?!?  Everytime I restart, I have to re-enter my hidden SSID into nm-applet... regardless of whether I'm using Gutsy or Hardy.

It's very sad that simple things like this can't be resolved after multiple releases.

---

### Post by lisati on 2008-06-05
Is using some kind of MAC restriction an option?

(rant deleted before posting)

---

### Post by grndslm on 2008-06-06
Correction... I guess Hardy's nm-applet does work a bit better than Gutsy's in terms of hidden SSIDs.  However, it takes 2 minutes after everything else is loaded before the power manager & network manager are even loaded.

I have had nothing but problems with Hardy & have found no benefits from its extra features.  On one laptop, I had to revert back to Gutsy because of *numerous* issues that popped up in Hardy.  The other laptop has Hardy, but it runs like crap.  Hardy only seems to be working for me on desktops... not laptops.

I can't wait for the 8.04.1 release!!!

---

### Post by cariboo on 2008-06-06
I've got hardy on an HP laptop and WPA setup was a snap, it may depend on who your wireless router is manufactured by I've use both an SMC barricade (forgot the model number and its out in my shop) and in the house I've got a Linksys wrt54g took less time to set it up that it did to navigate through the menu's. In my case I set it up 64 bit security ( no sense in using anything more as wap is inherently insecure if you know what you're doing), but in my neighborhood the first wireless router other than my two didn't show until January of this year.

Jim

---

### Post by grndslm on 2008-06-06
Like I said... Hardy isn't as functional for me as Gutsy, so I'm not upgrading just yet.  And on Gutsy, there's no way to solve this problem.

So, I'll just keep on typing my routers name in... and wait for a newer, more functional release.

---

