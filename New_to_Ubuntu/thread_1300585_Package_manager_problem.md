---
title: "Package manager problem"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by Phil Hansen on 2009-10-25
Hi,
Rebooted and got a 'no entry' icon on the top right.
Package manager failed to start and gave the same error message as apt-get.
Message follows:

phil@rosetta1:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

How do I get this fixed. (this might be why my printer will not print as well)

Thanks

---

### Post by Waappu on 2009-10-25
Hi,

Have you changed your sources.list ?
If you are , revert changes and then run
```
sudo apt-get update
```

---

### Post by Phil Hansen on 2009-10-25
> **Waappu said:**
> Have you changed your sources.list ?
No haven't changed the source. Ran apt-get update again and it always comes back with a deb.opera error.
How to delete as I cannot get into Package manager to uninstall.
Thanks

---

### Post by MelDJ on 2009-10-25
try removing the opera source from software sources- third party sources

---

### Post by QLee on 2009-10-25
[QUOTE=Phil Hansen]Hi,
Rebooted and got a 'no entry' icon on the top right.
Package manager failed to start and gave the same error message as apt-get.
Message follows:

phil@rosetta1:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

How do I get this fixed. (this might be why my printer will not print as well)

Thanks[/QUOTE]

I don't see how this could stop your printer from printing but that's another question.

Look closely at what the error message is saying, the stated file can not be read or opened. The error message tells you where the file resides, you could investigate to see if there is anything about it that is corrupt or that would prevent it being read (it is a text file).

If I couldn't figure out why it can't be read after examining it, I would try deleting it and doing and apt-get update to let the system download it again. All of this assumes you have a correct stanza for the repository in your sources list.

---

### Post by Phil Hansen on 2009-10-26
> **QLee said:**
> 
Look closely at what the error message is saying, the stated file can not be read or opened. The error message tells you where the file resides, you could investigate to see if there is anything about it that is corrupt or that would prevent it being read (it is a text file). I would try deleting it and doing and apt-get update to let the system download it again. All of this assumes you have a correct stanza for the repository in your sources list.

Thanks that worked.

---

