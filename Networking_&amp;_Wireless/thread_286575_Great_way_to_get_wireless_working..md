---
title: "Great way to get wireless working."
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by dbcalo on 2006-10-27
this might not be the best way for some people, but hell, it worked for me.

i was using a linksys wrt54g with a wusb54gsv2 adapter. that setup didn't fly in ubuntu, so i eventually came up with a better solution.

what i did was purchase a second wrt54g (now called wrt54gl), install a third party firmware ([http://www.thibor.co.uk/)](http://www.thibor.co.uk/)), set one to AP mode, & one to wireless ethernet bridge mode. Done.

i know most people will think this is more expensive, but if you consider that a good wireless adapter is going to cost you as much as another router, then you might see how i came to using this setup. you also have the option of expanding your wireless network with WDS mode. WDS mode links the two routers together.

hope that helps someone out.

---

### Post by magicfab on 2006-10-28
Could you please elaborate on what was not morking before and what problem you specifically solved ? I am not quite sure why I would want to use a full router instead of my internal wifi adapter (or USB)...

---

### Post by dbcalo on 2006-10-28
the problem this solved for me was that it was that i could never get my linksys wusb54gs card to run under linux. first it was the ndiswrapper, then it was wpa supplicant. was just a compounding of complication that i couldn't break through.

being that i wanted to use ubuntu, with internet, and theres almost no setup for ethernet -- compared to wireless --, i just used the ethernet bridge capabilities of the modified router.

the benefits are:

1. ease of setup
2. increased range (power of transmission can be set higher in each router)
3. you can setup a distributed wireless network (more coverage)
4. routers are handling all wireless communication and encryption.
5. did i mention that it was about the same price as a good wireless adapter?
6. the wrt54gl runs embedded linux (thats what the "L" stands for)

---

