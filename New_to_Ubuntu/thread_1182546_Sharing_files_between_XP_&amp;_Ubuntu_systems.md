---
title: "Sharing files between XP &amp; Ubuntu systems"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by Scunnered on 2009-06-09
I have one custom written programme which is on a XP system.  This system like my Jaunty one are both wireless connected to the internet. What I would like do is access the XP machine from Jaunty to let me process data without having to mess about from machine to machine and room to room.

Can you offer guidance on how I may achieve my aim.

Thanking you in anticipation

---

### Post by nandemonai on 2009-06-09
Depends. Do you just need to access data on the XP machine? Or full control of the desktop?

If you just need to access data then use samba (Windows network sharing):

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

If however, you need access to the desktop then look into VNC:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by Scunnered on 2009-06-09
**nandemonai**

Many thanks for your reply.

I have 2 wishes.  Firstly I want to be able to enter all the data that I require into the programme which is on the XP machine.  Secondly having entered all the data print the results.  Both of these actions I wish to do from Jaunty.

Looking at the Samba link this refers to a server how does this work? If I load Samba does this make Jaunty into a server?

I have a very vague idea of what a server does but no idea of what I need to do to achieve my requirement.  I am having difficulty in getting my head round the instructions.

Hope you can offer more assistance

---

### Post by nandemonai on 2009-06-09
> **Scunnered said:**
> **nandemonai**

Many thanks for your reply.

I have 2 wishes.  Firstly I want to be able to enter all the data that I require into the programme which is on the XP machine.  Secondly having entered all the data print the results.  Both of these actions I wish to do from Jaunty.

Looking at the Samba link this refers to a server how does this work? If I load Samba does this make Jaunty into a server?

I have a very vague idea of what a server does but no idea of what I need to do to achieve my requirement.  I am having difficulty in getting my head round the instructions.

Hope you can offer more assistance

Ah ok, sounds more like you need VNC then. Samba is only for sharing files and printers which wont, by the sounds of things, let you input data into the application on Windows.

You'll need to install a VNC server in Windows then use Applications -> Internet -> Remote Desktop viewer in Ubuntu to connect to the XP machine.

As far as servers go it's a pretty loose term. A server is anything that listens for a connection and serves data of some form to a client. Any machine running any OS can act as a server of some description.

---

### Post by longtom on 2009-06-09
Sorry for chipping in...

Which VNC would you recommend?

---

### Post by superprash2003 on 2009-06-09
server version available at system->pref->remote desktop
client version available at applications->internet->remote desktop viewer

---

### Post by longtom on 2009-06-10
> **superprash2003 said:**
> server version available at system->pref->remote desktop
client version available at applications->internet->remote desktop viewer

Thank you.  However, I was more thinking of a Ubuntu (client) Windows (server) relationship.

But I figured it out with TightVNC - works as it should.

---

### Post by Scunnered on 2009-06-10
Many thanks to you all for your input. 

If I am reading things right you both are saying that I have to work with Windows initially and load a VNC programme.  After that I will be able to work with my custom programme in Jaunty.  Is this correct ?

I am trying to totally remove myself from Windows and wanted to work exclusivly with Ubuntu as my OS.  Is it not possible to access the XP system directly from Jaunty ?

I have had bad experiences with XP failing and lost a load of data for no apparant reason.  I do not want to increase the odds of any further failings with Windows by adding more programmes for XP to interact with and screw up.

Is there any hope of being totally in control from Ubunto or have I to chase the XP laptop round the house just to work with one programme.

Looking forward to your further comments

---

### Post by longtom on 2009-06-10
This is what I did:

I downloaded tightVNC (their website appears to be down, but you'll find it on filehippo or other download centers) for windows and installed it as server on the windows machines I intended to use it.  Make sure you choose a password when asked.

After that (in Hardy) I installed xtightvncviewer via synaptic.  In Applications > Internet I start up "Remote Desktop Viewer".  
Press "Connect", type the Name of the Windows machine and the password you chose and of you go.

Have fun!

Edit:  This is on a LAN network - haven't tried connections over the I-net because I don't need to.

---

