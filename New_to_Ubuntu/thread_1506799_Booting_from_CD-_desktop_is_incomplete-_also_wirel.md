---
title: "Booting from CD- desktop is incomplete- also wireless LAN"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by sumithar on 2010-06-10
I booted up using the 10.0.4 CD.  But I can't see the full desktop on my 15" LCD monitor.  So I'm not sure if I should go ahead and actually install Ubuntu- how can I be sure if it will be OK?

Can I resize?

Also, it doesn't appear to recognize my wireless LAN card.  If I boot from CD I should still be able to access the network, right?

---

### Post by apjone on 2010-06-10
I would say try changing the the resolution settings in ubuntu or the H/V values on your monitor. What Wireless Card do you have? It may be that you need to install the driver "System > Administration > Drivers". If you post what card you have we can check out the HCL and see if it works

---

### Post by sumithar on 2010-06-10
> **apjone said:**
> I would say try changing the the resolution settings in ubuntu or the H/V values on your monitor. What Wireless Card do you have? It may be that you need to install the driver "System > Administration > Drivers". If you post what card you have we can check out the HCL and see if it works

I don't know how to change the settings in Ubuntu since I can't see the menu options at the top of the screen.  They seem to be 'outside' the monitor's display.
I tried right clicking on the visible desktop but only options to change b/g and theme are available none to change graphics properties.

I have WUSB300N linksys card.  Again, I can't click on the System menu item since I can't 'see' it!

I tried live booting on a m/c with a 17" inch screen and I can see everything properly.

---

### Post by sumithar on 2010-06-11
OK- the monitor display problem seems to have fixed itself when I rebooted again today.
But it doesn't recognize my wireless card.  I went into System/Admin/Hardware Drivers and I get a rather pointless message titled "no proprietary drivers are installed"

And a quick search on WUSB300N Ubuntu
gives me links talking about ndiswrapper.

That was the very reason I gave up on Ubuntu a couple years back- the inability to get it to work with LAN adapters that worked perfectly well with Windows.  I mucked around with this NDISWRAPPER business till I was blue in the face.

If 4 releases later, nothing has changed in that regard, then I guess I will just stick with XP.

---

### Post by Guilden_NL on 2010-07-26
No need for NDISwrapper.
The problem is that due to an oversight, Lucid/10.04 does not have fakeroot on the install CD so in order to get the wifi going you will need to connect to a hard-wire network cable to get the files you need. Without fakeroot neither the proprietary driver or NDISWrapper will work. NDISWrapper is a last resort solution and one that is rarely needed anymore

---

