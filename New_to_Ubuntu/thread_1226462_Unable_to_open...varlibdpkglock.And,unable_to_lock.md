---
title: "Unable to open.../var/lib/dpkg/lock.And,unable to lock.../var/lib/dpkg/"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by faron45 on 2009-07-29
Attempting..."Getting rid of "orphaned" packages" as per [http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")

I received this message in the terminal window...

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Can anybody help with this ?? 
For now,I have to run.But,will check back later [couple of hours maybe] for any answers anyone may have.Appreciate any & all help [as always].Ya'lll have a fantastic day [if I don't get the chance to talk to you].Peace/goodwill [and good computing] to all ! {And,please [as always] be gentle with me}.{I am only an "aspiring geek}Aka:a wannabe !!
              Thanks again,faron45
                 aka:GuitarFiend.

---

### Post by ubudog on 2009-07-29
Reboot and post back.

---

### Post by ptn107 on 2009-07-29
Try restarting.  You need to make sure you have only one open package manager (apt-get, aptitude, synaptic, add/remove) as they all use dpkg and can hold it up.  If your still getting the error type the following in a terminal before trying again.  This, of course, is a last resort:
```
sudo rm /var/lib/dpkg/lock
```

---

### Post by bodhi.zazen on 2009-07-29
You can only use one package manager at a time (well they all use apt, so only 1 instance).

Close any other instances of synaptic, add/remove, update manager, etc.

If that fails , what ptn107 said.

You almost never need to reboot Linux (Reboot is soooo [s]Windows[/s] that other OS we know).

---

