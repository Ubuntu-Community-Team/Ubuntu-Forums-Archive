---
title: "laptop pcmcia WIFI"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by matt91 on 2008-05-12
I have a laptop in which i want to run Ubuntu on however I am having wifi problems. First of all a great job has been done with 8.04, the laptop will now run Ubuntu out of the box with graphics, audio and proper track-pad support.
I currently have a Belkin Wireless G Notebook Card (F5D7010uk). I can get it installed with the ndiswrapper and the windows driver and will connect to the network, however it will intermitantly disconnect, if connect at all when encryption (WPA or WPE) is enabled. I cannot run without encryption. Is their any way to get this running, possibly with proper linux drivers? ... Or can you recommend any cheap linux-compatible network cards?

Thanks, Matt

---

### Post by matt91 on 2008-05-13
Anybody? Would rather buy a new one which works with linux without any driver installation. my Budget is up to £20

Thanks

---

### Post by matt91 on 2008-05-14
*bump* 

Any recommendations? I have looked at the supported hardware however is is difficult to tell what I will get because some use different chipsets on different revisions.

---

### Post by prshah on 2008-05-14
> **matt91 said:**
> I am having wifi problems. 

I currently have a Belkin Wireless G Notebook Card (F5D7010uk).  will connect to the network, however it will intermitantly disconnect

Maybe a power saving issue? You can disable power management for the wireless card with the command ```
sudo iwconfig eth1 power off
``` and check if it makes a difference.

Replace "eth1" with the actual wireless interface in your notebook.

---

### Post by matt91 on 2008-05-15
Thank you, that has worked. I have also reduced the WPA key to a shorter key to make it faster.

---

