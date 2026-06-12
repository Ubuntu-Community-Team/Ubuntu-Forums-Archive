---
title: "Can't install restricted drivers"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by HittingSmoke on 2009-06-18
My friend has an HP dv5140us laptop that I installed Ubuntu Intrepid on tonight. The restricted drivers manager came up with drivers for his Broadcom wireless card as well as his ATI video card.

When I click "Activate" the installing progress bar shows up at 0% then disappears but the driver does not activate. The little green button next to the drivers wont light up and rebooting always produces the same results, no activated drivers. I tried finding the drivers in Synaptic but it reports them as already installed.

Could this be a hardware limitation of the laptop with Linux or is it a software issue that can be fixed?

---

### Post by kwacka on 2009-06-18
You don't say which broadcom card you're trying to get working. 

For example, if it's a 43xx you need a wired connection to router to allow computer to download Windows drivers for b43-fwcutter to get you up and running.

If you open a terminal and type ```
lspci
```
you should be able to identify the card.

Any problems, post the output of lspci here.

---

### Post by HittingSmoke on 2009-06-18
> **kwacka said:**
> You don't say which broadcom card you're trying to get working. 

For example, if it's a 43xx you need a wired connection to router to allow computer to download Windows drivers for b43-fwcutter to get you up and running.

If you open a terminal and type ```
lspci
```
you should be able to identify the card.

Any problems, post the output of lspci here.

Thanks, don't have the laptop with me. I'll post back with results when I can.

---

### Post by DeathMetal on 2009-06-18
Ok so here it is.  I plugged my ethernet cable directly into my laptop, pulled up the drivers list and was able to activate the driver for the wireless card no problem.  Shift over to my graphics card, and it does the same thing.  The download/install window appears and stays at 0% and then disappears and the driver has not been activated.  My graphics card is an ATI Radeon Xpress 200M if that is of any help.  Oh and by the way, I'm the guy HittingSmoke was helping out.

---

### Post by DeathMetal on 2009-06-18
So after upgrading to 9.04 I decided to go ahead and see if I could activate the driver for my graphics card.  I opened up the Hardware Drivers menu and clicked on the driver for my graphics card and lone behold, it activated no problem.  Thanks for the help and advice guys.

---

