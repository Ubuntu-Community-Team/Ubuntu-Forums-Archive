---
title: "[backup] automated backup of folder changes"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by oponto on 2009-03-29
heyo !

how do I set up an automated backup procedure for my Home Folder, 

which **knows what files have been changed/added/removed** and **applies/transfers** those changes (c*hanges only, not every file*) to the **Home Folder backup on a hdd**

every day/at any time I say it should do so (command, etc.) ?



How do I set up **the same thing** for a special folder ?
(for a quicker interval to backup my most important work every hour)

[SIZE="1"]Hopefully I didn't miss any keyword an searched for it.[/SIZE]

[COLOR="DarkOrange"]many thanks ![/COLOR]

---

### Post by hyper_ch on 2009-03-29
use rsync to copy the changes over and cron to setup a schedule when rsync shall run...

---

### Post by oponto on 2009-03-29
Great, that was the tip I needed. :KS 

I will post my solution when I finally got it, shouldn't be a bigger problem now.

:)

---

### Post by hyper_ch on 2009-03-29
there are many howtos on rsync and cron out there. I'm sure you'll manage.

---

### Post by MrWES on 2009-03-29
> **oponto said:**
> heyo !

how do I set up an automated backup procedure for my Home Folder, 

which **knows what files have been changed/added/removed** and **applies/transfers** those changes (c*hanges only, not every file*) to the **Home Folder backup on a hdd**

every day/at any time I say it should do so (command, etc.) ?



How do I set up **the same thing** for a special folder ?
(for a quicker interval to backup my most important work every hour)

[SIZE="1"]Hopefully I didn't miss any keyword an searched for it.[/SIZE]

[COLOR="DarkOrange"]many thanks ![/COLOR]

If you are backing up folder/files that need root access, you'll need to edit the root crontab

```
sudo crontab -e
```

Otherwise, just crontab -e

Here is my crontab set to run every Sunday at 3:30am

```
# Weekly backup of Documents on external drive to /data/backup
30 3 * * 0 rsync -av /media/external/Documents /data/backup

```

Edit the time and paths to match your needs. You'll get a system email when it's completed. To ensure you get root email to your user account, make sure the /etc/aliases file is propely set:

```
root:YOURUSERNAME
```

Bill

---

### Post by nobodysbusiness on 2009-03-29
Coincidentally, I just [posted something]("http://ubuntuforums.org/showthread.php?t=1109968") about automated backup a few minutes ago. My suggestion is a little different than the replies so far. I suggest using an online service called Dropbox. I wrote a [blog post on this service]("http://pragmattica.wordpress.com/2009/03/29/protect-your-important-data-with-dropbox/"), in case you're interested.

---

### Post by oponto on 2009-03-29
I am currently doing this stuff, 

my status is:  
```
rsync -a --delete (--progress) /home/xxxx/ /media/disk/xxxx/
```

works great -.-

but there is one detail to solve, which would make bakcing up faster:

How can I log the changes I made (manually or by any program, like changing bookmarks usw..) so that only the changed folders are scanned, to avoid to waste^^ time with scanning folders, whose change date is before last backup ?

thanks for all the other suggestions, I will apply them in the next minutes^.

EDIT1: ok, currently grappling with 
```
rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3] 
```
but don't care about this error here, it was discussed very often, as google says

---

