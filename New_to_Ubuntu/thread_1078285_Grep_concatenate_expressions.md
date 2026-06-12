---
title: "Grep: concatenate expressions"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by SentientFluid on 2009-02-23
Is there a way I can concatenate expressions when using grep?  For example, let's say I want to run du on my home folder, but there are multiple folders I don't want to include.
```
du /home/username | grep -v "folder1"
``` will give me sizes everything but folder1.  But what if I want to exclude folders 3, 6, 10, 12 as well?

---

### Post by geirha on 2009-02-23
You can pipe it through more greps
```
du ~ | grep -v "folder1" | grep -v "folder3" | grep -v "folder4" # etc
```

or you can use one grep that "or"s all the expressions
```
du ~ | grep -v "folder1\|folder3\|folder4"
```

---

### Post by SentientFluid on 2009-02-23
> **geirha said:**
> You can pipe it through more greps
```
du ~ | grep -v "folder1" | grep -v "folder3" | grep -v "folder4" # etc
```

or you can use one grep that "or"s all the expressions
```
du ~ | grep -v "folder1\|folder3\|folder4"
```

Ok that works the way I described I wanted it to, but it's not having the effect I was looking for.  That probably means I asked the wrong question. ;)

I'm teaching myself a little scripting and here's the exact code I'e tried using along with it's output:
```
~$ du --summarize --human-readable /home/*
4.0K	/home/folder1
4.0K	/home/folder2
4.0K	/home/folder3
736M	/home/user
du: cannot read directory `/home/lost+found': Permission denied
16K	/home/lost+found
```

I want the last two lines gone. I tried piping it to grep -v "lost" but was left with
```
4.0K	/home/folder1
4.0K	/home/folder2
4.0K	/home/folder3
736M	/home/user
du: cannot read directory `/home/lost+found': Permission denied
```

Ok, so the lost+found size output was gone, but I still got the Permission Denied  error.  So using your instructions I added "Permission" to grep:```
du --summarize --human-readable /home/* | grep -v "lost\|Permission"
``` but got the exact same output.

So I'm guessing I can't grep out the error like I thought.  Since it was a permission error I tried to sudo the command.
```
sudo du --summarize --human-readable /home/* | grep -v "lost"
[sudo] password for user: 
4.0K	/home/folder1
4.0K	/home/folder2
4.0K	/home/folder3
du: cannot access `/home/user/.gvfs': Permission denied
736M	/home/user

```

Now .I understand gvfs is a virtual file system abstraction layer and I can't even get rid of it using sudo (haven't tried logged in as root though) so I'm guessing I don't want to do anything to it.

So this leaves me at figuring out a way to get the output with out the Permission Denied error showing up. Any ideas? :)  If it ends up being to complex right now, I'll skip it as I'm just learning right now. *shrug*

---

### Post by geirha on 2009-02-23
Error messages are sent to stderr, while normal output is sent to stdout. Only stdout is sent through the pipe, so only the normal output gets filtered by your grep. One way to circumvent this is to redirect stderr to stdout
```
du -hs /home/* 2>&1 | grep -v "lost"
```
Or you can simply decide to ignore errors, and send any error messages into oblivion (aka /dev/null)
```
du -hs /home/* 2>/dev/null
```

---

### Post by SentientFluid on 2009-02-23
> **geirha said:**
> Error messages are sent to stderr, while normal output is sent to stdout. Only stdout is sent through the pipe, so only the normal output gets filtered by your grep. One way to circumvent this is to redirect stderr to stdout
```
du -hs /home/* 2>&1 | grep -v "lost"
```
Or you can simply decide to ignore errors, and send any error messages into oblivion (aka /dev/null)
```
du -hs /home/* 2>/dev/null
```

You're a genius!  Or at least closer to one than I am.  Thanks!

For purposes of learning, could you explain what exactly the 2>&1 means?  Where's it come from?

---

### Post by llamabr on 2009-02-23
2>&1 just sends all error messages to /dev/null

be careful with it, since you're not not reading any error messages.

Why do you want to omit that last line?

---

### Post by snova on 2009-02-23
> **SentientFluid said:**
> For purposes of learning, could you explain what exactly the 2>&1 means?  Where's it come from?

It redirects the standard error stream (2) to the standard output stream (1). Otherwise stderr isn't piped to grep, only stdout.

---

