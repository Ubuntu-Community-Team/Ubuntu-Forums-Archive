---
title: "unable to connect to secured network"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by beew on 2010-10-13
I have an old hand me down Dell Inspiron 8500. It was running slow and froze frequently under Xp so I installed Ubuntu 10.04 on it instead. The performance is better except that wireless is not working (It worked in XP so the card is good)

The laptop uses the broadcom 4306 (rev2) Wifi card. I installed the b43legacy driver from System > Hardware Drivers. I checked wireless Linux and other sources to confirm that this is indeed the right driver for the card. However, I just couldn't connect to my wireless AP (which uses WEP encryption, it is an old router in a shared house).After supplying the password it will struggle for a long time to connect and then simply dies.

Then I discovered something interesting today. I took the computer to a coffee shop which features open wifi access (no encryption, no password). I opened nm, clicked the network and connected right the way.

It seems that the problem is with encryption. I wonder if that is a problem with the old b43legacy drivers and if there is a fix (would ndiswrapper be better in that regard?)

Thanks.

P.S. I have two other Ubuntu machines (actually one Ubuntu and one dual boot). They had different cards (an usb card and an athero). Both connect to my home wifi network with no problem(connection is immediate on start up). so I don't think it is a problem with Ubuntu or the network manager,it is most likely a driver problem.

---

### Post by Ctrl-Alt-F1 on 2010-10-13
Are you the one that controls the router?  Someone could be doing some weird stuff like mac filtering the network.

---

### Post by beew on 2010-10-13
> **Ctrl-Alt-F1 said:**
> Are you the one that controls the router?  Someone could be doing some weird stuff like mac filtering the network.

Yes, I am the only one who knows the password (actually it was there before the current landlord bought the house from the former owner so even he doesn't know. I was able to crack it :))

It cannot be the router because all my other machines (Ubuntu and windows) as well as my roommates machines all work.

---

### Post by AggravatedGestalt on 2010-10-13
This may seem entirely ridiculous, but I have had similar problems connecting to my WEP access point. I installed wicd and wifi-radar so as to avoid Network Manager. I do not understand why, but for months, wicd will not connect unless I use wifi-radar simultaneously. I have thought it may have something to do with the fact that wifi-radar requires root permissions. However, I do not know. This is obviously a grotesque solution at best, but it has worked for me.

---

### Post by Zero++ on 2010-10-13
I believe Ctrl+Alt+f1 wanted you to make sure that mac filtering was turned off. If your router is filtering mac addresses it would accept you current computers but stop new ones from joining the network unless the mac address is added to the "guest list"

---

### Post by PaulReaver on 2010-10-13
broadcom's are patchy at best... 

but they've open sourced they wifi drivers for never cards so it won't be long before the drivers filter though to ubuntu.

---

### Post by beew on 2010-10-13
> **Zero++ said:**
> I believe Ctrl+Alt+f1 wanted you to make sure that mac filtering was turned off. If your router is filtering mac addresses it would accept you current computers but stop new ones from joining the network unless the mac address is added to the "guest list"

It is off, has always been off.

---

### Post by anewguy on 2010-10-13
> **beew said:**
> Yes, I am the only one who knows the password (actually it was there before the current landlord bought the house from the former owner so even he doesn't know. I was able to crack it :))

It cannot be the router because all my other machines (Ubuntu and windows) as well as my roommates machines all work.

As already mentioned, you need to check the router for MAC filtering.  Also - WEP is about worthless and can be cracked in seconds.

As far as Broadcom goes, the adapter can be made to work with no problem in ubuntu, so ignore other remarks.  However, if you are able to SEE networks to try to connect to it would indicate that the driver is probably working.

Dave ;)

---

### Post by beew on 2010-10-13
> **anewguy said:**
> As already mentioned, you need to check the router for MAC filtering.  Also - WEP is about worthless and can be cracked in seconds.

As far as Broadcom goes, the adapter can be made to work with no problem in ubuntu, so ignore other remarks.  However, if you are able to SEE networks to try to connect to it would indicate that the driver is probably working.

Dave ;)

Yeah, I can see the network, it just wouldn't connect. But it connected immediately to an open network.

I know WEP is easy to crack, but this is not my router, I won't change its setting unless I have to.

