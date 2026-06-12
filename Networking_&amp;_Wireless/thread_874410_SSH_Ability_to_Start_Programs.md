---
title: "SSH Ability to Start Programs"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by Yuki_Nagato on 2008-07-29
I have a server that I run Bittorrent traffic through.  It is a Linux server.  Is there any way that I can initiate the proper programs through SSH?

I know for instance, that I can run Firefox through SSH, and it will be as if I am surfing the Web from the server, but the data will appear on the client computer.  What I want to do is to start the Bittorrent programs, and then let them run.  I do not need to view or modify them; just start them, and then close my session.

---

### Post by ilrudie on 2008-07-30
Best thing I can think of to do is use screen which allows persistent terminal sessions even when you log off ssh and a command line bittorrent client.  Good luck.

---

### Post by MasterXandrex on 2008-07-30
There's also nohup (**no****h**ang**up**) that allows an application to persist after the session has ended. This usually works by redirecting the screen output to a file, but with things like full-terminal clients this can create a large file in a short period of time. Of course, if you don't care about the output at all you can push it into null. It'd go something like this:

```

nohup *bittorrentclient* > /dev/null &

```


Xan

---

### Post by ilrudie on 2008-07-30
Thats a good option too.  I had forgotten about that.

---

