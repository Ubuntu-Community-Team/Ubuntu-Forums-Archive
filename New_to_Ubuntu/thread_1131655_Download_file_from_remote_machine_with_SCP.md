---
title: "Download file from remote machine with SCP"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by ugly_peter on 2009-04-21
How can you download a file from a remote host using scp. I am trying

scp remotehost:file .

But this gives me an error: "standard input: Invalid argument"

---

### Post by Walter Melon on 2009-04-21
> **ugly_peter said:**
> How can you download a file from a remote host using scp. I am trying

scp remotehost:file .

But this gives me an error: "standard input: Invalid argument"

you have to specify a target directory. so type```
scp user@host:file ~/Desktop/file
```

---

### Post by mattj7 on 2013-01-08
I see this thread is 4 years old, but I'll post anyway lol.  I was wondering how to do this when downloading from ubuntu to windows.  For example, I'm putty'd into my ubuntu box on my windows machine, trying to download a file, and when I type:

scp user@host:/home/user/file "C:\Users\User1\Desktop\file"

it says "could not resolve hostname C: name or service not known"
Clearly this is because of the windows style directory path, but how do I make it compatible?

---

### Post by oldos2er on 2013-01-08
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

