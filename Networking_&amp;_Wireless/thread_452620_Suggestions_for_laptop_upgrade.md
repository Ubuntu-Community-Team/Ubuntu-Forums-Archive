---
title: "Suggestions for laptop upgrade"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by Mime on 2007-05-23
My laptop is running an old Dapper install that I've always been too busy to mess around with much.  I've got the dreaded broadcom 4318 controller, so wireless has always been a pain.  I can get everything to work... usually, but it's anybody's guess as to when my connection will get dropped once I actually do get a connection.  I've tried both ndiswrapper and the native firmware and they both seem to give about the same results.

I'm thinking of upgrading to Fiesty to see if that has better wireless support.  If need be then I'm also thinking of going all out and getting a new mini-PCI card and replacing the thing altogether. So... does Fiesty have better wireless support?  And if I do need to hack my laptop, what controller should I get?

The laptop is an HP L2000 which uses a 2ghz Turion, so I'd like to stay with 64bit stuff if possible.

Cheers,
Mime

---

### Post by spd106 on 2007-05-25
You might have better results with Feisty as both ndiswrapper and bcm43xx have seen some improvements over the last few months. Bear in mind that you should upgrade via Edgy or do a completely new install with the Feisty CD. These are the only two supported methods.

Though both have better support than Dapper, Feisty isn't a huge leap forward from Edgy for most Broadcom based devices, just small improvements to the same drivers. The next big change will be the move to d80211, which is scheduled to happen in the next kernel release (2.6.22).

If you just want to drop the Broadcom card then investigate whether your laptop will support the Intel pro wireless 3945abg miniPCI card as they are reported as working quite well (and the new Dell E1505N laptops have them). You can purchase them separately, though you will need to be reasonably competent at hardware to install it yourself. A quick google search suggests that some L2000 series can support the Intel card. Make sure you check first as it might vary between models.

---

