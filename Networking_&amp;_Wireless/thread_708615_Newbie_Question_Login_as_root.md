---
title: "Newbie Question: Login as root?"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by Grimhound on 2008-02-26
What does it mean when something says to log in as root? I'm a complete newbie to Linux and I'm trying to install ndiswrapper.

---

### Post by Grimhound on 2008-02-26
So, no help?

---

### Post by tommohawk on 2008-02-27
The root user is the administrative account for any Linux system.  A normal user only has privileges to access certain files and modify certain parts of the system.  When you are trying to undertake an administrative task (something that has system wide implications) then you can be asked for the root password.  This is a security feature designed to protect your system (unlike windows where you can make system wide changes with a normal account).  

You will have set a root password when you installed your version of Ubuntu.  If you are asked for it when you are logged in on your own user account then the password is usually the same as your own user password (unless you have changed it at some point).

---

### Post by Eiríkr on 2008-02-27
One thing about Windows -- a "normal" user is actual unprivileged on WinXP, and thus is not able to completely bork the system.  The problem is that the first user account Windows creates is by default an "administrator" account, i.e. effectively the same thing as "root" in Unix terms.  And while it's technically possible to use XP as a "normal" user, there's so much Windows software that assumes administrator privileges that it's not really a pragmatic possibility.  

Anyway, to the issue at hand --

Ubuntu and a few other Unixy OSes have the root account disabled by default as a security measure.  There are differing schools of thought, but in general, the rough consensus is that it's a *very* bad idea to log in directly as root unless you have a clear idea of what it is you're doing.  One typo and you could easily wipe your harddrive.  (No, I'm not posting that command here, but leaving out a period in the wrong place is all it takes.)

The alternative is to use the [font=courier]sudo[/font] command preceding any commands that require "root" access.  [font=courier]su[/font] is the usual way to change users when you're already logged in and working from a terminal, and means "switch user".  It will switch to whatever username you type in (provided that user exists), and with no arguments, it switches you to the root account.  [font=courier]sudo[/font] is similar, but rather than logging you in as the alternate user, it runs a command (the "do" part) as that other user.  

So say you need to create a directory "utils" in another directory that you don't have privileges for, say [font=courier]/usr/local/[/font].  You'd type this:
```
sudo mkdir /usr/local/utils
```
The system will prompt you for your password (*not* the root password) and then runs the command as root.  In this case, since root made it, the new folder belongs to root.  If instead you need to create the "utils" directory in another user's Home, and want the new "utils" directory to belong to that user, you'd type:
```
sudo -u Other_Username mkdir /home/Other_Username/utils
```

While it's still possible to do Really Bad Things&#8482;, it's harder to do them accidentally.  Plus, [font=courier]sudo[/font] only runs the one command as the other user, immediately returning control to your username and thus making it that much harder to run a series of commands as another user.  While this might introduce some inconvenience, the clear improvement in system security makes it worth the trade-off.  

Good luck in your Ubuntu explorations!  :)

Cheers,

Eiríkr

---

### Post by tommohawk on 2008-02-27
> **Eiríkr said:**
> One thing about Windows -- a "normal" user is actual unprivileged on WinXP, and thus is not able to completely bork the system.  The problem is that the first user account Windows creates is by default an "administrator" account, i.e. effectively the same thing as "root" in Unix terms.  And while it's technically possible to use XP as a "normal" user, there's so much Windows software that assumes administrator privileges that it's not really a pragmatic possibility.  

Correct!  The simple answer is that 99.99% of windows users (home users) run their systems using the default administrator account that is set up when they install windows and thus it is possible for almost all windows users to bork their systems without really trying.  Or maybe I just have alot of friends who are computer illiterate!!!

---

### Post by Eiríkr on 2008-02-27
> Or maybe I just have alot of friends who are computer illiterate!!!
Well, everything's relative, but I think the root of the problem (no pun intended) is that MS is ultimately security-illiterate.  They're ever-so-gradually getting better, but oi, what a mess.  

I've read that Vista is supposed to be more like Unix in that regard, in that the default account is locked down and software is required to respect user privileges.  But then again I have no Vista and will never pay the MS tax again if I can avoid it, so I cannot evaluate these claims first-hand.  I've also read about how it's possible to set up XP for use as a normal unprivileged user, but the instructions were not for mere mortals, and even after all that hassle there's still a lot of "run as"-ing required due to bad practices followed by application writers -- ultimately making it far more trouble than it seems to be worth...  :-|

Cheers,

Eiríkr

---

