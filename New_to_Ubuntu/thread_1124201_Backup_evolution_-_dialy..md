---
title: "Backup evolution - dialy."
date: 2009-04-13
forum: New to Ubuntu
---

### Post by longtom on 2009-04-13
Hi,

how can I backup my evolution files on a daily basis on a file server.

Or - in simple words, what (files, directories) needs to be copied onto an external device.

Thanks

longtom

---

### Post by hyper_ch on 2009-04-13
I guess it's:

~/.evolution

or maybe 

~/.gnome/evolution

and backing up I'd use rsync (over ssh) and cron to run it daily at given times.

---

### Post by longtom on 2009-04-13
> **hyper_ch said:**
> I guess it's:

~/.evolution

or maybe 

~/.gnome/evolution

and backing up I'd use rsync (over ssh) and cron to run it daily at given times.

Yes - found that.

I'm backing up from an external machine with Cobian - which works like a charm.  A pity he never went on with it.
So if I backup that folder I have all my mail and addresses backed up?

---

### Post by howefield on 2009-04-13
> **longtom said:**
> So if I backup that folder I have all my mail and addresses backed up?

Yes

Explore the folder, it is all there.

---

### Post by longtom on 2009-04-13
> **howefield said:**
> Yes

Explore the folder, it is all there.

I saw that - just needed a nod from someone - thanks!

---

### Post by vigyani on 2009-04-14
Use the following commands in a terminal on $ prompt:

To Backup Evolution:

$gconftool-2 --shutdown
$evolution --force-shutdown
$cd ~
$tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .spamassassin .gnome2_private/Evolution


Transfer the backup file to the destination machine:

To restore evolution:

$gconftool-2 --shutdown
$evolution --force-shutdown
$tar xzf evolution-backup.tar.gz
$gconftool-2 --unload evolution_setting.xml
$gconftool-2 --load evolution_setting.xml

It will backup all mails, accounts, settings & spamassassin bayes database.

---

