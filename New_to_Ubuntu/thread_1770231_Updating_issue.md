---
title: "Updating issue"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by quik_lives on 2011-05-28
Whenever my update manager runs, it installs everything but one thing and tells me one package could not be installed. I tried it in the terminal just now, and this is what I got:


Setting up halevt (0.1.6.2-1.3) ...
dpkg: error processing halevt (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 halevt
E: Sub-process /usr/bin/dpkg returned an error code (1)

I haven't the faintest idea what that means or what to do about it. Any help would be greatly appreciated!

---

### Post by candtalan on 2011-05-29
I am running ubuntu 10.04.2, and looking in package manager I see that halevt is not one of the packages which has been installed. Its package description is:

=================
Generic handler for HAL events

halevt is a daemon that acts as a policy agent on top of HAL. It
listens to HAL events and reacts with user-configurable
actions.  It is a reimplementation of ivman project.

Among other things, halevt is useful as an automount daemon that will mount
removable devices but with a much smaller set of dependencies than tools such
as gnome-volume-manager.
=================

So it looks as if your system thinks halevt is installed, and needs updating, although from my system  halevt is marked as getting updates from the community only, not Canonical.


Hope that information might help?

---

### Post by dnairb on 2011-05-29
It seems the error lies with the post-installation script: [https://bugs.launchpad.net/ubuntu/+source/halevt/+bug/746949](https://bugs.launchpad.net/ubuntu/+source/halevt/+bug/746949)


Workaround is to, in terminal, run:

```
gksudo gedit /var/lib/dpkg/info/halevt.postinst
```

find the line

```
invoke-rc.d --quiet hal restart
```

and change to

```
#invoke-rc.d --quiet hal restart
```

i.e. comment it out. Save the file, then again in terminal run

```
sudo dpkg --configure -a
```

then reboot

---

### Post by quik_lives on 2011-05-29
Yes, that seems to have solved it! Thank you!

---

### Post by dnairb on 2011-05-29
You're welcome!

---

### Post by Cincinnatux on 2012-02-02
dnairb's suggestion worked for me, too, running 64-bit Natty, for which I'm grateful.  What kills me, though, is that I've been running Ubuntu on my home computers since Feisty and I *still* have little sense for how to properly troubleshoot my own problems.  It's great that folks like dnairb take their personal time to solve user problems, but how much greater would it be if long-term users stopped having problems beyond their ability to troubleshoot?

I'm not expecting a response (since this thread is SOLVED and on a different issue), but if anybody out there has gone from being a newbie to being a competent troubleshooter, let me know how you got there.  I'm not averse to putting in effort, but I feel that I am not getting much better with all the time I've put in, and that's just embarrassing, you know?

---

