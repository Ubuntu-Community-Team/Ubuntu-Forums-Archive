---
title: "cant locate ntfs partitions in xubuntu"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by thedoommaker on 2009-08-07
well I can't locate ntfs partitions in Xubuntu
i thought they would be in the media folder 
and I would just need to mount them manually 
but they aren't there
I have a 40gb harddisk on my laptop
10GB for XP, 3GB for Xubuntu, 2GB swap area
all I can see in media is cdrom and cdrom0
Xubuntu automounts CDs but why doesn't it recognize ntfs drives
any reccomendations appreciated

---

### Post by synapsys on 2009-08-07
Have you checked the 'Places' menu on the top panel of the desktop?

---

### Post by thedoommaker on 2009-08-08
> **synapsys said:**
> Have you checked the 'Places' menu on the top panel of the desktop?

yes I did
what I can see in Places menu is 
<my folder>
trash
desktop
file system
----------------
documents
download
music
pictures videos

Ubuntu and Kubuntu live CDs detect my ntfs drives
they are present in Places menu but Xubuntu ignores them 
I installed Ubuntu and no problem now, I'll install Xubuntu desktop over it
but I still wonder what the reason could be

---

### Post by synapsys on 2009-08-09
Check if you have ntfs-3g installed. If not, install it, that may be your problem.

---

### Post by thedoommaker on 2009-08-10
@synapsys thank you for your help
ntfs-3g was installed 
so i downloaded another package called ntfs configuration tool
with just a few clicks ntfs drives were successfully mounted on /media
switched back to xubuntu, my old laptop is now happier

---

### Post by synapsys on 2009-08-10
Mmm clicky gui goodness. If you are having trouble with a particular filesystem, it's usually a good idea to open up your favorite package manager and search for it. Say you're having problems with a hfs+ partition, search your package manager for hfs and you will probably be able to figure it out.

---

