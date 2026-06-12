---
title: "gedit - all remote files are read only!"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by beeltejuice on 2009-01-08
Hey -

I recently upgraded from 8.04 to 8.10 x64 - got to say it's nice.  I have a major issue, though - I opened up gedit and connected to the server at work thru sftp and all my files are opening as read only.  Permissions are correct.  I was able to edit them fine on Ubuntu 8.04.

I used gconf-editor to see if sftp saving was enabled and it was in the list so I don't think it's that. 

Anyone know what's up with this?

---

### Post by Tim Sharitt on 2009-01-08
Can you change files with any other applicaton on the server, or is it restricted to gedit?

---

### Post by beeltejuice on 2009-01-08
Its just gedit.  SSH thru terminal works fine.  I found some other ppl were having this problem.  It has to do with when the owner of the remote files is not the user that is logged in (i'm sftping as Root so wtf).

Some guys had better luck with gedit 2.22 -- i've downloaded the tar.gz file but how do i go about installing it?? lol i'm a nube

---

### Post by beeltejuice on 2009-01-08
[http://ubuntuforums.org/showthread.php?t=947189](http://ubuntuforums.org/showthread.php?t=947189)


ok

so i downloaded the tar.gz - then ran ./configure in the right directory and got this error:
checking for intltool >= 0.35.0... 0.37.0 found
checking for xgettext... no
checking for msgmerge... no
checking for msgfmt... no
configure: error: GNU gettext tools not found; required for intltool

man...i just need to edit files remotely.  isn't that why i'm using linux?

---

