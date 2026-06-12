---
title: "(simple?) regular expression problem using grep"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by MichaelBurns on 2010-01-26
I want to sift the error messages from the output of "dmesg".  I am trying to use grep for this.  Neither
```

ubuntu@ubuntu:~$ dmesg | grep -i err

```
nor
```

ubuntu@ubuntu:~$ dmesg | grep [eE][rR][rR]

```
give me what I want (they should be identical, right?), because this also matches "interrupt", for example.  So, I tried to specify the beginning of the word (including occurances of "*ERROR*").  But the result from both
```

ubuntu@ubuntu:~$ dmesg | grep [ *][eE][rR][rR]

```
and
```

ubuntu@ubuntu:~$ dmesg | grep \b[eE][rR][rR]

```
is empty.  The first attempt was to specify a string that starts with a space or an asterisk.  The second attempt was to specifiy a string that begins with a "word boundary".

Any suggestions?

---

### Post by jd65pl on 2010-01-26
```
dmesg | grep -iE err
```
```
dmesg | grep -iE error
```

```
man grep
```

Perhaps you haven't any errors reported through dmesg, what are you trying to find?

---

### Post by MichaelBurns on 2010-01-26
Thanks, jd65pl.  I was approaching this as a regex issue rather than a grep issue.  I appologize for not reading the grep manpage.  Actually, after reading the grep manpage, I found that
```

ubuntu@ubuntu:~$ dmesg | grep -iw err.*

```
works.  I still don't understand what I was doing wrong with my regular expressions, but based on your suggestion, I guess it has something to do with the difference between basic and extended?

---

### Post by jd65pl on 2010-01-26
Ah misunderstanding I thought you were just not getting the expected return, using regex...

Try
```
grep '[eE][rR]\{2\}'
```

---

### Post by MichaelBurns on 2010-01-26
> **jd65pl said:**
> Ah misunderstanding I thought you were just not getting the expected return, using regex...No, you understood me, I believe, just perhaps not in so much detail.  I got the expected return, but then noticed that it was overwhelmed by matches to "interrupt".  Then, I tried to refine the regex, but apparently grep didn't interpret my word boundary as I intended.

> **jd65pl said:**
> Try```
grep '[eE][rR]\{2\}'
```Well, that seems to be just another way to get the same result as the other two attempts that I made, which matches "interrupt" and "Pierre" (I did verify this).  But, like I said, I got it sorted out (using the -w option), thanks to your suggestion to read the grep manpage (see my previous post).  Thanks again.

---

