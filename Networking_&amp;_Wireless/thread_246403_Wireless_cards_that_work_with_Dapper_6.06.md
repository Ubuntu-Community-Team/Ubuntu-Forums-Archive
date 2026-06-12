---
title: "Wireless cards that work with Dapper 6.06"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by alanmzifa on 2006-08-29
I'm new to Linux and Ubuntu. Just downloaded the first live cd and installed a couple of weeks ago.

What I find really frustrating however is the appalling wireless support. I know many manufacturers aren't playing ball but as wireless is so essential now this is an issue that *has* to be sorted for Linux development and uptake to avoid sliding into obscurity. Wireless is the way forward, it's the only road forward.

I've spent 20 to 30 hours reading threads, trying this, trying that, checking this list and that list, uninstalling a utility, installing another etc. I've eventually got to the point where my card now connects wirelessly, although without security and cetainly not ideal, but along the way I've found thread after thread from others that petered out unsolved or unanswered despite bumps while others involve the most impenetrable workarounds. I'm sure I'm not the only desperate/frustrated would-be Ubuntu user out there.

I know there's a list (which seems incomplete and out of date) of devices said to work but the 6.06 release probably makes this list now defunct anyway.

***Would it be an idea to update USB/PCMCIA devices via a thread or a more detailed page explaining where users report what [B]currently** works, links to the driver used and any special set-up required re drivers/network utilities/blacklists.?*[/B]

Perhaps something like this below. That way an individual's device can be *searched for easliy* and a concise set-up that works found instantly.


*Device:* [Netgear WG121 USB WLAN adapter]("http://kbserver.netgear.com/products/wg121.asp") 802.11g (man.2003)
*Use driver built into Linux:*  No, see below
*Ndiswrapper used:* Yes
*Driver used:*  WG121.inf taken from NDIS folder downloaded [from here]("http://kbserver.netgear.com/release_notes/d102275.htm")
*Linux drivers to be blacklisted:* islsm
*Software used:* Ndiswrapper, Wifi-radar
*Fully working:* no, no WEP or WPA
*Anything else:* using Network Manager seemed to block connection. Had to uninstall it and re-boot to get card working in Wifi-radar.



Your thoughts please?

---

### Post by oxalá on 2006-09-02
I'm all for it.
Unfortunately, I'm still trying to figure out madwifi -- that's how hopeless i am at this moment.

---

### Post by alanmzifa on 2006-09-13
works + set-up

**Device** ***Asus WL107G PCMCIA*** wireless card
**Software** Ubuntu 6.06 standard unmodified 2.6.15-26-386 kernel
**Software** Network Manager installed
**Security** WEP, 128 bit, hexadecimal, open.
**Connection** used static connection rather than DHCP
**Driver** driver is already pre-installed in Ubuntu 6.06, Ralink 2500

---

### Post by eltorodeoro on 2006-09-16
I posted a request similar to this last week.  To be truthful, Ubuntu's community support has always been one of the top selling points for this flavor, and the first time I really desperately need it, I have found it to be - well, less than ideal.  Aside from the couple folks who responded, my fact-finding probe was lost amidst the scores of issues everybody else is having.

Ubuntu's community support is supposed to be waht sets it apart from everything else - particularly the boys in Redmond.  I must admit, I am nothing more than an advanced end-user.  I am years away from being able to meaningfully contribute to this community.  But I think its worth the effort, and the wireless forum is going to be a huge part of Ubuntu's future adoption.

So, if anyone with any say so is reading this post, PLEASE forge some sort of list like the one mentioned above.  I'll gladly post my findings once I finally dive into the realm of Wi-Fi.

---

### Post by General Skanky on 2006-09-18
I'm new to Ubuntu as of yesterday.

I saw immediately the lack of wireless support.

My problem is with BCM34XX. Unless someone explains that in plain english I will just hold off until it is fixed by some bright spark.

I really like Ubuntu, but having to plug into a router is such a strange experience!:biggrin:

---

### Post by eltorodeoro on 2006-09-18
There's a really thorough HowTo for BCM cards in this forum by compwiz18.  Give that a try.

---

### Post by thedreaming on 2006-09-18
I recently installed more memory on my old laptop so I could install ubuntu, I had xubuntu installed before and with it, I could use my wireless pcmcia card with no problems, but when I tried using the live cd of ubuntu, it didn't recognize the wireless card?  It's a linksys wpc11 card, which only does 802.11b, but under xubuntu and windows 2000, it works great.  I rather ben running under ubuntu cause I've used it before on my desktop and it's easy to get setup for day to day use, but I don't want to install it on the laptop, then find out it won't support my wireless card.  Also, why would xubuntu support it but not ubuntu.  As far as I know, I have the latest of both.

---

### Post by selam on 2006-09-19
hi,

this thread will be very useful to the ubuntu users especially for the new ones as me. I have installed ubuntu for my laptop. Shall I replace with Xubuntu? I also want to mention that I have a Dell inspiron 7500 for linux. I also have a linksys wpc11b version 4 card. I want to ask whether or not it supports WPA or xsupplicant? Does it just work with unsecure wireless lans?

---

