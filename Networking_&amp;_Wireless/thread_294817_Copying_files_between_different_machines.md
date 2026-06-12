---
title: "Copying files between different machines"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by leodp on 2006-11-07
Hi,

I've always used sftp to copy files from/to a remote machine, but now would like to have also a graphical possibility to do that, in particular to recur directories.

I tried to ssh to the remote machine, opening a konqueror  instance, and drag-dropping files on my local desktop, but it complains that the files do not exist.

What do I do wrong?
Is there another tool that can do that?

Thanks, Leo

---

### Post by jazzgossen on 2006-11-07
One easy way to do it is to add an SSH connection on the desktop. Not sure how it works if you use Kubuntu, but in Gnome you can do it under Places/Network Servers...

Then you get a directory that links to the remote computer so that you can drag and drop as much as you like.

---

### Post by leodp on 2006-11-07
Oh yes, it's too easy!

Under kde I can open konqueror and go to:
system:/remote
then I can Add a Network Folder, voila'.
In the address line on the connected folder I read:
fish://username@remotemachine

Thanks, Ciao, Leo

---

### Post by leodp on 2006-11-07
Ok, it was too easy:

under Suse it's not system:/remote
but it's under:
remote:/

And it works perfectly.
Ciao, Leo

---

### Post by bluenova on 2006-11-07
In gnome/nautilus you can just do sftp://pathtolocation or sftp://remoteusername@remotelocation if your username is differnt to sftp to the remote machine. This is how I do it, you then get to look at the remote folder in exactly the same way as you would your local folders.

---

