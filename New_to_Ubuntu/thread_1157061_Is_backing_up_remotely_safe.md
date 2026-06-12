---
title: "Is backing up remotely safe?"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by kramer65 on 2009-05-12
Hello,


I want to backup my complete pc on a remote server which I rent. This server is located at the company and although I do want to backup, I do not want to give the employees at that company access to my files. If I backup my pc, is the remote backup then encrypted and thus not accessible by other people who want to access those files?

Thanks!

---

### Post by Celauran on 2009-05-12
I think there's a certain expectation of privacy when you use such services, but you're always free to encrypt your date before backing it up.

---

### Post by kramer65 on 2009-05-12
So the simple backup doesn't encrypt or something?

I (unfortunately) don't have any world domination plans as yet, but there is some work related stuff in there which I would not like to spread around the internet..

So is there any way of automatically making those backups encrypted without me needing to intervene all the time?

---

### Post by Celauran on 2009-05-12
There are multiple encryption tools available; ccrypt, truecrypt, etc. You could create a cron job to handle the encryption for you.

---

### Post by Paddy Landau on 2009-05-12
Look up duplicity (install through Synaptic Package Manager, and then use *man duplicity* in a terminal for instructions).

It will:

[LIST]
[*]Encrypt all your data with GPG before transmitting it over the network. The employees won't even know how many folders or files you have, never mind their names or contents.
[*]Transmit only the bits of files that you've changed (after the initial backup), so incremental backups are fast.
[*]Keep incremental copies, so you can revert a changed file (or even a deleted file) to a previous version if necessary.
[*]Let you delete old increments if you start to use too much space for your backups.
[/LIST]
It has a several other useful features. For example, look at the option *--archive-dir*.

---

