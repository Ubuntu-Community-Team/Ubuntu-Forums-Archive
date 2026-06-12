---
title: "Firewall - Firestarter, FW-Builder, Info needed"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Ordes on 2009-07-19
i am using Firestarter.... Happy so far....
Except there is only:
1) Support for one interface at a time ( i checked FS. they announced that the new FS will have multiple interface support. but that was in 2005. so i think its off the table..)
2) Quick enable/ disbale of rules... So far FS only allows add/ remove


Q1: Are there any FW that are like FS plus those settings?

I tried guarddog... didnt like it.. it feels to restricted in the options u have...

---------------------

People always say that Iptables are very safe... but isnt it that, as soons as you open a port e.g HTTP/80, every app that uses this port can connect through? In Win i used Commodo, and besides the IPs i could allow/ deny applications to connect... e.g firefox.exe... in this case even when the port is open, i have one more layer of control.

Q2: Is there a FW that also supports this on Ubuntu?

-------------------------

FW-Builder
Now i am checking out FW-Builder. I think i am going to like it... But didnt install the build FW yet... Want to check first

Q3: FW-Builder seems to install the build FW. In case i completely f@@@ it up. How do i restore the original FW? Would it be enough to just run e.g the Firestarter setup wizard again?

Q4: FW-Builder seems to be just a building tool of Policies. Is it possible that after install of FW policy to real time monitor your network/ FW, like in Firestarter. e.g active connections, events.

Q5: If Q4 no. To startup e.g Firestarter for monitoring?

thanks

---

### Post by Ordes on 2009-10-20
using guardddog and load up firestarter for monitoring if needed...

---

### Post by Bradtek on 2009-10-20
> **Ordes said:**
> but isnt it that, as soons as you open a port e.g HTTP/80, every app that uses this port can connect through?

You only 'open" port 80 (http) on your computer if you are running a Web Server.

Your browser connects to port 80 on the website you are going to.
eg. ubuntuforums.org server will have port 80 open or else no one can view the web page.

---

### Post by Ordes on 2009-10-20
> **Bradtek said:**
> You only 'open" port 80 (http) on your computer if you are running a Web Server.

Your browser connects to port 80 on the website you are going to.
eg. ubuntuforums.org server will have port 80 open or else no one can view the web page.

not for guarddog.. guarddog closes all ports in and out.. so you have to open port 80 outgoing to be able to browse the internet...of course you keep your in-port 80 closed..


>> and my question was leading for outgoing port.. 
e.g firestarter.. is normally permissive to all outgoing...you can set it to restrict all outgoing and than open out-ports for certain applications e.g port 80, which your browser will use... but you actually have no control over which application uses this outport... which is different in e.g commodo firewall on windows... even when the out-port is open you can still define which application is allowed to use it... this kind of control in a firewall i didnt find yet in any ubu firewalls...

---

