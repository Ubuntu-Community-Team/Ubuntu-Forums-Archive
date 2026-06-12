---
title: "Transmission permissions"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by lapis72 on 2009-09-15
Hi all, I'm a Ubuntu newbie . Been using for a few months. Here is where im at . Transmission works just fine off my" live" cd . But when im trying to use it normally i get permission denied errors on torrents. i understand that transmission is probably trying to download to a location that it doesn't have permission for , but I dont know how to fix it?? I tried removing transmission completly and reinstalling it. But same problem?:confused:

---

### Post by Geoff918 on 2009-09-15
In your transmission program where does it state that your downloads will be saved? If it's on the desktop (which it may default to--I don't use that client often, I don't remember changing anything) it should be fine--insofar as it's your desktop that it wants to save to and not another user you have set up on the system.

You could try the old:

sudo aptitude remove transmission
sudo aptitude purge transmission
sudo aptitude install transmission

to completely uninstall any custom settings and reset the whole install.

Or, there are other torrent programs out there. I believe I've used Monsoon before, maybe? Unsure if that was on an earlier version of Ubuntu or openSUSE where I used that, but I'm pretty sure I have.

---

### Post by k33bz on 2009-09-15
Find out where Transmission is trying to save your files. If you can not do so, try what Geoff918 told you to do. This will completely remove all transmission files as well as configuration files for it. 

I dont use transmission, I do use Deluge. It has worked perfectly for me.

---

### Post by lapis72 on 2009-09-15
Thanks for replies, used sudo to remove,purge and install. opened up transmission an dan old torrent was still listed? and attemped to download new torrent and just sits there idle? destination folder is desktop. :confused:

---

### Post by lapis72 on 2009-09-15
oh forgot can you use deluge with gnome?

---

### Post by wojox on 2009-09-15
Yes see this thread:

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=7956004](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=7956004)

Your still having problems with transmission because you need to delete any files/folders from your user directory.

~/.config/transmission

---

### Post by k33bz on 2009-09-15
> **lapis72 said:**
> oh forgot can you use deluge with gnome?

Runs perfect on my system. Some KDE programs work wonderful on gnome as well as KDE. Deluge, Kget, and K9kopy I use on gnome.

---

### Post by lapis72 on 2009-09-15
thanks guys , seems to be working now.

---

### Post by prabath_fun on 2009-09-18
Hi,
   Can anyboby tell, how to get search bar worked in transmission. I typed kubuntu in search box available. No result out. Please someone help me.
Prabath

---

### Post by Charles Kerr on 2009-09-22
> **prabath_fun said:**
> Hi,
   Can anyboby tell, how to get search bar worked in transmission. I typed kubuntu in search box available. No result out. Please someone help me.
Prabath
The text entry field in Transmission is for filtering your existing torrents, not for finding new ones.  Transmission doesn't have a torrent search feature...

---

### Post by prabath_fun on 2009-09-24
Hi Charles Kerr,
   Thanks for your information.
Prabath

---

### Post by 3rdalbum on 2009-09-24
> **lapis72 said:**
> Thanks for replies, used sudo to remove,purge and install. opened up transmission an dan old torrent was still listed?

Removing a program does not remove its per-user settings file, which is stored in a hidden folder in your home directory.

Program executables don't usually get corrupted, because only root can write to them, and they almost never get written to. If you're having unexpected trouble with a program that worked before, then you should try removing the per-user settings file in your home directory FIRST. If you just reinstall the program, chances are that you are replacing a clean copy with a clean copy.

---

