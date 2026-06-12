---
title: "RTL8185 Driver problem Resolved"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by cab_bae on 2008-05-29
Well I don't know if you know this but the problem isn't with driver assigned from Ubuntu. Thats what I thought and went to install Ndiswrapper but when I installed it, the program already told me that it had the driver I was trying to install already installed. I tried two ways to install Ndiswrapper first was to go manual but that didn't work because every time I tried making the make file I would get errors as well with the make install so what I did was to add/remove in applications and then I set it to all supported applications. I searched Windows Wireless Drivers and it came up Ndiswrapper in a GUI. How cool huh. Well I proceeded to install and nothing. So I had herd that the problem wasn't with the driver but the WEP and anything that has to do with encryption. So what I did was switch to MAC filtering in my router and there I got my wireless in Ubuntu. I did this on a Gateway MX3410 notebook with  a Chipset: Realtek RTL 8185L for any more information regarding my laptops networking card go to [http://support.gateway.com/s/Mobile/eMachines/StormE/105825/105825sp2.shtml](http://support.gateway.com/s/Mobile/eMachines/StormE/105825/105825sp2.shtml)

Hope this works for you in any way!!!

*Edit*
--------
I'm using the newest edition of Ubuntu which is I think 8.04 and I'm going to try this on Kubuntu if it works aswell.

---

### Post by UYBGragh on 2008-06-05
Thanks for the info.  However, I am not doing as well.  I get my card to blink the status LED.  In Network Settings, I can see the available networks (so the card CAN do something).  But it just won't actually connect to one.  Am I missing something stupid like not properly killing the wired connection first?

---

### Post by UYBGragh on 2008-06-05
Never mind, I got it.  Just need to make sure it comes up by default now, every reboot, even in console only mode.

---

