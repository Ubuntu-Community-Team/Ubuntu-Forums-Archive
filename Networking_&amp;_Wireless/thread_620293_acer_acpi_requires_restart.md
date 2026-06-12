---
title: "acer acpi requires restart"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by howbag on 2007-11-22
hey, I've installed Acer acpi from their repositories and my network card works perfectly fine. (Im running an Acer Aspire 5044WLMi).

Though the card NEVER works after a normal boot from "not powered on" to powered-on mode, but if I click RESTART in gnome, the card works perfect every time after the restart.

Why is this? anyone go the same problem?
Im running Ubuntu 7.10

---

### Post by aavikkosorsa on 2007-12-04
i got the same problem with acer aspire 5040. Wifi works just fine after second boot. I also install acerwificontroller but it did'n do enything!

---

### Post by DennisMonague on 2007-12-04
I just finished posting this at Re: Ubuntu 7.10 - Atheros Wireless AR5005G - HELP PLEASE.  Maybe it will help someone figure this one out for everyone here.

I solved it!!!!! YAY!!!! Well actually what you said about turning on then having to restart solved it. And I think I found out why we (me and you, that is if you still have to do a this) have to do that restart to make the wireless work. 

It seems that when I turn the laptop on "fresh" the wireless card has to do a start up. This start up happens after Ubuntu tries to do a wireless network sensor sweep. So Ubuntu figures that there are no wireless networks and defaults to the wired configuration. Now when a restart is done the wireless card doesn't actually shut down, so now it's on when Ubuntu does the wireless sensor sweep and finds wireless networks in range, so it doesn't default to the wired connection configuration. I actually found a post (have since lost it and can't find again) that tells you how to make Ubuntu do a new sweep (maybe it just resets the configuration to make wireless work again .... not to sure, I'm just learning the new Linux language and processes) without having to restart. 

I'll pass that on if I find it again. 

Thank you very much with your help through all this.

---

### Post by aavikkosorsa on 2007-12-09
I got it work too. I change the current unworking madwifi driver to win xp driver with ndiswrapper. With ndiswrapper wifi is working with just one boot. 

I would like to hear how you get it work Dennis if you find that post???please?

Here*s the post i use : 
[https://answers.launchpad.net/acerlaptop-wifi/+question/4809](https://answers.launchpad.net/acerlaptop-wifi/+question/4809)

---

