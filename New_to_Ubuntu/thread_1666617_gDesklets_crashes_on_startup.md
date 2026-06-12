---
title: "gDesklets crashes on startup"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Light Knight 22 on 2011-01-13
When I try running gDesklets on 10.10, my connection to Daemon times out. 

I've completely removed and reinstalled, still doesn't work. But I found a few other people who had the same problem, and apparently this guide worked out for them: [http://forum.linuxmint.com/viewtopic.php?f=90&t=32554](http://forum.linuxmint.com/viewtopic.php?f=90&t=32554)

The problem is... I don't understand how to use it. Especially the last code in the article, I don't really get it. I paste it to the terminal, but nothing really happens. 

Can anyone help me with this guide and/or help me fis dDesklets?

---

### Post by Light Knight 22 on 2011-01-14
Ok, so I figured out the guide, but it didn't help any.  Here is some more information of my problem.

Starting gdesklets via terminal I get:

```
darcy@Desktop:~$ gdesklets
Starting gdesklets-daemon...
Connecting to daemon [ ###         ]
==========================================================[01/14/11-13:47:46]===
Could not import tiling module!


Cannot establish connection to daemon: connection timeout
The log file might help in solving the problem.
```
So I run:
```

darcy@Desktop:~$ gdesklets check
Checking requirements:
 - sys ... found
 - xml.parsers.expat ... found
 - xml.sax ... found
 - gtk ... found
**
ERROR:/build/buildd/pyorbit-2.24.0/src/pyorbit-utils.c:39:_pyorbit_escape_name: assertion failed: (keyword_mod != NULL)
 - ORBit ...Aborted (core dumped)

```

As you see, I'm still pretty new at linux and ubuntu and need help with things like these. 

I've removed and reinstalled gdesklets. I've also reinstalled python.

---

### Post by Light Knight 22 on 2011-01-14
Ok, so I figured out the guide, but it didn't help any.  Here is some more information of my problem.

Starting gdesklets via terminal I get:

```
darcy@Desktop:~$ gdesklets
Starting gdesklets-daemon...
Connecting to daemon [ ###         ]
==========================================================[01/14/11-13:47:46]===
Could not import tiling module!


Cannot establish connection to daemon: connection timeout
The log file might help in solving the problem.
```
So I run:
```

darcy@Desktop:~$ gdesklets check
Checking requirements:
 - sys ... found
 - xml.parsers.expat ... found
 - xml.sax ... found
 - gtk ... found
**
ERROR:/build/buildd/pyorbit-2.24.0/src/pyorbit-utils.c:39:_pyorbit_escape_name: assertion failed: (keyword_mod != NULL)
 - ORBit ...Aborted (core dumped)

```

As you see, I'm still pretty new at linux and ubuntu and need help with things like these. 

I've removed and reinstalled gdesklets. I've also reinstalled python.

---

### Post by Light Knight 22 on 2011-01-17
Bump

---

