---
title: "Do we need a proxy?"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by tacomodo on 2008-08-18
My friends workplace has blocked both msn and the chat function inside gmail, so we're looking at ways to get around this and to get msn to work.

We don't really know where to start, but I was wondering if maybe some sort of proxy would work, if I set it up at home? Perhaps if we set it to port 80 or 53 it should be open and work?

Does anyone have any suggestions that might help? Links/guides and so forth also greatly appreciated.

---

### Post by sstusick on 2008-08-18
You can use meebo: [http://www.meebo.com/](http://www.meebo.com/)

---

### Post by tacomodo on 2008-08-18
All the web-based ones are blocked too it seems.

He tried most of these:
[http://ofwlayf.com/best-alternative-for-msn-web-messenger-yahoo-web-messenger/](http://ofwlayf.com/best-alternative-for-msn-web-messenger-yahoo-web-messenger/)

---

### Post by sstusick on 2008-08-18
Wow, that sucks.

---

### Post by amo-ej1 on 2008-08-18
You could try to connect through an ssh tunnel. In order for this to work you need to be sure you can 
a) use ssh
b) access a port of your pc at home. 

Then you could issue 

ssh -p yourhomeport -L 1863:messenger.hotmail.com:1863 youruser@yourhomeip

this will create a tunnel, and all connection to localhost on port 1863 will travel through the tunnel to your home ip and end up at messenger.hotmail.com on port 1863. 

This will require you to modify the connection settings on your local system to connect to localhost.

Edit: you can also use this to gain access to other blocked websites, when you tunnel to port 80, but it will fail if they block connection to your home pc.

---

### Post by tacomodo on 2008-08-18
Hmm I guess that would work great if he used Ubuntu too. Unfortunately he uses Windows XP :(

---

