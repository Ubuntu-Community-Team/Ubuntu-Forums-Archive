---
title: "I'd like to set my wireless adapter up as an access point, not a client"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2008-05-11
My girlfriend just bought a Nintendo Wii.  The house she stays at has no Internet connection, but I often have my laptop and cellphone with me which gives me about a 25 KBs downstream.  What I'd like to do is share my Internet connection to the Wii wirelessly from my laptop using my d-link card.  I'd also like the ability to quickly switch the wireless adapters from Access Point mode to client mode, so when I'm at *my* house, it'll be just as it is now, and connect to my wireless router with no problem.

---

### Post by Rohaq on 2008-05-16
Bumping this, because I'm having trouble creating an accessible wireless network from my wireless network adapter too. I try to create the wireless network using network manager, is spends ages seemingly configuring the network, then it goes back to my wired connection. Scanning on other machines reveals no new wireless networks by the name I specified.

Running Ubuntu Hardy 64-bit, wireless card is an RT2500 based model.

---

### Post by diablo75 on 2008-05-18
Another bump....:)

---

### Post by Phil Urich on 2008-05-19
I'm pretty sure you'll need to do some mucking about with a config file; should be pretty straightforward though.  I'd suspect fooling around with /etc/network/interfaces could do the trick, the main problem would be having a wireless card that supports the modes you'd need . . . which is tough, considering how strangely hostile wireless manufacturers seem to be towards linux!  To be perfectly honest I have no clue how common or uncommon this is.

If you're using the madwifi drivers, [http://madwifi.org/wiki/UserDocs/SimpleAccessPoint](http://madwifi.org/wiki/UserDocs/SimpleAccessPoint) looks promising. In fact, looking at that article, I'd suspect that it would work for many different cards, but YMMV and all; also, Hardy did some strange (to me) things to wireless so I'm unclear on whether this would still work or not.  I'm interested now though, so I'll stick around and see if I can help you folks out if at all possible :)

---

### Post by diablo75 on 2008-05-19
Well I've had no problem putting my card into that passive monitor mode using a Backtrack 3 Beta Live CD.  The card uses an Atheros chipset, which I've heard is very linux friendly and hackable.  So I could use that OS as a start.  Perhaps I need to go over to the BT forums and see what they think.

---

### Post by diablo75 on 2008-05-19
It looks like there's a HOWTO out there:

[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283)

I've not gone over it yet, but am hopeful it will work.  I'll try it out when I've got time later tonight.

---

