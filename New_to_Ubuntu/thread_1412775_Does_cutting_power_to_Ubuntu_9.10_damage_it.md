---
title: "Does cutting power to Ubuntu 9.10 damage it?"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by RedOctober on 2010-02-21
(IMPORTANT: Assume that the computer is not doing anything at the time of power outage)

I'm from the Microsoft world where, if you pull the power cord out of the wall on your PC, you run a 40% chance of damaging the OS so it complains and has to repair itself, and a 5% chance that it will not be able to recover and you'll have to reload the OS.

Does Ubuntu have the same vulnerability?  Or can it loose power without damage.

Remember, I'm only interested in an idling situation. No files are actively being written to or read from, no databases are involved.

Thanks in advance for your help.

---

### Post by Temposs on 2010-02-21
As far as I know, the main concern would be cutting power while you're writing to the disk. I've read there is a chance of losing/corrupting the data you were working with in that case, but it doesn't happen too often.

Other than that, I'm not aware of a problem with cutting power to the machine, other than that your applications and Ubuntu's background processes may have shutdown scripts which, if not run, may make for a slightly less smooth experience when you start them again. So, you should try to shut down properly when possible.

---

### Post by spiky001 on 2010-02-21
I have done it a couple of times still ok lol, like any system it dose have to shut down background process so i,m sure it can do just as much damage to the system  best avoid doing it

---

### Post by ChildOfMana on 2010-02-21
The filesystem Ubuntu uses (ext3) isn't as vulnerable to sudden shut downs as the Windows filesystem (NTFS) is so sudden loss of power is *less* likely to result in data loss/corruption.

That said though, ext3 isn't invulnerable and you should always try to shut down properly where possible.

As stated above if you're actively reading from/writing to disk when the power loss happens then you may lose/corrupt the date being read/written.

**Edit:** ext3 is a [journaling]("http://en.wikipedia.org/wiki/Journaling_file_system") filesystem - which is what makes it slightly more resistant to data corruption than NTFS... just in case you were wondering.

---

### Post by mcduck on 2010-02-21
> **RedOctober said:**
> (IMPORTANT: Assume that the computer is not doing anything at the time of power outage)

I'm from the Microsoft world where, if you pull the power cord out of the wall on your PC, you run a 40% chance of damaging the OS so it complains and has to repair itself, and a 5% chance that it will not be able to recover and you'll have to reload the OS.

Does Ubuntu have the same vulnerability?  Or can it loose power without damage.

Remember, I'm only interested in an idling situation. No files are actively being written to or read from, no databases are involved.

Thanks in advance for your help.

There really isn't such thing as truly idle on any modern operating systems. There's *always* some system task going on in the background, if nothing else then at least some system log process that every now and then writes to your disk...

So, there is always a risk of something breaking in case of power outage, no matter what operating system you run and what file system you use. But, like already mentioned, Ext filesystems are pretty good at recovering from such situations so I'd say that the risk of things breaking badly is a bit smaller than on Windwos. But it's still something you really want to avoid from happening...

---

### Post by paydaydaddy on 2010-02-21
I experienced a sudden and unexpected power outage a few weeks ago. I was working at the computer at the time (Kubuntu 9.10). After power was restored the computer would not boot. Was able to get into recovery mode and the OS basically fixed itself. The only data loss was what I was working on at the time. Another computer running pcbsd ran a self check, auto corrected a few things and booted. My wife's computer with xp home did a check disc then booted. What does it all mean? I have no idea!

---

### Post by switch10 on 2010-02-21
cutting the power on any machine, with any OS is possibly destructive.  Don't do it.  Power down your machine properly.  Press and hold the power button until it shuts off.

---

### Post by mkvnmtr on 2010-02-21
Here in Mexico I have experienced over 20 power outages since I started running Ubuntu. Normally on rebooting it runes a disk check before letting me log in. Sometimes it has to fix something sometimes it does not. It has never broken my system and I have never lost anything.So far it has not happened when I had a virtual system running. I understand that will require some repair. I never used windows but with mac I never lost the system either.

---

### Post by lovinglinux on 2010-02-21
I have experienced more than 10 power outages since November and none of them resulted in any damage.

---

### Post by Mark Phelps on 2010-02-22
Just to set the record straight, NTFS is ALSO a Journaling file system, in fact, Vista and Win7 use an enhanced version of NTFS known as Transactional NTFS.

So, with a modern version of Linux or MS Windows, you WILL get a journaling filesystem.

---

