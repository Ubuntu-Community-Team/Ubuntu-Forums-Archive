---
title: "Trying to access Ubuntu Server edition through Vista SSH"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by iammatic on 2010-02-15
Hi everyone,

So I am a big newbie and trying to login remotely to my newly setup older compaq pc which I loaded the Ubuntu Server edition on.  I am attempting to use secure shell on my laptop which runs vista to login remotely to my server. I am not sure how to go about doing this. I do know that I already have openssh-server installed on the Ubuntu server. Any help would be very much appreciated.

---

### Post by Satoru-san on 2010-02-15
There is a windows program called putty, this will allow you to ssh into your ubuntu, if you of course set up port forwarding in your router (if you want to access from outside the network) otherwise you can type in your local IP.
[[img]http://www.cs.uregina.ca/Links/class-info/115/gifs2/putty_icon.gif[/img]Putty Download](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by iammatic on 2010-02-15
I have secure shell already so I was going to use that. Do I need to use putty?  How do I set up port forwarding on my router? I am not familiar with why I would need to, could you explain? I know the host name and the user name on the server but how do I find out what port it is using with secure shell? Thanks again.

---

### Post by bodhi.zazen on 2010-02-15
> **iammatic said:**
> I have secure shell already so I was going to use that. Do I need to use putty?  How do I set up port forwarding on my router? I am not familiar with why I would need to, could you explain? I know the host name and the user name on the server but how do I find out what port it is using with secure shell? Thanks again.

The short answer is your router acts as a firewall and in order to connect to your home computer you need to "port forward".

The exact way to port forward is dependent on your router.

[http://portforward.com/](http://portforward.com/)

(open) ssh uses port 22 by default.

Make sure you are using a strong password ;)

---

### Post by iammatic on 2010-02-15
Thanks for your help

---

### Post by Iowan on 2010-02-15
[Here]("https://help.ubuntu.com/community/SSH") is a help page for SSH (which includes links to several more).

---

