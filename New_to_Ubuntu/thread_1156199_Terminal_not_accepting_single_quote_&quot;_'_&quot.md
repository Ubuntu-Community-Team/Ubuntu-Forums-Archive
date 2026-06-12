---
title: "Terminal not accepting single quote &quot; ' &quot; but accepts &quot; ` &quot; which I can't type"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by davidstri on 2009-05-11
The terminal won't except my single quotes with this command for some reason. This is how it looks like when I type out the command:
```
echo 'date +%y-%m-%d_AT_%T'   something happened at this time >> what_happened_at_these_times
```(notice the single quotes before date and after T)
This is what the input of the file looks like with my single quotes:

date +%y-%m-%d_AT_%T something happened at this time

but when I type in the command like this with quotes copied from website:
```
echo `date +%y-%m-%d_AT_%T`   something happened at this time >> what_happened_at_these_time
```(notice different single quotes before date and after T)
the input looks like this:

09-05-11_AT_14:08:48 something happened at this time

which is correct.

How can I make the keyboard type this single quote ' and this single quote ` ?

---

### Post by bodhi.zazen on 2009-05-11
The second single quote is a ` or back tic and as you can see is not the same a '

Location varies, but the back tic on  my keyboard is just to the left of the number 1 key.

---

### Post by decoherence on 2009-05-11
As bodhi.zazen said; backticks, not single quotes.

The preferred way of writing

```
echo `date +%y-%m-%d_AT_%T`
```

is to do it like

```
echo $(date +%y-%m-%d_AT_%T)
```

at least in BASH. The $(...) notation, aside from being clearer, has other benefits like nesting and more sane handling of escape sequences. A couple of contrived examples:

Nesting:
```
$ echo `echo `echo thing``
echo thing

$ echo $(echo $(echo thing))
thing
```
 
Escaping:
```
$ echo `echo \\`
                           <-- (no output!)

$ echo $(echo \\)
\
```

---

### Post by davidstri on 2009-05-12
Thanks, I overlooked the backtic on my keyboard, guess I never used it before, and the parenthesis also worked perfectly.

---

