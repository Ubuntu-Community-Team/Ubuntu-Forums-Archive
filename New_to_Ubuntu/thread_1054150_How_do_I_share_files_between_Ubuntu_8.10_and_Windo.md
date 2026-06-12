---
title: "How do I share files between Ubuntu 8.10 and Windows XP on VirtualBox?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by gymophett on 2009-01-29
I need to share a folder from Ubuntu 8.10 to Windows XP on VirtualBox. Help?
Thanks :)

---

### Post by hyper_ch on 2009-01-29
install the guest addons

---

### Post by gymophett on 2009-01-29
> **hyper_ch said:**
> install the guest addons

It freezes up :(

---

### Post by DGortze380 on 2009-01-29
> **gymophett said:**
> It freezes up :(

how much RAM do you have?

---

### Post by gymophett on 2009-01-29
> **DGortze380 said:**
> how much RAM do you have?
1 Gig.

---

### Post by DGortze380 on 2009-01-29
> **gymophett said:**
> 1 Gig.

and how much given to XP?

---

### Post by gymophett on 2009-01-29
> **DGortze380 said:**
> and how much given to XP?
192mb.. Which I guess isn't enough.
What should I change it to?

---

### Post by DGortze380 on 2009-01-29
> **gymophett said:**
> 192mb.. Which I guess isn't enough.
What should I change it to?

I would give it at least 512Mb

---

### Post by gymophett on 2009-01-29
> **DGortze380 said:**
> I would give it at least 512Mb

Ok. I'll do that, and post if it works back here :)

---

### Post by gymophett on 2009-01-29
> **gymophett said:**
> Ok. I'll do that, and post if it works back here :)

It installed! I'm rebooting it. What do I do when I get back into XP to access my files?

---

### Post by DGortze380 on 2009-01-29
> **gymophett said:**
> It installed! I'm rebooting it. What do I do when I get back into XP to access my files?

Set up a share folder in the VirtualBox Window in Ubuntu.

You will be able to access the share via Network Places in Windows. Mine is very slow (I used Host-Interface and typical network shares instead, faster).

---

### Post by cerealtx on 2009-01-29
> **gymophett said:**
> It installed! I'm rebooting it. What do I do when I get back into XP to access my files?

using the manager setup the paths for the virtualbox to look for, then when u load your vbox go to network and add a network drive, you should be able to guess what to do from there, look for VirtualBox and the folder you wanted to add

---

### Post by Therion on 2009-01-29
You'll need to set up a Shared Folder.  To do that you need to navigate to a folder on your Host machine that you want to share (e.g. /Home) and configure it as such.

Once it's "shared" in your VM, you go to your XP VM and look under Network Places and drill down to the shared folder (/Home or whatever folder you set up as shared in your VM).

See this pic for a visual guide:  [Picture!](http://3.bp.blogspot.com/_0X-TK87ZE0g/Ry32GaH-oWI/AAAAAAAAABM/Bnxk2fHFw2Q/s1600-h/Schermafdruk-XP+-+Settings-3.png)

---

### Post by gymophett on 2009-01-29
Thanks you all! :D

---

