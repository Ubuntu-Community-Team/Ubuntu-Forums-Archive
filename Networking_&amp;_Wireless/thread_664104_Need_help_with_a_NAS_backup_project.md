---
title: "Need help with a NAS backup project"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by RustyWyatt on 2008-01-10
Hi Folks,

Well I am very happy new Ubuntu user and learning fast. I have tried everything I could find to solve my problem before I realized that I was trying to do something slightly different from most folks.

I was trying to mount my Thecus NAS (Raid 1, 500 Gb) via my home wireless network, when I booted  a laptop that travels with me every day.  I think that part of my problem was timing the booting of my laptop, signing on to my home wireless network and mounting the NAS on the laptop.

So here is what I really want to do:

1 &#8211; Keep all of my files on my laptop (because they are used at multiple locations).

2 &#8211; Backup my laptop files to my NAS on a daily basis, unattended, in the evening.

Therefore, I need to ask for help figuring out how to accomplish and/or writing a script to:

A &#8211; Mount my NAS on my laptop and then,

B &#8211; Start a back-up program (Google Flyback?) and then,

C &#8211; Back-up my laptop data, from a specific laptop partition, &#8220;D&#8221; to my NAS..

D - I will also need the ability to mount the NAS and access files on a as-needed basis when I need to retrieve files from the NAS.

All thoughts and comments GREATLY appreciated!

Thanks,
Tom

---

### Post by PilotJLR on 2008-01-10
A backup program might be overkill... a common, easy, effective solution is rsync.

You would need to only write a script (just a series of commands) to:
- mount the NAS share on your laptop
- rsync a directory or list of directories to a folder on the NAS share
- profit!

Rsync is nice because it copies changes in files, rather than entire files. So your first backup will take the longest time, and later backups will be shorter (depending on how much changes).

I use rsync for a lot of purposes. For example, I maintain a small business server that does nightly rsync offsite backups. An an ordinary cable modem, I keep 3 GB of important client files (encrypted and over ssh) replicated remotely. This is feasible because rsync only copies CHANGES to files.

---

### Post by RustyWyatt on 2008-01-11
Thanks PilotJLR!

That's just the tip I needed;)

What scripting language do you recommend?

I see a lot of choices but, since it is all new to me,I might as well learn something useful.

[http://ubuntuforums.org/showthread.php?t=497579&highlight=batch+language](http://ubuntuforums.org/showthread.php?t=497579&highlight=batch+language)

Thanks again!

Tom

---

### Post by Mithrilhall on 2008-01-11
[http://synkron.sourceforge.net/](http://synkron.sourceforge.net/)

Synkron is a simple Qt application that allows you to sync folders, for example a flash disk with a folder on your hard disk.



    * Tabs allow you to have more synchronisations running at once.
    * Periodical synchronisations automatically sync your folders in selected intervals.
    * Restore files, which were overwritten during the synchronisation.
    * Add files and folders to black list to make sure they won't be synchronised in the future.
    * Make schedules and backup using multisync
    * Synkron is Free Software



    * Apple Mac OS X (Universal)
    * Microsoft Windows (Installer)
    * Linux/Unix (Source code, Ubuntu and Archlinux packages)

---

### Post by RustyWyatt on 2008-01-14
Thanks VERY much for the recommendation!

I managed to get Synkron up and running with the help of Matus and... now I'm working on mapping my NAS drives.

Thanks again,
Tom

---

