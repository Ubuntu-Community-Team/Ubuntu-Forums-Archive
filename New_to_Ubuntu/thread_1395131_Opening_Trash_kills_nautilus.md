---
title: "Opening Trash kills nautilus?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by bpowell2005 on 2010-01-31
Edit: I'm marking this as "Solved"...although I do not believe the problem is solved, I've at least identified what the problem is (unstable version of libglib2.0) and I'll be rolling this package back to the previous version which is a confirmed fix (see link below). The root cause is of course still an issue, but that's for the developers. I've submitted a bug report, all the crash logs, a Valgrind log, and others have submitted multiple back traces...I'm sure the team has more than enough data to mine through to work out a solution.

Thanks everybody for the suggestions / assistance! What a community!

[http://ubuntuforums.org/showthread.php?t=1395237](http://ubuntuforums.org/showthread.php?t=1395237)




Hi All,

I just discovered a problem today, hope you can help...whenever I click on the trash icon, or right-click and select "Open trash" my desktop icons all disappear, and my conky disappears...I'm left with my desktop background, and the upper and lower tool / status bars...but no Icons.

I have the desktop cube, it's still working...not sure what is happening here...any help?

Thanks!

Just an edit: Also, if I open a Nautilus window, and select "Trash" the nautilus window crashes out as well.
Edit #2: Running Ubuntu Jaunty with latest updates...also, I can't find a .Trash folder in my home directory

---

### Post by bpowell2005 on 2010-01-31
Here's an update:

When looking at /var/log/messages, I see the following error appear any time I click the trash icon:

Jan 31 11:40:04 computer kernel: [  609.482053] nautilus[4283]: segfault at 7f00656d614e ip 00007f6aba315169 sp 00007fff2456db10 error 4 in libglib-2.0.so.0.2200.3[7f6aba2bb000+c6000]

Help! Please!

---

### Post by philinux on 2010-01-31
> **bpowell2005 said:**
> Here's an update:

When looking at /var/log/messages, I see the following error appear any time I click the trash icon:

Jan 31 11:40:04 computer kernel: [  609.482053] nautilus[4283]: segfault at 7f00656d614e ip 00007f6aba315169 sp 00007fff2456db10 error 4 in libglib-2.0.so.0.2200.3[7f6aba2bb000+c6000]

Help! Please!

Try removing the trash can from the panel and then add it back.

---

### Post by chaanakya_chiraag on 2010-01-31
Also, check if there's a folder in ~/.local/share

---

### Post by bpowell2005 on 2010-01-31
> **philinux said:**
> Try removing the trash can from the panel and then add it back.

Okay, remove and replace trash can does not help.

If I empty the trash, then I can open it just fine...however, once there is something in the trash, it causes this segfault.

Natulius will also segfault if I go to "Computer" from places or "Network"...I just updated the computer today...and libglib was updated...it seems like this could be related?

I tried to force the "Jaunty updates" version of libglib 2.0 (2.20xxx instead of 2.22.xxx) but Ubuntu wanted to remove a LOT of programs as a related task...

I'm not sure what's going on.

---

### Post by bpowell2005 on 2010-01-31
> **chaanakya_chiraag said:**
> Also, check if there's a folder in ~/.local/share

Yes, it's located in .local/share/Trash/files... thanks! Still having the segfault.

---

### Post by chaanakya_chiraag on 2010-01-31
Does it segfault if you open up ~/.local/share/Trash/files?

---

### Post by Ohrer on 2010-01-31
Hi, I'm having the same issue. any news?

---

### Post by bpowell2005 on 2010-02-01
> **chaanakya_chiraag said:**
> Does it segfault if you open up ~/.local/share/Trash/files?

No, I can browse via nautilus and terminal to the Trash files location without a segfault.

Upon further testing, I also get a segfault when I click on "Places > Computer" or "Places > Network"

I'm running 9.04, fully updated (problem started after the last round of updates). I'm seeing this reported more and more...seems to be restricted to 64-bit folks.

---

### Post by bpowell2005 on 2010-02-01
> **Ohrer said:**
> Hi, I'm having the same issue. any news?

No news...this is very frustrating, as a general rule, I've never seen Ubuntu break after updates! This is a first for me.

You're running AMD64 version of Ubuntu? Did this just happen after recent updates?

I've submitted a bug ([https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/515336](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/515336)) please check the bug out, subscribe to it, and click the "this affects me" button...Hopefully we'll get this resolved.

---

### Post by chaanakya_chiraag on 2010-02-01
What happens if you create a shortcut labelled "Trash" to ~/.local/share/Trash/files?  Does it let you do that?

---

### Post by Ohrer on 2010-02-01
> **bpowell2005 said:**
> No news...this is very frustrating, as a general rule, I've never seen Ubuntu break after updates! This is a first for me.

You're running AMD64 version of Ubuntu? Did this just happen after recent updates?

I've submitted a bug ([https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/515336](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/515336)) please check the bug out, subscribe to it, and click the "this affects me" button...Hopefully we'll get this resolved.

The problems seems to be caused by the smbclient, see [this]("http://www.uluga.ubuntuforums.org/showthread.php?t=1394101&page=3").

---

### Post by Ohrer on 2010-02-01
I downgraded to prior version of libglib2.0-0 like Polkan said [here]("http://www.uluga.ubuntuforums.org/showpost.php?p=8759620&postcount=18"). until they release a fix.

---

### Post by bpowell2005 on 2010-02-01
> **chaanakya_chiraag said:**
> What happens if you create a shortcut labelled "Trash" to ~/.local/share/Trash/files?  Does it let you do that?

Great idea! Made a link, works just fine.

The problem is with an unstable version of libglib2.0...see this other thread:
[http://ubuntuforums.org/showthread.php?t=1395237](http://ubuntuforums.org/showthread.php?t=1395237)

The fix is to downgrade libglib to the previous version, which I will do shortly. I enabled apport and submitted a full bug bug report...other users have submitted backtraces and other log files to support the troubleshooting...hopefully this will be resolved...in the mean time, I'll be telling aptitude to forbid this version of libglib!

---

### Post by bpowell2005 on 2010-02-01
> **Ohrer said:**
> The problems seems to be caused by the smbclient, see [this]("http://www.uluga.ubuntuforums.org/showthread.php?t=1394101&page=3").

It's some kind of issue, that's for sure!

Definitely related to the libglib2.0 upgrade...I'll be rolling that back directly.

Thanks!

---

### Post by bpowell2005 on 2010-02-01
> **Ohrer said:**
> I downgraded to prior version of libglib2.0-0 like Polkan said [here]("http://www.uluga.ubuntuforums.org/showpost.php?p=8759620&postcount=18"). until they release a fix.


Thanks, I'll be following suit shortly!

---

