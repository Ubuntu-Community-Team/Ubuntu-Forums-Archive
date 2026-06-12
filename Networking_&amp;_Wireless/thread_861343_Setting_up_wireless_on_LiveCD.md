---
title: "Setting up wireless on LiveCD"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by Poteighteau on 2008-07-16
I've searched through the forums to find several guides to setting up the broadcom wireless card (4311 rev02) on my computer, but I'm using the LiveCD for now. I don't want to install Ubuntu on this computer if i can't use the built-in wireless card.
If I follow the HOWTO correctly, should I see results if I'm using the LiveCD or will I not be able to do this until I fully install Ubuntu?

This is the HowTo I was following:
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

I'm running 8.04, but I've read that this should still work.
Any thoughts?

---

### Post by PinkFloyd102489 on 2008-07-16
I used a guide from Feisty on my 4328 rev 03. If you have the right driver and are using ndiswrapper, it should work.

---

### Post by Poteighteau on 2008-07-16
> **PinkFloyd102489 said:**
> I used a guide from Feisty on my 4328 rev 03. If you have the right driver and are using ndiswrapper, it should work.

I can get the card to work (the light changes from red to blue, it recognizes networks in the area, and has a pretty strong signal to mine) but it asks for my WEP key, tries connecting, but then asks for my WEP key again, without ever establishing the connection.
Removing the encryption really isn't an option for me at this time. Is there something I can do to fix this?

---

