---
title: "Home network using ubuntu  as server."
date: 2010-12-07
forum: New to Ubuntu
---

### Post by gettinit on 2010-12-07
I want to take an older laptop I have, load Ubuntu on it and use it as a print/file server. 

I have looked around through the posts, googled etc. and it doesn't seem that difficult. 

What I want to do is use my old dell laptop with parallel port and USB ports to run my one HP laser printer, 2 usb printers (one multifunction) and 2 external hard drives. My brother and I live together and both have home offices in the same office with all our own personal stuff. 

we have 3 laptops (1 win7/ubuntu , 2 xp)and a freshly built win7 desktop and the above mentioned printers etc.. 

Currently I have it all setup and working through the dell laptop running xp and sharing the printers. It works fine but I can't get the scanning utilities etc to work on the other computers. Plus I have been told by several people if I'm running that much stuff you should just use Ubuntu and network it like a server, so here I am.. 

Before I start anything I would like to know where to start. As I said its up and running now, so ideally I would like to install Ubuntu beside the xp install to retain functionality of the network. That way if something goes wrong and I cant take the time to figure it out then, I can just reboot in windows until i can get back to it. 

I am fairly decent with computers, I have built a few and can get around better than some but will still consider myself a beginner. My knowledge in networking is limited, I'm starting this basically as a learning process for myself and to see if I can figure it out! 

Sorry for the long post but the long and short of it is how should I install Ubuntu to work like described and what are my first couple of steps? 

And if there is already a perfect thread for this I am sorry. Please point me in the direction but I have looked off on on for a few weeks now and couldn't find one starting from square 1. 

Thanks for any help!

---

### Post by bodhi.zazen on 2010-12-07
You can share printers via samba.

A server in Linux typically does not have a graphical interface, not sure how you feel about that.

[https://help.ubuntu.com/10.04/serverguide/C/samba-printserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-printserver.html)

Not sure what you want with networking. Could be anything from setting a static IP to a dns server (use dnsmasq).

---

### Post by gettinit on 2010-12-07
Well thats kind of my question. Is just sharing the computers like what I am doing now the best way to have it setup? Maybe I don't fully understand the advantages or disadvantages to setting it up like a server. Basically what I am shooting for is to have a secure way to use the full functions of all of my printers. Mainly the scanning function. 

As I said it works fine now but what would be the advantages of setting it up as a server?

---

### Post by bodhi.zazen on 2010-12-08
> **gettinit said:**
> Well thats kind of my question. Is just sharing the computers like what I am doing now the best way to have it setup? Maybe I don't fully understand the advantages or disadvantages to setting it up like a server. Basically what I am shooting for is to have a secure way to use the full functions of all of my printers. Mainly the scanning function. 

As I said it works fine now but what would be the advantages of setting it up as a server?

As always, it depends =)

The larger your network, the more the advantages.

It takes a little time to learn to admin the network (did I mention dnsmask ? ) and set up the servers, but once you learn you gain a few advantages.

Samba is probably the most common server on a small LAN, followed by NFS. These services are used for file and printer sharing. File sharing serves both as a central location and backup of data.

dnsmask provides DNS services and is easy to configure. Works well on a small LAN. You can then connect to the server by server name rather then IP address.

Now that I am familiar with servers I can have samba set up for a LAN in a few minutes.

With all that in mind, "server" is a broad term and again it depends on what you are wanting to do exactly. A print server is much easier to manage on a LAN (easier to share one printer between 10 computers then 10 local printers on 10 computers). Some printers are already network enabled.

I am not sure about the scanning part, I have not tried to scan documents.

You will have to get a start and ask questions if you get stuck.

---

