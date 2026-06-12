---
title: "Screen greying out and lockup PC"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2009-02-01
Just recently my PC screen has started to go dark grey and the keyboard and mouse stop responding .It stays that way for between ten and twenty seconds and then lightens up again and alls well till the next time . Its as if the computer is unable to cope and has to shut down for a rest .The components have not changed and worked perfectly for a long time , it's just started since the last update .

---

### Post by halovivek on 2009-02-02
Could you post your system configuration? and operating system details?

---

### Post by linux_tech on 2009-02-02
can you login with safe mode?  It sounds like a graphics issue.  You could try reinstalling display adapter driver.  If result is still grey screen after driver install, you could try using a different xorg.conf.  In /etc/X11 there should be a few different xorgs to pick from.

---

### Post by mcduck on 2009-02-02
If you are using the desktop effects, the window/desktop becoming grey is just the way how Compiz tells you that the program in question has stopped responding.

So they greying effect is a feature, not part of your problem. Instead you should tell us what programs you are running when that happens.. (and no, it's definitely not a graphics card/driver issue :))

---

### Post by ex-wirecutter on 2009-02-02
I have just looked up some old replies to this problem posted on this forum and it appears to be Firefox related , i.e. overloaded I/O so it'snot my PC at fault.
Thanks anyway .

---

