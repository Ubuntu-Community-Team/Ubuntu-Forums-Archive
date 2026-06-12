---
title: "How to silence commands?"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by TheCraneMan on 2010-08-19
Hello this is probably a dumb question but I need to check Root access on Ubuntu using the Terminal, I'm using the command
[FONT=Microsoft Sans Serif]
if touch /root/.profile; then
{ #Code }

[FONT=Arial]which works fine except if it cannot touch root (i.e. a regular user) it outputs:
[FONT=Microsoft Sans Serif]touch: cannot touch `/root/.profile': Permission denied
[FONT=Arial]which looks ugly to me since the program is outputting to a file. How do you "silence" the touch command? Thanks in advance![/FONT]
[/FONT]
[/FONT]
[/FONT]

---

### Post by scorp123 on 2010-08-19
```
touch /path/to/what/it/should/touch > /dev/null 2>&1
```

Explanation can be found here:
[http://www.xaprb.com/blog/2006/06/06/what-does-devnull-21-mean/](http://www.xaprb.com/blog/2006/06/06/what-does-devnull-21-mean/)

---

### Post by marshmallow1304 on 2010-08-19
```
if [ $(whoami) == 'root' ]; then
```

---

### Post by TheCraneMan on 2010-08-19
> **scorp123 said:**
> ```
touch /path/to/what/it/should/touch > /dev/null 2>&1
```

Explanation can be found here:
[http://www.xaprb.com/blog/2006/06/06/what-does-devnull-21-mean/](http://www.xaprb.com/blog/2006/06/06/what-does-devnull-21-mean/)
Thank you! And thanks for the explanation too, I hate doing something and having no idea as to what it actually does :)

---

### Post by David Andersson on 2010-08-19
> **TheCraneMan said:**
> 
if touch /root/.profile; then


This has the side effect of changing the time stamp of the file. Why not test *whoami* as marshmallow suggests, or test if *id -u* is 0? If it must be a file test, you can *check for write access* without writing nor changing any time stamps (and no error message) with

```
if [ -w /root/.profile ]; then
```

Even simpler, [ -w /root ] or just [ -w / ]. The result should be the same.

---

### Post by TheCraneMan on 2010-08-19
> **David Andersson said:**
> This has the side effect of changing the time stamp of the file. Why not test *whoami* as marshmallow suggests, or test if *id -u* is 0? If it must be a file test, you can *check for write access* without writing nor changing any time stamps (and no error message) with

```
if [ -w /root/.profile ]; then
```

Even simpler, [ -w /root ] or just [ -w / ]. The result should be the same.
Thank you I have not tried the *whoami* technique but* id - u* won't work, because even when logged in as Root it doesn't work, I posted another thread asking about it. I didn't realize there were side effects so thank you for pointing it out I like
*-w /root* works perfectly and so does *$(whoami) *and 2>&1 Thank you everyone for the help!

---

