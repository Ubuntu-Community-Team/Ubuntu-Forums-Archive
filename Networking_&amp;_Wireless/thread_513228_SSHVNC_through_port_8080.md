---
title: "SSH/VNC through port 8080"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by Prometheus7 on 2007-07-30
Here is the situation:

**I have a windows machine at work** which is behind routers/firewalls/you name it and basically only accepts stuff through a proxy. So in firefox or ie on that machine, you have to go and set the special internet settings to go through that proxy or else you won't be able to browse the net.

**I have a home machine running Ubuntu** which is behind a router and have forwarded ports 80, 22, and 5900.

**I would like to access my home machine from work**, but have had absolutely no success trying to do so (I am not sure if I am correctly setting sshd/vncserver to go through port 80). 

I have tried many different workarounds -- including setting up apache and the tightvnc java applet on my home computer (this works at the login screen, but then routes vnc through port 5900 and thus fails). I have also tried running the following command: vncserver -httpport 8080 :0.

I have also tried to setup sshd to run on port 8080 (sshd -p 80) and use an ssh tunnel via putty on my work machine.

I am getting really frustrated because no matter what I try (and I've tried for almost a week now), I can't access my home computer via ssh or vnc (and I know that this theoretically has to be possible).

Does anyone have an idea of what I am doing wrong? ](*,)

---

### Post by dmizer on 2007-07-30
well, you can only have one process accessing a port at any one time.

or in other words, you can't have both vnc and ssh listening on port 8080.

now.  to get around your firewall, you simply need to set up a revers ssh tunnel, where your work computer dials home.  once it's dialed home, you can use your home computer to connect to your work computer via the tunnel.  here's a good howto for that: [http://www.brandonhutchinson.com/ssh_tunnelling.html](http://www.brandonhutchinson.com/ssh_tunnelling.html)

here's something specific about working with proxy's: [http://www.linuxsa.org.au/pipermail/linuxsa/2003-July/057962.html](http://www.linuxsa.org.au/pipermail/linuxsa/2003-July/057962.html)

not too sure what to tell you about the vnc, but my thoughts are that vnc is not going to work well over the internet anyway.  just use the "-X" switch with ssh, and you can start any gui application.

---

### Post by dreadlord_chris on 2007-07-30
maybe this will help:
[http://www.buzzsurf.com/surfatwork/](http://www.buzzsurf.com/surfatwork/)

---

### Post by Prometheus7 on 2007-07-30
I'm not sure I understand. I am trying to access a linux machine using windows and thus would need to use a program like putty to ssh, right? The windows machine is the one behind the firewall/proxy. Is there any tutorial out there for using putty in this situation?

My linux machine is behind a router but port 22 is already forwarded.

---

### Post by dreadlord_chris on 2007-07-30
> **Prometheus7 said:**
> I'm not sure I understand. I am trying to access a linux machine using windows and thus would need to use a program like putty to ssh, right? The windows machine is the one behind the firewall/proxy. Is there any tutorial out there for using putty in this situation?

My linux machine is behind a router but port 22 is already forwarded.

The link I sent you describes how to connect with SSH through a firewall/proxy to your home comuter...

did you look at it?

---

### Post by Prometheus7 on 2007-07-30
can't access that one -- I'm at work 8-[

---

### Post by Prometheus7 on 2007-07-30
tried everything. still not working...

---

### Post by dreadlord_chris on 2007-08-02
> **Prometheus7 said:**
> tried everything. still not working...

OK, this is a little more detailed:
[http://www.tldp.org/HOWTO/text/Firewall-Piercing]("http://www.tldp.org/HOWTO/text/Firewall-Piercing")

---

