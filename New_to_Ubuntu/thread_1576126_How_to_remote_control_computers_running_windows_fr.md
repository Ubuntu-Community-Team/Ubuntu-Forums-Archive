---
title: "How to remote control computers running windows from ubuntu"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by tacotime on 2010-09-16
hey party people, 

as tech support for family and friends, I often find myself having to ride out to relatives' houses to fix their computer problems.

I'm wondering if there's any way I can control their computers from my ubuntu laptop even if they're not on my network. 

All help is appreciated, 

-tacotime-

---

### Post by jkurtisr32 on 2010-09-16
Hmm... I wonder if there is a way to use the Windows Remote Assistance on Ubuntu. I used this feature back when I used to run Windows, and it was very useful.

Using Remote Assistance, someone in need of help just sends an invite via email, and you would follow the link in the invite. I don't know whether or not there is a way to do this with an Ubuntu computer as the client

---

### Post by r+9 on 2010-09-16
yes, but likely no.

You can set up a ssh-tunnel then run a VNC through the tunnel, but you need an external IP for that to work out.

Also your "clients" need to be running a ssh-server and vnc-server (not to hard to set up) then you can remote into their desktop and do whatever you like.

My ISP "ran out" of external IP addresses so when I'm on the road I cannot ssh back home to fix things or access files.  Bummer.

---

### Post by jkurtisr32 on 2010-09-16
> **r+9 said:**
> My ISP "ran out" of external IP addresses so when I'm on the road I cannot ssh back home to fix things or access files.  Bummer.

I think you could use some type of redirect client to fix this issue. I plan on using No-Ip once I'm done building my server. No-Ip will read your dynamic external IP address and match it to the domain that you create on the No-Ip website.

**EDIT: Oops, I think I misinterpreted what you meant. My bad

---

### Post by r+9 on 2010-09-24
yeah I looked into that, my "external" is the ISP's IP so I look like a guy behind a router without any port forwarding.

---

### Post by kendoori on 2010-09-25
While it won't work to go back the other way (Windows --> Ubuntu), Logmein free works very well and gets around the IP issue. As the name implies, it's free.

[https://secure.logmein.com/welcome/access/fasteasy/7/?wt.srch=1&originid=6591&utpk=LogMeIn&destination=/welcome/access/fasteasy/7/](https://secure.logmein.com/welcome/access/fasteasy/7/?wt.srch=1&originid=6591&utpk=LogMeIn&destination=/welcome/access/fasteasy/7/)

---

### Post by saporito on 2010-09-25
I actually did this yesterday. You have to forward their router's port (the port that uses VNC) to there ip on their network and then make sure they have a vnc server installed (I used tight vnc) and then use your remote desktop connection. Not a simple solution if they have to do the forwarding though

---

### Post by karthick87 on 2010-09-25
Use Teamviewer [http://www.teamviewer.com/download/teamviewer_linux.deb](http://www.teamviewer.com/download/teamviewer_linux.deb)

---

### Post by CharlesA on 2010-09-25
> **getyourkarthick said:**
> use teamviewer [http://www.teamviewer.com/download/teamviewer_linux.deb](http://www.teamviewer.com/download/teamviewer_linux.deb)

+1

---

