---
title: "Restore Point equivalent"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by wojmur on 2009-08-24
Hi all,

I recently started playing with Ubuntu on a home desktop. All good so far, trying to navigate through the wide ocean of possibilities.

One of the questions is: apart from beeing a BAD THING, windoze has a few nice ideas, one of them being a Restore Point. It occasionally saves one's back side or at least some nagging from  wife and kids.

Is there any equivalent of that in linux / ubuntu world? I'm guseesing that would have to involve some sort of "version control" system spanning config files (/etc), various bin, lib and other links under /usr, settings in all users' home dirs, etc. All sounds more and more unlikely while I'm writing.

I guess what I'm asking is, say I'm mucking around with installing/updating/configuring software or system and something goes wrong, and something stops working. And, say, being a poet rather than a computer enthusiast, I don't really know what I've actually done. I might have read something on the net and tried it, but I put space in the wrong place. Is there a big Ctl-Z button (logically speaking, not necessarily being an actual button) I can press to undo my last few actions, up to some sort of a checkpoint? Or is it just me and the internet full of friendly computer enthusiasts who will grab my hand and steer me back to the path? That's provided my internet is still up :)

I know there is backup/restore.

But, being a poet, I don't even know what you mean ;)

I guess I want a miracle (not that windoze is that miraculous). Any chance?

---

### Post by rsiddharth on 2009-08-24
Check this link out : [http://ubuntuforums.org/showthread.php?p=7629686](http://ubuntuforums.org/showthread.php?p=7629686)   and see whether that helps . It seems to me that there is no Restore Point like functionality in ubuntu by default .

---

### Post by kpkeerthi on 2009-08-25
There are applications that you could use to create periodic 'Snapshots' of your harddrive and then 'Restore' back from any of the snapshots you created. You could even automate the snapshot creation process.

Checkout backintime and flyback.

---

### Post by wojmur on 2009-08-25
Thanks for that, I had a look at both. Yes, they both sound like tools that could be used in implementing a Restore Point like system. The difference between them and windoze is, of course, that being an average mum and dad user I don't have a hope to know what and where should be getting backed up. I'd only hope to know where to find my "Ctl-Z button".

So we are not quite there yet.

Oh well, one day, perhaps.

---

### Post by 3rdalbum on 2009-08-25
> **wojmur said:**
> Thanks for that, I had a look at both. Yes, they both sound like tools that could be used in implementing a Restore Point like system. The difference between them and windoze is, of course, that being an average mum and dad user I don't have a hope to know what and where should be getting backed up. I'd only hope to know where to find my "Ctl-Z button".

So we are not quite there yet.

Oh well, one day, perhaps.

Those sorts of snapshot programs should come preconfigured to avoid the directories that don't need to be backed up, like /tmp, /var/log and (sometimes) /home.

If in doubt, create snapshots of everything except /tmp; if you're not worried about deleting or messing up your user-specific files (things in /home) then I'd recommend telling your software to avoid that directory too.

---

