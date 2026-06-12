---
title: "ssh -X from a TTY"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by tears.of.angels on 2008-09-07
hey everyone, quick question;

i really like using ssh with x forwarding from my headless box, but one thing i was hoping to do to make it better is to setup x forwarding from a tty so i don't need to open up another terminal window and have it open as long as i'm using the app.

i vaguely recall something about ```
export DISPLAY=:0
``` or something like that, but that doesn't work, and i haven't had much luck with it.

thanks

---

### Post by dmizer on 2008-09-07
This is probably your answer: [http://www.linuxquestions.org/questions/slackware-14/slackware-12-ssh-x11-fowarding-issue-589145/](http://www.linuxquestions.org/questions/slackware-14/slackware-12-ssh-x11-fowarding-issue-589145/)

My google search was the following:
ssh tty X11

---

### Post by tears.of.angels on 2008-09-08
so from what i gathered i cannot use ssh forwarding from a TTY?

it seems wierd to me that something simply CAN'T be done in the linux world.

does anyone know of a way to do so?
bear in mind i have X forwarding working from a virtual console (xfce-terminal) within my environment, i just thought it would be nice to have it work from tty2.

---

### Post by dmizer on 2008-09-08
No, nothing in that thread says it can't be done from tty. It says that you'll have to start a dedicated X session in the tty:
> So before you start the SSH-connection start a dedicated X-session (If you wish so) xinit -- :2

The thread starter solved the problem by using this script:
```
#!/bin/bash
export DISPLAY=:0.1
ssh -Y xxx.xxx.xxx.xxx foo
#
```
where "foo" is the program you want to run remotely.

---

