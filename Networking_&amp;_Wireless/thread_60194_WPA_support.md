---
title: "WPA support"
date: 2005-08-26
forum: Networking &amp; Wireless
---

### Post by robfindlay on 2005-08-26
Can someone point me to a FAQ, how-to or walk through on how to setup WPA on a hoary install?   Can this be setup to work under the gnome interface for networking ?  


This is on a Dell 6000 laptop BTW. 





Rob

---

### Post by matthew on 2005-08-26
Hmm..., you didn't give us much in the way of specifics about your hardware so it is hard to know which way to point you. As a starting point, a good question to anticipate in these instances are "what wireless card do you have?" I any case, I really want to give you something that may be helpful so here are a copule of links to explore for starters.

[http://www.ubuntuforums.org/showthread.php?t=31418](http://www.ubuntuforums.org/showthread.php?t=31418)
[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

Also, to answer your question directly, I am using wpa with the computer I am writing on right now using Ubuntu and Gnome. I needed the info in the first link's post to make it work.

---

### Post by robfindlay on 2005-08-27
Thanks for helping, here's the output from an lspci: 

0000:03:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

The hoary install recognized the card right out of the gate so i'm assuming that
it's using a native driver and not madwifi or ndswrapper. 

By working under gnome what I meant was that I would like to be able to use the gnome utility to configure networking.  I.e. right now i have a profile setup for work and one for home each configured to point at the applicable access points for where I'm at.   It currently has a slot to put in a WEP key, it would be nice if there was a slot for wep OR wpa. 

I'll look over those links you gave and see what I can come up with. 


Rob

---

### Post by matthew on 2005-08-27
You have the same card that I have so the link to the Howto on using the ipw2200 and wpa should work well for you.

---

