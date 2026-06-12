---
title: "Unable to print from networked Mac"
date: 2015-12-17
forum: Networking &amp; Wireless
---

### Post by asb3 on 2015-12-17
I have a printer attached to a computer running Ubuntu 14.04 and Cups.  I can print fine from my linux box.  I also have a networked Mac laptop.  The mac sees the Linux printer, but when I try to print, nothing happens.  According to the printer Properties dialog box, the state of the printer is Enabled, Accepting Jobs, and Shared.  What am I doing wrong?

---

### Post by Hadaka on 2015-12-17
Hi,verify your settings in the Ubuntu machine. Is this the host of your network?
click System Settings >> Printing....Does it say "Connected to localhost" ?
Right click the printer icon....are both "Enabled and Shared" checked?
Click Properties...are all those fields correct???
Click Policies...are "Enabled-Accepting Jobs-Shared" checked??
*if all that is correct verify network Default printer name. From the Ubuntu machine do.
```
echo "print test U" > testprint
lp testprint
```
*Example from my machine..
```
hadaka:~$ echo "print test U" > testprint
hadaka:~$ lp testprint
###request id is Deskjet-3900-91 (1 file(s))###

```
It should print "print test U"  U being Ubuntu
*Request I.D. this should be the DEFAULT printer the MAC prints to.
verify the MAC .. same as above..From the MAC machine do...
```
echo "print test M" > testprint
lp testprint
```
the request ID should be the same as the Ubuntu machine.
Hopefully this will give you some idea where to look.

---

### Post by asb3 on 2015-12-20
Success!  Thanks for the help.

---

### Post by Hadaka on 2015-12-20
Glad you got it working !

---

