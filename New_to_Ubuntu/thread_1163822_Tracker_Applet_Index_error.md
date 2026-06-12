---
title: "Tracker Applet??? Index error?????"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by leenyx64 on 2009-05-19
I just got on my computer and this error message kept popping up. is this a real issue or is it a virus? I have never had this problem. I am attaching a image to this post. whatever the image says is all i know. the computer fan is also runing louder than normal and after the computer has been on for about 15min the whole system runs VERY slow. PLEASE HELP!!!!!
[IMG]http://i726.photobucket.com/albums/ww270/leenyx64/trackerproblem5-19-09.png[/IMG]

---

### Post by lisati on 2009-05-19
If you have the patience, the "reindex" option might be worth a shot.

---

### Post by leenyx64 on 2009-05-19
I can do that tomorrow while I am at school. I just wasn't sure what "reindexing" even is or if this was a virus or a common error.

---

### Post by Didius Falco on 2009-05-19
Hi,

This is a know bug with Tracker. From the 9.04 Release notes:

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

 
> **Tracker index corruption**

  In some cases it can happen that the index of the "tracker" desktop search engine becomes invalid. A dialog will be shown, offering you to "Reindex all contents". This button does not work, and the tracker service might start to use large amounts of CPU and disk resources. As a workaround, please press Alt+F2 and run tracker-processes -r. This will be fixed in a post-release update soon ([361205]("https://bugs.launchpad.net/bugs/361205")). 

I hope this helps...

Regards,

Didius

---

### Post by leenyx64 on 2009-05-19
Thanks Didious! I will try that as soon as I get the chance.  Probably expect a new reply to this thread tomorrow when something else goes wrong.

---

### Post by lisati on 2009-05-19
> **leenyx64 said:**
> Thanks Didious! I will try that as soon as I get the chance.  Probably expect a new reply to this thread tomorrow when something else goes wrong.

Good luck! I wasn't aware of the bug (sorry about that, chief!), and I hope nothing serious goes wrong for you.

---

### Post by TheGoktor on 2009-06-05
Thank you for posting this - I've been experiencing this bug since yesterday, and had no idea what it was, or why it was crashing my laptop. Now I know...and have worked around it! Fab!:D

---

