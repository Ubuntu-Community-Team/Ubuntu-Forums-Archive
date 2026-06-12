---
title: "MS AD users and Ubuntu groups"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by bmobley on 2008-04-01
I am starting to run in circles and have decided to call in for help. I have my Ubuntu workstation setup to authenticate to my 2003 MS Active Directory server. I can do this just fine (log in), even browse the directory. I am not having any luck adding my AD account to the Ubuntu local groups. I have edited the group- file and tried to add my account there in both "the username" and "DOMAIN+username" format to the same groups as my local account has with out success. I did setup a group in AD called UnixAdmins and added my AD account to this group. Then added this AD group to sudoers. This at least gave me the right to SUDO, but no other rights to the workstation (ie. sound, mounted media, add printers, etc.). Can someone point me in any direction?
Thanks in advance,

---

### Post by bmobley on 2008-04-02
bump
This should be a real easy question for those in the Know! I just need the syntax of the domain username that is expected in the GROUP- file, I believe.

---

### Post by kmartshopper on 2008-04-17
Been looking for a similar answer.  I used likewise-open to configure AD and needed to have access to the sudoers file.  The answer I found was to use double \\s:

IE

AD\\dgoodma ALL=(ALL) ALL
rather than what you put

AD\dgoodma ALL=(ALL) ALL

see [http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/2008-February/000116.html](http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/2008-February/000116.html) for original post...

Must include domain of course if using a domain account...

---

### Post by cebesius on 2008-04-25
I've created such a UnixAdmins group on my Active Directory domain, and got my Hardy Heron server joined to AD using Likewise.  Here is the last line of my /etc/sudoers file:

```
%UnixAdmins ALL=(ALL) ALL
```

Here is a screenshot of what happens when I log in as a member of UnixAdmins AD group and try to use sudo:

[IMG]http://img125.imageshack.us/img125/7771/likewiseem0.png[/IMG]

Have I missed something?

Many thanks!


EDIT: Since this thread has long since been moved to the archive, I felt it was appropriate to start a new thread, which I have posted at [http://ubuntuforums.org/showthread.php?t=766763](http://ubuntuforums.org/showthread.php?t=766763).

---

