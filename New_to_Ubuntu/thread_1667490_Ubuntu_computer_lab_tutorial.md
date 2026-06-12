---
title: "Ubuntu computer lab tutorial"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by rock84 on 2011-01-14
Hello, I am somewhat of a beginner when it comes to ubuntu and when I try to customize something I always just follow tutorials. I have 3 computers that I want to install Ubuntu on. I would like to have them on a LAN and make it so that anyone can log in to their user account from any computer and have their own desktop settings and home folders.  I have been looking all over the internet like crazy but haven't found any step by step guides or articles that explain how this would all work. I have a very vague understanding of what a server is. And its role on such a setup like the one I'm looking to create. I've found a couple of posts with this same question but the reply's are always just links to things like Samba or edubuntu, but when i click on em its just info about the projects and i feel like i'm at a dead end, and samba to me sounds more like just file sharing, and edubuntu is thin client based.
Does anyone have some step by step tutorial on creating this computer lab type setup? or a beginner's guide/diagram  to how this would work?

Can the server computer also be a client at the same time? or will the server computer have to sit there untouched?

---

### Post by Naitsirhc Hsem on 2011-01-15
Yes a server can be a client.

I use ssh with X forwarding:

ssh on server with multiple user accounts
default user account on client machines
open terminal
log into "server machine" eg "ssh -X user@192.168.0.12"
this will allow you to run gui commands over the network, like the file manager nautilus, firefox, chromium, tetris.
It uses the "server"'s settings for that user for the specific application
please ask for more info if needed, I have been playing with this for a while

XDMCP,

remote login from client log in screen, need an older version of ubuntu, 8.04 or so.  Or, find a way to enable it on the newer versions


I would recommend the first option,  1 server with accounts, multiple clients with generic login.  use ssh -X to connect to server.  Open applications.

Good luck!

---

### Post by rock84 on 2011-01-15
Thanks for your reply. I understand that you have two ways of solving this problem:

1. by using ssh on server

or

2. by using XDMCP

I want users to have the same experience as if they are always using the same computer. From reading about xdmcp i get that it uses a lot of bandwidth and is a type of remote desktop viewing system. I think this will slow down the computers/user experience.
I don't think I would want to use SSH because the users are not that computer literate. Unless it can be integrated at the user log in screen, and some how set the 'home' folder to that of their respective users. 
I appreciate your reply though.

---

### Post by Ocxic on 2011-01-15
check out [http://www.ltsp.org/](http://www.ltsp.org/)

---

### Post by rock84 on 2011-01-15
> **Ocxic said:**
> check out [http://www.ltsp.org/](http://www.ltsp.org/)

Thanks but I had already come accross this and I'm not looking for a thin-client solution because I want to be able to use each computer's hardware such as video cards and HDD. Also, I am looking for a tutorial or some general steps that will set me in the right direction as I am not that knowledgeable.

---

### Post by rock84 on 2011-01-16
Alright, I found this website and I think its what I'm looking for:

[http://jonathancarter.org/2010/11/24/how-do-ltsp-fat-clients-work/](http://jonathancarter.org/2010/11/24/how-do-ltsp-fat-clients-work/)

I'm gonna follow these steps.

---

### Post by rock84 on 2011-01-16
Alright, I found this website and I think its what I'm looking for:

[http://jonathancarter.org/2010/11/24/how-do-ltsp-fat-clients-work/](http://jonathancarter.org/2010/11/24/how-do-ltsp-fat-clients-work/)

I'm gonna follow these steps.

---

