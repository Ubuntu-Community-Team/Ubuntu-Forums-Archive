---
title: "ssh tunneling?"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-07-20
[http://www.linuxjournal.com/video/quick-and-dirty-ssh-tunneling](http://www.linuxjournal.com/video/quick-and-dirty-ssh-tunneling)

was the video I saw so how do I set my my home network for this?

I want to be able to access the computer for files and programs so I will need x forwarding. I also want to use firefox for web broswing. Is their a way to do this with sshfs to mount folders?

for web browsing
ssh -C -N -L 8888:192.168.1.1:3128 spowers@homeserver

for programs
ssh -C -X -L 8888:192.168.1.1:22 spowers@homeserver gnome-terminal

How does the place from home let say free wifi tea shop know the home address of 192.168.1.1:port? what do i need to do to my router?

---

### Post by stlsaint on 2011-07-20
You need to setup port forwarding. Check your router model and do a quick google search of the model and port forwarding.

---

### Post by jhargis1012 on 2011-07-20
If the question is how will I connect to my home pc remotely when the router has a generic ip address of 192.168.1.1, then I was actually wondering this myself. Is it possible for the average home user to SSH home from a remote location?

EDIT: Sorry, stlsaint, we posted at the same time and I didn't see your post. I'll have to check out port-forwarding. Thanks.

---

### Post by stlsaint on 2011-07-20
> **jhargis1012 said:**
> If the question is how will I connect to my home pc remotely when the router has a generic ip address of 192.168.1.1, then I was actually wondering this myself. Is it possible for the average home user to SSH home from a remote location?

Yes, again you must setup whats called port forwarding.

---

### Post by bodhi.zazen on 2011-07-20
> **jhargis1012 said:**
> If the question is how will I connect to my home pc remotely when the router has a generic ip address of 192.168.1.1, then I was actually wondering this myself. Is it possible for the average home user to SSH home from a remote location?

EDIT: Sorry, stlsaint, we posted at the same time and I didn't see your post. I'll have to check out port-forwarding. Thanks.

You set up port forwarding and use your public IP address rather then your private LAN (192.168...)

[http://www.whatismyip.com/](http://www.whatismyip.com/)

---

### Post by androssofer on 2011-07-20
best way to access it from the interwebz is to hav a dynamic host name.  dyndns.org is the best option (in my opinion) as its free etc etc... to get an account, go here (pick the free option ):

[http://www.dyndns.com/](http://www.dyndns.com/)

then follow this tutorial on how to link it to your computer

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

tht will mean if ur ISP changes ur ip, u dnt need to worry, then if u've set up port forwarding on your router all u need to do is:

```
ssh -X -C username@hostname.dyndns.org
```

and u'll b connected to home via ssh with x11 forwarding.

if u where to use:

```
ssh -X -C -D 1024 username@hostname.dyndns.org
```

it will forward port 1024 on for u... and if u confiure a local firefox's SOCKS proxy to use localhost 1024 it will forward all ur Internet traffic thru tht and u dnt need to run firefox over the ssh tunnel, which can b slow (i do this in work :) )

---

### Post by lance bermudez on 2011-07-27
I get an error I have 
ssh -X -C 8888:1.2.3.4:22 user@hostname
ssh: Could not resolve hostname 8888:1.2.3.4:22: Name or service not known

I have port forwding set up on both of my routers

---

### Post by lance bermudez on 2011-07-27
I also have a bind9 dns cash

---

### Post by bodhi.zazen on 2011-07-27
> **lance bermudez said:**
> I get an error I have 
ssh -X -C 8888:1.2.3.4:22 user@hostname
ssh: Could not resolve hostname 8888:1.2.3.4:22: Name or service not known

I have port forwding set up on both of my routers

You have a syntax error ;)

Read the link I gave you or look at the command androssofer gave you.

> **lance bermudez said:**
> I also have a bind9 dns cash

why are you running bind ?

You should probably start a separate thread on bind ;)

---

