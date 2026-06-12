---
title: "Startup-Manager seems to be editing the wrong grub menu list"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by diablo75 on 2011-05-02
After the upgrade the appearance of my grub menu changed to in that several old kernal versions were removed from the system and the screen resolution was increased for a sharper look.  It also changed the default option I'd like to have, which used to be Windows.

I've used the program "Startup-Manager" to do this in the past but when I run startup manager is acts as if Windows is the default already and shows it listed among a bunch of old kernel versions that are no longer present on the system.  Moving these options around and rebooting doesn't have any affect on grub at all and I can't seem to get Startup-Manager to edit the correct config file, even after purgeing it and reinstalling it with Synaptic.

Perhaps someone knows how to fix this or knows of another startup manager program I could use to change my default grub settings.  I also have some entries I'd like to remove.

---

### Post by oldfred on 2011-05-02
I was trying to help this user and suggested startup manager amoung my usual many suggestions and it seemed to add a menu.lst as if it was using grub legacy.

[http://ubuntuforums.org/showthread.php?t=1744705&highlight=startup](http://ubuntuforums.org/showthread.php?t=1744705&highlight=startup)

drs305 came in and suggested some fixes and for now I would just directly edit the grub file. You can use a number or the exact text description for grub default:

find your windows entry in this and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

