---
title: "how to VNC into a remote computer with vinagre?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by switch10 on 2010-01-03
I installed ubutnu on a friends computer not too long ago, and hes running into problems with VirtualBox.  

I had him set up his remote desktop so hes "allowing others to view your desktop" and allowing others to control your desktop".  

I am running vinagre.

He is across the country from me.  how would I connect to his computer with VNC?  I cant use ssh because i have to mess with settings in VirtualBox.

Thanks

Dave

---

### Post by switch10 on 2010-01-03
ok im trying to create an ssh tunnel with:
```
dave@dave-laptop:~$ ssh -L 5901:127.0.0.1:5901 -N -f -l jarrett 192.168.1.5

```

and it wont connect??
```
ssh: connect to host 192.168.1.5 port 22: Connection timed out

```

---

### Post by mocoloco on 2010-01-05
You are probably both behind a router.  When remote desktop is enabled he probably sees the words "Your desktop is only reachable over the local network."  This is because the IP remote desktop shows is one assigned by his router, and is internal to his local network. You will need to set up his router to do [port forwarding]("http://portforward.com/") so that traffic for Remote Desktop (VNC) that comes from the internet to his router gets forwarded to the right computer. Follow that guide, to forward port 5900.

Another solution and the one I use is to set up your own router for port forwarding, then instead of using Ubuntu's Remote Desktop use [Gitso]("http://code.google.com/p/gitso/"), which establishes a reverse connection from the user's computer to yours, but gives you the control.  That's usually easier if the user on the other end is less computer savvy.

---

### Post by bodhi.zazen on 2010-01-05
> **switch10 said:**
> ok im trying to create an ssh tunnel with:
```
dave@dave-laptop:~$ ssh -L 5901:127.0.0.1:5901 -N -f -l jarrett 192.168.1.5

```and it wont connect??
```
ssh: connect to host 192.168.1.5 port 22: Connection timed out

```

You can not use 192.168.1.5 over the internet, you have to use your friend's public IP address and have him or her forward port 5900.

You will be more secure if you use ssh with the -X option

```
ssh yoru_friend's_user@public_ip -X
```In that case forward port 22 from your friend's router. 

You then simply start virtualbox

```
Virtualbox
```If you wish you can tunnel VNC over ssh as you did with your command.

---

### Post by switch10 on 2010-01-05
Awesome, thanks for the help guys!

---

### Post by doas777 on 2010-01-05
I use 
```

vncviewer -via sshuser@sshserver localhost:0

```
to connect to vino over ssh. is often less cumbersome than separately creating the tunnel with ssh. not sure if vinagre supports it, but real/tight do. x4vncviewer doesn't though.

[http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/](http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/)

---

### Post by mrhhug on 2011-05-18
doas777, 

thanks for that, I had 2 computers running maverick then i sligtly messed up the visual effects on my home computer, and found that as a perfect excuse to clean install natty. installed natty and my old method of ssh into the maverick box ```
ssh -L 5900:localhost:5900 **REMOTE**HOST**IP**
``` then just typing localhost into vinagre, that just wasnt working. and i set that up months ago.... i didn't feel like re-configuing a bunch of stuff.

your method worked excellent out of the box for Natty to Maverick. Thank you

---

### Post by OM NOM NOM on 2011-05-18
A couple of options that I found easier to use than VNC/Vinagre:

Teamviewer - has a Linux client to allow you to control a remote machine. Simple as installing the .deb package: 

[http://www.teamviewer.com/en/download/index.aspx](http://www.teamviewer.com/en/download/index.aspx)

I also like nomachine's NX client/server package. I use it almost daily and in my expeience blows away most other remote desktop utilities. Easy as pie to install as well:

[http://www.nomachine.com](http://www.nomachine.com)

---

