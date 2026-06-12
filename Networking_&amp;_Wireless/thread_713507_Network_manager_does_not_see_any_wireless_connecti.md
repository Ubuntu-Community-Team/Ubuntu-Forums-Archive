---
title: "Network manager does not see any wireless connections"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by justinclark on 2008-03-02
I have a Toshiba Satellite laptop with a new Ubuntu 7.10 install (dual boot with Vista).  When I open the network manager (system-admin-network) it only shows a wired connection, no wireless.  It works on Vista and yes, the wireless switch is on. I have searched around and have read that it should be as simple as opening the manager, selecting the wireless conn and enetring the wep but it dont seem to be detecting it. I dont have any experience with wireless on linux so any help is appreciated.  Thanks

---

### Post by scottro on 2008-03-02
I think the best way to start is go into Windows, open the Device Manager and find out the make of the card.  IIRC (If I remember correctly) a lot of them use the AR5007EG.  If so, then Ubuntu probably didn't discover the card which is why it didn't show up in Network Manager.  

If you're running 32 bit Ubuntu and it is an AR5007EG, then fear not, the problem is easily solved. (I won't go further till you report back on the make of the card.)

The reason I suggest using Windows rather than the native Linux lspci is because with this particular card, lspci doesn't yet recognize it properly. 

At any rate, once you find the model of the card, I'd put that into the search box of the forums--the chances are that no matter *which* card it is, someone has had it and hopefully gotten it working.  :)

---

