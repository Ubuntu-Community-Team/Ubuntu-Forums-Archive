---
title: "Wireless &quot;eyecandy&quot; issue.."
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by HarshReality on 2007-07-02
I'm going to do a bit of explaining before I get to the question..

OK, some time ago I took my zd7010 (before broadcom realeased a driver) and decided I wanted a complete native linux driver... HP Laptops have a 'whiteist' od supported hardware and if your not fortunate enough to have the funds to buy a 'HP Approved' card then you get a 104 error for unsupported hardware on boot and the system halts.. Low and behold there is a flash for the bios on HPs website, I chose the cheaper of two roads and got a Intel 2915 a/b/g for 20.00 and popped it in and got my error, but after editing the bios file and making a substitution of Intel for Broadcom it works wonderfully.

So, granted I'm messing with Gibbon tribe 2 here is my dilema. In windows when the wireless switch is active in the upper right there is an indicator light (flashes and remains solid when connected, off when disabled) the switch works fine as does my wireless trick is when I am not connected I cant really tell the position of the switch or its status without that stupid light. So, I press it and try and if it fails internet I press it again and try... and if it fails I press it again and try... and then I go looking for one of my routers to just hardwire because I am now annoyed.

So my question is this if I dmesg I get:
Unknown key pressed code 0xf8 on isa0
Use setkeycodes e078 <keycode> to make it known.

Now even though the system seems to say unknown its more or less a hardware switch to the wireless, but how would I go about getting the goofy light to function?

---

