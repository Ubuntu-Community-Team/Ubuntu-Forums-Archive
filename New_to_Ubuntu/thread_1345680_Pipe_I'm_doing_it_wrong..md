---
title: "Pipe: I'm doing it wrong."
date: 2009-12-04
forum: New to Ubuntu
---

### Post by knottshawk on 2009-12-04
I have intermittent luck with piping output to a new program... for example, this fails but I'm not sure why... help?

```
dmesg | gedit
```

---

### Post by kellemes on 2009-12-04
```
 dmesg > - | gedit -

```
Strange how this works with gedit..
With vim I can just..
```
dmesg | vim -
```

---

### Post by Mornedhel on 2009-12-04
Pipes work by redirecting the standard output of the left command to the standard input of the right command.

In our case, dmesg outputs text on stdout, so the pipe sees that and directs it to the stdin of gedit... who does not do anything with it. Unlike some other commands, gedit only takes filenames as an argument.

For instance, less takes an optional list of filenames as its arguments, but if none is given, it will use the stdin and work with that, so "dmesg | less" will do what you expect (display the stdout of "dmesg" in the "less" pager).

If you need to edit the contents of the dmesg output, I suggest you redirect it to a temporary file with dmesg > filename, and then edit it with gedit filename.

kellemes: I think you're editing a file literally called - here. Vim does use stdin if you tell it to, so that works.

---

### Post by knottshawk on 2009-12-04
Interesting... I swear I've had it work before without all the complication, but thanks for the answer. Hopefully I can get my simple mind to remember it! lol

---

