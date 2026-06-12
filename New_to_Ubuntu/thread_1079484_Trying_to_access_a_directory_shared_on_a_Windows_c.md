---
title: "Trying to access a directory shared on a Windows computer"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by litlfrog on 2009-02-24
I've been using Ubuntu for a while, but I know practically *nothing* about how it operates in a multi-OS network. A coworker has shared a drive on his Windows 2000 system. The people in my office with Windows systems are able to access the drive, but I'm pretty stuck. I can see the drive I'm looking for by using the following command in samba:

> smbclient -L -n yourhostname


Where do I go from here to actually access the files in that drive? I've tried looking through the HOWTO files for samba, but I'm honestly overwhelmed.

---

### Post by OffAxis on 2009-02-24
The command line can be a little cumbersome for that, and xfce has no native samba browser. Try installing pyneighborhood

```
sudo apt-get install pyneighborhood
```

which is a graphical frontend for browsing.

Here's it's page in launchpad:
[https://launchpad.net/pyneighborhood](https://launchpad.net/pyneighborhood)

and here's a how-to:
[http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

Note: that how-to is for version .4 the current version is .5

---

### Post by litlfrog on 2009-02-24
Thanks! That's some progress, anyway. I've got pyneighboor installed. I found the system I was looking for by going to Edit -> Add machine and searching by IP address. pyNeighborhood can see the computer and it lists the directory I'm looking for. When I click on that directory, I have the option to mount the directory as SMB or as CIFS. I've tried both. pyNeighborhood just comes back with "Failed to mount" on both commands. I don't see an option to enable logging, so let me look through and see if I've configured something incorrectly.

---

### Post by litlfrog on 2009-02-24
Hmm, no joy on this so far. I've edited the smb and cifs lines to add "sudo" before the commands. I've also created a separate directory for the mount points and made sure I have Read and Write permissions. No dice--when I right-click on the directory and try to mount, it still comes back with the "Failed to mount" message. Any ideas?

---

### Post by OffAxis on 2009-02-24
try this thread:
[http://ubuntuforums.org/showthread.php?t=424489](http://ubuntuforums.org/showthread.php?t=424489)

seems like installing midnight command did the trick for many people

```
sudo apt-get install mc
```

---

### Post by OffAxis on 2009-02-24
The other thought I have is have you tried starting pyNeighborhood with sudo or gksudo?
The program itself may need the administrator privilege to initiate the mounts.

---

### Post by OffAxis on 2009-02-24
Here's another option for you using Thunar (the file manager in xubuntu)
[http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)

This thread is actually mentioned in the xfce docs, specifically post #5 as the easiest way of doing it.
[http://ubuntuforums.org/showpost.php?p=1834271&postcount=5](http://ubuntuforums.org/showpost.php?p=1834271&postcount=5)

---

### Post by achase79 on 2009-02-24
you could just add nautilus (from gnome) or dolphin (from kde) to initiate the mounts.

---

### Post by mrearl on 2009-02-24
Sorry for the stupid question, but did you make the directory sharable in Windows?

I access directories on my 3 Windows machines using Samba from my Dell mini 9 running Ubuntu Hardy.  I usually just go to
Places > Network > Windows Network > smb://hostname/.  It prompts me for the Windows password and voila!  There are all of my shared folders.

---

