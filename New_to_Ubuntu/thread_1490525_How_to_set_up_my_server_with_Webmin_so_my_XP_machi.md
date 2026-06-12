---
title: "How to set up my server with Webmin so my XP machines can get to it."
date: 2010-05-22
forum: New to Ubuntu
---

### Post by techsupp on 2010-05-22
Let someone talk me into this new server and hopefully once i understand I will really like it.  However, I have no clue where to begin to set up my server.  I am replacing a Windows NT server with this one and still have it running just in case.

I need some type of tutorial or documentation to tell me what the steps are to use Webmin to setup this box as my server and what I have to change on the XP PC's that will be connecting to it for data files, storage, etc.

Thought Webmin looked easy but seems that the terminology is somewhat different as well as I am not that technical.

---

### Post by Nythain on 2010-05-22
Webmin is really nothing more than a web based front end for various other services/daemons running on the server, it not a requirement, and its gonna take more than *just* webmin to get your server servin. But it is a good starting point i guess, better option than installing a DE on it.

just googled around, cant find any decent "just webmin" guides, since its a fairly easy piece of webpage to install.

i will note, other things you might want to look into

Samba - smb file sharing (allows sharing with windows networks)
Apache2 - web server
lighttpd - a very lightweight alternative to apache2
php and mysql - gonna be required for just about anything you want to do with a webserver

SSH - secure shell, ssh encrypted connection to the server for command line maintenance... this is your best friend on a server

---

### Post by techsupp on 2010-05-22
I already have all these things installed, just looking for documentation to give me the steps required to put this server into the network.  Thinking I'll just keep the NT server as it is still running and I understand it.  Doesn't seem to be much in the way of documentation on Webmin or Ubuntu for beginners. Have already spent way too much time trying to figure this stuff out.

Thought this was going to be easier and better than going to the new Windows Server software.

---

### Post by bodhi.zazen on 2010-05-22
> **techsupp said:**
> Let someone talk me into this new server and hopefully once i understand I will really like it.  However, I have no clue where to begin to set up my server.  I am replacing a Windows NT server with this one and still have it running just in case.

I need some type of tutorial or documentation to tell me what the steps are to use Webmin to setup this box as my server and what I have to change on the XP PC's that will be connecting to it for data files, storage, etc.

Thought Webmin looked easy but seems that the terminology is somewhat different as well as I am not that technical.


You are asking a very broad question.

First this link my help:

[Detailed Debian + Webmin  (web based graphical interface) guide, with screen shots]("http://woodel.com/")

Installing anc configuring your "server" depends on what server ? Apache ? Samba? what ?

See:

[Ubuntu 10.04 Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html")


Connecting windows boxes ? Well, what problem are you having ? Should work out of the box.

Your problem could be anything from server configuration to network to firewall to well who knows.

---

### Post by drdos2006 on 2010-05-23
I found this to be very, very useful.

"Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood"


regards

---

