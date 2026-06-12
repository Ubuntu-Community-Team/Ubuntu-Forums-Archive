---
title: "superuser?"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by beelzebufo on 2010-07-16
I am new to ubuntu and to computers in general, but I am enjoying playing around with my new obsession (ubuntu).  But I keep running into access problems, even when running bleach bit and things like that, I know that these access resrictions are there to protect me from myself, but I still would like to be able to access everything on my computer.  I am sort of expecting to kill this thing at some point, so I am not particularly concerned about it (I keep no important information on this machine)  Is there any way to make myself a superuser so to speak?

P.S. I understand that this is a stupid idea and will probably result in several re installs, but that's ok

---

### Post by techunit on 2010-07-16
yes but because we don't like causing problems for ourselves I can't morally tell you... there is a finite reason for those limitations... Now if all you need is root (superuser access to the filesystem I will let you know how to do that...

To get superuser access to the filesystem

hold Alt-F2 and type ```
gksu nautilus
```please be careful.

Oh and for some tips check out the link in my signature

---

### Post by 3rdalbum on 2010-07-16
Anything that requires access to things outside your home directory, or anything that could affect other users of the computer, you need to run using the "sudo" or "gksudo" (for graphical programs) commands.

---

### Post by Samulus on 2010-07-16
What are you trying to do that requires root access? Installing software and performing other admistrative tasks like modifing directories other than /home/username/etc and using software that performs tasks like that require superuser. Everything else doesn't require a password. But runnning constantly in superuser is bad. Because if you do one thing wrong on accident then the entire system could be bork if you're not careful. It's also very insecure to run as superuser. Every program you run will have the ability to do whatever it wants on the computer. Somebody else can probably explain this better..

---

### Post by staf0048 on 2010-07-16
Well, you can always use:

```
sudo
```

in front of whatever command you're issuing.

If you don't like typing sudo all the time, there's always```
su root
```

which will get rid of the need to type sudo all the time, but you're very likely to mess something up with that. You are strongly advised NOT to use your computer this way, because if you do mess something up you may not be able to fix it (without a complete reinstall anyway).

---

### Post by lisati on 2010-07-16
The preferred approach for using "superuser" privileges in Ubuntu is through the "sudo" command. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by beelzebufo on 2010-07-16
thank you guys very much, I am really just more curious than anything else about this, but I can't even seem to run an av like clam av because I never have access... anyway, thanks, just hoping to figure ubuntu out by dinking around and like I said, I am expecting to kill this poor computer a few times in the process, so no big deal

---

### Post by bodhi.zazen on 2010-07-16
> **beelzebufo said:**
> P.S. I understand that this is a stupid idea and will probably result in several re installs, but that's ok

Yep, deleting system files on any OS is a bad idea, more so if you do not yet understand how the OS works.

I suggest you take the time to learn Linux permissions and how they work:

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

chown
chmod
set permissions from nautilus

etc ...

Also read teh rootsudo wiki page.

```
sudo -i
```gives you a root shell.

```
gksu nautilus
``` give a root file manager.

Keep in mind, [s]if[/s] when you break Ubuntu you get to keep both pieces. Be careful with BleachBit and similar apps (computer janitor).

---

### Post by jrrader on 2010-07-16
> **beelzebufo said:**
> anyway, thanks, just hoping to figure ubuntu out by dinking around and like I said, I am expecting to kill this poor computer a few times in the process, so no big deal

I did that on purpose several times when I started learning Linux. It has actually been quite useful in my current job, where we all work as root all the time...  When someone kills their box I can usually spot the problem, like when someone rm'ed their etc folder...

---

### Post by beelzebufo on 2010-07-16
well... gosh, this is kind of irritating, as I have been messing around on here, I decided I wanted a vm.. for no good reason at all, but I downloaded the .bundle file and after I enabled running as executable or whatever under properties, I double click and it says I need root access... which I thought I now had...  what am I missing?

---

### Post by bodhi.zazen on 2010-07-16
> **beelzebufo said:**
> well... gosh, this is kind of irritating, as I have been messing around on here, I decided I wanted a vm.. for no good reason at all, but I downloaded the .bundle file and after I enabled running as executable or whatever under properties, I double click and it says I need root access... which I thought I now had...  what am I missing?

run ....
the ...
.bundle ...
as ...
root 

:lolflag:

```
sudo /path/to/.bundle
```

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by beelzebufo on 2010-07-16
ha ha, thanks man

---

### Post by bodhi.zazen on 2010-07-16
> **beelzebufo said:**
> ha ha, thanks man

=)

---

