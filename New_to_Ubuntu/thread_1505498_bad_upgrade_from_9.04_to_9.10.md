---
title: "bad upgrade from 9.04 to 9.10"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by kweetniet on 2010-06-09
after upgrade

kde won't start up automaticly

after "kdm" command KDE starts up.
but no internetconnection (wired wireless vpn) and no mousepad (a ext mouse yes)

What should i do?
please help step by step

*i'm a wannabe but still thinking as a newbe*

---

### Post by cariboo on 2010-06-09
It sounds like your upgrade didn't finish. Start in recovery mode, hold the shift key down just after post, to see the grub menu, use the arrow keys to select recovery mode. Once at the menu select drop to root prompt with networking. Once at the prompt type:

```
apt-get -f install
```

Once that command has finished type:

```
aptitude update && aptitude safe-upgrade
```

The first command with install any missing dependencies, and the second command will install any missing programs that weren't installed during the upgrade process.

---

### Post by kweetniet on 2010-06-09
thanks for  reaction.

I tried:
I reached grub menu bij hitting <esc> on the right moment

I tried several 9.04 recovery modes text.17 text .18 and 19

each time it started with memory check then each time starting up th e same way::

shows lines like
starting ......
...done

last line :
checking battery state...
... done

cursor

so same point of no return??I can log in by <windows tag f5>

I have no clue

---

### Post by kweetniet on 2010-06-10
please need help on this 
my laptop is stuck and i need it for my job

---

