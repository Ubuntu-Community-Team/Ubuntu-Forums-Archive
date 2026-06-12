---
title: "Can't boot 10.04 any more..."
date: 2011-06-19
forum: New to Ubuntu
---

### Post by akelsall on 2011-06-19
I'm not sure when this occurred, but it happened either when I was trying to install the new gnome-shell, or after installing kbuntu. In any event, when I try to boot 10.04 now, I get the following error messages (in this order):

Cannot open consolekit session: unable to open session: failed to execute to program /lib/dbus-daemon-launch-helper:success

cannot enter home directory. Using /

could not duplicate ICEauthority file/.Iceauthority.

Any ideas on how to correct this?

Thanks,

Andy

---

### Post by jtarin on 2011-06-19
Do you get returned to a command prompt?

---

### Post by akelsall on 2011-06-19
No command prompt. It just hung on a blank desktop and that was it.

---

### Post by jtarin on 2011-06-19
Have you tried booting with the install CD/DVD using the CHROOT method to access your installed files, before? You might need to edit and/or reinstall somethings.

---

### Post by jtarin on 2011-06-19
Do you get to any kind of login screen at all? Where you can use a failsafe desktop?

---

### Post by akelsall on 2011-06-20
I'm not familiar with the CHROOT method. What exactly is that?

 I did get the login screen, and I tried logging in under different options (gnome, failsafe, kde) but all of them generated the messages I noted earlier. 

Any other thoughts?

Andy

---

### Post by jtarin on 2011-06-20
When you get to the login screen switch to another terminal (Alt+Ctrl+F1-F6)then login as root and try the command ```
start gdm
```if that reports errors note them and post here. You can try the same command noting process for ```
start kdm
``` ```
startx
```

---

### Post by akelsall on 2011-06-23
I have tried so many ways to recover my .Private data it's not even funny. Very frustrating. It shouldn't be this difficult, yet it is. I went ahead and re-installed Ubuntu 10.04 on my root (and still have all my data on the other partitions I had before). Thanks for trying. I'm moving on to Fedora now, as I did a test drive of Unity and was not impressed at all. I did like Gnome3, so I'll give that a go. Ubuntu needs to work on the encrypted drive recovery. A good idea that's poorly executed based on my experience. 

Thanks again,


Andy

---

