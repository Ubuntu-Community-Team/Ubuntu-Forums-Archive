---
title: "Permission denied trying to link External HD to mpd"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by snapback77 on 2011-02-27
I am trying to make a symbolic link in GNOME holding the Ctrl+Shift Keys while dragging my MUSIC directory to my var/lib/mpd file and I get the following window saying:
Error while copying "Link to MUSIC".  there was and error copying the file into /var/lib/mpd
Error making symbolic link: Permission denied.
What gives?  How do I get MPD data base to link with my external HD where all my music files are?
All I need is permission?
Thanks.

---

### Post by cchhrriiss121212 on 2011-02-27
You could use:
```
sudo nautilus
```
to drag and drop the link.

But I would rather edit the mdp.conf file to set the chosen directory. You should find it in your home folder after pressing ctrl+h to display hidden files.

---

### Post by snapback77 on 2011-02-27
Thanks for your response.  I tried sudo nautilus and was able to move the MUSIC directory from the external Seagate Expansion Drive to mpd but it did not work and I lost the files in my Home Folder Music
I may have to reinstall MPD. 
MPD and Sonata up and running again. I still have to move all my music from my Seagate External Hard drive to my Music folder which is a drag. Is there a problem the HD being formatted for Windows? The name of the HD is Expansion Drive. When I try to symlick it tells me no such file as 'Expansion'

---

