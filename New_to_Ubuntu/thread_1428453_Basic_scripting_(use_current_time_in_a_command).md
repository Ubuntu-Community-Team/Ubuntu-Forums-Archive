---
title: "Basic scripting (use current time in a command)?"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by PreciousBodilyFluids on 2010-03-12
Hi -

I'm trying to put together a simple way to backup a MongoDB database that I'm building. The idea is that I click an icon and a copy of my data is dumped to a USB thumbdrive plugged into my laptop. I've formatted the thumbdrive to Ext3.

So, the mongo backup command looks like:

mongodump --db database-name --out "/media/Backup Thumbdrive"

I've made a custom application launcher that runs this command, and when I click it, it works! Hooray!

However, what I'd like to do now is change this command so that it dumps my data to a timestamped folder in the thumbdrive, and not just the root of the thumbdrive. I'm doing this because I want to keep several backups, and not have to go delete the previous one every time I make a new one.

So if I were using Ruby (the only programming language I know) it would look something like:

mongodump --db database-name --out "/media/Backup Thumbdrive/#{Time.now.strftime('%Y%m%d%H%M%S')}"

(The exact format of the timestamp isn't important, so long as it increments properly with time.)

Is it possible to do something like this in an application launcher like I already have?

Thanks!

---

### Post by cjhabs on 2010-03-12
/media/Backup Thumbdrive/$(date +%y)_$(date +%m)_$(date +%d)

---

### Post by thesenu on 2010-03-12
;)

---

### Post by PreciousBodilyFluids on 2010-03-12
> **cjhabs said:**
> /media/Backup Thumbdrive/$(date +%y)_$(date +%m)_$(date +%d)

That works great when I run it from the command line, but if I put it in a launcher and click it it winds up creating a directory named $(date +)_$(date +)_$(date +)

:???:

---

### Post by Dayofswords on 2010-03-12
i think he meant for you to do this```
mongodump --db database-name --out "/media/Backup Thumbdrive/$(date +%y)_$(date +%m)_$(date +%d)"
```
and just replace what you had
just guessing though
i know nothing of this

---

### Post by PreciousBodilyFluids on 2010-03-12
Yeah, that's what I'm doing.

---

### Post by Dayofswords on 2010-03-12
after google found this
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/109512-how-add-system-date-filename.html#post534109](http://www.linuxforums.org/forum/redhat-fedora-linux-help/109512-how-add-system-date-filename.html#post534109)

so i think the "y" needs to be "Y" then it might work , idk i dont know much about this
```
mongodump --db database-name --out "/media/Backup Thumbdrive/$(date +%Y)_$(date +%m)_$(date +%d)"
```


not on linux and not sure, but trying to help

---

### Post by cjhabs on 2010-03-12
> **PreciousBodilyFluids said:**
> Yeah, that's what I'm doing.

I tested it by creating a script - create_folder.sh:
#/bun/sh
mkdir ~/tmp/Backup\ Thumbdrive_$(date +%y)_$(date +%m)_$(date +%d)

put it in the panel and ran it.
It worked as expected. I didn't place any quotes around the folder but escaped all special characters (the space)

---

### Post by PreciousBodilyFluids on 2010-03-12
Never mind, I just wrote a one-line Ruby program to do it. Thanks anyway, everyone.

---

