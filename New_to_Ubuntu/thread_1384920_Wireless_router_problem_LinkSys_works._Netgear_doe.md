---
title: "Wireless router problem: LinkSys works. Netgear does not."
date: 2010-01-19
forum: New to Ubuntu
---

### Post by fociwm on 2010-01-19
I installed Ubuntu Server latest version. And I want to connect to router. I'm using "WPA personal" with "TKIP".

Symptoms:
1. I can connect to LinkSys router and pinging to the router is OK. WPA works fine. Good.
2. I tried to connect to NetGear WGR614. It gets IP address from the router using dhcp, but that's it. Pinging does not work. Internet doesn't work. Nothing. ifconfig shows the wireless lan is set but in reality there is no connection. I checked "attached device" of the router from Windows PC, and it does not show Ubuntu machine.

Additional information:
1. I'm using NetGear WG511U PCMCIA card.
2. If I use this card with Windows XP or Windows 7, no problem at all.

Thank you.

---

### Post by PenguinInside on 2010-01-19
Is the Netgear working otherwise? I mean from an Ethernet wire?

If so, you can narrow your problem to the wireless aspect.

I can confirm that the Netgear WGR614 does work with Linux for a wired connection (and also for wireless with an Asus netbook).

---

### Post by lisati on 2010-01-19
I have a Netgear 614v7 which I sometimes use
Sometimes if it doesn't want to connect to internet, I find that logging into its configuration page and running its setup wizard helps.

---

### Post by PenguinInside on 2010-01-19
Oh, by the way, the WGR614 is sometimes flakey. I have to turn it off and on every two weeks or so.

Why don't you try that and report back?

---

### Post by fociwm on 2010-01-19
Thanks guys.

But those solutions did not work. As I mentioned everything is fine except the wireless connection between Ubuntu Server and Netgear. Connection between Windows machines and the Netgear, and the internet connection are all fine. This is very weird. Ubuntu even get IP address from Netgear, but didn't succeed in pinging to the router. (Whereas, of course, Linksys works great.)

I've been spending a couple of days already. Isn't there anybody who experienced the same symptoms?

BTW, the version of the router is v8.

---

### Post by lyall on 2010-01-20
Having two routers is not the best way to go. 
Use one router and hub or switch

the router is your gateway to the internet thru the cable/dsl modem.

a hub or switch are the branches for the intranet (home network)

see the following link for info about Networking
[http://ubuntuguide.org/wiki/Ubuntu:Karmic]("http://ubuntuguide.org/wiki/Ubuntu:Karmic")

it might help you with your networking

good luck and have fun learning

---

### Post by fociwm on 2010-01-20
> **lyall said:**
> Having two routers is not the best way to go. 
Use one router and hub or switch

the router is your gateway to the internet thru the cable/dsl modem.

a hub or switch are the branches for the intranet (home network)

see the following link for info about Networking
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

it might help you with your networking

good luck and have fun learning


Thank you for your reply. I know about those things very well. I'm not going to use two routers.

Unfortunately, I have to use Netgear instead of Linksys because Linksys router is not mine. I borrowed it for test (because Netgear didn't work with my Ubuntu server) and I have to give it back to its owner.

I plan to test the system with other UNIX based distribution like BSD, assuming that any LINUX system might have the same problem...

FYI, I tested the router with Macbook of my friend and there was no problem. So, it is pretty obvious to me that it is Ubuntu Server problem. I even tested with Ubuntu Desktop but it didn't work.

Honestly, I really want to use Ubuntu Server, because of its support and user base and it is cool~. But it is apparently not the answer for me. I hope other Linux distribution work fine but they use the same network driver, so I doubt.

Anyway, I still don't understand why Ubuntu server and my Netgear do not work together. Very weird...:(

---

### Post by walt.smith1960 on 2010-01-21
but I wonder if the Netgear is having issues with WPA? Perhaps try connecting briefly with no encryption?

---

### Post by lemsx1 on 2010-08-03
Funny thing is I'm getting the exact same problem and I do networks for a living.

I have 2 wireless routers setup with wpa and in different channels. all my other computers and devices work fine with both. my linux (lucid) system works with linksys (WRT160NL) but not with netgear (WGR614v6).

Of course Ubuntu must work fine with the *L Linsys router as this is running Linux! I'm not sure about Netgear's router OS... this is puzzling and frustrating.

The only hint is:

Aug  2 20:56:12 minios NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed

searching for that yields a lot of bugs and no solution.

---

