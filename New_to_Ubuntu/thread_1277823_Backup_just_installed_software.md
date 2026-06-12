---
title: "Backup just installed software"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by jsarao on 2009-09-28
I installed Ubuntu on a few different machines (read: different hardware configurations.)

I then install lots of different software via "sudo apt-get install <blah blah blah>".

Some of these software installs may require additional configuration (tftpd for example).

Is there an easy way to install the same software packages on multiple machines (or a new machine) and any configurations that may go with it?

My ideal procedure:
1. Install Ubuntu from live-cd.
2. Install all additional software (from CD or network location)
3. Install custom configurations

---

### Post by earthpigg on 2009-09-28
if you wish, you can do this:

1) run remastersys on the existing install to generate a custom Ubuntu LiveCD .iso file.
2) Install from that LiveCD on target machine.

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by jsarao on 2009-09-30
And I can use this CD on different hardware configurations (i.e. different processors, etc.)?

---

### Post by cariboo on 2009-09-30
Yes, all the necessary drivers are included with the kernel.

---

