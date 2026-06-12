---
title: "Backing up my Server"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by Radioman991 on 2009-10-02
Hi All:

Been running various versions of Ubuntu for a good while, but posting in the beginners forum, because I am working with my FIRST Ubuntu Server.

Running an old P III with a Gig of RAM, and not a lot of hard drive space, but that's OK for now.  Administering it with Webmin, and have DynDNS working so I can admin from work as well as home.  Also able to browse my shares at home or anywhere else for that matter.

Here's the issue.....

I need an easy way to backup my /home folder on the server.  I have an 80 Gig USB drive attached.  When I tried using the filesystem backup in Webmin, it seemed like it destroyed the partition every time, even though it says it is successful.  I unmount the drive, and plug it into my laptop, and it says unknown partition.  Go figure.

I'd be happy with a command line string and a way to make it run, say 2 or 4 times each 24 hour period.

I did pretty well so far, and made no posts when building this sucker.....although a couple of installs to  get it right, but who's counting  :-)

Any suggestions appreciated

Regards,

Radioman991

---

### Post by Paqman on 2009-10-02
> **Radioman991 said:**
> 
I'd be happy with a command line string and a way to make it run, say 2 or 4 times each 24 hour period.


Assuming your server runs 24/7, you just need a cron job that will check your backup drive is mounted and/or mount it as required, then run rsync to copy the files over.

If your server isn't on all the time you can do the same but using anacron instead of cron.

---

### Post by Radioman991 on 2009-10-02
The plan is for it to be on all the time.  I am not as well versed at the terminal as I would like.  The idea of rsync is appealing, from some Google serches I have done, but the syntax is somewhat baffling at first.

I'd feel confident if I could run the command, unmount the drive, mount it in the laptop, and SEE the results, and I would put it back and forget...until the server crashes, and I NEED that backup.

---

### Post by Paqman on 2009-10-02
Rsync is pretty straightforward, it just has a baffling amount of options. Which ones you pick depends on what kind of result you want. For example, do you want it to delete files on the destination that are no longer on the source? And do you want it to skip syncing files that are newer on the source?

The first time it runs, it'll be fairly slow, as it will create all the files on the destination. After that it can be very fast if you set it up to only copy the changes. The result on the destination is an identical copy of the source, so you could certainly plug it into another machine and inspect the result.

---

### Post by MrWES on 2009-10-02
> **Paqman said:**
> Rsync is pretty straightforward, it just has a baffling amount of options. Which ones you pick depends on what kind of result you want. For example, do you want it to delete files on the destination that are no longer on the source? And do you want it to skip syncing files that are newer on the source?

The first time it runs, it'll be fairly slow, as it will create all the files on the destination. After that it can be very fast if you set it up to only copy the changes. The result on the destination is an identical copy of the source, so you could certainly plug it into another machine and inspect the result.

+1 for Rsync, it's what I use on my home file/media server. I put the cron job in root's crontab with:
```
sudo crontab -e
```
I then added this line:
```
# Weekly backup of Documents on external drive to /data/backup
30 3 * * 0 rsync -av --delete --progress  /media/external/Documents /data/backup

```
It runs the backup weekly, on Sunday morning and I use the --delete flag, as I wanted files that I deleted from the source to also be deleted in the backup destination. It'll send an system email when the job is completed, just make sure you have your username set to root in /etc/aliases
```
root:	yourusernamehere

```

Change the date/time, source and destination to suit your needs.

~Bill

---

