---
title: "Unable to mount everytime"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by Mamalethea on 2010-08-03
Thanks for this service! Heads up I am truly an absolute beginner!
My acer laptop is sending me a variety of error messages, and I suspect I have only complicated this in my attempts to fix. I run Linux mint 8 Helena x64, Linux 2.6.31-14, If you tell me how to I will like to add more info about my os. First off I power on, grub loading, lm leaf graphic, lm green bubbles graphic, then hourglas symbol spinning for eternity, it will stay at this for days if I let it...
So then I hit ctrl-alt-f1, login&password, then -bash: /dev/null: permission denied, a whole screen of that with a cute non-sequiteur slash-dot-dash animal and $prompt
I have learned to get past this by as root typing "rm /dev/null" "mknod -m 0666 /dev/null c 1 3"
then reboot
init: mountall main process (492) killed with status 3
mount of filesystem failed
maintenance shell will now be started
root for maintenance or ctrl-d which leads to:
one or more of the mounts listed in /etc/fstab cannot yet be mounted:
/: waiting for /dev/sda1
/tmp: waiting for (null)
swap: waiting for uuid=xxxxxxxxxxx...
It does not leave this message, so I ESC to recovery shell
reboot takes me to choose between boot (/dev/sda1) or (recovery mode)
I choose recovery leads to more options:
resume, clean, dpkg, netroot, root
  dpkg leads to lots of errors and fails to fetch archives and security 
  resume leads to login&password which gets me permission denied again since I've rebooted I workaround that temporarily and resume normal boot, login, no errors, no desktop,  sudo mountall, resume normal boot, no errors, login, where to go from here?

Other:
I read I could type "startx" to get to desktop but that says "(EE) failed to load module i810 (module does not exist, 0)"
mountall from other than root leads to a flashy mess of "process 2983: arguments to dbus _pending_call_set_notify() were incorrect, assertion "pending != NULL" failed in fil dbus-pending-call .c line 596"
"this is normally a bug in some application using the D-Bus library"

sometimes I am directed to run fsck manually, which leads to me pressing y for yes to all kinds of fixes clears salvages

I think that is the jyst of it
now who wants to save me?
Peace

---

### Post by NoBugs! on 2010-08-03
Sounds like a bad hard drive? Have you checked it with gsmartcontrol?

---

### Post by Mamalethea on 2010-08-03
k 
will try it

---

### Post by Mamalethea on 2010-08-07
running "apt-get install gsmartcontrol"
responds with : 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic main...............
could not resolve 'archive.ubuntu.com'
  ((repeat))
failed to fetch [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)..............
  ((repeat))
E:unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

apt-get update also returns many "failed to fetch [http://archive](http://archive)
                                                                             //security
                                                                             //packages................."
and i do not understand --fix-missing?

even though  i run linux mint, not ubuntu??

---

