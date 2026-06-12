---
title: "Rsync with SSH keys"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by beansbbq on 2007-03-04
Hello all,


I'm hoping that someone will be able to help me translate the OS X centric instructions on the first link.  I'm trying to follow the instructions from the first link to automatically backup my SAMBA share to my Joyent Connector as illustrated in the second link. 

[http://blog.invisible.ch/2005/10/06/back-up/](http://blog.invisible.ch/2005/10/06/back-up/)

[http://blog.invisible.ch/2007/03/02/joyent-strongspace-and-my-samba-server/](http://blog.invisible.ch/2007/03/02/joyent-strongspace-and-my-samba-server/)

Thanks,

---

### Post by indeterminate on 2007-03-04
I don't see anything on that page that wouldn't work in Linux. If you check google, there are lots of other pages about how to set up SSH for automatic logins:
[http://www.google.com/search?q=ssh+automatic+password&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=ssh+automatic+password&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

which all give basically the same directions. Are you having any particular problems with any of the steps in the instructions?

---

### Post by beansbbq on 2007-03-04
Thanks for the feedback.  

I saw that SSHKeychain was an OS X based program.  Additionally the instructions call for creating a "dsa" file. 

$ ssh-keygen -t dsa -b 1024

While all of the other SSH sites that I've seen, including those from your search link, discuss generating an "rsa" file.  I'm not sure what the difference is, but I'll give it a go and report back.

---

