---
title: "Windows + byebye grub"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by RobotAlligator on 2010-01-01
Installed 9.10 and then windows 7, got hit with the pretty standard grub disappearance.  I did some searching around, tried to set up grub but it wasn't installed, so I reinstalled grub to my linux partition

now whenever i boot grub loads but its command line grub; i dont know the names of my os's to command line.

i think i need menu.lst but i'm not entirely sure what to do

---

### Post by Sef on 2010-01-01
You have GRUB2, which does not have menu.lst.   Read [Ubuntu's GRUB2 wiki]("https://help.ubuntu.com/community/Grub2") for help.  If you do not understand what to do, then please post a message here.

---

### Post by phillw on 2010-01-01
Hi,

If your grub ran away after installing Win (which is usual), then pop over here to coax it back to where it should be :)

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Regards,

Phill.

---

### Post by robertsaron on 2010-01-01
When installing windows and linux, it is _*always*_ best to install windows first. Then install linux. Linux will automatically set up the dual boot. Windows will not.

The next best thing is to insert a live cd of linux (gnome or KDE) and then use that to fix grub. This has to be done from command line. This is similar to the fix MBR command that is done from the windows CD/DVD.

Doing a google.com/linux search with the search string "fix grub after installing windows" revealed how to fix this issue. I have fixed it many time myself.

Boot with a live cd that has grub. Issue this command:
sudo grub or just grub at command line

root (hd0,?) (? being where your controlling distro is installed)
setup (hd0)
quit

Then reboot, that is all there is to it.

---

### Post by Magnesium on 2010-01-01
RobotAlligator, since you have Grub2 (as Sef said), the easiest thing for you to do is to:
[LIST]
[*]Boot from your Ubuntu Live CD
[*]Open a terminal
[*]Execute "sudo update-grub" (no quotes)
[*]Reboot
[/LIST]

Then you should be good to go!:)

Mg

---

### Post by kansasnoob on 2010-01-01
> **RobotAlligator said:**
> Installed 9.10 and then windows 7, got hit with the pretty standard grub disappearance.  I did some searching around, tried to set up grub but it wasn't installed, so I reinstalled grub to my linux partition

now whenever i boot grub loads but its command line grub; i dont know the names of my os's to command line.

i think i need menu.lst but i'm not entirely sure what to do

Exactly how did you "install" grub?

---

