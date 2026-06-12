---
title: "Default gateway device keeps vanishing"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by RogerD on 2007-03-14
Hi

I've got a little problem that's making my lovely new PC nearly useless - the default gateway device keeps disappearing from the network setting window.

My internet connection is via a wireless LAN, using an Edimax USB adapter. I obtained this from the Linux Emporium, who also supply the drivers, which I'm sure I've installed correctly. Initially, everything worked fine. The Network setting window, obtained via System>Administration>networking, showed that the wireless connnectin rausb0 was active (indicating that the drivers are OK), and rausb0 appeared as the default gateway device. However, when I re-started my computer, I had no wireless signal, and the default gateway device box was empty. I can get the wireless connection restored by first deactivating and then reactivating the the wireless connection. This get rausb0 back in the default gateway device box, and, after which I can generally, get an internet connection. Which is again lost when I shutdown and re-start my PC

Can anyone help please. I'm just lost for what to do next. Would editing a configuration file help? I'm happy to give it a go.

Best regards

Roger D

---

### Post by dannyboy79 on 2007-03-14
have you tried this?
[http://opendns.com/start/ubuntu.php](http://opendns.com/start/ubuntu.php)
using the guide, use hte dns servers that your router has in it it's config page. or call your isp to find out what dns servers they use. also, not sure what you mean about default gateway, this should be your router or your modem's ip address, the one that is between you and the world. the dns issue is due to dhcp, so maybe try static. good lcuk

---

### Post by RogerD on 2007-03-14
Thanks for responding. The suggested URL looks a bit scary. My "default gateway device" box appears at the bottom of the "Network setting window - what you get from System>Administration>networking. Initially this contains rausb0, and everything works, but when I start my PC up again, the box is empty, and nothing works.

---

