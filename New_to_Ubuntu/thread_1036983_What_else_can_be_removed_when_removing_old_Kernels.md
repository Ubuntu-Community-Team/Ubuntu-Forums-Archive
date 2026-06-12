---
title: "What else can be removed when removing old Kernels?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by RedMartin on 2009-01-11
Ubuntu 8.04 (32 bit)

I'm wanting to remove the old Linux-images from my drive. 

Can I also delete the linux headers for each kernel release as well as the restricted-modules for each release?

Is there anything else that would be made redundant and suitable for deletion?

---

### Post by mc4100 on 2009-01-11
> **RedMartin said:**
> Ubuntu 8.04 (32 bit)

I'm wanting to remove the old Linux-images from my drive. 

Can I also delete the linux headers for each kernel release as well as the restricted-modules for each release?

Is there anything else that would be made redundant and suitable for deletion?
It's good practice to keep at least two kernels around (and thus the headers, etc,) in case problems arise later on, but if you've successfully booted into a newly-installed kernel and want to free space by removing some older ones, then you can remove those older images and the corresponding headers and res modules. Note that you should be sure you're not removing the "generic" meta-packages which will provide you with the latest headers and modules.

---

### Post by RedMartin on 2009-01-11
> **mc4100 said:**
> Note that you should be sure you're not removing the "generic" meta-packages which will provide you with the latest headers and modules.

Would you mind expanding on that, please?

---

### Post by mc4100 on 2009-01-11
> **RedMartin said:**
> Would you mind expanding on that, please?

It's relatively simple, there are so-called meta-packages, for example:
[list][*]linux-image-generic[/list]
> This package will always depend on the latest generic
kernel image available.
[list][*]linux-restricted-modules-generic[/list]
> This package will always depend on the latest restricted modules available
for generic kernels.

You need these metapackages to make sure updates can work correctly, since the names of the actual images are different, e.g., linux-image-**2.6.27-x**-generic (and this makes it easier to see/manage the images, and allows many versions to be installed at the same time).
Perhaps it is easier to say it like this: the ones with version numbers are the actual images, and in order for this to be possible, another package (which is number-less) is present so that when this number-less package is updated, it then *depends* on a new package, the newer kernel -- meaning **that** will be installed.

---

### Post by RedMartin on 2009-01-11
Ah! 

If it ends with just 'generic' it's a keeper. If it ends '2.6.24-23-generic' it can go.

Correct?

---

### Post by RedMartin on 2009-01-11
Right, I've removed all but the two most recent linux-images. They in turn removed the restricted-modules.

I'm left with linux-headers. Can they be dumped too. I'm a tad concerned as 'generic' version of these appears not to be installed. They are all numbered versions.

---

