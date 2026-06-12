---
title: "Seeking advice regarding multibooting."
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Miscible21 on 2010-05-02
Hello everyone

Got my hands on 10.04 on the release date and I'm so eager to install it. However, I want to get all my ducks in a row before I do the install.

I have 2 hard drives in my machine. Recently i reformatted one of them and did a fresh install of XP, and also installed Open SUSE 11.2. I let Open SUSE automatically configure the partitions as i wasn't familiar with it's installer. Everything worked out okay and I have been successfully dual booting with SUSE and XP for at least a month. 

On the other hard drive i still have Ubuntu 9.04. This drive not only holds the operating system but all of my data. I set my BIOS to boot from my SUSE/XP hard drive so that i can avoid any complications with GRUB (This is because i dont really know how to configure GRUB). So effectively my 9.04 hard drive is not really in use. I only boot into it when i need a file or document.

My plan is to install 10.04 on my SUSE/XP hard drive, thereby making it a multiboot system, and then move the remainder of my data from the 9.04 drive onto it. Once that's done I want to format the 9.04 drive, and send all my data back to it and use it exclusively for storage.

So that's the plan. I just don't know what to expect during the install. If i install and mess up the boot loader up for SUSE I wont be able to get into any operating system. I would prefer not to let that happen. I need to access all three. Windows for some of my proprietary programs and open source software that I've already downloaded, SUSE for it's flawless use of my poorly supported desktop modem, and Ubuntu 10.04 because thats my Operating system of choice.

I would greatly appreciate any advice. Thank you in advance!

---

### Post by sixthwheel on 2010-05-02
Do a thorough search in these forums about dual booting with Lucid.
There seems to be a lot of unresolved issues with Grub.

---

### Post by oldfred on 2010-05-03
I prefer to have at least one operating system on every drive so that if a drive fails I can quickly switch and boot the other drive. With my install of Karmic I moved all data & /home out of root and now root is only 5-6GB. I now have 3 versions of Ubuntu with previous install, so I can go back and find an old setting if need be, current install, and beta just for testing. All data is linked in and since I am running the same version I can use the same home (although when I fully convert to Lucid I may just copy all the /home  data into a new partition as it is only 1-2GB with all data in the data partition)

The issue you will have is that every system wants to install its boot loader. On Lucid screen 8 'Ready to Install' is an advanced button which gives you the choice of where to install grub. You can elect not to install it if you know/can add the boot stanza to your existing boot. Or you can install grub to the Lucid partition. They do not recommend that as it uses blocklists and if some files get moved, booting may break. ( you would have to reinstall grub). If installed to the partition you can easily chainboot into Ubuntu with just a couple of chainboot commands in your current boot loader.

Another thought:
Since you have another MBR you still can install grub to it and chainboot to that from your present boot loader.

Grub2 entry
menuentry "Chainload Other System on sdb" {
set root=(hd1)
chainloader +1
}

---

