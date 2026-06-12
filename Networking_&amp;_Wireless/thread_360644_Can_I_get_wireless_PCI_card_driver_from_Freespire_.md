---
title: "Can I get wireless PCI card driver from Freespire into Ubuntu?"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by Tesgin on 2007-02-13
Can someone help me with this? Is it possible to get the driver for my wireless PCI card (which runs perfectly in Freespire) OUT of the Freespire set up, and copy it into my Ubuntu installation? 

The card is a Linksys WMP11, v. 1.0 card.  Does not run under Ubuntu, but DOES run under Freespire.   I did a test drive of Freespire from a live cd , and my wi-fi card works there without a hitch.  No configuring at all. CANNOT get it to work in ubuntu.

Please help!

Thanks in advance,
Tesgin

---

### Post by spd106 on 2007-02-13
I think it's very unlikely that it would work as they have different kernels. 

It looks like you have a prism 2 based card, so you could try installing the linux-wlan-ng package from the universe repo.

---

### Post by Tesgin on 2007-02-13
"installing the linux-wlan-ng package from the universe repo"

I'm sorry.  I'm a total newbie to Linux.  I don't know what that means.  How do I do that?

Thanks,
Tesgin

---

### Post by spd106 on 2007-02-14
Actually, I was wrong it's in the main repository, so there's no need to add any extras. 

You can install it straight away through System -> Admin -> Synaptic. 

For future reference to add the universe repository in Synaptic see [this]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by Tesgin on 2007-02-14
spd106,

Thanks.  I followed the above, and now I have the linux-wlan-ng package installed.  Then I rebooted.  What next?

Thanks in advance,
TB

---

