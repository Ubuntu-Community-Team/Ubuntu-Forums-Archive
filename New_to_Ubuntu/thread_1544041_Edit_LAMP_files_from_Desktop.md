---
title: "Edit LAMP files from Desktop"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Keinan on 2010-08-02
Is there a way for me to be able to locate, access, and edit files for my LAMP server from Ubuntu 10.4 desk top(like php.ini) without using the command terminal?


I don't mind having to use command terminal in general, but VNC (I'm remotely operating my Ubuntu desktop) won't let me use gksudo gedit, because its missing something to handle that. 


I would like to bypass needing to use that command altogether if possible.


I think the LAMP files are hidden at first?



If there is a way, please walk me through the steps to make this happen. Thanks!

---

### Post by 3rdalbum on 2010-08-02
Why don't you SSH into your server and forward X?

```
ssh -X <ip-address>
```

Then you can run gksudo gedit.

---

### Post by Keinan on 2010-08-02
Thanks for answering! :)

I'm sorry I'm a bit of a noob... which ip address should I be typing in? The ubuntu box's ip or My XP computer's external or internal ip (my XP box is behind a router)?

---

### Post by Darkness Des on 2010-08-02
I assume that your LAMP sever is your XP Box? If they are under the same router, internal IP. If not, external IP.

---

### Post by orethrius on 2010-08-02
> **Keinan said:**
> Thanks for answering! :)

I'm sorry I'm a bit of a noob... which ip address should I be typing in? The ubuntu box's ip or My XP computer's external or internal ip (my XP box is behind a router)?

You'd enter the IP of the rig you're connecting to; so, if that's the Ubuntu box, then it'd be the Ubuntu box's IP.  :)

Otherwise, you're either running a WAMP server, or a LAMP server inside a virtual machine on the XP box.

---

### Post by Keinan on 2010-08-02
I'm tunneling to my Ubuntu Box via PuTTY from my home PC which is the XP box. The ubuntu machine is in a data center and not behind any routers or particular firewalls.


I used the command, and now I can't log in through tightVNC at all for some reason...is there a command to undo what I just did? :(

---

