---
title: "Force Mounting a Drive"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Flirtilizer on 2009-08-04
I have a drive that is sickly.  I hoped I could read it with Ubuntu but couldn't.  Got the instructions to force a mount and tried it but I couldn't figure out what format it wanted for my password. What do I need to do after I enter the command.

Any danger with ths?  If the drive is already trashed, I don't see what I could hurt.

thanks

---

### Post by Sidewinder1 on 2009-08-04
If you've installed Ubuntu, the password is your usual log-in password. If you're running Ubuntu from live CD???? If so, perhaps someone more knowlegable than I could chime in...
HTH,
Side

---

### Post by wizard10000 on 2009-08-04
> **Sidewinder1 said:**
> If you've installed Ubuntu, the password is your usual log-in password. If you're running Ubuntu from live CD???? If so, perhaps someone more knowlegable than I could chime in...

Well, I'm probably not more knowledgeable but I'll throw in my [IMG]http://ebassist.com/forum/images/smilies/2c.gif[/IMG]

:)

I wouldn't mount *any* local partitions if I had a drive in my machine that was questionable - boot the thing from a live CD, mount the drive then run your diagnostics on it.

BTW - you've still gotta mount it using sudo but the superuser account on a live CD doesn't have a password.

---

### Post by Sidewinder1 on 2009-08-04
Thanks Wiz!  Forgot about that. Haven't run a live CD since my initial install (2007). Unless, of course, I'm installing on someone elses system. :-)
Side

---

### Post by harry2006 on 2009-08-04
i guess force mounting will not do any harm...

---

### Post by H2SO_four on 2009-08-04
I ran into a similar issue and the live CD was asking me for a login and password. login: ubuntu and leave password blank. 

Best of luck!

---

### Post by wizard10000 on 2009-08-04
> **H2SO_four said:**
> I ran into a similar issue and the live CD was asking me for a login and password. login: ubuntu and leave password blank. 

Best of luck!

I mounted a bad hard drive with a 32-bit Jaunty live CD and sudo just worked.  Guess maybe different releases have different requirements  :)

edit:  Oops.  That's a lie - it wasn't a Jaunty CD, it was Hardy because I couldn't find my Jaunty CD  :)

---

### Post by Flirtilizer on 2009-08-05
My problem was the format of sudo / password it wanted.  I remembered sudo but it would never take my password.  Hmmm, maybe I was where I was suppose to be and didn't realize it.  LOL

I'll dig up the entire command and post it if I can't get booting from a CD to work.

Thanks.

---

