---
title: "Where are kernel source and pcmcia source located?"
date: 2005-12-06
forum: Networking &amp; Wireless
---

### Post by harisund on 2005-12-06
Ok.. so after a lot of searching, I came upon this website

[http://theblackmoor.net/dwl650.shtml](http://theblackmoor.net/dwl650.shtml)

where the author has neatly explained how to configure a DWL 650 using linux-wlan-ng driver. 

I download the driver, and *make config* asks me for the path of linux source. I guess the next question will be pcmcia source. 

So can someone please help me find that? pcmcia-cs package is already installed (atleast according to dpkg) so where do I find the source for that? Also, I am guessing the Ubuntu kernel would have been by default configured to support the Wireless Radio, and hence I don't need to recompile the kernel. 

So basically I need to know where to find the kernel source tree and the PCMCIA-CS package's source tree. 

Thanks for your help !

---

### Post by az on 2005-12-06
There are three drivers that make the prism2 chipset work.  Orinoco, hostap and linux-wlan-ng.  

Your card should hotplug the orinoco drivers.  If it is not doing that, building any of the other drivers will not work.

I assume that your card is not working.  Does the light even come on?  If yes, show the ooutput of the /var/log/messages log (use the log tool) when you insert the card for the first time (boot without it).

If the light does not come on, show the output of 
lspci
lsmod

---

