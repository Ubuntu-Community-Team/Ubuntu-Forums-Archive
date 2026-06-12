---
title: "&quot;dialog package?&quot;"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by kcohen1017 on 2010-03-20
Forgive me, please, if this is listed somewhere, but I have searched the entire forum without finding anything on a "dialog package."

I'm a rank beginner to Linux in general and Ubuntu in particular, and I'm trying to install LIRC (Linux Infrared Remote Control).  I really want to start getting away from Microsoft, but a few hours in and I'm already stuck. 

The installation instruction say to run a setup.sh, but it fails with a "dialog not found!" response.  The instruction then say 

"To use LIRC's setup.sh script you need the dialog package. It already should be installed on most systems. The setup.sh script makes configuration of LIRC much easier but using it is not obligatory."

It then goes into a bunch of possible configuration options for installing without the script, but frankly, it's way over my head.  Obviously, it would be a lot easier if I could get the script to run.

So where's the "dialog package?" Or am I completely misunderstanding something fundamental?

---

### Post by 3rdalbum on 2010-03-20
On Linux, we don't trawl the web for software, download it from a website and install it. Instead we use a "package manager", which keeps track of software for us and makes it very easy to install.

LIRC is available in Ubuntu's package manager. Go to System > Administration > Synaptic Package Manager and do a search for 'lirc'. You will see the 'lirc' and 'gnome-lirc-properties' packages there. Right-click each one and choose "Mark for Installation". When you have marked each one, click the Apply button and then OK.

The software will download and install.

When you install LIRC in this way, it doesn't need the 'dialog' package; but now you know where to find packages, so if anyone ever tells you to "get such-and-such a package", you'll know where to look: Synaptic Package Manager.

---

### Post by kcohen1017 on 2010-03-21
3rdalbum -

Thank you for your fast reply.  To be fair, I wasn't trawling the net looking for software, I followed threads in the Ubuntu forums which pointed me the the LIRC website.  There is no mention there of an installation package, and their HOWTO only describes installation from their downloadable tar files.

I did search for LIRC in the Update Manager, but not the Synaptic Package Manager.  My mistake, and hopefully the next time I run into an issue I won't have to bug anyone.

Thanks again!

---

