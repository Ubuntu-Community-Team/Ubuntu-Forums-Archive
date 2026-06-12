---
title: "Just updated everything and I get &quot;can't mount \home&quot;"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by buntavid on 2010-05-08
Hi

I was wondering if it was possible to update Ubuntu just like "Windows Update" when I found out about the Synaptic update thing ... when I opened it, "All" was highlighted ... it seemed forward ... I clicked "Reload" just in case ... then "Mark all Updates" ... then "Apply" .... downloaded everything then restarted ... i noticed a new version of the linux-gnu thingy ending with 22 instead of 21 in the boot-loader ... when i select the 22 option i get "can't mount \home" ... everything is fine when I select the 21 option.

Also, for your information, prior to all of this, I've installed Avira Antivir for Linux/Solaris. I remember it asking me for a folder to watch over with the resident-scanner (they call it Guard) ... I went with the default option \home. Does this have anything to do with the mounting problem ? Will I have to reinstall Antivir again each time Linus-gnu updates?

thanx

---

### Post by spiky001 on 2010-05-08
can you post output
```
df -h
```
 
it will help ppl

---

### Post by buntavid on 2010-05-08
myname@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            9.4G  2.7G  6.3G  31% /
none                  995M  292K  994M   1% /dev
none                  999M  356K  998M   1% /dev/shm
none                  999M  104K  999M   1% /var/run
none                  999M     0  999M   0% /var/lock
none                  999M     0  999M   0% /lib/init/rw
/dev/sda1             128G   98G   31G  76% /host
/home                 9.4G  2.7G  6.3G  31% /home
/dev/sdb1             932G  665G  268G  72% /media/SimpleDrive
myname@ubuntu:~$

---

### Post by bumanie on 2010-05-08
Just boot with the 2.6.32-21 kernel - it happens occasionally that a new kernel doesn't suit your particular setup for some reason. That is why most users keep a known booting kernel on their computer for this exact reason. You should also put a bug report in to launchpad for the developers to look at.

---

### Post by jvc26 on 2010-05-08
To get a bug off to launchpad run:

```
sudo apport-bug linux
```

J

---

