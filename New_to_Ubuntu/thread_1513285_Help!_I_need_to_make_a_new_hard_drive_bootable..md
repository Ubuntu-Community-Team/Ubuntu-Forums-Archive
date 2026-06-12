---
title: "Help! I need to make a new hard drive bootable."
date: 2010-06-19
forum: New to Ubuntu
---

### Post by Old Newville on 2010-06-19
My sad story: I bought a new hard drive and installed Ubuntu 10.04 LTS. Works great. Just one little problem... It worked so well that I decided to erase the old hard drive, where I just learned all the boot info apparently was stored. My machine does not boot. I got it up and running with a Live CD.

My old drive contained Windows XP and Ubuntu 8.04 LTS in a dual-boot set-up. When I added the new drive and loaded 10.04, it went to triple boot.

So, how do I make the new hard drive bootable by itself?

I just installed GRUB from the Live CD's terminal, but I'm not familiar enough with it to know what I'm doing.

---

### Post by freddiespagheti on 2010-06-19
So this is an internal hard drive I take it? And you want to use it as your only hard drive and you want it to contain just 10.04?

It's been a little while since I've tinkered with hard drives but it's possible that there's a kind of switch you need to set in order to make it boot able. Do you know what type it is? (IDE, or SATA?)

---

### Post by Old Newville on 2010-06-19
I want the new drive to be the only drive (it replaces the original) running Lucid Lynx exclusively.

Its a Seagate SATA drive; my box is a Dell Dimension 4600. The Dell bios screen comes up, and then, instead of getting the menu list of boot options, I get a black screen and a message telling me to hit F1 or F2.

My files have all been migrated to the new drive. Its ready to go, except for this, uh, minor problem. (I transfered Windows files to a VirtualBox install.)

Thanks for your reply.

---

### Post by freddiespagheti on 2010-06-19
I'm not sure what the best fix is because it's difficult to know how the install occurred the first time. It sounds like GRUB (the Linux boot loader) was installed to the old hard drive. Make sure the new drive is the only one in the computer and then boot from cd and install grub.  

EDIT: I posted the wrong link. Use the one in yetiman's post

That should fix your problems. If it doesn't. You could try backing up your data to a different place and putting only the new drive in the computer. Then reinstall Ubuntu.

Tell me how it goes.

---

### Post by yetiman64 on 2010-06-19
> **freddiespagheti said:**
> I'm not sure what the best fix is because it's difficult to know how the install occurred the first time. It sounds like GRUB (the Linux boot loader) was installed to the old hard drive. Make sure the new drive is the only one in the computer and then boot from cd and install grub.  

[]("http://ubuntuforums.org/showthread.php?t=224351")<link removed see post #6>

That should fix your problems. If it doesn't. You could try backing up your data to a different place and putting only the new drive in the computer. Then reinstall Ubuntu.

Tell me how it goes.

The instructions in that link are for grub legacy (and from 2006 btw), whereas Lucid uses grub2, very different instructions required. Hold on, as they won't work.

Edit: check this link section 13 from the grub2 guide [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by freddiespagheti on 2010-06-19
Woops, my mistake. I'll remove the link to avoid confusion.

---

### Post by larryfroot on 2010-06-19
I had a horrid time with the same problem. I don't know how old your machine is, but older bios fail to recognise a hard drive if its over a given size...I think its either 40 or 80 gig.

I had to go into a live session, go to gparted and right at the beginning of the drive create a small partition, a gig or two is plenty and set its flag to boot. The rest of the drive I left as unformatted space and put the standard install onto that, leaving the /boot partition alone.

Basically this ruse fools the bios into thinking you have a small drive when you start your machine, therefore it recognises the drive and all is well. 

I hope you get a solution soon because it is a very frustrating one.

---

### Post by oldfred on 2010-06-19
The link posted will work, but here are links dealing directly with reinstalling grub or grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

From a liveCD:

Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

If you have grub in your old hard drive, but were able to boot the new one you should not have any issues with BIOS size limits. You may have some minor issues with it getting redefined as sda instead of sdb, so I would run this after you boot:
sudo dpkg-reconfigure grub-pc

---

### Post by Old Newville on 2010-06-19
I've marked this as solved. The link to GRUB 2 instructions posted by yetiman64 is the correct link, and those instructions worked. I can now boot from my new drive. 

Also, it took one other step -- I went into the Dell bios setup (F2 key on start-up) and changed the primary drive. I tabbed to primary sata drive and changed the setting from "auto" to "off." The box then booted up just fine.

Just one final, relatively minor, question. Grub still shows me about a dozen boot options, ranging from the various previous upgrades of Lucid to the now non-existent Ubuntu 8.04 and Windows XP. How do I remove them from the list?

---

### Post by yetiman64 on 2010-06-19
> **Old Newville said:**
> I've marked this as solved. The link to GRUB 2 instructions posted by yetiman64 is the correct link, and those instructions worked. I can now boot from my new drive. 

Also, it took one other step -- I went into the Dell bios setup (F2 key on start-up) and changed the primary drive. I tabbed to primary sata drive and changed the setting from "auto" to "off." The box then booted up just fine.

Just one final, relatively minor, question. Grub still shows me about a dozen boot options, ranging from the various previous upgrades of Lucid to the now non-existent Ubuntu 8.04 and Windows XP. How do I remove them from the list?

If the old drive is removed, then in terminal in lucid run,
```
sudo update-grub
```

---

