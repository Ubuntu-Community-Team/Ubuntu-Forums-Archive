---
title: "booting from command line"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by StuSchu on 2010-02-25
I just tried to change my dual-boot configuration so the Ubuntu is the default instead of Windows as outlined [here]("https://help.ubuntu.com/9.10/switching/dualboot-custom.html")

However, instead of changing this, the fix changed what happens once I select 'Ubuntu' at the dual-boot menu.  Now, instead of going into the Linux OS automatically, it shows mw a bunch of code, asks for my username and password, and then gives me a command line.

This must be a horribly basic question, but what command do I enter so that it will boot Ubuntu and so I can reverse the changes I made?

---

### Post by MooPi on 2010-02-25
Try ```
startx
```

---

### Post by Kakers on 2010-02-25
If you are in the command line bash, 'sudo startx' should do it. I haven't used KDE before but you might have to use 'sudo startx kde'

---

### Post by drs305 on 2010-02-25
This can be caused by a variety of issues. Since you get to a login prompt, it may not be a specific boot issue, but to give us a clear picture, please run meierfra.'s [boot info script]("http://bootinfoscript.sourceforge.net/") and post the results between "code" tags by using the # icon in the post's menu area.

---

### Post by StuSchu on 2010-02-25
this worked.  thanks so much.

---

### Post by StuSchu on 2010-02-25
and by "this" I mean entering 'startx'

---

