---
title: "No task bar or menu's in nxserver-Gnone"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by Nigel Lew on 2007-08-04
Hi folks, I finally got nxserver working sorta, at least locally.  My problem is I don't get any task bars or menus on the linux box(server).

I am connecting from an xp64 machine to feisty.  It works fine but I just can't see the top or bottom task bars.

any suggestions,
thanks,
Nigel

---

### Post by kevdog on 2007-08-04
What client are you using??

---

### Post by Nigel Lew on 2007-08-04
Hi, I am using the nxclient from the NoMachines website for windows v. 3.0.0-73

I seem to have it set right as it will only work with unix and gnome settings.  Changing resolution settings doesn't fix the issue.  All computers are 1024x768.

thanks,
Nigel

---

### Post by kevdog on 2007-08-04
Sorry and server version?

You stated 
> I seem to have it set right as it will only work with unix and gnome settings

So you are saying everything is working??

---

### Post by Nigel Lew on 2007-08-04
It works ok locally.  I still have a few things to sort out to hook it to my no-ip address but I will get to that.


I followed a tutorial stating I should download the client, server, and node, for linux.

I am using feisty and the nxserver build came from nxserver_3.0.0-63_i386.deb


thanks again, looks like I may have version issue.  both the client and the node are -76

Nigel

---

### Post by kevdog on 2007-08-04
Here is another guide in case you get stuck, although I know it does not specifically address your problem:
[http://ubuntuforums.org/showthread.php?p=3134834#post3134834](http://ubuntuforums.org/showthread.php?p=3134834#post3134834)

---

### Post by Synflux on 2007-08-05
> **Nigel Lew said:**
> My problem is I don't get any task bars or menus on the linux box(server).

I have exact same problem on two machines running freenx, the workaround I use is as follows:

1. Connect to machine (get no menu bars)
2. Close session and choose the Suspend option
3. Connect again straight away and you get the menu bars back.

I've got no idea why this happens but that workaround always sorts it for me. Hope that helps you. :)

---

### Post by Nigel Lew on 2007-08-05
Hmm. when all else fails kick it....

while a bit of a pain, it works great!.  Thanks alot.

Nigel

---

