---
title: "sshfs - mount only home folder"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by valdiks on 2008-03-28
Hello!

I have installed on remote server openssh and sshfs, created user, and added it to fuse group.
user can mount **any** remote folder: 
sshfs user@remotehost:/etc/ /mnt/remote
or
sshfs user@remotehost:/ /mnt/remote
or any other
(ubuntu installed with default settings)

how to make that user can mount only it's home directory without setting permissions on other files and folders? and esle user may not connect by ssh (disable ssh).

why i need this:
i copy to user home directory, for example, movie, user (or guest, allowed by ip) make sshfs connection to server and start watching movie without downloading to local folder.

p.s. sorry for my english, if any. (:

---