P.S. As said above Mac filter has always been off.

---

### Post by AggravatedGestalt on 2010-10-13
Consider trying what I posted above. I too only have issue with encrypted access points. Crackability is irrelevant here. And by any chance, is it a Verizon router?

---

### Post by beew on 2010-10-13
> **AggravatedGestalt said:**
> Consider trying what I posted above. I too only have issue with encrypted access points. Crackability is irrelevant here. And by any chance, is it a Verizon router?

Sorry, I missed your earlier post.

No, I am using a Dlink router. 

I have played with WICD with my other Ubuntu installations before. In those installations nm is definitely a lot better. WICD connected on startup, but after about 15 minutes or so it would drop the connection and it would take forever for it to reconnect if at all, but if I rebooted it would connect immediately, then after about 15 minutes it would drop the connection again and in order to get reconnect I will need to reboot again. NM however work perfectly.

P.S. Do you also have a broadcom card? If yes, which one? I have actually installed Ubuntu on one of my former house mate's machine which has a newer broadcom card (4311?) and there was no problem.

---

### Post by AggravatedGestalt on 2010-10-13
> **beew said:**
> P.S. Do you also have a broadcom card? If yes, which one? I have actually installed Ubuntu on one of my former house mate's machine which has a newer broadcom card (4311?) and there was no problem.

No I don't. My problems have been with a realtk 8172 (I think;, not using that chip right now though.) I have certainly had problems with Broadcoms in the past. I responded to your post because the issue with WEP connections has been afflicting me for months now, and I have received not a single reply on my posting. Anyway, good luck.

---

### Post by Homicide on 2010-10-13
This Inspiron 1501 was pretty crappy about getting its Broadcom chipset working. The router is literally 2' from it, so after installing via wubi I just hooked up my trusted ethernet cord and ran System -> Hardware drivers and now it works rather fine. I'm glad, because I just read all 7 of my other posts and most of them were me fighting with my old 1800 and Dapper.

---

### Post by Zero++ on 2010-10-13
Do you have an external USB wi-fi card you could try to install? That would tell you if it is a driver issue. I would also disable the WEP and try to connect. Enable it after you are done testing. This will also tell you if it is a problem with connecting to an encrypted network or just this hardware.

---

### Post by anewguy on 2010-10-13
Crackability is not irrelevant here - we're talking about supposed encryption problems.  Maybe you missed it - the OP said in their 2nd post that THEY had cracked the network because it was all there before they got there.  We have learned the router is not the OP's, so changing encryption will be a last resort.

I have had problems myself in the past with Broadcom wireless and a 2Wire DSL modem for AT&T DSL many years ago, so I'm not downplaying the potential role it may have in the equation, particularly since the adapter itself is working.  That's why I asked the obvious first - MAC filtering.  I normally start at the obvious and work my way into the more obscure.  Some people don't like that, but it tends to give the normal reader of this forum some basic troubleshooting ideas before just automatically thinking it's some more obscure.  In this case, after knowing MAC filtering is off, and with the OP convinced he has cracked the encryption key correctly, it lends itself to a little more investigation on more obscure terms.  For instance, the OP says MAC filtering is not on, so I must believe them - but I could have asked "have you connected to the same router with the same computer before?" to try to isolate that, but haven't.  The OP mentioned it is not their router and that others connect to it, so while it may be a problem with the router, the solution may still involve CHANGING encryption.  My comments on crackability do apply.

Myself and many thousands of others have also had Broadcom wireless working with countless routers, but as I mentioned I had problems with a Broadcom 4318, 2Wire DSL modem/wireless router and WEP.  I had to leave my network wide open.

So, I'm not arguing with you - why argue with me about something that can deal directly with the problem?

---

### Post by beew on 2010-10-14
> **Zero++ said:**
> Do you have an external USB wi-fi card you could try to install? That would tell you if it is a driver issue. I would also disable the WEP and try to connect. Enable it after you are done testing. This will also tell you if it is a problem with connecting to an encrypted network or just this hardware.


Yes indeed, the usb card connects with no problem so I think it is a driver issue. Cannot disconnect WEP because it is a shared router, I will change the settings if everyone experiences problems but I try not to change anything just for myself. But the point is moot now because it is just a conincidence that the router died on us just two days ago. :)

