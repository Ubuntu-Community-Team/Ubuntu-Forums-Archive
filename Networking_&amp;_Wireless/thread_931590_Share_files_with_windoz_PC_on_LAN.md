---
title: "Share files with windoz PC on LAN"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by roblinux on 2008-09-27
Okay....Heres the setup...

Win XP home upstairs...Ubuntu 8.04 LTS downstairs.

Both hooked into a D-link router.

Ubuntu can see and access files and folders and printer on Win xp but win xp does not see the linux machine...

How do I share files with the upstairs PC ??

In windows you find and put a check mark beside share files and printers through the control panel..

Is there a simple way to do this under linux ??

Thanks 

Rob

---

### Post by Iowan on 2008-09-27
First, have you installed Samba-server?  Ubuntu comes with Samba-client installed - which is why Ubuntu can access files/printer on XP. The server must be installed separately installed (some threads say SMBFS must also be installed).

---

### Post by roblinux on 2008-09-29
Thanks....That is probably it....I never did that ...

Rob

---

### Post by Another Monkey on 2008-09-30
Did you ever get this working?  If so, can you please let us know how you did it?

---

### Post by superprash2003 on 2008-09-30
as mentioned you need to have samba installed..
for reference : samba setup [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by roblinux on 2008-10-01
Haven't tried it yet...will report later...

Rob

> **Another Monkey said:**
> Did you ever get this working?  If so, can you please let us know how you did it?

---

### Post by roblinux on 2008-10-01
Okay...I installed Samba package from synaptic...went upstairs to the windows machine and the Ubuntu machine now shows up !!

All is well in Muddville !!!

Thanks again

Rob

---

