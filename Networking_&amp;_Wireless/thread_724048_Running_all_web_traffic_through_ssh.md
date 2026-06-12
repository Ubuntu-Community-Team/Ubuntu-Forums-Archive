---
title: "Running all web traffic through ssh"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by gardara on 2008-03-14
I am currently on a network that is only open for http traffic and has port 22 open for ssh.

Can I run all my web traffic through ssh? So I can use xchat, pidgin, etc.

I did read something about ssh tunneling but I am not understanding if that's what I need, since in all the tutorials I have read it only shows how to tunnel http traffic.

Thanks in advance.

---

### Post by pana.corbului on 2008-03-14
Youu could watch this: [http://www.irongeek.com/i.php?page=videos/sshdynamicportforwarding](http://www.irongeek.com/i.php?page=videos/sshdynamicportforwarding)

I currently use tunneling throught for utorrent. It could be used for almost every app that has socks5 proxy setup.

---

### Post by gardara on 2008-03-14
> **pana.corbului said:**
> Youu could watch this: [http://www.irongeek.com/i.php?page=videos/sshdynamicportforwarding](http://www.irongeek.com/i.php?page=videos/sshdynamicportforwarding)

I currently use tunneling throught for utorrent. It could be used for almost every app that has socks5 proxy setup.

Thanks I'll watch this.
Can you run many applications at once through tunnel? Or can I only run one application at a time?

---

### Post by pana.corbului on 2008-03-14
The ideea is that only one port per application can be used [that is something that can't be changed] 

I simply open dynamically on localhost a port for http [my web content is filtered] and choose in firefox settings socks5 proxy on localhost on port xxx and so on for every other application. You can even connect remotely to your vnc server from home ;)

---

