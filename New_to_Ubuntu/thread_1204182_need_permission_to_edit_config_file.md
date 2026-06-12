---
title: "need permission to edit config file"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by insanity99 on 2009-07-04
i got mediatomb and i need to edit the config. i open the document in text editor but it wont let me save changes, can anyone help me please?

---

### Post by derekeverett on 2009-07-04
what are the permissions of the file?

---

### Post by TheForumTroll on 2009-07-04
Just edit it as root.

```
gksudo gedit /file/path
```

---

### Post by insanity99 on 2009-07-04
ok thanks the gksudo gedit /file/path command worked.

though i still cant get mediatomb to work. it's a real pain.

---

### Post by TheForumTroll on 2009-07-04
What's wrong with it?

---

### Post by insanity99 on 2009-07-04
i use this config: [http://boardsus.playstation.com/playstation/board/message?board.id=ps3media&thread.id=114797](http://boardsus.playstation.com/playstation/board/message?board.id=ps3media&thread.id=114797)

changed <home>/home/anindya/.mediatomb</home>
<webroot>/home/anindya/Local Software/mediatomb/share/mediatomb/web</webroot>

to <home>/home/neil/.mediatomb</home>
<webroot>/home/neil/Local Software/mediatomb/share/mediatomb/web</webroot>

but when i run mediatomb i get an error saying '/home/neil/Local Software/mediatomb/share/mediatomb/web' no such directory existes. anyh idea why?

---

### Post by TheForumTroll on 2009-07-04
Does the directory exist? ;)

---

### Post by TheForumTroll on 2009-07-04
You could try ps3mediaserver if you can't get it fixed somehow. It works great if you just need to share and transcode some stuff to playstations, xboxes and so on.

[http://code.google.com/p/ps3mediaserver/]("http://code.google.com/p/ps3mediaserver/")

---

### Post by insanity99 on 2009-07-04
> **TheForumTroll said:**
> Does the directory exist? ;)
no but i thought ubuntu would handle that -_-

> **TheForumTroll said:**
> You could try ps3mediaserver if you can't get it fixed somehow. It works great if you just need to share and transcode some stuff to playstations, xboxes and so on.

[http://code.google.com/p/ps3mediaserver/]("http://code.google.com/p/ps3mediaserver/")
oh ps3 media server has a linux version? cool

---

### Post by TheForumTroll on 2009-07-04
It's java so it works everywhere ;)
I'm running the latest beta. Works great so far.



Does creating the directory fix the problem?

---

### Post by insanity99 on 2009-07-04
i changed it to '/home/neil/.mediatomb' which seemed to work. i think the config might be made for an older ubuntu, which stored files in different places.

i also have to turn off firestarter because it get's blocked. how do i stop this?

and finally, when i run mediatomb i get this

Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2009-07-04 17:17:05    INFO: Loading configuration from: /home/neil/.mediatomb/config.xml
2009-07-04 17:17:05    INFO: Checking configuration...
2009-07-04 17:17:05    INFO: Setting filesystem import charset to UTF-8
2009-07-04 17:17:05    INFO: Setting metadata import charset to UTF-8
2009-07-04 17:17:05    INFO: Setting playlist charset to UTF-8
2009-07-04 17:17:05    INFO: Configuration check succeeded.
2009-07-04 17:17:05    INFO: Initialized port: 49153
2009-07-04 17:17:05    INFO: Server bound to: 192.168.0.2
2009-07-04 17:17:06    INFO: MediaTomb Web UI can be reached by following this link:
2009-07-04 17:17:06    INFO: **[http://192.168.0.2:49153/](http://192.168.0.2:49153/)**

which is good but but the enblolded address is always wrong it's [http://192.168.0.2:49152/](http://192.168.0.2:49152/).

---

### Post by TheForumTroll on 2009-07-04
Great it worked out :)

---

### Post by insanity99 on 2009-07-04
yeah worked out ok, thanks :D

---

### Post by TheForumTroll on 2009-07-04
You can add an exception to allow inbound traffic in Firestarter > Policy > Click below 'Allow service' or 'Allow connections from host' > Add rule :)

---

