---
title: "Installing/configuring a home server"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by gtg947h on 2009-02-22
So I'm getting ready to set up a home server.  I have a basic AMD desktop system for the hardware, and am planning on installing Ubuntu server edition.

The server will have several roles:
network storage
print server
light-duty webhost
SSH (for secure remote access to files)
eventually mail server

However, I'm not quite sure about the best way to set the thing up.

First, regarding the network configuration, which is better:

Cable modem --> server --> router --> rest of network

or

Cable modem --> router --> server and rest of network?

Second, once I have the OS installed on the server (I assume the install CD will handle the partitioning, formatting, and initial install) how do I configure the software?  There doesn't seem to be a GUI included; do I want to install one, or find some kind of administration program, or do I have to just use the command line?  

I should add that I'm pretty new to Linux, and have only used it a handful of times at school and work.

Thanks for the help!

---

### Post by marshall.robert on 2009-02-22
Well, its a bit of a jump doing a web server like this if your new to linux as a whole. But that said, I have done exactly what you are asking here and I'll put my experience to good use by helping you.

First, your question regarding the network configuration, I'd use the second way you have suggested. This will allow you to use your router as a firewall through port forwarding.

Second, when you install ubuntu server you have a choise of what you want it to do, dependant on the version (i.e. 8.04 or 8.10) there will be some differences in whats included. You can install a GUI but thats not necessary. I use a package called Webmin, not in the repos, found here [http://webmin.com/](http://webmin.com/) .

SSH comes out the box. If you want to use SSH, just type "ssh serverip" into a terminal in linux, and for windows use PuTTy.

The web server bit is easy, just dump it all in /var/www/. Unless you have specific needs.

The mail server is somewhat tricky, depending on your needs. You can take either a webmail approach, which I have done. Or the POP3 approach, which uses a client like Thunderbird. I also have this enabled but don't use it. For webmail I have RoundCube  ([http://roundcube.net/](http://roundcube.net/)), which I believe can be installed from the repos.

As for the print server side of things, I only just managed that yesterday after several hours. I found the simplist way to set your print server up is to connect with another ubuntu machine via Administration -> Printing -> File -> Connect to server (something like that, im working off memory here). And then add a printer that way. I have it shared via samba, allowing use with windows easily, which seemed to be done automatically.

Best of luck to you, and post if you have problems and I'll do my best to help.

-Rob

---

### Post by yeats on 2009-02-22
> First, regarding the network configuration, which is better:

Cable modem --> server --> router --> rest of network

or

Cable modem --> router --> server and rest of network?

Definitely option 2.  If you do it the first way, your server will almost certainly NOT be on your LAN.

> Second, once I have the OS installed on the server (I assume the install CD will handle the partitioning, formatting, and initial install) how do I configure the software? There doesn't seem to be a GUI included; do I want to install one, or find some kind of administration program, or do I have to just use the command line?

IMHO, you should learn the command line, and actually use this server project as an opportunity to do so.  It will be a steep learning curve if you've never done it before, but there are MANY resources for you out there. (Keep in mind that Ubuntu is derived from Debian, so almost all Debian documentation out there will be relevant for configuration files, etc.).

Having said that, there are graphical front ends to programs that you'll need to be able to use, but they can be used on a client computer on your network through a web browser (CUPS - the Common Unix Printing System - comes to mind).  Also, once you've got SSH up and running, you can use a terminal program to manage and configure your server from other computers on your network.

Good luck - sounds like a great Linux project!

---

### Post by bryanl on 2009-02-22
Where [Ubuntu seems to be going for this](https://help.ubuntu.com/community/eBox) is towards [eBox](http://ebox-platform.com/). It is an integrated (the advantage over Webmin) server management through a web interface.

The focus is more on the small office but it would fit right in to your router upstream and LAN downstream model.

---

