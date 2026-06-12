---
title: "SSH and running programs from client"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-03-24
I installed openssh-server the other day, and it's working great. I was able to SFTP to my computer from a computer at my university no problem.My next step, however, is puzzling to me. By the way, I use WinSCP and/or PuTTy on the client computer.

I want to be able to run programs from the client computer that runs on my server. I.E. if I'm ssh-ing to my server computer, I want to be able to run Firefox, or Google Earth, or what ever program. I want the program to run on the server, but I'd like to see the display on the client.

I was trying this with the command ```
ssh -Xp (port#) username@servername firefox
```

It tells me it won't run because a display isn't specified or something like that.

Maybe it'd be easier to VNC through SSH to my server?

---

### Post by kanikilu on 2009-03-24
I believe a local X server needs to be running on the client for this to work.

If you were doing this from another Ubuntu (or other *nix) computer, it would "Just Work(TM)" ;)

From Windows, you need to install an X server. Back when I first tried this, I believe I first tried Cygwin/X, with limited success. More recently, I used Xming, and that was a lot easier to get working. Check it out here:

[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)
[http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming)

---

### Post by MrWES on 2009-03-24
In PuTTY navigate to the SSH | X11 Settings and enable X Forwarding.

Bill

P.S. As posted below, and I forgot to mention -- you need xming running on the windows machine.

[http://www.straightrunning.com/XmingNotes/]("http://www.straightrunning.com/XmingNotes/")

---

### Post by kanikilu on 2009-03-24
Check out this brief guide for how to use ssh and putty+Xming:

[http://solaris.reys.net/english/2006/04/x11_forwarding](http://solaris.reys.net/english/2006/04/x11_forwarding) (just skip the bit related to solaris, although the sshd_config file is in the same place)

---

### Post by Lazy-buntu on 2009-03-24
I installed Xming on a flash drive, ran it. Then, I SSH'd with PuttyPortable, and voila. Worked like a charm.

The only thing that didn't work was anything that required the use of the client's graphics card. I.E. I tried google-earth and it wouldn't run. I'm guessing any games requiring the use of a graphics card would also fail to run, but hey.

Would VNC work in that situation?

---

