---
title: "remote desktop"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by vagelism on 2009-04-09
Hello to all. 

I want to make a remote desktop to one of my laptops that has windows xp and will remain home.
The other one has Ubuntu. 
Is there a user friendly solution like teamviewer for windows or something similar that can cooperate with both systems?
Thank you.
THANK YOU FOR YOUR TIME

---

### Post by Hospadar on 2009-04-09
You could use vnc:
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

or (I prefer) ssh:
[http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)
(You may want to google around for other tutorials on ssh as well, there's a lot you can do with it)

I like ssh because while it doesn't provide a full remote desktop, it can launch graphical applications remotely (even in windows, with a windows x server like xming and x11 forwarding) and is much more responsive than vnc, which is a full remote desktop solution.

With either of these, if you want to use them outside of your network, you'll need to configure your router to forward the appropriate port (if you use a router).
ssh uses port 22, and the vnc port excapes me, but a google search will turn it up.

There are many ssh and vnc clients for windows and linux.  In windows I like to use puTTY+xming for ssh.  You should be able to look up more on this stuff, exactly what it can do and how to do it.  Once you learn what to type in where, both are very easy to use.  All my friends regularly use ssh to access and get files from my server even though there are not programmers like myself.

---

