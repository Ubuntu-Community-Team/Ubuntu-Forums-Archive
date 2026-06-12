---
title: "Can't get ndiswrapper installed right"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by duns0014 on 2007-01-29
Hi, I installed Dapper sucessfully.  I then needed to get ndiswrapper working so I could get wifi.  I went through the instructions once but had some error doing modprobe, I forgot what it was.  So I went through the instructions for reinstalling ndiswrapper which included purging the system of anything ndiswrapper related.  Included in this was deleting the ndiswrapper folder under /lib/modules.  I reinstalled ndiswrapper and successfully installed the driver for my laptop.  I did depmod -a and it did its thing, then when I did modprobe ndiswrapper, it gave me a fatal error saying that it couldn't find ndiswrapper.  Even though I reinstalled ndiswrapper, I could not find it under /lib/modules, I did a search.

I was poking around and it looks like the ndiswrapper entry under /lib/modules originally came from the linux-image package (it was listed as an installed file in synaptic).  Unfortunately, I couldn't reinstall linux-image because I couldn't find this package anywhere in my install cd.  How'd it get there to begin with then?  Also, I used sudo for all commands.  Any ideas?  Thanks.

---

### Post by hggdh on 2007-01-29
I am somewhat lost here. You say you reinstalled ndiswrapper. How did you do it?

---

### Post by phansiizwe on 2007-01-29
Are you compiling ndiswrapper from source, or are you installing it via Synaptic (System->Administration->Synaptic) ?
If you do not need the latest version, install via Synaptic, this is much less prone to errors and should automatically setup everything correctly.
Reinstall the wifi driver afterwards...

---

### Post by duns0014 on 2007-01-29
I reinstalled ndiswrapper by browsing the install cd and double clicking.  It said all the dependencies were met.  But considering the missing module under /lib/modules, I don't think the ndiswrapper package is what's giving me problems.

---

