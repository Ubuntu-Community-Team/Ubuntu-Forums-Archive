---
title: "Ubuntu 9.04 + Pidgin 2.5.5 = can't join facebook chat"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by WestCity on 2009-10-27
Hi,

I have a problem with "Pidgin". If I add my facebook account, I can see my friends list for about 5 sec long. Then the list dissapears and it says "error while trying log in" (or something similar - I dont remember now) and "try to log in again". Sometimes it says "incorect username or password". Reconnection did not helped. Again same messages. If I delete that account and create it again, my friends list appears for about 5 sec. And everything reapeats...

Any ideas?

At the moment updated to 2.6.3 and still the same problem... Now sometimes it says "chat service currently unavailable".

Is it possible to fix it?

---

### Post by CaptainMark on 2009-10-27
is this happening all the time, i get this intermittently, although i put it down to facebooks chat server, i dont think theyre quite up to date with it because half the time the chat doesnt work through http.

---

### Post by WestCity on 2009-10-28
It is happening all the time. So, nobody has ideas how to fix it? Am I alone with such a weird problem? :D

Just in case, if someone will ask...yes, other protocols are working fine. Only facebook makes no sence.

---

### Post by leolca on 2009-10-28
I keep have this problem also. :(

---

### Post by Dangger on 2009-10-28
> **WestCity said:**
> Hi,

I have a problem with "Pidgin". If I add my facebook account, I can see my friends list for about 5 sec long. Then the list dissapears and it says "error while trying log in" (or something similar - I dont remember now) and "try to log in again". Sometimes it says "incorect username or password". Reconnection did not helped. Again same messages. If I delete that account and create it again, my friends list appears for about 5 sec. And everything reapeats...

Any ideas?

At the moment updated to 2.6.3 and still the same problem... Now sometimes it says "chat service currently unavailable".

Is it possible to fix it?

The problem lies in the plugin for fb chat. The new fb chat requires some dependencies that are only available in Karmic. I suggest updating to karmic if you really need to have fb in pidgin. I am currently using it and I have no problems.

---

### Post by WestCity on 2009-10-29
Thank you for answering my question. ;) I will upgrade (or install) to Karmic as soon as possible. But now i've read, that everything i'll see on my laptop (Asus K50IJ), will be black screen. :( Maybe they fixed this issue already?..

---

### Post by steve228 on 2009-11-04
Try this.. it worked for me...

```

sudo apt-get remove pidgin-facebookchat

```

Then go here:

[http://code.google.com/p/pidgin-facebookchat/downloads/list]("http://code.google.com/p/pidgin-facebookchat/downloads/list")

And get the .deb file
> pidgin-facebookchat-1.62.deb

When you go to install it, it will tell you there is an older version, but install the 1.62 and it *should* work for you.

---

### Post by userid on 2009-11-09
I get this on karmic and plugin 1.62 also..

---

