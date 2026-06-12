---
title: "&quot;Ralink open-source friendly Wifi vendor&quot;? BAH!"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by stormfrog on 2007-03-01
Since I have had nothing but complete and utter chaos since I picked up a wlan card that was supposed to work with Ubuntu I have looked around alot for a solution.

I found this on a page at ubuntu.com:

> Make sure you buy wireless cards supported fully under Linux. It is worth noting that the [WWW] Free Software Foundation (FSF) recommends the Ralink 2500/RT2400 and Realtek RTL8180 chipsets. A recent (December 20, 2006) [WWW] article also mentions Ralink and Realtek as open-source friendly Wifi vendors, as well as Atmel.


[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[http://www.thejemreport.com/mambo/content/view/293/](http://www.thejemreport.com/mambo/content/view/293/)

Thats worst lie Ive ever heard. Ralink is completely unsupported by Ubuntu. Ralink's own drivers are completely utterly pathetic. Even with the supposedly working 3d party open source drivers Ubuntu systems repeatedly freezes and crashes while NIC is enabled.

How hard can it be? Even Microsoft manages to support this card. Sure, if you are a linux expert I dont doubt you wont have any problems. But this is Ubuntu, linux for everyone... or is it really?

*growl*

---

### Post by ncappel1 on 2007-03-02
I have a ralink2500 type wireless card in my desktop machine, and it worked pretty well until I updated to edgy. for me I don't think the problem is the card. what specific problem are you having?

---

### Post by stormfrog on 2007-03-03
> **ncappel1 said:**
> I have a ralink2500 type wireless card in my desktop machine, and it worked pretty well until I updated to edgy. for me I don't think the problem is the card. what specific problem are you having?

Among other things random crashes. At one point my system crashed and when I alot of my modules were gone. And this on a system that previously has run for quite a time without a single issue or error. One thing that really makes me annoyed is that all RaLink drivers for edgy is totally unsupported by Ubuntu. The Wlan tools in Ubuntu actually remove and disable your cards instead of helping you.

I suppose this thread was more an expression of being annoyed with Ubuntu than a true support issue. Most of all I am annoyed of people that really things that Linux can be for anyone. I have a pretty good idea about how Linux systems works but I admit to still being an amateur. When my system rebooted and modules were gone I was dead in the water. There was absolutely no way for me to repair whatever broke. No logs reported errors! At the end I bribed a friend of mine (who is something of a linux genious) to fix it. After 30 minutes of researching and a couple of pages of perl-code he was able to get the modules loaded again. There is absolutely no way for an average user to do this. 

So, why does Ubuntu claim their flavor is different? Its the exact same as Debian or even SlackWare beneath the pretty colors. To be able to operate a Linux system by yourself you have to devote an insane amount of time into it. There is no changing that.

Throwing in an easy install interface and add a custom theme to Gnome does little to create a human friendly computing interface.

So, the subtitle really should be **Ubuntu - Linux for computer geeks that have no idea what good HCI is.** :biggrin:

---

### Post by bionnaki on 2007-03-03
rt2500 from serialmonkey works perfectly for me. see my signature for details.

---

### Post by peterbakker on 2007-05-15
amen:mad:

---

### Post by jml on 2007-05-15
My RaLink experience has been sketchy as well.  Not really impressed with either the chip set, nor the native drivers.  Although, I have not tried the serial monkey drivers for quite some time.

I think the real problem is one of Ubuntu's design philosophy.  Now don't get me wrong, I use Ubuntu and am for the most part satisfied with it.  But it is based on Debian Unstable, and has an aggressive six month release cycle.  These two facts are both Ubuntu's strength (nearly bleeding edge applications,) and its weakness ( not infrequent crashes and breakage.)  For my laptop, I run Feisty on a laptop I bought from System 76.  For my home computer, I run a laptop with very modest hardware requirements, I run Debian Etch (stable.)  Not quite as up to date as Feisty, but since it has been installed, I have had no problems.  I even got my dreaded Broadcom wireless card working.  Once you get a system tweaked and stable, a long upgrade cycle is a very good thing.:mrgreen: 

Joe

---

