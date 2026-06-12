---
title: "[SOLVED] setting up ltsp on gutsy"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by angelot on 2008-01-21
I've just installed ubuntu 7.10 server edition selecting LAMP and mailserver as preconfigured packages.

On the ubuntu-server edition pages on ubuntu.com it's written that ltsp-support are included.

How can I kown that ltsp-support is enabled? I have no files in /opt...

I didn't check DNS-server as a pre-configured package during install. Did I need this to have ltsp-support enabled? There was no ltsp option in the list....

Can I still install ltsp-support?

Will sudo apt-get install ltsp-server-standalone and then ltsp-build do the trick?

On my server I have two ethernet-cards:

eth0 getting ip (dhcp) from my adsl connected to internet
eth1 static ip 192.168.0.1 local

I've connected a thin client to eth1 on the server.

Where to go from here?

Any howto's on ltsp on a gutsy server with two network-cards?



Angel.ot

---

### Post by fredsnet on 2008-01-21
This page should answer all your questions.  It has a step-by-step instructions.


[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

Fred

---

### Post by angelot on 2008-01-22
Yeah - I knew about that howto, and of 

[http://ubuntuforums.org/showthread.php?t=599166&highlight=ltsp]("http://ubuntuforums.org/showthread.php?t=599166&highlight=ltsp")

But my question - do I have ltsp included (as stated on the ubuntu.com-site) and a running dhcp-server or do I have to install ltsp-server-standalone.

As the guide you provided say - I need a Ubuntu 5.10. I've got a 7.10 server...

1. If I don't have ltsp included - how can I install the server edition to include it by default?
2. If 7.10 server does not come with ltsp, can I use the ltsp-server-standalone on my server?
3. If not - how can I do this?

Thanks !

---

### Post by fredsnet on 2008-01-24
1.) Unless you installed Edubuntu server which automatically installs LTSP by default. You            will have to install LTSP manually.  

2.) Yes or install Edubuntu.    [http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)

3.) All installs are manually configured except the Edubuntu edition.

As a friendly suggestion, spend some time and read over the different ways LTSP can be installed.  A lot has changed over the years with LTSP and Ubuntu web sites are behind in updateing and consolidating their instructions and procedures pertaining to LTSP.  

I have spent a great deal of time reading and asking questions and as of yet am not ready to proceed myself.  Still a few unanswered questions.  But I am in no rush, just carefully proceeding.

Fred,

---

### Post by maybeway36 on 2008-01-25
I just installed edubuntu-server. That got LTSP up and running.

---

### Post by angelot on 2008-01-25
Well, I 'll try edubuntu-server if I can't get the LTSP on Ubuntu-server up and running.

I've installed LTSP standalone, and everything is running fine: DHCP3, NAT, NFS...

The problem is that I can't login from the client. The clients boots, get IP, run PXE, splash screen and loginscreen.

But I can't login - I get a XSESSION error (can't find .xsession in my homedir). I have no GUI on my server an no X-server running.
I can't login from a shell either - I get "Login incorrect" using my own account on the server....

---

### Post by maybeway36 on 2008-01-25
edubuntu-server only installs the LTSP and D?HCP servers, and related packages. It doesn't install GNOME  or the Edubuntu colors or anything like that.

---

### Post by angelot on 2008-01-27
> **maybeway36 said:**
> edubuntu-server only installs the LTSP and D?HCP servers, and related packages. It doesn't install GNOME  or the Edubuntu colors or anything like that.

I've just installed edubuntu-server 7.10 and finally ltsp is up and running with no problems :lolflag:

And - yes, edubuntu installs by default GNOME and all the Edubuntu colors...

I belive to get ltsp running you'll have to have a working X-enviroment on the server....

Thanks for all help...

---

