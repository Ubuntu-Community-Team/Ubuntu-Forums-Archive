---
title: "Ooopppsss!!! I blew up the OS"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-05-22
Trying to upgrade Evolution, I followed the instructions at:

[http://www.omgubuntu.co.uk/2011/05/evolution-3-now-available-for-ubuntu-11-04-gnome-3-users/](http://www.omgubuntu.co.uk/2011/05/evolution-3-now-available-for-ubuntu-11-04-gnome-3-users/)

but did not understand that I first had to upgrade to Gnome3 or "Gnome 3". Using - gnome 3 - as keyword terms for a search is a mistake. Anyway, I next tried to upgrade my Gnome to Gnome 3, I added the ppa: and tried several times to get it all to work, but it's a goner. Note to others: this is the first time that the install order of Linux software has made a difference.

So, I need to backup my /home and while I have an external usb disk for this, it's formatted NTSF. So, before I really do some harm, I'm asking if I can run Natty via LiveCD and use Deja-Dup to back up the /home to an NTFS formatted drive? And, once the backup is on the external hard drive, can it be 'restored' to a clean install of Natty. I have the .iso of Natty.

Also, I don't want to lose the emails (if that is still possible) so what part of the / -other than /home- needs backup to allow the re-installed OS and Evol to find my emails?

Also, if anyone knows how to run the checksum for my natty-desktop-i386.iso under Windows please let me know how to do that. I have the hash, but is there a way to do this?

---

### Post by jtarin on 2011-05-22
Yes you can backup and return our files to and from an NTFS formatted drive with no problem....I do it weekly.

---

### Post by sanderd17 on 2011-05-22
every program (except maybe root-only programs like gparted) keeps its settings in a subdirectory of your home directory, mostly it's an invisible directory. You can get it in nautilus by pressing CTRL+H.

But if you copy your entire /home, your mails will be copied with them.

---

### Post by audiomick on 2011-05-22
> **Mark_in_Hollywood said:**
> 
Also, if anyone knows how to run the checksum for my natty-desktop-i386.iso under Windows please let me know how to do that. I have the hash, but is there a way to do this?

md5sum instructions here. Windows is a fair way down the page.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Your mails are in a folder called 

```
.evolution
```If you save that, then put it back in the new install before starting evolution, you should find all your stuff. This is a hidden folder, as can be seen from the point at the start of the name. To see these folders, choose "show hidden folders" from the view menu, or use ctrl + h. This also applies if you are viewing your old home folder from a Live CD


If you have to re-install, you might consider creating a seperate /home partition. That way, the next time you do something like this  ( ;) ) , you will be able to just re-mount your /home and carry on. Here is a some info:

[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

edit: that link is lousy, I just realised. Look here, perhaps:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Mark_in_Hollywood on 2011-05-22
If you have to re-install, you might consider creating a seperate /home partition. That way, the next time you do something like this  ( ;) ) ,

edit: that link is lousy, I just realised. Look here, perhaps:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)[/QUOTE]

I have my /home on it's own partition! What do you mean? I can re-install / and it's associated dir & sub-dirs and it will work?

PS ( ;) ) , - sorry no internet speak here, pls. explain is significant.

---

### Post by audiomick on 2011-05-22
> **Mark_in_Hollywood said:**
> ...

I have my /home on it's own partition! ....

If this is the case, when you do a re-install, you can re-mount the old home in the new install and everything will be in place.

You have to go into the "manual" option when the installer gets to the partitioning stage. Choose the mount point /home for you old home partition, do not format it.

As long as the damage done is not to files that are somewhere in /home, you should then be back where you where before the problems started.

---

