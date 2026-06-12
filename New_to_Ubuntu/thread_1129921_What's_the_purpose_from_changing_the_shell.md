---
title: "What's the purpose from changing the shell?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by JCC_0864049 on 2009-04-19
hi my friends :)

**What's the purpose from changing the shell?**

---

### Post by yeats on 2009-04-19
Different shells are available for different needs.  Bash is the default shell and is more than sufficient for most people's general needs.  It's actually a very rich programming environment, aside from giving you direct access to configuration files, logs, etc.  Do you need a specific shell other than bash?

---

### Post by ddrichardson on 2009-04-19
Just a minor correction - bash is the default login shell, the default system shell (/bin/sh) is dash and has been since 6.10.

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

### Post by yeats on 2009-04-19
> **ddrichardson said:**
> Just a minor correction - bash is the default login shell, the default system shell (/bin/sh) is dash and has been since 6.10.

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

Hmm.  On all my Ubuntu installations it has always been bash:

```
lrwxrwxrwx 1 root root 4 2009-03-20 15:08 /bin/sh -> bash
```

---

### Post by ddrichardson on 2009-04-19
Not here:
```
lrwxrwxrwx 1 root root 4 2009-03-13 00:02 /bin/sh -> dash
```

---

### Post by unutbu on 2009-04-19
That's interesting. How did you install Hardy? from a LiveCD?

---

### Post by ddrichardson on 2009-04-19
> **unutbu said:**
> That's interesting. How did you install Hardy? from a LiveCD?
Who? FWIW from a Live CD.

---

### Post by blueridgedog on 2009-04-19
> **ddrichardson said:**
> Just a minor correction - bash is the default login shell, the default system shell (/bin/sh) is dash and has been since 6.10.

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

On my 8.10 install, bash is the default.  I would have noticed

```
root:x:0:0:root:/root:/bin/bash
```

I installed via liveCD.

---

### Post by yeats on 2009-04-19
> **unutbu said:**
> That's interesting. How did you install Hardy? from a LiveCD?

If you mean me - I installed from a Live CD of Hardy and have since upgraded to intrepid, but it's always been bash for me.  I would have noticed, too as I do some (albeit minor) bash programming from time to time on both Ubuntu and Debian systems (both using bash as default).

---

### Post by ddrichardson on 2009-04-19
This is a Jaunty install BTW.

---

### Post by unutbu on 2009-04-19
> **ddrichardson said:**
> Who? FWIW from a Live CD.

I'm in agreement with you, ddrichardson. I believe Ubuntu symlinks /bin/sh to /bin/dash. I was asking chrissharp123 how he had installed Ubuntu.

Edit: Oops again... You guys are too quick for me :)

---

### Post by yeats on 2009-04-19
> **unutbu said:**
> I'm in agreement with you, ddrichardson. I believe Ubuntu symlinks /bin/sh to /bin/dash. I was asking chrissharp123 how he had installed Ubuntu.

Edit: Oops again... You guys are too quick for me :)

Hey again - 

I've read the wiki, which pretty plainly says that dash is the default system shell while bash is the default login shell.  I'm now trying to see where I would find that out on my system.  I have not altered the symlink from /bin/sh, and mine lists bash:

```
ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2009-03-20 15:08 /bin/sh -> bash

```

Any way I would otherwise know that dash is being used elsewhere?

---

### Post by ddrichardson on 2009-04-19
Its not a show stopper or anything its just that dash is smaller and fully POSIX compliant. Is this upgraded to Hardy or a fresh install?

---

### Post by blueridgedog on 2009-04-19
Perhaps the shells listed in /etc/passwd are all login shells, but the system shells on our systems are indeed dash.  I have always specified bash in my shell scripts, so I would not have had an issue.

---

### Post by blueridgedog on 2009-04-19
And the proof as to it being a system shell on my box:

```
james@Ripstop:~$ ls /bin/sh -al
lrwxrwxrwx 1 root root 4 2008-12-26 21:46 /bin/sh -> dash
```

So, it is indeed dash as a default, but bash as a login shell.  But, if I have bash as a login shell, I assume then that any xterms I launch are then bash?

It appears so:

```
james@Ripstop:~$ echo $SHELL
/bin/bash
```

---

### Post by ddrichardson on 2009-04-19
Yes, its the execution of shell scripts where #/bin/sh is specified

---

### Post by yeats on 2009-04-19
> **ddrichardson said:**
> Its not a show stopper or anything its just that dash is smaller and fully POSIX compliant. Is this upgraded to Hardy or a fresh install?

It was a fresh install of Hardy 8.04.2 back in February that I have since upgraded to Intrepid.

> Re: What's the purpose from changing the shell?
And the proof as to it being a system shell on my box:

Code:

james@Ripstop:~$ ls /bin/sh -al
lrwxrwxrwx 1 root root 4 2008-12-26 21:46 /bin/sh -> dash

So, it is indeed dash as a default, but bash as a login shell. But, if I have bash as a login shell, I assume then that any xterms I launch are then bash?

It appears so:

Code:

james@Ripstop:~$ echo $SHELL
/bin/bash



That's so weird.  I KNOW I haven't changed anything and mine symlinks to bash.  I wonder why?

@OP

sorry we've hijacked your post to talk about this - has your question been answered? :-)

---

### Post by JCC_0864049 on 2009-04-20
yes thx
 but what is **POSIX** ?

---

### Post by ddrichardson on 2009-04-20
[http://en.wikipedia.org/wiki/POSIX](http://en.wikipedia.org/wiki/POSIX)

What is Google ;-)

---

