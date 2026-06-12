---
title: "Start Up Manager failed to hold XP as default OS after a kernel upgrade in Linux."
date: 2010-12-23
forum: New to Ubuntu
---

### Post by diablo75 on 2010-12-23
I have a laptop that, for the time being, I've set to boot into Windows by default via Grub.  I used Startup Manager (from Ubuntu Software Center) to make the change.  Then yesterday, I did an upgrade on Ubuntu which resulted in a new kernel being added to the list, but I shut the thing off and went to bed and didn't notice until today, when my mom turned it on, that it was now defaulting to the Ubuntu Memory Testing application.

I'm always hesitant when it comes to filing bug reports; every time I've bothered someone says something annoying like, "Oh, that's not a bug, that's a feature.  You need start all over."  So, I learned early on that what I call a bug and what others call a bug can be two completely different things, which is discouraging.  So I am asking you all:  Is this a bug?  It's got to be, in my opinion.  Why would you want your computer to boot a different item from the grub menu after a kernel upgrade if you've told it not to?

---

### Post by oldfred on 2010-12-23
I thought they adjusted the number to boot from when kernels were updated, but they must not.

This way is better as you use the name.

But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:

gedit /boot/grub/grub.cfg
find windows title and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by MooPi on 2010-12-23
Are you asking for help or conformation of a bug ? Can you edit your grub config ? Link with needed info [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

