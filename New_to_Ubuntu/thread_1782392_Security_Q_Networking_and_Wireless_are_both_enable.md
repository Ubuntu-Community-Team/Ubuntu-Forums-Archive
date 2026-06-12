---
title: "Security Q: Networking and Wireless are both enabled"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by held7over on 2011-06-14
Ubuntu10.10 - 2 Questions. In my computer room, my Tower is connected to wire, but in my living room it now communicates via a wireless card I installed. 

I have noticed that when I boot up connected to wire, the Internet Icon reports that both Ethernet and Wireless are enabled, but hovering my pointer over the Icon, it reports I am connected to wire. However, the Connection Information section reports both capabilities.

Q1: Does this mean that someone can contact my computer via wireless while I am using Ethernet....if I forget to disable wireless when I boot up up? Or is only one service actually authorized by my choice at a time?

Q2. It appears that Firestarter wants me to run the wizard in order to change between protecting Ethernet or protecting Wireless...or is there a way to protect both so I can forget having to remember to put the shields up as I switch between Internet connections? If not, will Uncomplicated Firewall do this?  (I'm forgetful.) Thanks! :p

---

### Post by doas777 on 2011-06-14
no, a wifi nic will not (under normal circumstances) accept an unsolicited request to peer with an unknown device. 

drop firestarter and try gufw instead. firestarter has been dead for years. also if you have a home router, and you do not provide any network services to other comptuers in your house, you probably don;t need a firewall at all. a firewall (in this context) is only really needed when you want to provide services, but only to a specific subset of entities.

---

### Post by held7over on 2011-06-14
Thanks doas777!

Actually, my router takes care of 4 wired computers (including a server I am trying to build, plus 3 wireless computers....(plus an occasional guest in my home from time to time). Don't take that to mean I know what I am doing. :p I am definitely in over my head. I will take your advice and switch to gufw.

I have a question concerning UFW and the server I am trying to build. I looked at shorewall/smoothwall but that looks to be way over my head. I have set up my host system with Debian, installed OpenVZ, and plan to put my web projects (when I get to that part of my learning process) in separate Virtual Containers running Ubuntu. What I want to know is, if I put ufw in its own Virtual Container, can I use it to screen all traffic and forward IP access to their proper Virtual Containers while sending all URL traffic to Apache (or hopefully and easier web server) in its own virtual container also, letting it direct URL traffic to their respective virtual containers? 

(I hope I said that so you could figure out what I want to do....)

I met a fellow who advised me that was how he did things and it worked quite well for him, but I don't have contact with him so that I can ask particulars now that I have gotten this far...

Thanks! And if there is anything you can direct me toward to study over, that would help me understand what I need to know, please point me at it! I have a lot of holes in what I don't know!!! :p

---

