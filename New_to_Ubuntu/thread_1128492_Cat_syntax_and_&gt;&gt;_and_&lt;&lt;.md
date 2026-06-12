---
title: "Cat syntax and &gt;&gt; and &lt;&lt;"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by BetterSense on 2009-04-17
I remember seeing an example of how to simply use either echo or cat to send text to a file, with the ability to constantly append until you enter a keyword. It was something like
```

cat >>mynotes.txt <<EOF
```

and you could type as long as you wanted until you typed EOF (which could be any 'code word' you wanted. But when I try this now, it acts like it's working, but after I type EOF I get a blank file called mynotes.txt.

---

### Post by StOoZ on 2009-04-17
try for example :
[PHP]ls -l > mynotes.txt[/PHP]

thats should work...
>> is to append.

---

### Post by kpatz on 2009-04-17
> **BetterSense said:**
> But when I try this now, it acts like it's working, but after I type EOF I get a blank file called mynotes.txt.

That command worked fine for me.

```

kpatz@jaunty-beta:~$ cat >>mynotes.txt <<EOF
> hello
> there
> how
> are
> you
> EOF
kpatz@jaunty-beta:~$ cat mynotes.txt
hello
there
how
are
you
kpatz@jaunty-beta:~$

```

---

### Post by llamabr on 2009-04-17
You must exit out of it with ctrl-d, not c or z.

---

