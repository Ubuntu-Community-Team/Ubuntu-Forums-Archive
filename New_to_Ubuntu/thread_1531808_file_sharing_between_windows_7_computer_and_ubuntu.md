---
title: "file sharing between windows 7 computer and ubuntu computer"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by Gr3ghammett on 2010-07-15
I'm using Hardy Heron Ubuntu, and my Ubuntu Desktop is acting as my media server for my house. I'm familiar with media sharing on windows, but only with windows as the source that's hosting the media, but not with how to do it on Ubuntu.

     I need to know how to share my media that's on my Ubuntu desktop computer, so all the other pc's and ps3's in the house can stream from it. the computers in the house use win 7 and one other uses vista. How do i mount and share my media source on my Ubuntu machine to where windows can access and stream from it? and is there anything fancy i need to do to have the ps3s access it as well?

     And if it's not too much trouble, and it's for my own personal knowledge, if i have media on my win machines that i want Ubuntu to see and stream from, how do i do that as well?

     Thank you for the help and guidance.

---

### Post by marshmallow1304 on 2010-07-15
Find the folder you want to share.  Right-click->Properties.  Go to the Sharing tab and check the "Share this folder" tab.  If necessary, it will prompt you to install samba.  Continue by filling out the fields and checkboxes as necessary then click "Create Share".


For media on the Windows machine(s), you need to set up file sharing on the Windows machine(s) then make sure sambaclient is installed on the Ubuntu machine(s).  The Windows share(s) should then appear in Places->Network or manually by Places->Connect to Server.

---

### Post by Gr3ghammett on 2010-07-15
for the windows sharing, windows works with workgroups. i haven't set a domain but if i do a manual "connect to server", do i need to put the workgroup name in domain, or is that moot when it comes to linux connecting to windows?

---

### Post by motorcity909 on 2010-07-15
I found a great app for sharing media with a PS3.

It's called** ps3 media server** - [http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)

Before I found that, I'd tried [Mediatomb]("http://mediatomb.cc/") which worked but only if I removed album covers from the ID tags of mp3s, whereas with PS3 Media Server the console happily displays the album art.

Have fun
Dave

---

### Post by marshmallow1304 on 2010-07-16
> **Gr3ghammett said:**
> for the windows sharing, windows works with workgroups. i haven't set a domain but if i do a manual "connect to server", do i need to put the workgroup name in domain, or is that moot when it comes to linux connecting to windows?

I don't *think* so.  You might just have to try it and see if it works.

---

