---
title: "Trying to install Ubuntu 10.10 and not working"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Radley90 on 2010-10-13
Hi all,

I've decided to install Linux on my machine yesterday for the very first time since it was suggested to me by a friend. I decided to use Ubuntu because it seemed like the easiest transition from Windows. After installation however, I ran into several problems. The very first thing I tried was to get Pidgin, but I couldn't install it due to dependency errors. I had my friend who's been using Linux for quite a while to look at it and it seemed like GTK+, ATK (didn't make much sense to me), and a whole variety of dependencies were not installed. When we tried to install all these dependencies many of them failed. I tried to get pidgin from the Ubuntu CD but it was trying to pull Pidgin from /cdrom instead of /media where the CD was mounted and we couldn't figure out how to revert it.

I'm starting to suspect that Ubuntu might not have installed properly on my system since I did receive an error after I finished installing. I'm trying to run it on Dual-boot with Windows 7. Windows 7 seemed to have already created 2 primary partitions, so I installed /, /home, and swap all on logical partitions. I'm not sure if that was the correct way of formatting those partitions. It should also be noted that my motherboard is an Intel dx38bt in which I have BIOS RAID 0 configured for 2 hard drives. I'm not sure if that could be causing the problem. I went to read the Fake raid howto on the ubuntu help page but ended up being confused when it started talking about Gpart and dmraid.

I would greatly appreciate it if someone could help with this issue.

Thanks

---

### Post by dr_kabuto on 2010-10-13
How have you tried to install Pidgin?
The easiest way is launching Ubuntu Software Center, search for Pidgin and it will install it along its dependencies. There's no need to install anything from the CD.

---

### Post by Radley90 on 2010-10-13
The first thing I tried was to download Pidgin through the software center. It gave me a dependency error "Pidgin|Finch" which didn't make much sense. So I went online and downloaded the PPA for Pidgin. But installing that required the Ubuntu CD.

---

### Post by scottiw2000 on 2010-10-16
If I were you the first thing I would install on Ubuntu is "Ubuntu Tweak" ([http://ubuntu-tweak.com/]("http://ubuntu-tweak.com")). It gives you a nice easy interface for doing a lot of maintenance tasks. Among other things, Ubuntu Tweak has a nice "Source Centre" that lets you activate a lot of commonly-used PPA repositories all at once. 

If you're running into problems with dependencies, the other thing to check is which of the basic repositories you have activated. Open up the Software Centre and under the "Edit" menu (of the menu at the top of the window) choose "Software Sources." You'll get a new window with several tabs listing the software sources you can enable. The first tab "Ubuntu Software" includes several extra repositories that are not enabled by default on a new installation but are needed for a lot of the software people usually use (They're not active be default because they don't adhere strictly to the "free" standards that some Ubuntu users want). Check all of the boxes on that tab to activate those extra repositories, then update your software information (either run update-manager or in a terminal type "sudo apt-get update" (without the quotes)). After updating you can try your installations again and may have better luck!

Ubuntu can still be a bit disorienting at first (though that's improving all the time), and there are always occasional bugs that require some digging around on the forums. But my experience has been that overall the usability is at least as good as Windows 7 (which I also installed and maintain on my wife's computer). So don't let the initial snags put you off!

---

### Post by kapi on 2010-10-16
Not sure if it helps but when ever I do a clean install and I did mine yesterday to install 10.10, I always ensure that the dvd I burned the iso to is burned at the slowest possible speed. I did try and locate a checksum key to verify the dvd but couldn't find any reference. 

Maybe a fresh install would be worth consideration, it only takes half an hour and might sort a few of your problems.

---

### Post by Quackers on 2010-10-16
Have you installed Ubuntu to a raid 0 array which was already set in the bios? Or could it have been a raid 1 array? Or is ubuntu on a separate disc from the raid array?

---

