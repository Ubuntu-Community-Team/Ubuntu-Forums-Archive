---
title: "Two way folder sync"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by jimmy the saint on 2010-01-31
I need to sync folders between several machines and would prefer not to use a cloud service.  What's the easiest way to do this?  I have a home server I can use if neccessary.

---

### Post by listerdl on 2010-01-31
I thought Ubuntu One offered this but that might be a cloud.

Cant think of another way aside from perhaps something offered by [www.dyndns.com/](www.dyndns.com/)

Check them out.....

---

### Post by warfacegod on 2010-01-31
Ubuntu One is cloud. (That's why it's icon is a cloud in Notification Area).

The link looks like it might be cloud too.




Try looking into rsync. I don't know much about it but I see it here all the time for syncing folders.

---

### Post by gslug79 on 2010-01-31
Unison [http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/~bcpierce/unison/") does exactly what you are looking for. It can sync two folders on the same machine, or between machines using ssh.

There are two diferent packages in the repos: unison (CLI) and unison-gtk (GUI).

---

### Post by jimmy the saint on 2010-01-31
Thanks gslug.  I settled on unison.  I'm going to have to see if I can expand it to cover more than two machines.  It looks like I might be able to pretty simply.

---

### Post by gslug79 on 2010-01-31
I think it should work between multiple machines - you will just have to remember which one was last updated. One way around this would be to sync all of your boxes to one server. I use this method to keep two laptops and a desktop in sync.

---

### Post by MrWES on 2010-01-31
> **warfacegod said:**
> Ubuntu One is cloud. (That's why it's icon is a cloud in Notification Area).

The link looks like it might be cloud too.




Try looking into rsync. I don't know much about it but I see it here all the time for syncing folders.

Or grsync -- the gui frontend for rsync

[http://www.linuxloop.com/2009/04/21/how-to-pain-free-backups-with-grsync-and-gnome-schedule/]("http://www.linuxloop.com/2009/04/21/how-to-pain-free-backups-with-grsync-and-gnome-schedule/")

---

### Post by BoneZZZ on 2010-02-05
I use Unison-gtk at the end of my gdm session. It works like XP offline shared folders. Only 9 seconds to scan a 5GB folder!!! I use a script in /etc/gdm/PostSession/ to execute it on logout. The problem is that I have to first logout and second shutdown from gdm login windows. I am trying to auto execute unison-gtk also when shutdown or reboot. Scripts in /etc/init.d or rc0.d or rc6.d doesn't work as Xsession is closed. Any help will be welcomed, as unison works much better than old XP offline folders system and is also Win compatible.

PS: I prefer unison-gtk before I can see if there is any problem in syncing before closing my computer.

---

