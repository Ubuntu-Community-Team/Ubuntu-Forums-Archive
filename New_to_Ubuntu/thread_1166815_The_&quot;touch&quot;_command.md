---
title: "The &quot;touch&quot; command"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by muteXe on 2009-05-22
Just curious really...
The first example in:
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

I don't get it.  I thought "touch" did things with the timestamp of a file.  In the case above it looks like he's using it to actually create a file.  Can it be used so?
Cheers,
mute

---

### Post by x33a on 2009-05-22
yes, you can also use touch to create a file

try
```
touch foo
```

it will create an empty file named foo.

for more on touch
```
man touch
```

---

### Post by fballem on 2009-05-22
> **muteXe said:**
> Just curious really...
The first example in:
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

I don't get it.  I thought "touch" did things with the timestamp of a file.  In the case above it looks like he's using it to actually create a file.  Can it be used so?
Cheers,
mute

Short answer is 'yes' - it will create an empty file that can then be edited. This is a common solution to permission issues where a group of users may be able to edit an existing file in a specific location, but cannot create it.

In the example that you cited, the objective was to create a file that could be 'found' - it didn't matter what the file contained or how it was created.

---

### Post by andrew.46 on 2009-05-22
Hi muteXe,

> **muteXe said:**
> Just curious really...
The first example in:
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

I don't get it.  I thought "touch" did things with the timestamp of a file.  In the case above it looks like he's using it to actually create a file.  Can it be used so?


Hey that is me :-). I suspect that touch is actually used more commonly to create new files than to simply alter timestamps, although I am ready to be contradicted here!

All the best,

Andrew

---

### Post by muteXe on 2009-05-22
Ah cool.  The man page on it isn't exactly clear that it can be used to create a file.

Thanks everyone for your replies.
mute

---

