---
title: "Shared Folders in Linux"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-03-13
I am trying to do something very simple...I think.

I have two identical machines running Intrepid. They both have wireless and are linked to a hum to receive internet.

I want them to both be able to see and read each others public folder.

I don't want to get into ssh and all that....samba seems to work well with XP and Ubuntu....and  a printer attached to one of the machines which both can now use via MSHOME and samba.....but how to get each machine to see the others public folder is becoming a bit of a mission!!

---

### Post by Ms_Angel_D on 2009-03-13
try right clicking on the public folder and selecting properties and looking at the share tab. It just may need those permissions set.

---

### Post by danrche on 2009-03-13
if your using samba, you need to have the public folder shared out via samba on both sides. since your not using any central auth service (LDAP or Server) you'll want to set up a samba user and passwd that matches your user within ubuntu. you'll need the usernames and passwords on both pc's to match and you should see the Public folders without a login prompt. But if your linking the 2 PC's together and it's just the 2 linux boxes, I recommend using NFS. If your going to link them together with a mix of linux and windows PC's, use Samba.    Hope this helps....


here's a helpful link that may provide a better explanition. [http://www.novell.com/coolsolutions/feature/1625.html](http://www.novell.com/coolsolutions/feature/1625.html)

---

### Post by dunbrokin on 2009-03-13
Sorry, what is NFS....and how do I got about setting that up?

---

### Post by nelskurian on 2009-03-13
nfs means network file sharing.Its the common way of sharing files between two linux machines.Checkitout the link.
[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

---

### Post by dunbrokin on 2009-03-13
Hmmm....seems very complex...just to read/write to public files....might just stick to the USB disk and walk to the other machine.

---

