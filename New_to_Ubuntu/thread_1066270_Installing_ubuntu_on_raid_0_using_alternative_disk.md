---
title: "Installing ubuntu on raid 0 using alternative disk"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by mrapoc on 2009-02-10
As title

It gets so far

Detects theres a raid and asks to enable it

Click yes, then it comes up asking what to do next

Logically i tried the one highlighted (partition disks)

At first it flashes up then goes straight back to that menu

Tried it a few more times..then it froze the install =/

ideas?

---

### Post by Felix-the-Cat on 2009-03-14
What you describe is strange but I have to say I have only done raid installs using the text based installer. All of them were successful. Nevertheless, to save you some time you cannot do an install on RAID0 alone. You must have a separate partition for your /boot directory it can either be a RAID1 or standard partition. GRUB can't boot to RAID0. So in the simplest setup you will have a non-RAID0 partition for /boot and a RAID0 partition for /

---

