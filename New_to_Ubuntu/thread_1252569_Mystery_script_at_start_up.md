---
title: "Mystery script at start up"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by myolbug on 2009-08-29
Whenever I reboot or start the computer, I get some script that flashes on my screen in white letters while thescreen is still black.  It happens just after is starts loading HDD 0.  I am just curious and I don't know how to stop it at that instant to see what it says.

Is there a way to read what scripts show when starting up?  Or, a way to pause it?

Thx!

---

### Post by izziere on 2009-08-29
It depends on what it says.  Try and read some of the words and then use them thus:

```
dmesg | grep words
```

Where "words" is an extract of the message you see flash up.  This will get you the full error message which you can then google or read through the lines around the error via

```
dmesg
```

to get fuller understanding. Most times it's not a problem, but it is basically an informational or error message

---

### Post by loomsen on 2009-08-29
Hi.

These are early kernel messages, telling you that your CPU is initialized and how it will be controled and so.
Many many messages, not that many infomations, so if you want to suppress them just add a quiet stanza to your bootmenu.

You may also configure the verbosity in /etc/sysctl.conf or /etc/sysconfig/*

(I dont remember exactly how ubuntu handles it)

The entry is
early.printk: 4 7 7 3 
or so.
Your actual values may be viewed with 
```

cat /proc/sys/kernel/printk

```

But these messages are for debugging purposes rather than anything else.

---

### Post by myolbug on 2009-08-30
This said command not found for the second command.  Cut and paste to terminal.

---

