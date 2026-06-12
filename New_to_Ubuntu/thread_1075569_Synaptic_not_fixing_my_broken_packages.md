---
title: "Synaptic not fixing my broken packages"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2009-02-20
Hi, I have broken packages on my system and Synaptic won't fix them. This is the error it is giving me:

> E: /var/cache/apt/archives/acroread-debian-files_0.0.24medibuntu1.1_i386.deb: trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu

How do I fix this please?

---

### Post by davideotape on 2009-02-20
Try ```
sudo apt-get autoclean
```

That might get rid of the broken packages.

---

### Post by cariboo on 2009-02-20
Go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages  and comepletely remove them. YOu can then reinstall the packages and all should be well.

Jim

---

### Post by Mega_Fauna on 2009-02-20
> **cariboo907 said:**
> Go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages  and comepletely remove them. YOu can then reinstall the packages and all should be well.

Jim

Thanks for your response.

Synaptic won't fix the packages, the error above is what it tells me when it fails to fix them.

---

### Post by Mega_Fauna on 2009-02-20
> **davideotape said:**
> Try ```
sudo apt-get autoclean
```

That might get rid of the broken packages.

Thanks for your response, but it the packages are still broken.

---

### Post by davideotape on 2009-02-20
Can you not manually select the packages in synaptic and re-install them?

---

### Post by Mega_Fauna on 2009-02-20
Hi,

Solved.

I searched by adobe and steadily removed all the hits I found one by one and it eventually ran smoothly again. Why the packages broke (it was adobe stuff I was installing) and why they unbroke, IDK.

Thanks all for the replies.

---

### Post by Mega_Fauna on 2009-02-20
> **davideotape said:**
> Can you not manually select the packages in synaptic and re-install them?

Weird, that didn't work, but the problem is somehow fixed now as I posted below, thanks for the responses though.

---

