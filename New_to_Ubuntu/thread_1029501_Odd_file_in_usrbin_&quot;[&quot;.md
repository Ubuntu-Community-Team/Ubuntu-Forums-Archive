---
title: "Odd file in /usr/bin: &quot;[&quot;"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Alex Carroll on 2009-01-03
Was messing about with "Open With" in nautilus, when I spotted this file, named simply "["

Not sure what it is, but it's certainly an odd filename. I'm using Ubuntu 8.10 AMD64. Can any of you guys check if you have it as well? What purpose does it serve?

---

### Post by Copernicus1234 on 2009-01-03
Yes we have it.

I remember reading something about it a long time ago, but cant remember its purpose right now...

---

### Post by Bonger1901 on 2009-01-03
I've got it as well. I don't know what it does but I'm sure it's nothing to be afraid of. ;)

---

### Post by Alex Carroll on 2009-01-03
Thanks for the replies, a relief to know it's not a virus as my paranoid mind would have me believe.

---

### Post by Copernicus1234 on 2009-01-03
Now I remembered (after doing a "man ["). Its a shortcut for the test command, used in shell scripting.

---

### Post by ibuclaw on 2009-01-03
Yes, it is a command :)

It is an alternative to **test**

ie:
```
test -d /home && echo "$_ is a directory"
```
Is the same as:
```
[ -d /home ] && echo "/home is a directory"
```
Which is also the same as:
```
if [ -d /home ]
then echo "/home is a directory"
fi

```
Depending on your outlook in life, you may use either one that picks your fancy :)

Regards
Iain

---

### Post by scorp123 on 2009-01-03
> **Alex Carroll said:**
> What purpose does it serve? **/usr/bin/[** is part of the **coreutils** package. To verify that you can easily ask **dpkg** to print a list of files in that package.
```
> dpkg -L coreutils | more
/.
/bin
/bin/cat
/bin/chgrp
/bin/chmod
/bin/chown
/bin/cp
/bin/date
/bin/dd
[ ... snip ... ]
/usr/bin
/usr/bin/hostid
/usr/bin/nice
/usr/bin/who
/usr/bin/users
/usr/bin/pinky
/usr/bin/[
/usr/bin/chcon
/usr/bin/dircolors
/usr/bin/du
/usr/bin/install
/usr/bin/link
/usr/bin/mkfifo
/usr/bin/nohup
/usr/bin/shred
/usr/bin/stat
[ ... snip ... ]
```

As for your other question, I simply asked the manual what the program was good for:
```
man [
```
Result I got was this:
```
TEST(1)                                                                          User Commands                                                                          TEST(1)

NAME
       test - check file types and compare values

SYNOPSIS
       test EXPRESSION
       test

       [ EXPRESSION ]
       [ ]
       [ OPTION

DESCRIPTION
       Exit with the status determined by EXPRESSION.
...
... snip ...
```

So in other words the "**[**" program is part of the OS and it performs the testing of expressions which are often used in shell programs and startup scripts.

**You best leave it untouched, OK?**

---

### Post by Bachstelze on 2009-01-03
For information, [font="monospace"][[/font] is just syntactic sugar for [font="monospace"]test[/font], and is often used instead of it in shell scripts to make their syntax more intuitive (since it makes it closer to that of C-like programming languages). Those two lines, for example, are equivalent :

```
$ if [ $x = $y ]; then echo "x equals y"; fi
```

```
$ if test $x = $y; then echo "x equals y"; fi
```

As shown here:

```
firas@nobue ~ % x=0; y=1; if [ $x = $y ]; then echo "x equals y"; fi
firas@nobue ~ % x=0; y=1; if test $x = $y; then echo "x equals y"; fi
firas@nobue ~ % x=1; y=1; if [ $x = $y ]; then echo "x equals y"; fi
x equals y
firas@nobue ~ % x=1; y=1; if test $x = $y; then echo "x equals y"; fi
x equals y

```

---

### Post by Bachstelze on 2009-01-03
For information, [font="monospace"][[/font] is just syntactic sugar for [font="monospace"]test[/font], and is often use instead of it in shell scripts to make their syntax more intuitive (since it makes it closer to that of C-like programming languages). Those two lines, for example, are equivalent :

```
$ if [ $x = $y ]; then echo "x equals y"; fi
```

```
$ if test $x = $y; then echo "x equals y"; fi
```

As shown here:

```
firas@nobue ~ % x=0; y=1; if test $x = $y; then echo "x equals y"; fi
firas@nobue ~ % x=1; y=1; if [ $x = $y ]; then echo "x equals y"; fi
x equals y
firas@nobue ~ % x=1; y=1; if test $x = $y; then echo "x equals y"; fi
x equals y

```

---

