---
title: "the most basic question ever?!"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by struyk on 2006-10-27
Hi all - first post for me!
I have a really simple question and would appreciate some help.
I am having to perform the IT admin role at my company without any formal training.  I know my stuff in the PC and Mac world but have only ever tinkered with Linux as a user.

I am wanting to set up a Ubuntu(or Kubuntu) box to handle file and/or printer sharing for the few users we have.  I am currently using one of those network storage devices and backing it up daily onto a removable drive.  All the laptops are running XP.

My question is this.  Is it relatively easy to set up Ubuntu to handle file sharing and allow VPN access to the files from remote users running XP? I would also like to use the Ubuntu to possibly back the existing hard drive (which I would like to remove it's current home and mount permanently in the same box as Ubuntu) in a redundancy (ala RAID) setup.

Can anyone offer any advise?  Would Kubuntu be better or worse than Ubuntu?

---

### Post by PriceChild on 2006-10-27
Ubuntu and Kubuntu are just the same base, just different environments to interact with the system.

For sharing files, samba.
cups will share your printers.
You can allow VPN access.

I'm sure you could start cron jobs to periodically backup files/folders.

---

