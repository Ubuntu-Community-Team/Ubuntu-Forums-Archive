---
title: "Uninstalling Samsung Smart Panel:can't find script"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by wannabegeek on 2010-03-13
Hi forum people...it's sunny outside my house, but I'm a student so 
I must slave away in front of my computer...

So I found this thread with the solution to my problem. I wish I knew where the script is that the author is referring to.

[http://ubuntuforums.org/showthread.php?t=682507](http://ubuntuforums.org/showthread.php?t=682507)

How does one search for a script ?
Do I use grep?
Having a hard time understanding the grep man pages.

thanks for your help,
wbg

---

### Post by wannabegeek on 2010-03-14
selfish bump...

---

### Post by wannabegeek on 2010-03-19
bump

---

### Post by wannabegeek on 2010-03-28
solved....

The script is in /opt   I just got lucky searching around, knew it couldn't be in too many places.
Found the Samsung directory and the uninstall.sh script, changed the header to  #!bin/bash
and then ran the script from there....

---

