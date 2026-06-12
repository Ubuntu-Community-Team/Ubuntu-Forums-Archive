---
title: "bad substitution error"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by evanryan on 2011-07-25
I've started writing bash scripts but I can't seem to get string substitution to work. When I type something like.
var="hello name"
echo ${var/"name"/"bob"}

into the terminal it works fine and prints "hello bob". But when I type the exact same thing in a .sh file I get a Bad substitution error. Help please!

---

### Post by idoitprone on 2011-07-25
> **evanryan said:**
> I've started writing bash scripts but I can't seem to get string substitution to work. When I type something like.
var="hello name"
echo ${var/"name"/"bob"}

into the terminal it works fine and prints "hello bob". But when I type the exact same thing in a .sh file I get a Bad substitution error. Help please!

It just means that somethings has changed between you running in the terminal to when you run it in the script

Since there is nothing wrong with your script, then there is something wrong with your shell

Add this at the beginning of you shell to figure out which shell are you using.
```
echo $0
```

To fix you problem, add this to the beginning of the script
```
#!/bin/bash
```

```
[\u@\h \W]$ echo $0
dash
[\u@\h \W]$ var="hello world"
[\u@\h \W]$ echo $var
hello world
[\u@\h \W]$ echo ${var/hello/cat}
dash: Bad substitution
[\u@\h \W]$ 
```

here is a case when the script will fail in the terminal

[http://ubuntuforums.org/showthread.php?t=1474591](http://ubuntuforums.org/showthread.php?t=1474591)
more proof

---

### Post by bodhi.zazen on 2011-07-25
lolwut ?

The problem is an ambiguous variable.

Brackets {} are used to prevent that.

So when you call a variable, say foo

$foo is clear

so is $foo bar

but without the space, $foobar is ambiguous.

use ${foo}bar

```
sh-4.2$ foo="ice cream"
sh-4.2$ echo $foo
ice cream
sh-4.2$ echo $foo bar
ice cream bar
sh-4.2$ echo $foobar

sh-4.2$ echo ${foo}bar
ice creambar
sh-4.2$
```

```
$sh
sh-4.2$ var="hello world"
sh-4.2$ echo $var
hello world
sh-4.2$ echo ${var}/hello/cat
hello world/hello/cat
sh-4.2$
```

---

### Post by bodhi.zazen on 2011-07-25
OIC, you are talking about dash.

In Ubuntu 'sh' is a link to dash, and you are doing string substitution using bash syntax.

There is not a direct way to do this in dash, you need to use tools such as grep, sed, or awk

```
#!/bin/dash
var="hello name"
echo $var
echo $var | sed -e 's/name/bob/'
```

In fedora, sh is linked to bash, which is why my example worked.

See also:

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

