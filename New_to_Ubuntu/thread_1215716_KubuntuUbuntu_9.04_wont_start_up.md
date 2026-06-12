---
title: "Kubuntu/Ubuntu 9.04 wont start up"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Genesis3 on 2009-07-17
Ive been using Ubuntu since 9.04 was released. This morning I installed KDE to give it a try. I prefered to use GNOME so I removed KDE. Problem now is that when I start my system,on the start up screen instead of the Ubuntu logo being displayed with the progress bar its the Kubuntu logo. It performs a routine disk check. When it gets to 70% is freezes and goes to command line which tells me that the check has failed. It asked me if I wanted to perform the check manually. I said yes in hope that by using this I could at least get to my desktop to sort out this nonsense with KDE. But after doing the manual check the system simply restarts itself and goes back to the disk check again (with the Kubuntu logo on display) gets stuck at 70% and goes back to the command line repeating the same circle over and over again. Over the phone me and a friend tried to sort out this problem using the following commands
startx
 
 
[SIZE=2][SIZE=1]sudo /etc/init.d/gdm restart[/SIZE]

[/SIZE][SIZE=1]These commands however failed to work and in return a I got a long list of errors:confused:[/SIZE]

[SIZE=1]Anybody got any solutions. I am desperate for help as I've needed to borrow somebody elses laptop just to even get this message on he forums.[/SIZE]

[SIZE=1]Many Thanks[/SIZE]
[SIZE=1]Genesis3[/SIZE]

---

### Post by Tman5293 on 2009-07-17
Try this command: "sudo tune2fs -c 0 /dev/hda1"

This will make it so that it will never disk check. To set disk checks again change the zero to 42.

---

### Post by ugm6hr on 2009-07-17
Can you login from commandline?

If you enter Grub (press Escape at bootup), select the Recovery Mode.

Then login using your username and password at the Terminal prompt.

Then remove Kubuntu and reinstall Gnome as here:
[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

The failed disk check may be due to a hardware problem, so if this doesn't work, get a HD diagnostic CD to check.

---

### Post by Genesis3 on 2009-07-17
Just to let you guys know,the guide posted n the previous post was the one I followed to remove KDE.

---

### Post by Genesis3 on 2009-07-17
Ive tried your solutions but both have sdly failed. The computer hinks that hda1 doesent exist. When trying to start in recovery mode from the GRUB menu it simply does the disk check again and fails at 70%

---

### Post by ugm6hr on 2009-07-18
Have you tried a diagnostic check of the HD?

I suspect it has failed.

This might have something suitable: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Otherwise, try the HD manufacturers website.

---

### Post by Genesis3 on 2009-07-20
Thanks for all your help guys but Im going to do a clean and fresh install of Kubuntu to start my computer from scratch. Im assuming this will erase everything on my hard drive like Ubuntu did when I installed it.

---

