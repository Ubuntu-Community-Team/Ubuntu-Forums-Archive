---
title: "ssh help?"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by Hawk__0 on 2007-08-19
okay, so me and my friend are trying to transfer a file from my computer to his using SSH.  i log on, its all good, i can execute commands and such... but we get a problem when i try to copy a file from my computer, to his.  here is the command im using (fake IPs used)
```
scp steve@70.70.70.70:~/slam.mp3 .
```
what i'm trying to accomplish: copy the file slam.mp3 from my computer (the files in my home directory, as you can see), to his computers desktop (i am already on his desktop, so i used "." to represent the current working directory)

it just times out.  what gives?
My idea is that its possibly getting confused because my brothers computer is also running ubuntu, also has ssh, and has the same user on his computer.  so im guessing that once it gets to my router it has no idea where to go kind of idea...

---

### Post by bvmou on 2007-08-19
I am not clear from your post if you are already logged in to an ssh session on the remote host.  SSH and SCP are actually two distinct packages; the thing is that if you are logged on to user@remotehost and execute scp you will be copying *from* the remote host to wherever.  To copy a local file to a remote host via SCP the syntax is:

```
scp [options, such as "-r" for recursion] /local/file.format username@remote.host:remote-folder/
```

Let us know if that works and good luck, reply here or via PM if you need clarification.

---

### Post by Hawk__0 on 2007-08-19
thanks, that did the trick.
what i was originally trying was logging onto that computer with ssh, THEN copying FROM this one, to that one.

---

