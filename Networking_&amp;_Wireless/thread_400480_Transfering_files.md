---
title: "Transfering files"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by gil michael on 2007-04-03
hi,

i've just installed ubuntu on my computer.
i want to connect to a Linux server to get some files from there, but i don't know how to do that.
i mannaged to get the files using Windows XP OS (using a program named 'putty').

can someone help?

---

### Post by spd106 on 2007-04-03
Assuming you trying to connect to an ssh server. You can access it through a terminal using the ssh client, just type this, then enter your password ```
ssh username@server.domain
```

Alternatively you can use nautilus, on the top panel of your desktop go to Places -> Connect to Server... then select ssh and enter your details.

---

### Post by cyph3x on 2007-11-29
i know the command to dump files to your ssh server is "scp localfile user@host:~/file" but how would i "download" the files i put on the server using the terminal? (ie, the opposite of scp)

---

### Post by spd106 on 2007-11-30
It's exactly the same as the normal cp or rcp commands.
```
scp source destination
```

e.g. "scp user@host:~/file localfile"

There are lots more options in the ssh and scp man pages.

---

