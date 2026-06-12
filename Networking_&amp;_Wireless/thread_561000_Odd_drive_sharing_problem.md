---
title: "Odd drive sharing problem"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by Conradle on 2007-09-27
Okay guys, this is the breakdown of my little home network.

Server running Ubuntu has three drives:
80GB for OS (IDE internal)
250GB for storage (IDE internal)
500GB for storage (USB external)

My computer dual boots Windows XP and Ubuntu 7.04 (Feisty).

Now, the problem:
I'm sharing both the 250 and the 500gb drives on the network. My XP installation can pick both of them up, with read and write, no problems.
However, if I go into Ubuntu, I can mount the 250GB fine but the 500GB says permission denied!

Anyone got any ideas? I'm stumped...

Thanks!

Conrad

---

### Post by Conradle on 2007-09-28
No one?

---

### Post by tisk on 2007-09-28
have you enabled samba, and set up a proper smb.conf file. You should set user = share or make a password file.

---

### Post by Conradle on 2007-09-28
Yes, done all that. I can share any file or folder and access it properly, it's just any external drives via USB that I have problems with.
If I access it in Nautilus it says:

The folder contents could not be displayed.
Sorry, couldn't display all the contents of "MEDIA".

And that's the only thing I get. If I go into LinNeighbourhood it says permission denied.

---

### Post by Conradle on 2007-09-29
I even tried reinstalling the server this morning from scratch and it still has exactly the same problem.
If it helps, the file system on the external USB drive is FAT32.

---

