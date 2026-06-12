---
title: "Please help me! How do I use one computer as a file server?"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by jamieh on 2008-10-04
I'm sure there is an easy answer to this, but I can't seem to find it.

There are 9 computers in a computer lab, plus a server which will store files. I have installed Ubuntu Desktop Edition 8.04 on all of them.

The server has 3 internal drives. One for the Ubuntu install and swap. And two 40GB drives for files.

Every other computer has one user account. I want each of the 9 computers to have read/write access to the two 40GB drives on the server, and every time the computer is logged in, I want the two drives to mount automatically.

Is there an easy way to accomplishing this?

---

### Post by Steveway on 2008-10-04
If everyone of those Computers runs Ubuntu then my advise would be to use NFS. It's pretty easy to set up, just google it.

---

### Post by lisati on 2008-10-04
There are a couple of methods you can use to share files across a network. One way uses "samba" - one tutorial can be found here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
Don't be put off by the reference to Windows - it should work even if your network is "ubuntu only".

---

### Post by Iowan on 2008-10-05
Just to inundate you with options: Check [SSHFS]("https://help.ubuntu.com/community/SSHFS").

---

