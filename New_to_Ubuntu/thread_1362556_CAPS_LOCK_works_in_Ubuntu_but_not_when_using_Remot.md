---
title: "CAPS LOCK works in Ubuntu but not when using Remote Desktop"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by hankyknot on 2009-12-23
After upgrading our Windows server to Server 2008 our Puppy Linux clients could no longer connect. A perfect opportunity to switch to Ubuntu I thought.

Installation was a breeze and everything worked fine, we could connect to the new server without issue, or so I thought.

It wasn't until a few hours into testing that we realised the CAPS LOCK key didnt work. Holding Shift and hitting letters displayed upper case letters as expected but the caps lock keys did nothing.

Everything is set to use the default US keyboard layout and yet CAPS LOCK works outside of a terminal services connection but not inside one.

Does anyone else have this issue or can you recommend a remote desktop application that with solve the problem?

---

### Post by audiomick on 2009-12-23
I am pretty sure I have seen that on windows machines using real VNC. Can't offer a solution, though. Sorry.:(

---

### Post by ancientt on 2010-03-26
I found a solution for what sounds like the same problem. I found this board when searching for a solution, so hopefully it will help others.

The tip that did it for me:
"I just now found a fix (from the thread).  Change the file /usr/share/rdesktop/keymaps/common .  Change the line that says “Caps_Lock 0×0 inhibit” to “Caps_Lock 0×3a capslock”.  I tried it out and everything works!"

[http://linuxsagas.wordpress.com/category/specific-software/rdesktop/](http://linuxsagas.wordpress.com/category/specific-software/rdesktop/)

---

### Post by tom.gobel on 2010-03-26
Thanks for the tip, changing the file worked for me too.

I could have used this a couple weeks back when I was remotely connected into a machine where the user had left caps lock turned on locally...and I was stuck holding the shift key for most of the session.

---

### Post by hankyknot on 2010-03-26
Will give this a try Monday AM.

Does it turn CAPS lock on all the time or just make the CAPS LOCK key function properly?

---

### Post by hankyknot on 2010-04-07
HOLD THE FRONT PAGE !!!!

I discovered that if you select the keyboard type US instead of EN-US the problem seems to be fixed.

---

### Post by eXtremer on 2010-09-22
> **hankyknot said:**
> I discovered that if you select the keyboard type US instead of EN-US the problem seems to be fixed.

I thought it was working but I was wrong, If I choose US, then the arrow keys aren't working and the number keys from the left same thing.

---

