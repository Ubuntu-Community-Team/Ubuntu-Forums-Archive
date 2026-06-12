---
title: "Best Backup Software ?"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by Frogs Hair on 2010-03-18
Hi,

I have searched the above question, and didn't find much . What is the best software in the
repository for a basic backup of current system configuration and documents? It seems that when I choose software, I return to the forums to find that the software is out dated and no longer supported. I would also be interested outside sources as well.

                                                              Thanks

---

### Post by Roasted on 2010-03-18
Hmm, I personaly use rsync. It's a command line based backup program, but I set it up to be fully automated.

What's your setup like? Do you have another hard drive in your system or something? What is your backup location?

My setup consists of 2 hard drives. 1 is my main drive, the other is for backup data. Then I set up my rsync command, which is:

rsync -a --progress --delete /home/jason/ /media/localbackup/

rsync = command
-a = archiving (preserves time stamps, etc)
--progress = shows me progress if I run it manually
--delete = deletes files that no longer exist in the host drive
/home/jason = my home directory (source)
/media/localbackup = my backup drive (destination)

Then I just tag that script to run every 12 hours and it runs accordingly.

That's the CLI way to do it. There's programs that work as frontend GUI's for rsync, such as GAdmin-Rsync. There's quite a few other programs that do zipped backups in increments, you could give that a whirl too.

But anyway, that's *my* setup in case it helps.

---

### Post by VernonA on 2010-03-18
You could try Back In Time (see [http://backintime.le-web.org]("http://backintime.le-web.org"))

---

### Post by Frogs Hair on 2010-03-18
> **Roasted said:**
> Hmm, I personaly use rsync. It's a command line based backup program, but I set it up to be fully automated.

What's your setup like? Do you have another hard drive in your system or something? What is your backup location?

My setup consists of 2 hard drives. 1 is my main drive, the other is for backup data. Then I set up my rsync command, which is:

rsync -a --progress --delete /home/jason/ /media/localbackup/

rsync = command
-a = archiving (preserves time stamps, etc)
--progress = shows me progress if I run it manually
--delete = deletes files that no longer exist in the host drive
/home/jason = my home directory (source)
/media/localbackup = my backup drive (destination)

Then I just tag that script to run every 12 hours and it runs accordingly.

That's the CLI way to do it. There's programs that work as frontend GUI's for rsync, such as GAdmin-Rsync. There's quite a few other programs that do zipped backups in increments, you could give that a whirl too.

But anyway, that's *my* setup in case it helps.

Thanks for your Time

I use a single hard-drive If I had two I would run a mirror setup so if one drops out the other takes over .

---

### Post by Frogs Hair on 2010-03-19
> **VernonA said:**
> You could try Back In Time (see [http://backintime.le-web.org](http://backintime.le-web.org))

Hi,

I decided to use your suggestion BIT is simple and does what I need it to do . Thanks!

---

