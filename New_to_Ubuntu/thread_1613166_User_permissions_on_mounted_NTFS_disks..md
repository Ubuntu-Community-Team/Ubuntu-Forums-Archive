---
title: "User permissions on mounted NTFS disks."
date: 2010-11-04
forum: New to Ubuntu
---

### Post by gewone on 2010-11-04
Hi guys!

Hope any of you could help me (us). Like this. Me and my brother have a computer with Ubuntu for operating system. The computer also has two NTFS disks that we both would like to access. Now, we have as sort of a rule (as silly it may seem) to not sit on the other ones account, but we use the 'switch user' feature regularly.

This is where the problems come in. If I wake up first, and log in, the two NTFS partitions are automatically mounted so that I can easily access them through the *Places* menu on the top menu applet. Sweet.

However, then say he logs in as well. The two NTFS partitions are not to be seen in the Places menu. We both know the origin of these 'menu links' though, so he navigates to /media/ where they sit. Permission denied! :| Evil has stroke. As we both are members of admin/adm group, it's an easy thing for him to chmod from 700 (which were set) to the more convenient 755. Strange thing is, the chmod command executes but nothing happens. When pulling *'ls -l /media'* both mount folders are still 700.

Please, you guys out there, help us out? As this is a two boys computer, without tons of (snoopy) users, it feels safe to set the permissions to 755. What's the approach here? Please tell us that it's not too complicated. I know that /etc/fstab is a key to lots of mounting. When I open that file, only my root file system (/) and my swap partition is present though. I've Google'd lots, and some Google results show threads about something called 'gnome-volume-manager', which seems obsolete slash deprecated though.

My best wish right now is that this is actually easy fixed, Linux has become so user-friendly with 'Buntu distros, so it would in fact not surprise me if the answer was so simple as that these 'default permissions' could be configured from somewhere in the GNOME administration/control menu.

Wow. I'm such an author. I now see that I've written five paragraphs of stupid text to describe an issue which I could have pulled as a simple one-liner:

**TLDR:**

> "Heey guys we're two dudes on a computer. GNOME mounts NTFS partitions on first superuser that logs on, whereas the second won't even get read axx. How to fix this??"

What can I say. I'm such an author! :)

---

### Post by mcduck on 2010-11-04
You simply need to configure the NTFS partition(s) in fstab, that allows you to set the permissions you want on them.

You can't just chmod/chow, as NTFS doesn't support file ownerships/permissions as Linux/Unix systems use them. It simply doesn't understand what you try to do and would have no way to store the permissions anyway. So they are instead set for the whole partition at the time its mounted.

And here's a link to fstab HowTo: [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by gewone on 2010-11-04
Ty for your quick response. Great wiki tutorial.
Seems I'll turn to pysdm for a quick fix!

---

