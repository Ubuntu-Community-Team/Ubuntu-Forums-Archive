---
title: "cal terminal command"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by dzon65 on 2011-03-14
How can I add the cal terminal command to my openbox menu?
Tried lxterminal -e cal, but that just shows the terminal for a split second.

---

### Post by Blutkoete on 2011-03-14
The terminal will close the moment it has executed the command. As cal doesn't wait for a keyboard input, that's quite immediately.

I don't know how it is with *lxterminal *(try *lxterminal --help* to look for the right option), but you might use

```
lxterminal --noclose -e cal
```

to solve your problem.

---

### Post by dzon65 on 2011-03-14
Nope. Doesn't work.

---

### Post by Blutkoete on 2011-03-14
Looks like *lxterminal *doesn't have a *--noclose* option.

Maybe we can build us one ourselves. Try

```
lxterminal -e "cal && read"
```The *read* part should make it wait for a key press, at least that works for me.

---

### Post by cipherboy_loc on 2011-03-14
Try:

```

lxterminal -e 'cal ; sleep 100000000'

```



You can (and probably should) change the sleep number. Its in seconds. 

Cipherboy

---

### Post by dzon65 on 2011-03-14
Same thing. Split sec.

---

### Post by cipherboy_loc on 2011-03-14
So after a bit of work, here is what you need to do:

```
lxterminal -e 'bash -c "cal ; read"'
```

What I think happens is that when you use -e, bash isn't called. Probably a bug which might need reporting; other terminals (gnome-terminal, xterm) call bash even with -e.


Cipherboy

---

### Post by dzon65 on 2011-03-14
Yep, works. Just read some on the bash.
Thanks.
Regards,J.

---

### Post by dzon65 on 2011-05-27
For  some reason there's no more highlighted current day in the call -y command.
I'm trying to get this workaround to open with lxterminal, but it keeps giving me syntax errors.
This needs to be inserted:
cal -y | awk -v month="`date +%m`" -v day="`date +%e` " '{m=int((NR-3)/8)*3+1; for (i=0;i<3;i++) {t[i]=substr($0,1+i*22,20) " "; if (m+i==month) sub(day,"\033[0;31m&\033[0m",t[i]);} print t[0],t[1],t[2];}'

---

### Post by dzon65 on 2011-05-27
Okay. I made a script for it and  use this command:
lxterminal -e  'bash -c "~/Scripts/calendar.sh ; read"'
Works a  charm.

---

