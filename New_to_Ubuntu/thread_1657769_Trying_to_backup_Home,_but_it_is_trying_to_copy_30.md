---
title: "Trying to backup /Home, but it is trying to copy 30X as much data"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by jimmy the saint on 2011-01-01
My /Home is 8 Gigs (after a LOOONG purging process).

I am trying to back it up to do a fresh install and it is preparing to move 250+ Gigs of data!  WTF?  I don't have that much free space on my backup drive, so it is failing.

What can I do here?

Thanks

Edit:  Now it's saying it needs to copy about 8 Terabytes!  WTF is going on here?

Edit2:  Now its 200 Terabytes!

Edit 3:  Now its up to 234,000 Terabytes!

---

### Post by jimmy the saint on 2011-01-01
This is nuts

---

### Post by AlphaLexman on 2011-01-01
Where are you backing up to?
It is possible to create an infinite loop during a backup... i.e. the backup file is being backed up!

---

### Post by jimmy the saint on 2011-01-01
That's kind of what I thought, but I tried to back it up to a remote server, then to a 32 Gig Thumb Drive, then to a 1.5 TB External drive.  

I'm going to try to do it from a live CD and see what happens.  Most bizarre thing that's happened to me yet.

Apparently Google should rent some storage space on my crappy laptop.  I've got room to spare!

---

### Post by AlphaLexman on 2011-01-01
post your backup script or terminal entry

---

### Post by jimmy the saint on 2011-01-01
No terminal entry.  Just drag and drop.  

The Live CD is working.  Still a little over double the reported size, but 17 Gigs can be copied to an external drive.

262 petabytes would strain my budget this soon after Christmas!

---

### Post by AlphaLexman on 2011-01-01
You should look into 'rsync'

---

### Post by tgalati4 on 2011-01-01
Perhaps you are trying to backup the entire internet?

Do you have any symbolic links or remote disk mounts in your home folder?  Perhaps a music directory on another machine?

"I'm gonna need a bigger disk . . ." :-?

---

### Post by stmiller on 2011-01-01
Yep - this won't work as it tries to infinitely copy hidden files and sym links.

Do something like this:

```

rsync -a /home/username /media/backupdrive

```

---

### Post by jimmy the saint on 2011-01-08
Thanks guys.  Next time, I'll do this.  I didn't really put much thought into it, as it was kind of a spur of the moment decision to travel with a fresh installation.

---

