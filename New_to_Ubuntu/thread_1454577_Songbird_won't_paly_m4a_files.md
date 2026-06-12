---
title: "Songbird won't paly m4a files"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by theweasel2345 on 2010-04-14
I'm using Songbird 1.4.3 with everything gstream installed like the ugly files.

---

### Post by theweasel2345 on 2010-04-14
Rhythmbox Music Player can play the files not songbird

---

### Post by cahlfors on 2010-07-04
There are so far as I know two ways:

1. make a script - 
add this into the file:
#!/bin/sh
export SB_GST_SYSTEM=1
/usr/share/Songbird/songbird

OR

2. remove the libgst* files -
The libgst* files are in /usr/share/Songbird/lib
remove them

I did the latter (remove libgst* files) but its your choice.
This is all assuming that Songbird is installed in /usr/share/Songbird as I did.
You could have it different, so you would have to do it according to your Songbird directory location.

Hope that helped.

Carl-Eric

---

### Post by mprice on 2010-07-05
Do you have "faac" installed? If not try installing that and see if it works?

---

