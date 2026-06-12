---
title: "Can't put files from windows onto Server user account"
date: 2005-04-28
forum: Networking &amp; Wireless
---

### Post by Zensunni on 2005-04-28
I've got a driver for a VGA card that's too big for a floppy. So, I tried putting it in through the network. However, I can't seem to put anything into my lunixbox's user folder from windows. It keeps saying "Cannot copy "<driver>":access is denied.

I've typed in a whole buch of chmod commands, but nothing lets me copy to the other computer.

BTW, I'm really new at linux. These are a couple of the commands i've tried:

chmod a+rw /home/<user>
chmod a=rw /home/<user>

---

### Post by nad on 2005-04-28
Please do not indiscriminately change permissions in your filesystem. This is a good way for it to become unstable and unusable. It is also one reason why we do not run with the superuser account as one poorly chosen or inadvertent thick fingered command can instantly trash your operating system.

Make a share directory and play with this, however, your problem appears to be a mount issue.

Please describe "putting it in through the network" so that we can begin to diagnose your problem.

---

### Post by Zensunni on 2005-04-29
Sorry. Maybe I should give you a little more detail...

While in windows, I've tried to place the file in the shared folder of a given username on linux (with samba). So, I've just got a user folder from linux showing on my windows computer in "my network places". Every time I try to put a file in it, a "access denied" message box comes up.

Oh, and I know i'm being really reckless. But this is just an install from complete scratch so I've nothing to loose. I know that i'm going to be reformatting soon when I start to use the OS more seriously.

---

### Post by nad on 2005-04-29
Ahhh... This is a windoze issue.

On the windoze machine you need to be logged in with the same name and password that you use for ubuntu or else request to use a specific name and password to the network. After all, in a networked environment, your one user name and password is expected to apply to all machines. This is one of the administration headaches of a peer to peer network.

---

### Post by Zensunni on 2005-05-01
Ah, I see. I'll play around with that and try to see if I can share with two accounts for the same user and post any revelations I have.

---

