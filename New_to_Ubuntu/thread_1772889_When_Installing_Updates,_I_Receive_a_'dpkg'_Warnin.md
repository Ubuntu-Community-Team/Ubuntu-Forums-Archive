---
title: "When Installing Updates, I Receive a 'dpkg' Warning Message"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by lhb1142 on 2011-06-01
:confused: I am running Ubuntu 11.04 on a 32-bit x86 machine (Acer Extensa 5620-6419) on which I previously had no problems. 

Soon after network upgrading to Natty, I (foolishly) ran Computer Janitor.

Now, every time I run the Update manager, when the updates are installing, I receive this message:

**dpkg: warning: parsing file '/var/lib/dpkg/available' near line 44439 package 'mac-3.99-04': error in version string 'b3-1': version number does not start with digit**

I do not know what this means but it does have some effect; since this has happened, once in a while my computer will crash and then restart. Also, when opening any of my Places (Home Folder, Documents, etc.), the computer will 'hang' for a bit - the Place opens but it takes quite a while until the circle turns into the cursor.

Also, every once in a while Firefox crashes (which it never did previously).

I have no idea what any of this means. Can anyone help me? Thank you.

P.S. I have subsequently found out that Computer Janitor is absolutely no good and it will be removed from Ubuntu in 11.10. I wish I had known that prior to running it.

---

### Post by seawolf167 on 2011-06-01
Please run

```
dpkg --clear-avail
sudo apt-get update
sudo apt-get upgrade
```

and let us know if it has been fixed

---

### Post by lhb1142 on 2011-06-01
> **seawolf167 said:**
> Please run

```
dpkg --clear-avail
sudo apt-get update
sudo apt-get upgrade
```

and let us know if it has been fixed

Dear Seawolf,

I ran the commands (I had to use sudo before the first one as well) and the whole process completed with no errors listed.

Of course I won't know if it worked or not until there are more upgrades to Ubuntu 11.04. If it did work, I won't see that message any more and I hope there well be no more crashes.

I'll be sure to let you know and I thank you very much for your help.

Lawrence

---

### Post by seawolf167 on 2011-06-01
If you ran the last two commands (update & upgrade) without problems then your issue has been fixed (those commands are the CLI versions of the Update Manager).

Glad the problem is solved!

---

### Post by lhb1142 on 2011-06-02
> **seawolf167 said:**
> If you ran the last two commands (update & upgrade) without problems then your issue has been fixed (those commands are the CLI versions of the Update Manager).

Glad the problem is solved!

Dear Seawolf,

There was an update this morning (gdm - Gnome Desktop Manager) and, when I downloaded & installed it, I did *not* see the dpkg error message.

I hope that this is the end of that particular problem and I thank you very much for your solution. I will not know for sure until several more updates have been offered but it appears that your solution worked.

It has not, however, solved the problem of the 'hanging' which occurs when I open any of my Places; I still have to wait for a number of seconds before the spinning wheel turns into the cursor.

Plus I will not know for sure that the crashing (both of Firefox as well as of the computer itself) has been solved until several days have passed; thus I will hold off in marking this problem 'solved' until I am absolutely certain that it has been.

But I do thank you again very much for your solution to the dpkg error message problem. I'll keep you posted as to any further developments.

Lawrence

---

### Post by seawolf167 on 2011-06-02
:) Hopefully [any] subsequent fixes for you are this easy!

---

### Post by lhb1142 on 2011-06-06
> **seawolf167 said:**
> :) Hopefully [any] subsequent fixes for you are this easy!

Dear Seawolf,

Today there were a lot of updates and, during installation, I saw no dpkg error message. So that problem has been fixed.

Thank you very much. I have marked this problem solved.

Unfortunately, this error was evidently not the cause for my computer crashing at various and unpredictable times.

Sometimes I'll go a whole day with no crashes but every once in a while - such as this morning - it does crash, generally in the middle of a Firefox session; the computer reboots and, when I open Firefox, I am taken right back to the page on which the crash occurred (even with my login credentials intact), so it's no *major* problem, just very annoying.

I had thought that that dpkg error was contributing to this anomaly but it is obviously caused by something else.

But thank you again for your solution to the dpkg error problem.

Lawrence

---

