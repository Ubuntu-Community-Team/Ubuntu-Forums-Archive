---
title: "Bypassing grub errors (Error 2 and Error 17)"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by droenn on 2009-04-28
I'm a fairly new user of Ubuntu and I've ran into a few problems resulting in errors through grub when I reboot, such as Error 2 and Error 17. I couldn't really find any approachable guides to help me get out of the situation I was in, so I decided to search around and make my own and hopefully others will find use out of it. Anyways lets get started.

First and foremost you'll need a LiveCD handy, I have done this a few times now on 9.04 Jaunty. Boot from the LiveCD and open a terminal located in Applications -> Accessories -> Terminal.

Once the terminal is open run the following.

> sudo bash
> sudo mount -f /dev/sda1 /mnt
> fsck -y /dev/sda1

You'll see fsck ansering "Yes" to alot of things. This is normal and was done because of the -y option. You will want to run that command a second time or even more than that until you get a "clean run". For it to be a clean install that means that you shouldn't see any "Yes" anywhere in that run, otherwise fsck had to fix something and you'll want to run it again. All fsck is doing is making sure the disk is intact.

Now this is the more important stuff, which entails fixing the grub.

> sudo grub-install /dev/sda1 --root-directory=/mnt --recheck

At the end of that command it will ask you to make sure the /mnt/boot/grub/device.map was modified by it's operation. Run the following and compare the two, these need to be exactly the same.

> cat /mnt/boot/grub/device.map

Once you've completed all of that you can close out of the terminal and reboot your system to hard disk. You should come up smoothly now.

If you have any problems hopefully I will be able to provide some answers, but like I said before I am some what new to Ubuntu. If I don't have the answers, I'm sure someone in tis great community will be able to provide some answers or even provide a better alternative.

Let me know if this works out for you, as this as worked for me multiple times.

~droenn

---

### Post by talsemgeest on 2009-04-29
Very nice droenn, thanks for helping out the community. :)

---

