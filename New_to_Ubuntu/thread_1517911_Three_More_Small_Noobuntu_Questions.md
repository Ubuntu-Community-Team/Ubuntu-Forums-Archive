---
title: "Three More Small Noobuntu Questions"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by Cleveland Rock on 2010-06-25
1.) How do I make a launcher on the desktop which launches multiple programs at once? With Windows, I could do this with a batch file or something.
2.) How do I move files into and out of protected folders *without* using the terminal? It's a pain in the butt to have to open the terminal, type in something like "sudo mv *.pk4 /usr/local/games/doom3/base", then enter my password. Why can't I just drag and drop?
3.) Can I make it so I don't have to enter my password as long as I'm logged in? I'm tired of entering my password just to use the "sudo" command or the update manager. Is there a way around this?

Thanks again, guys.

---

### Post by oldos2er on 2010-06-25
You can create batch files on Linux; they are referred to as shell scripts or just scripts. [http://bash.cyberciti.biz/guide/Main_Page](http://bash.cyberciti.biz/guide/Main_Page)

**gksu nautilus** will give a GUI file manager with admin privileges. You may need to open two instances of it depending on where the files you want to move or copy are. Also, **sudo -i** will give you a persistent terminal with admin privileges. Type "exit" when you're done.

There is info on tweaking /etc/sudoers here: [http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

---

### Post by Cleveland Rock on 2010-06-25
Thanks, but I still have a problem with #3. I want everything to always assume that I am the root user as long as I am logged in. That way, I don't have to enter my password to perform administrative commands, I don't have to use the sudo command, etc.. Is that possible?

---

### Post by oldos2er on 2010-06-25
> **Cleveland Rock said:**
> Is that possible?

Yes, it's possible, but I would advise against it. See [https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account](https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account)

---

### Post by -kg- on 2010-06-25
What you are asking for is tantamount to logging in as root.  That is strongly discouraged by Canonical and the majority of the users and forum administration and staff, and is information that is restricted from being published in these forums.

There is a wealth of information on the Internet and numerous sites that have published this information.  It is highly recommended that you not do so, since when you log in as root, anyone who has access to your computer (including someone hacking in from the outside) will have root access as well.

In any case, Google "Ubuntu log in as root" or something similar and I'm sure you'll find the information you're looking for.  Before you do, though, I wanted you to consider what I said above.

---

### Post by Cleveland Rock on 2010-06-25
That's no good, then. Okay, that means all three of my questions are answered. Thanks!

---

### Post by -kg- on 2010-06-25
> **oldos2er said:**
> Yes, it's possible, but I would advise against it. See [https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account](https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account)

I am amazed that this link gives that information.  I was under the impression that information was all but forbidden on this site, but obviously I was wrong.

***_Do read and heed the warnings_, though!***  They are quite right, and a reason that the very few viruses that have been written for Linux have gone anywhere.  For that matter, that's why the viruses written for Windows have been so successful.

Make those viruses, trojans, and hackers hack your strong password, and they'll come up against a brick wall rather than easy pickin's.

> **Cleveland Rock said:**
> That's no good, then. Okay, that means all three of my questions are answered. Thanks!

YW, and I'm glad you made the right decision.

---

### Post by oldos2er on 2010-06-26
> **-kg- said:**
> I am amazed that this link gives that information.  I was under the impression that information was all but forbidden on this site, but obviously I was wrong.


I don't think the idea of "forbidden information" is a viable one, because in explaining Linux security to someone new to it you need to explain the root account, why Ubuntu disables the root account, and why very few other Linux distros do the same. At some point the fact that one *can* enable a root account on Ubuntu is going to be discovered, hopefully *after* the new person's understood the Ubuntu security philosophy.

Making informed decisions is what's important.

---

