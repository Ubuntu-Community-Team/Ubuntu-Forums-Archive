---
title: "Simple Noob Question"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by newbwarning on 2009-12-14
I am editing the squid.confi on my server.

I am done editing.

How do I exit the confi file?

Thank you.

---

### Post by Geoff918 on 2009-12-14
Which editor are you using?

Nano, VIm, gedit?

---

### Post by newbwarning on 2009-12-14
I was trying to edit from the command prompt, after entering the command:

sudo vi /etc/squid/squid.conf

following this tutorial: [http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html).

So, I should be accessing this file with a editor?

Thank you.

---

### Post by Geoff918 on 2009-12-14
Okay, so you're using VIm (VI Improved)

That's a multi-modal editor.

You need to enter something to change from command mode to input mode. I assume you did this.

To then exit the command mode, you need to do a Ctrl-C

You can then enter a colon (:) before a command.

To write the file and get out you can do the following:

:update # will update the file / write to disk
:quit # quits back to the command prompt--can also be shortened simply to :q

---

### Post by newbwarning on 2009-12-14
Oh, Yes!

Thanks Geoff. Much appreciated.

---

