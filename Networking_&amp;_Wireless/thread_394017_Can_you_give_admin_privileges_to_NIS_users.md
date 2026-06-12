---
title: "Can you give admin privileges to NIS users?"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by BrianK on 2007-03-26
There *has* to be a way to give NIS users admin privileges right?  I'm having a hard time with this & would prefer not to create my account locally on every machine in my office.

---

### Post by netztier on 2007-03-26
> **BrianK said:**
> There *has* to be a way to give NIS users admin privileges right?  I'm having a hard time with this & would prefer not to create my account locally on every machine in my office.

(Without knowing a lot about NIS).. 

Well, that's what NIS is for, isn't it? You should be able to make sure that there exists some kind of "administrators" group in your NIS Domain that is part of the "sudoers" group on all the systems in your office, right?

So whenever you add a certain user to the NIS database and make him part of the "admistrators", that user should automatically b allowed to sudo on every system in the NIS domain.

best regards

Marc

---

### Post by BrianK on 2007-03-26
> **netztier said:**
> (Without knowing a lot about NIS).. 

Well, that's what NIS is for, isn't it? You should be able to make sure that there exists some kind of "administrators" group in your NIS Domain that is part of the "sudoers" group on all the systems in your office, right?

So whenever you add a certain user to the NIS database and make him part of the "admistrators", that user should automatically b allowed to sudo on every system in the NIS domain.
Well, that's what you'd think.... that's what I'd think too, however, it doesn't seem to work.  At least, not as far as I can tell.

On my NIS server (also an ubuntu machine, but Ubuntu 6.06), I am a member of the admin group.  On my local machine, I am not.  I noticed that the group IDs were not the same on both machines, so I just fixed that, but still, I have no admin privs.

When you don't have admin privs, even your pulldown menus are different, i.e. no synaptic in System > Administration.. so I have to launch it from the command line. This is all well and good except for things like printer management which I can't seem to find the executable for - which makes me log off & log back in as a local user.  Very annoying.

edit:  So I can have admin privileges if I edit /etc/group & add myself to the admin line.  It just seems that this should be taken care of via NIS.  I double checked that my nsswitch.conf looks at NIS before files, but still, I don't get admin unless I'm in my local group file. hrm

---

### Post by Mr. C. on 2007-03-26
NIS works perfectly fine for what you want.  But you are missing an important security issue, that NIS is configured to avoid.

By allowing admin (root) access via any NIS client, any sufficiently knowledgeable person can add an NIS client station to your network and become admin.  NIS is fairly weak security-wise.

If this is on your home net, and you are unconcerned about this possibility, then read on.

When the NIS databases for the passwd and group files are updated, there is a minimum UID and GID setting, that strips out UIDs/GIDs below this threshhold.  See the file /var/yp/Makefile, and search for MINUID and MINGID.  You may change the values there if you insist on making these privileged IDs available via the NIS.  After your "make" is done, the databases will be updated and pushed, and your uses/groups will be available via NIS.

MrC

---

### Post by BrianK on 2007-03-26
> **Mr. C. said:**
> When the NIS databases for the passwd and group files are updated, there is a minimum UID and GID setting, that strips out UIDs/GIDs below this threshhold.  See the file /var/yp/Makefile, and search for MINUID and MINGID.  You may change the values there if you insist on making these privileged IDs available via the NIS.  After your "make" is done, the databases will be updated and pushed, and your uses/groups will be available via NIS.
Ahhhh!!  That's it!

I *knew* I had changed some sort of MINUID/GID on my last NIS server but couldn't, for the life of me, remember where that setting was.  I was even grepping through /etc to find "UID" & was coming up with nothing (obviously, as it's in /var)

Worked like a charm. Thanks!

---

### Post by Mr. C. on 2007-03-27
You're welcome.  Here are some NIS notes for your viewing entertainment; Week 5: "NIS/NIS+": 

[http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

