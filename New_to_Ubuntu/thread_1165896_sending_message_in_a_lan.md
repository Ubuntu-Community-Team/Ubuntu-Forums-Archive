---
title: "sending message in a lan"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by anand9 on 2009-05-21
hai , i am new to linux.
is there a command to send messages to other clients in a lan from comand line? all the systems are working on ubuntu.
i had seen sending messages in windows using netsend command. is there any command like that in linux? 
plz help me out...

---

### Post by nhasian on 2009-05-21
take a look at the command wall

```
wall
```

your cursor will go to the next line, waiting for your message. You can enter multiple lines by just pressing the enter key at the end of each line. Once you're done, press CTRL+D to send to all users logged in.

You must be logged in as root in order to send to all users.  Only users logged in a console/terminal can receive the message.

for more info try

```
man wall
```

---

### Post by ganesanrajesh on 2009-05-21
Hi:p,
Try empathy. LAN communications need telepathy-salut to be installed. Rest is self explanatory (I mean, just like a chat client). We can transfer files too:D.
Giver is another utility ... just to transfer files with LAN.
Regards,

---

### Post by bacardiandwatermelon on 2009-05-21
I used to love net send, I'd always send my gf pop messages that she had a virus, pity ms started blocking the service from default install, I think there was some security bug with it or something. Can't remember.

---

### Post by Astarroth on 2009-05-21
I think the real reason ms started blocking it by default was that it was being used to spam advertisments to users. At least that is why the company I work for started blocking it.

---

### Post by anand9 on 2009-05-25
i tried wall command, but through it i could not send messages to a different computer, that is a computer with a different ip. but the messages i tried to send were shown in another terminal which i opend.. :(

---

