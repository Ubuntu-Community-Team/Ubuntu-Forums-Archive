---
title: "I'm looking for a SiS761GX graphics driver"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by bwallum on 2009-10-02
Hi

I'm looking for a SiS761GX with Mirage 1 graphics engine driver.

This is on an ECS GS7610 Ultra motherboard. The board runs fine, the integrated graphics are terrible at the moment Two columns of flicker either side of vertical centre.

I suspect that it is trying to run accelerated graphics without a driver being installed and Karmic is trying to run it with a standard vesa driver.

This is a very fast cheap 64bit board (tech about 4 years old hence cheapness), still lots of new stock around and I would love to get the graphics going properly.

Can you help me find an appropriate driver please?

---

### Post by wobin77 on 2009-10-02
[http://www.opendrivers.com/categorycompany/12/11552/display-and-video-sis-free-driver-download.html](http://www.opendrivers.com/categorycompany/12/11552/display-and-video-sis-free-driver-download.html)

?

---

### Post by 3rdalbum on 2009-10-02
> **bwallum said:**
> The board runs fine, the integrated graphics are terrible at the moment Two columns of flicker either side of vertical centre.

I suspect that it is trying to run accelerated graphics without a driver being installed and Karmic is trying to run it with a standard vesa driver.

From what I hear about SiS drivers, it sounds more like Karmic is trying to run it with an SiS driver and that you'd be better off with vesa :-)

---

### Post by bwallum on 2009-10-02
> **3rdalbum said:**
> From what I hear about SiS drivers, it sounds more like Karmic is trying to run it with an SiS driver and that you'd be better off with vesa :-)

So how do I tell Karmic just to use vesa?

Also, thanks for the drivers link but they all appear to be for Windows. Is the SiS761GX chip locked into Windows? I.e. Linux can't run on it and I might as well use the board for combing my dog?

---

### Post by sandyd on 2009-10-02
well... if you feel like compiling outdated drivers that were meant for fedora, you can try
[http://www.sis.com/download/agreement.php?url=/download/](http://www.sis.com/download/agreement.php?url=/download/)

otherwise, a comb for a dog  would be perffect

---

### Post by halitech on 2009-10-02
if the rest of the system is fine, you could check the board and see if it supports PCI-e and pop a new video card in and use it instead of the onboard graphics.

---

### Post by bwallum on 2009-10-03
> **halitech said:**
> .....pop a new video card in and use it instead of the onboard graphics.

Thanks everybody, before the dog gets a treat I will pop in a pci-e card. I did try tracking down a driver on the ECS support site but a machine acknowledged...and that was it. Are ECS dead?

---

### Post by halitech on 2009-10-03
ECS website and info on the board here
[http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?DetailID=846&CategoryID=1&DetailName=Feature&MenuID=48&LanID=0](http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?DetailID=846&CategoryID=1&DetailName=Feature&MenuID=48&LanID=0)

Looks like it does support PCI-e
```
EXPANSION SLOT   	
 	1 x PCI Express x16 slot
 	1 x CNR slot
 	2 x PCI slots
```

---

### Post by bwallum on 2009-10-04
Thanks Halltech, I found the Windows drivers but no linux ones. Is there a site that specialises in linux drivers for chipsets?

---

### Post by halitech on 2009-10-04
typically most drivers are included in the kernel so there is no need to install other drivers. The main exceptions are video cards for 3d support and wireless cards. SiS isnt well known as being a linux friendly company so chances are you won't find a specific driver online to use. Check Synaptic and see if there are any sis drivers in there you don't currently have loaded.

---

### Post by bwallum on 2009-10-06
> **halitech said:**
> ...Check Synaptic and see if there are any sis drivers in there you don't currently have loaded.

Thanks, a really useful steer. I found xserver-xorg-video-sis in synaptic. I'll give it a go.

---

### Post by bwallum on 2009-10-07
...and here's another useful bit of info for anybody following:-
[http://www.sis.com/support/support_faqs_16.htm](http://www.sis.com/support/support_faqs_16.htm)

---

