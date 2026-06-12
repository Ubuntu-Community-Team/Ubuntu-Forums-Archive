---
title: "Increasing the swap space"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by newbie01.linux on 2010-06-24
Hi all,

Am very new to Linux. I've installed Ubuntu10 using Virtualbox. The swap space created by the install is 400MB on /dev/sda5 which I believe is the default.

I want to increase the allocated swap space by extending /dev/sda5 instead of adding a new swap file. Can any one advise if this is possible?

I've seen a similar post where it is recommended to boot from a GParted LiveCD. Unfortunately that is not possible on a Virtualbox disk file, is it or am I wrong to make that assumption?

This post is just to sort of "experiment" on whether increasing a swap file is possible via extending the filesystem as opposed to creating a new swap file  ... :confused:

Or can I remove and add the /dev/sda5 swap?

Any response will be very much appreciated. Thanks in advance.

BTW, am using Virtualbox with the purpose of having a portable Ubuntu.

---

### Post by M!K3_$ on 2010-06-24
hmm. logically seems fine. give a shot...

plus because you're using virtualbox just take a snapshot before you do it.

---

### Post by sikander3786 on 2010-06-24
Hi.

You can boot of the live cd in virtual box. That is not something impossible. Just configure the bios of the virtual box to boot from the cd. And allow access from virtual box to the cd-rom drives on your system.

Otherwise install gparted in your ubuntu install

```

sudo apt-get install gparted

```

And then run

```

gksu gparted

```

Then you should be able to shrink and format the partitions and change their flags.

HTH.

---

### Post by M!K3_$ on 2010-06-24
> **sikander3786 said:**
> Hi.

You can boot of the live cd in virtual box. That is not something impossible. Just configure the bios of the virtual box to boot from the cd. And allow access from virtual box to the cd-rom drives on your system

He has already done this. He just wants to know if he can change the size of his swap partition.

---

### Post by sikander3786 on 2010-06-24
> **M!K3_$ said:**
> He has already done this. He just wants to know if he can change the size of his swap partition.

Sorry. I misread his post.

---

