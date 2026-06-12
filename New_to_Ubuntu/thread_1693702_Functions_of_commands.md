---
title: "Functions of commands"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by MGTHEBOSS on 2011-02-23
What are the functions of these commands:
1.pon dsl-provider
2.poff
3.plog
4.ifconfig ppp0
????
I am using Ubuntu 10.04.

---

### Post by aeiah on 2011-02-23
read the manuals. eg:
```

man pon
man poff
```

---

### Post by Old_Man_Unix on 2011-02-23
+1[I]

pon[/I],* poff*, and *plog* all refer to the PPP protocol.  One man entry. 
```
man pon
```*ifconfig* configures a network interface.

Before you try to figure out the man pages, you might want to do some research on PPP (the Point-to-Point Protocol)

---

### Post by seawolf167 on 2011-02-23
Yup, man pages are your best friend

```
man *<command>*
```

There are some [good ]("http://ss64.com/bash/")resources online to view [general ]("http://www.linuxmanpages.com/man1/")commands, though for program specific manuals either read the man page or the provided documentation

---

### Post by whatthefunk on 2011-02-23
I also like 'whatis'  It gives a brief, one line description of something.  For example:

```
~$ whatis poff
poff (1)             - starts up, shuts down or lists the log of PPP connections

```

---

