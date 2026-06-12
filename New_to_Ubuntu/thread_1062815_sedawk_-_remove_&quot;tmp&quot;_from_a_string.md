---
title: "sed/awk - remove &quot;/tmp/&quot; from a string"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by jasonmh on 2009-02-07
Hello, thank you for reading.
I'm trying to isolate the file **Flashxxxxx**, where **xxxxx** is wild.

With the pattern:
```
$ echo /tmp/FlashdrVWoY
```
How do I remove the "/tmp/" from the echo so that I'm left with only FlashdrVWoY?

The full command that I'm using to find that Flash file is this:
  This command finds the firefox [pid], does a lsof on it, and spits out the location and name of the Flashxxxxx file.
```
$ lsof -p `ps -A|grep firefox|grep -v grep|awk '{print $1}'` | grep /tmp/Flash | awk '{print $9}'
/tmp/FlashdrVWoY
```

---

### Post by glennric on 2009-02-07
Just add
```
| sed 's:/tmp/::'
```
To the end of your command

---

### Post by cmnorton on 2009-02-07
How about this?

echo /tmp/FlashdrVWoY | awk -F '/' '{print $3}'

---

### Post by jasonmh on 2009-02-07
Thank you! :D Those man pages for sed and awk are no help at all! I looked through them looking to explain your examples, and it's like they're not written in any form of English :/

---

### Post by sdennie on 2009-02-07
There is also a command to do this just append a:

```

| basename

```

That strips off the the path (and if you specify an extension, the extension too).  Conversely, dirname strips off the filename in a path.

Edit:
Actually, it looks like basename doesn't accept input from stdin (odd).  You'd have to backtick your final awk command and use it as the argument to basename.

---

