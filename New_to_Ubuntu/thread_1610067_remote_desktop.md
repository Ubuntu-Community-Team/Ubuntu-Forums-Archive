---
title: "remote desktop"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by arju305 on 2010-10-31
Guys. I am at work. I want a remote desktop to control my office computer through my home computer. 
I googled it and found that it is possible through remote desktop.
I am new to linux and i didn't get the point in different websites.
I would be grateful if u could provide me the procedure.
thanking you in advance.

---

### Post by P4man on 2010-10-31
Its highly unlikely your corporate network will just let you connect to your PC very easily. There will be firewalls and NAT addressing preventing you from doing that.  You should talk to your IT department ask them what is and isnt possible, but most likely you will need to initiate the connection from your work pc to your home pc (since you will have full control over your home network and not your corporate network). Once that is established, you can go home and remote desktop the other way.

Setting up a connection that way is called a reverse tunnel, it requires you have a static IP (or dyndns or similar) at home, that you have configured your router/firewall at home correctly  and you must be allowed to install additional software on both PCs, including the work pc (ssh being the most important one).

If  none of that sounds impossible, then I can explain how to do it.

---

### Post by luvshines on 2010-10-31
> **arju305 said:**
> Guys. I am at work. I want a remote desktop to control my office computer through my home computer. 
I googled it and found that it is possible through remote desktop.
I am new to linux and i didn't get the point in different websites.
I would be grateful if u could provide me the procedure.
thanking you in advance.

It is very much possible. You need to allow remote desktop connections from your office computer and then connect to it from home.
But it can be a potential security threat since it won't be secure and may be open on public ip's. If that is not the case then it should work

Else, you may want to try Teamviewer. Though I havent' tried it, but ppl on this forum say that it works gr8
[http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)

---

### Post by sahabcse on 2010-10-31
#sudo apt-get install rdesktop
#rdesktop -F ipaddress

---

### Post by P4man on 2010-10-31
> **sahabcse said:**
> #sudo apt-get install rdesktop
#rdesktop -F ipaddress

You really think at work he has a public IP address and all ports are open? Somehow I doubt that.

---

### Post by NickJones on 2010-10-31
I know that TightVNC for Windows has a built in Web sever, so if yo use that you will find that you should bypass the firewalls. I'm pretty sure that the Linux version would have it too.

---

### Post by arju305 on 2010-11-01
guys. it was possible through team viewer...... 
thanks....

---

### Post by jfbooth on 2010-11-01
Teamviewer is awesome.

---

### Post by rcayea on 2010-11-01
> **jfbooth said:**
> teamviewer is awesome.

[size="5"]+1[/size]

---

### Post by HermanAB on 2010-11-01
Howdy,

Teamviewer is a kind of Reverse VNC.  Ultra VNC can also do that.

---

