---
title: "Command 'sudo dpkg --configure -a' doesn't work"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by umaroxx on 2009-10-09
Hi everybody,
I tried to add/remove programs with Update/Synaptic package manager. Starting the installation an error occurs:

[I]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
E:_cache->open() failed, please report.[/I]

As mentioned I tried to run 'sudo dpkg --configure -a'. It runs until the message

Adding extention usr/lib/openoffice/basis3.0/program/mailmerge.py...

appears and the PC freezes. After restarting the PC the problems are the same. Can anyone help? I'm running Ubuntu Studio and I'm fairly new to Linux.
Thanks

---

### Post by umaroxx on 2009-10-09
Hi everybody,
I guess I fixed the problem after hours by myself :)
It's an Ubunto Studio bug I suggest that belongs to Openoffice Emailmerge. Installing the Openoffice package installs Emailmerge as well and the problems begin. I solved it in the following way (I don't know if all steps are necessary but anyway):

First I created a script for *libgksu2-0_2.0.9* with Synaptic. Iran the script and opened the terminal. I ran *sudo dpkg -i libgksu2_0 2.0.9-1ubuntu3_i386.deb*.

With Synaptic I searched for *openoffice.org-emailmerge* and deinstalled it.

After that I was able to download any software again.

Rock til you drop :guitar:
umaroxx

---

