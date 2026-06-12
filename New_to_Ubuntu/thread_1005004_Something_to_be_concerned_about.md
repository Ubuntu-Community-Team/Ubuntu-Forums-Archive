---
title: "Something to be concerned about ?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by kdm on 2008-12-07
Hi,

EVERYtime I now go to shutdown Ubuntu, I get the attached error message.  Is this something I should be concerned about, and/or is there a way I can know for sure which program it is ?

Thanks

---

### Post by Bölvaður on 2008-12-07
you can try closing one program/process at a time and see if it was the one causing problems.

System &#8594; Administrator &#8594; System Monitor

If that isn't working you might need to get more dirty and see what processes are REALLY under the hood.

open up the terminal Applications &#8594; Accessories &#8594; Terminal

```

ps -A

```
This gives you **A**LL processes (hence the -A)


```

ps -A | more

```
This gives you all processes in a list you can move with your keyboard.. like "space bar" and end scrolling through the list by pressing ctrl+c

to kill a process use this (note that 26400 is an example of number of the process.. you'll get the number from ps -A)
```
kill 26400
```

---

