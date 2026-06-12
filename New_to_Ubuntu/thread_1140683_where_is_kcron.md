---
title: "where is kcron?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by blairm on 2009-04-27
Hi,

Have downloaded kcron via synaptic in jaunty but it isn't appearing anywhere in the menu. When I try to start it from the command line the response is command not found.
Have tried using sudo but that made no difference.
Anyone else had this problem?

Cheers,

Blair

---

### Post by llamabr on 2009-04-27
```
which kcron
```

---

### Post by blairm on 2009-04-27
Sorry, not sure I understand. Entered which kcron in the command line and nothing appeared to happen ie

```
blairm@blairm-desktop:~/Documents$ which kcron
blairm@blairm-desktop:~/Documents$ 

```

Blair

---

### Post by llamabr on 2009-04-27
Hi, yes, I'm sorry, I just installed it to check, and I don't know where it put it, either.

Have you tried booting into kde, where it's probably easily findable in the menu?  Gnome probably doesn't include a spot for it.

I also just installed the kdeadmin package, which tells me that:

```
kde4-menu: You must specify an application-id such as 'kde4-konsole.desktop'

```

Try running it inside of kde.

---

### Post by llamabr on 2009-04-27
fwiw, there's a gnome version:

```
gnome-schedule - GNOME scheduler for automatic tasks

```

probably already installed.

---

### Post by blairm on 2009-04-27
Hi,

Thanks for your reply. I am in KDE; did a search in the menu and checked manually as well, and the attempt to launch it from the command line was also in a kde session.
I can do cron manually, but find it a bit of a pain; was hoping kcron  might make things faster,

---

### Post by llamabr on 2009-04-27
I edit my own cron too, and so put the following in there, to help me keep it straight:

```
#*     *     *     *     *  command to be executed
#-     -     -     -     -
#|     |     |     |     |
#|     |     |     |     +----- day of week (0 - 6) (Sunday=0)
#|     |     |     +------- month (1 - 12)
#|     |     +--------- day of month (1 - 31)
#|     +----------- hour (0 - 23)
#+------------- min (0 - 59)

```

---

### Post by george1984 on 2009-04-28
Hello

Running Jaunty_64-ext4-Gnome (Candidate + updates)

Kcron installed, but I have same problem i.e.

            no entry in menu
            command kcron gives response "command not found"

Also, if do command "cron" this is the response...

"cron: can't open or create /var/run/crond.pid: Permission denied"

Also, if I do command "sudo cron" this is the response...

"cron: can't lock /var/run/crond.pid, otherpid may be 3316: Resource temporarily unavailable"

   Is it possible that I have done something to cause this? I can backup as at today and over-write using previous backup to check this. Have to use dd which is a bit of a pain. I'll do this and report back.

---

### Post by george1984 on 2009-04-28
Overwrote the backup dated 2009-04-19.

Behavior of kcron and cron are unchanged.

    Are many people having this problem?

---

### Post by mbeltagy on 2009-04-28
Having the same problem here too.

---

### Post by dixonstalbert on 2009-06-08
For some reason Kcron package in Jaunty repository does not contain the executable binary /usr/bin/kcron

I downloaded kcron from debian etch here:

[http://packages.debian.org/etch/kcron]("http://packages.debian.org/etch/kcron")

It seems to have installed and is working without errors.

---

### Post by fchristophersen on 2009-06-23
I had the same problem in Jaunty. I downloaded Hardy's Kcron .deb file from [http://packages.ubuntu.com/hardy-backports/kcron](http://packages.ubuntu.com/hardy-backports/kcron) and it seems to work fine. It's the KDE 3.5 version, probably nobody ported Kcron to KDE 4 yet. It's necessary to block this old version package in Synaptic, so it doesn't get overwritten with the new (not working) one, when updating the system.

---

