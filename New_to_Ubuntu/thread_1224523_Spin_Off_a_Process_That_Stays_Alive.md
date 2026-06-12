---
title: "Spin Off a Process That Stays Alive"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by Zerocool3001 on 2009-07-27
This is going to sound like a very stupid question. I'm trying to find out if theres a way to spin off a process (say from a X forwarded ssh connection) so that it not only launches on the target machine, but that it stays alive after I logout of the ssh connection. Mostly I just don't want to have to run in to the server when I want to start a process that I want to keep open.

Thanks for any help you can provide.

P.S. I forgot to add that I have to stay logged in locally on the server so my external USB drive gets mounted for remote Time Machine backup.

---

### Post by superfoor on 2009-07-27
you should be able to tack a & at the end of the process. like "firefox &"
 you will then see its process ID. Let me know if this works out for you

---

### Post by Zerocool3001 on 2009-07-27
I've tried backgrounding processes, but that only seems to work if I'm not X forwarding. I think it may have something to do with what user its trying to run the process for (local or remote).

---

### Post by whitethorn on 2009-07-27
As far as I know, if you start a program with X window, close the ssh connection and then connect again, you won't be able to get the x window back.  What I know that works with cli programs is screen.  Have a look at the screen man page.

---

