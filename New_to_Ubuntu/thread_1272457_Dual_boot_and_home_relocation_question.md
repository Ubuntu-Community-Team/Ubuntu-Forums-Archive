---
title: "Dual boot and /home relocation question"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by msaint on 2009-09-22
I've been using 8.10 exclusively for a while now, and would like to upgrade. I'm planning on dual booting Windows XP and 9.04. I'd also like to relocate the /home directory to a different partition (or hard drive) than the Ubuntu install.

The XP install will only be for gaming and the occasional use of Adobe Illustrator, so I won't need a lot of space for that.

I have 2 500GB hard drives. The primary drive will be a 100GB/400GB split (XP/Ubuntu), and the secondary drive will be my /home directory. 

This install will be from scratch. What's the best way of going about this? Install XP first, then Ubuntu? Or the other way around?

Also, I've never relocated the /home directory before. Is there an option during the initial install to relocate the /home directory, or should this be done after installation?

Thank you!
Mike

---

### Post by scragar on 2009-09-22
XP first, less trouble, and you can choose manual during install and set up you dedicated home quite easily.

---

### Post by msaint on 2009-09-22
Wow, thank you for the lightning fast reply!:)

---

### Post by scragar on 2009-09-22
I was just coming to edit that, was eating when I posted that with one hand.

Windows first is easier because ubuntu sets up dualboots without much work, windows last would mean setting up grub again afterwards because windows will remove grub in favour of it's own bootloader that doesn't support linux.
As for the partitioning thing, I don't know what to say, it's rather easy
[http://welcometoubuntu.blogspot.com/2008/02/how-to-install-ubuntu-710-with-separate.html](http://welcometoubuntu.blogspot.com/2008/02/how-to-install-ubuntu-710-with-separate.html)
That guide is still mostly spot on, just read over it first to make sure you understand the basic idea, then try it. If it doesn't work you'll get a home folder on the main HD which can be moved to the second HD at a later time anyway.

---

### Post by mikeyphi on 2009-09-22
Partition the first drive as you have indicated, then install XP; then install Ubuntu. During the 'partition' phase of the Ubuntu install make sure you select the correct partitions for '/' for the OS and for '/home' for your personal files.

Not sure from your post whether you need to keep your current '/home' section....if yes, that is more problematic.
Two choices: first and better option, save all your files elsewhere then copy into your new /home partition; second and not to be tried lightly! look at this guide: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Good luck!!

---

### Post by bearsomg on 2009-09-22
> **msaint said:**
> I've been using 8.10 exclusively for a while now, and would like to upgrade. I'm planning on dual booting Windows XP and 9.04. I'd also like to relocate the /home directory to a different partition (or hard drive) than the Ubuntu install.

The XP install will only be for gaming and the occasional use of Adobe Illustrator, so I won't need a lot of space for that.

I have 2 500GB hard drives. The primary drive will be a 100GB/400GB split (XP/Ubuntu), and the secondary drive will be my /home directory. 

This install will be from scratch. What's the best way of going about this? Install XP first, then Ubuntu? Or the other way around?

Also, I've never relocated the /home directory before. Is there an option during the initial install to relocate the /home directory, or should this be done after installation?

Thank you!
Mike
Just install XP first, then install ubuntu on the second partition with the bootable CD and use the custom partitioner and put your /home directory on the hard drive you want it on. If it overwrote the windows bootloader, simply add the XP partition to the GRUB loader.

---

### Post by louieb on 2009-09-22
Just some food for thought. Separate your data completely from both OS. 
/home is the place user configuration files are kept. I give / (root) about 20GB and I do have a small /home - 5GB on laptop, 10GB on desktop.  Remainder of space on hard drives is for data. 

It a lot easier to plan and partition your drives in advance of installing any OS.  Windows does give you the option at install time to select its install partition. It just needs to be a primary partition with the boot flag set to on.

The Ubuntu installer is very flexible - choose manual - click on a partition - tell it where to mount it - repeat until you've selected all the partitions you want automatically mounted (including /home) when Ubuntu boots.

---

### Post by LewRockwell on 2009-09-22
> **louieb said:**
> It a lot easier to plan and partition your drives in advance of installing any OS.  **Windows does give you the option at install time to select its install partition.**

It should be pointed out that the majority of computer users buy machines with Windows pre-installed

The OEM recovery/re-installation disk(s) do not always give the option to install/re-install to an existing partition

What is much more common with these OEM Recovery/Re-Installation/Reset-To-Factory-Fresh disk(s) is that they demand and require usage of the complete hard drive and subsequently will reformat the drive

We highly recommend cloning the fresh windows install after all the updates are current(while the drive is still completely "windows")

Then do your incremental partition shrinking process(see posts/guides/tutorials for this very important procedure...Vista users use Vista Partitioner)

Once the partitioning is exactly the way you want it then make a fresh clone of the current windows partition(your previous clone of the whole drive will NOT fit into your new smaller partition)

Now...and this is pretty important if you value your time and sanity...the windows partition clone that you just created will allow you to "clone-back" your windows partition whenever you need to(so you won't need to go through the previous drawn-out process again)

Kewl!

.

---

