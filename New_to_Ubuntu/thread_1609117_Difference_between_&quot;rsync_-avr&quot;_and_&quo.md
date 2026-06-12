---
title: "Difference between &quot;rsync -avr&quot; and &quot;cp -r -u &quot;?"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-30
Hello 

I would like to know what could be the difference between using:


```
rsync -avr source/ target/
```

and

```
cp -r -u source/ target/
```


If those results to same results, so why to use rsync then, since cp has already a formidable sync embedded...

---

### Post by BugBuster on 2010-10-30
> If those results to same results, so why to use rsync then, since cp has already a formidable sync embedded... 

Always use what best serves your purpose. Also rsync, as the name suggests, is intended for remote sync ( i.e ) syncing files over a network though it can be used locally as well.Basic cp cannot be used for remote file copy scenarios.

---

### Post by ubudog on 2010-10-30
Rsync can be used locally and remotely (hence the name, rsync).  The cp command can only be used locally (I believe that is right). :)

---

### Post by honeybear on 2010-10-30
> **BugBuster said:**
> Always use what best serves your purpose. Also rsync, as the name suggests, is intended for remote sync ( i.e ) syncing files over a network though it can be used locally as well.Basic cp cannot be used for remote file copy scenarios.

heuu... :confused: sorry but I do not understand. remote, what do you mean? a command is command, no. You mount a filesystem and then copy only :confused:


> 
Here's an example under Linux on how to set up a replication through SSH:

    rsync -avz -e ssh [email]rsync@remote.acme.com[/email]:/home/rsync/out/ /home/rsync/from_remote 

An important thing here, is that the presence or absence of a trailing "/" in the source directory determines whether the directory itself is copied, or simply the contents of this source directory.

In other words, the above means that the local host must have a directory available (here, /home/rsync/from_remote to receive the contents of /home/rsync/out sitting on the remote host, otherwise Rsync will happily download all files into the path given as destination without asking for confirmation, and you could end up with a big mess.

On the other hand, rsync -avz -e ssh [email]rsync@remote.acme.com[/email]:/home/rsync/out /home/rsync/from_remote means that the an "out" sub-directory is first created under /home/rsync/from_remote on the destination host, and will be populated with the contents of the remote directory ./out. In this case, files will be save on the local host in /home/rsync/from_remote/out, so the former commands looks like a better choice.

Here's how to replicate an Rsync share from a remote host:

    rsync -avz [email]rsync@remote.acme.com[/email]::out /home/rsync/in 

I mean you can do that with ssh also, and then run cp -u -r
so what is better?

---

