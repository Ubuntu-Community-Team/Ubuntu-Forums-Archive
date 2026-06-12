---
title: "bash: run a command from a variable"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by PGScooter on 2009-04-12
Hi, I do not understand why this works:
```

onecommand="ls"
$onecommand

```

but this does not:
```

anothercommand="ls | head -4"
$anothercommand

```

I do not want to do this:
```

anothercommand=`ls | head -4`
echo "$anothercommand"

```
Because I want to be able to run the command on the fly, not get the contents of a command I previously ran.

Does this make sense?

Thank you!

---

### Post by Linteg on 2009-04-12
If I understand you correctly I think the following would do what you want:
```
anothercommand="ls | head -4"
eval "$anothercommand"
```

---

### Post by PGScooter on 2009-04-12
Linteg,

yes that is exactly what i wanted, thank you!

I have another problem though:

```

onecom='cd /media/storage/My Music/'
eval $onecom

```
produces "bash: cd: /media/storage/My: No such file or directory"

How can I take care of that space between 'My' and 'Music'?

---

### Post by Sir Jasper on 2009-04-12
Hi,

I think I read use "My Music" including the quotation marks
alternatively try My/Music.

My regards

---

### Post by drowner on 2009-04-12
> **Sir Jasper said:**
> Hi,

I think I read use "My Music" including the quotation marks
alternatively try My/Music.

My regards

No, its a slash the other way

My\ Music

the \ tells linux to read the next character as a character, not formatting for the command.

---

### Post by PGScooter on 2009-04-12
thanks!

To my surprise, the double quotes thing worked! very strange- I used single quotes on the outside and double on the insite for "My Music". The backslash also escapes the space (although I tried that before and it didn't work, must have been doing something else wrong).

thank you

---

### Post by llamabr on 2009-04-12
Instead of writing little scripts for something like this, you could make an alias:

```
alias rm="rm -i"

```

I use it for all kinds of things.  Even apps I usually misspell, I just make an alias.

Then, put them in your .bashrc and they'll get loaded on login.

---

### Post by PGScooter on 2009-04-12
thanks for the tip, I will look into that.

---

### Post by robertrej on 2009-05-12
I created a bin/bash script it runs fine but at the end I get a
error:               big endian not yet supported

I use Sox in my script maybe Sox defaults to big endian
instead of little?

                              any ideas?
                              thanks/bob

---

