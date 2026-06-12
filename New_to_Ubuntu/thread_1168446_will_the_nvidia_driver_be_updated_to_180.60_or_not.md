---
title: "will the nvidia driver be updated to 180.60 or not?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by freak42 on 2009-05-24
Hi

simple question but I am still not sure:
Will the proprietary nvidia gpu driver (which is currently at version 180.44 on Jaunty) be automatically updated through the repositories to version 180.60, or will this not happen until 9.10?

tia

---

### Post by freak42 on 2009-05-24
bump

anyone?

---

### Post by Tibuda on 2009-05-24
> **freak42 said:**
> Hi

simple question but I am still not sure:
Will the proprietary nvidia gpu driver (which is currently at version 180.44 on Jaunty) be automatically updated through the repositories to version 180.60, or will this not happen until 9.10?

tia

Unless it is a security fix, no.

---

### Post by cwsnyder on 2009-05-24
This is one of the drivers which would not be automatically suggested as an update because nVidia driver updates may break your installation by no longer supporting your video card.

If you want to take a chance, you can always update to Karmic, then wait for the system crashes.

---

### Post by AaronP_ on 2009-05-26
> **cwsnyder said:**
> This is one of the drivers which would not be automatically suggested as an update because nVidia driver updates may break your installation by no longer supporting your video card.
We don't drop support for GPUs in the middle of a release series.

---

### Post by Paqman on 2009-05-26
Any updates that did happen would go into the backports repo, so make sure you've got that enabled. Having said that, unless 180.60 fixes some serious bugs you probably won't see it until Karmic is released later this year. In fact by then you might be in line for an even newer driver.

---

### Post by taavikko on 2009-05-26
> **AaronP_ said:**
> We don't drop support for GPUs in the middle of a release series.

AaronP, might be wise to mention somehow that you're employed by nvidia.
signature maybe. Just for clarification :)

---

### Post by mcduck on 2009-05-26
If you want up-to-date graphics cards drivers you might want to use the X updates-PPA repository: [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/")

This kind of stuff is not likely to be updated in normal repositories, or even in backports.

---