I have been going to the coffee shop to get internet access for the last couple of days. I brought this laptop  just to see if the connection the first time was a fluke(it is not really a "laptop" because it is huge, normally I wouldn't carry it around). Well it connects every time flawlessly and I think the fact that the AP has no encryption is crucial. (I am now typig this from the coffee shop, the connection is fast!)

I have had Ubuntu running on machines with newer broadcom cards(>=4311) with no wifi problem. I am just wondering if this is a known issue for the legacy drivers and whether there is a work around.

---

### Post by beew on 2010-10-14
> **anewguy said:**
> Crackability is not irrelevant here - we're talking about supposed encryption problems.  Maybe you missed it - the OP said in their 2nd post that THEY had cracked the network because it was all there before they got there.  We have learned the router is not the OP's, so changing encryption will be a last resort.

I have had problems myself in the past with Broadcom wireless and a 2Wire DSL modem for AT&T DSL many years ago, so I'm not downplaying the potential role it may have in the equation, particularly since the adapter itself is working.  That's why I asked the obvious first - MAC filtering.  I normally start at the obvious and work my way into the more obscure.  Some people don't like that, but it tends to give the normal reader of this forum some basic troubleshooting ideas before just automatically thinking it's some more obscure.  In this case, after knowing MAC filtering is off, and with the OP convinced he has cracked the encryption key correctly, it lends itself to a little more investigation on more obscure terms.  For instance, the OP says MAC filtering is not on, so I must believe them - but I could have asked "have you connected to the same router with the same computer before?" to try to isolate that, but haven't.  The OP mentioned it is not their router and that others connect to it, so while it may be a problem with the router, the solution may still involve CHANGING encryption.  My comments on crackability do apply.

Myself and many thousands of others have also had Broadcom wireless working with countless routers, but as I mentioned I had problems with a Broadcom 4318, 2Wire DSL modem/wireless router and WEP.  I had to leave my network wide open.

So, I'm not arguing with you - why argue with me about something that can deal directly with the problem?

Actually I have cracked the password to trouble shoot the router. Everyone knows the password to connect. Sorry for not being clear.

Yes, I have connected to the internet with this machine and through this router before. It is a 2003 hand me down computer came with Windows NT. It was very slow and overheating so I installed XP instead, that was before I started with Ubuntu. It was able to connect under XP.

---

### Post by beew on 2010-10-14
Thanks for everyone who shared his/her insights. As I said it is just a coincidence that the router just dies (even plugging a cable in it doesn't connect, try all computers in the house all of them except mine run windows or mac) I will try to restore it to factory condition to see if it works, if not we are getting a new router in a few days and I will try to connect again (probably with WPA encryption) and will report the outcome here.

---

### Post by anewguy on 2010-10-14
The router going bad (or at least losing part if not all of its' configuration) could explain your problems.  I agree with you getting a new router and using WPA or WPA2.  MAC filtering is an iffy, because under normal circumstances it does help, but all it takes is a packet sniffer and then the MAC can be spoofed to one allowed by the router.

One thing I would suggest when you get your new router:

- try things one at a time - like try WEP and if it works then move up to WPA.  You should be able to connect to WEP with no problem as long as you know the password.  Once that works, you should feel comfortable in knowing that WPA *should* work.  Many releases ago you had to worry about installing wpasupplicant, but that is done now.  Sometimes you have to mess with the config on the Linux side to hard code in some of the WPA things, but I have never had that problem as long as I used network manager.  I know others prefer wicd, but I can't comment on that as I simply have never tried it.

Dave ;)

---

### Post by beew on 2010-10-14
> **anewguy said:**
> The router going bad (or at least losing part if not all of its' configuration) could explain your problems. 

I think the router is only going bad recently but I have not been able to connect with this laptop for several weeks while all the other computers had no problem so I think the router problem may just be a coincidence. But anyway, I will find out in a few days when we get a new router. Thanks for your tips and I will keep them in mind.

P.S. In case you are wondering, I am accessing the internet now by plugging a cable into the modem. We will be rationing internet access like this for the next few days. :)

---

### Post by anewguy on 2010-10-14
Well, since everyone seems intent on trying to shoot down every answer I give in this  thread, to hell with it.

lotsa luck

---

