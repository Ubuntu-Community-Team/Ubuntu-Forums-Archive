---
title: "Upgrade from 7.04 to 8.10, How?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Pal369 on 2009-01-17
Greetings, I have Ubuntu 7.04 installed and running, when I go to Update Mgr it wants to update to 7.10, downloads a bunch of files and then gives me an error message ans can't continue.  But I did download the latest and greatest, 8.10 have it on a disk, how can i install 8.10? Tried to boot from the disk for a install, but it just did not happen. 

What can I do to install 8.10?

Thank you

---

### Post by mikewhatever on 2009-01-17
You can't upgrade 7.04 to 8.10 directly, the only way to make a move is to backup your files and reinstall.

---

### Post by Pal369 on 2009-01-17
Thank you, OK, there are'nt any files that I need, do I need to format the drive? What's the best way to do that?

Or is there information on this forum to help me.

Thank you

---

### Post by mikewhatever on 2009-01-17
Yes you do, and the installer of 8.10 is very similar to that of 7.04. Not sure what info you'd like, ask if there is something specific. Here is an installation guide [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall).

---

### Post by Hendrixski on 2009-01-17
Yeah, normally if you want to upgrade to a newer version you have to do it in order.  If for some odd reason it breaks on one of the versions in-between... umm. Yeah.

If you have a separate /home partition then you only have to re-install the / partition and then mount /home later on.   I know a lot of people do that, that way they have a few different distributions installed, but share all the same files between them.

You should have regular backups of all your files anyways... and you should do a backup before an upgrade.

---

### Post by ibutho on 2009-01-17
You can upgrade manually if you wish. Edit /etc/apt/sources.list and change all instances of "feisty" to "hardy". Logout of GNOME and at the login manager screen do
[LIST=1]
[*]CTRL-ALT-F1
[*]sudo /etc/init.d/gdm stop
[*]sudo apt-get update
[*]sudo apt-get dist-upgrade
[*]sudo reboot
[/LIST]

---

### Post by Pal369 on 2009-01-17
Thank you all for the advice and help.

---

