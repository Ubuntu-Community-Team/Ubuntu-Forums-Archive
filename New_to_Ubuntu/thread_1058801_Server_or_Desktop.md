---
title: "Server or Desktop"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by tomsimmons on 2009-02-03
Hi Folks

I've had a bit of play with the server install of Ubuntu, namely added a GUI (explain why in a sec before I get shot at), got DNS and DHCP working, however I'm wondering if I'm taking the right approach, here's why....

What I'm looking at doing is building a light weight server, that will also be used for a small amount of desktop work (hence the GUI install).  I want this server to act as a post office (Exchange style ie web interface, collection of mail, sending, contacts, etc etc).  I also want DHCP/DNS and Samba.  Other machine on the network are all Windows.

I'm wondeirng if I need the server here, or whether Desktop would be better/sufficient?  It's running on a ITX Intel Atom with 2 GB of memory.  I used Webmin for what I have so far, namely because eBox wasn't working with 8.10.

Any thoughts guidance is appreciated.


Tom

---

### Post by johnjohn2 on 2009-02-03
I adore webmin and i find it the easiest to use!

In my circumstance i have a DAAP server running as a process on my desktop, which i also use for gaming surfing etc!

When i have the money i am going to build another rig dedicated for file serving the clients which i currently have. This will be based on the dektop version and not the server!

Ijust prefer it thats all, too much terminal makes me go BLIND :p

---

### Post by Neural oD on 2009-02-03
it all depends on your skill level! Personally I prefer doing things in the command line - so server would be the way to go for me. But if you are more comfortable in a gui environment - I don't see the problem!

---

### Post by tomsimmons on 2009-02-03
For now I'm happier with GUI, maybe later I'll get to doing everything on the command line.

Webmin seems OK so far, though I've yet to find a guide for the current version, everything I've come across seems to be for older versions?  I would like to try eBox, not least because from what I read it seems to have a guided set up for the Post office side of things too.  However I was unable to decide whether eBox modifies the correct config files, or creates alternate ones?  Has anyone heard if there is a fix due/done for the eBox issue?

From what the replied so far, it seems that I would lose nothing from using the desktop install?

I understand that Kbuntu is KDE rather than Gnome, however I thought I read somewhere that KDE has more GUI config tools, is this tools for configuring the GUI, or for setting the machine up?  The reason I ask is a long time ago I played with Mandrake, which I think was KDE, and that has GUI tools for Samba etc.


Tom

---

### Post by Neural oD on 2009-02-03
you should be able to find gui tools for most things that you do, whether you use kde or gnome

and yes - you should run into no problems running a "server" off a desktop install - in fact I have one still going after a couple of years - and no problems

---

### Post by handydan918 on 2009-02-03
KDE is generally acknowledged to be more feature-rich, including system config tools. That said, I find KDE integration in Kubu to be lacking as compared to some other KDE distros, and I still prefer the KDE 3.X environment over 4.x
And there is no compelling reason NOT to use a gui on a server. The amount of space the DE takes up is not significant at the current price of disk space, and if you are concerned about resources, just use runlevel 3 except for when you need the gui...

---

### Post by tomsimmons on 2009-02-03
> **Neural oD said:**
> you should be able to find gui tools for most things that you do, whether you use kde or gnome

This is some of the best news I've heard.  Sorry to push the point, but could you give some pointers as to where I'd find them?  A How To or guide would be more than sufficient.

Sounds like I'll swap to another spare drive and try again on Ubuntu desktop tonight.


Tom

---

### Post by albinootje on 2009-02-03
> **tomsimmons said:**
> However I was unable to decide whether eBox modifies the correct config files, or creates alternate ones?  Has anyone heard if there is a fix due/done for the eBox issue?

I recommend to refrain from using eBox unless you want to let eBox do everything.
Try eBox on another machine or in a Virtual Machine first to get an impression.
> 
The reason I ask is a long time ago I played with Mandrake, which I think was KDE, and that has GUI tools for Samba etc.


There's system-config-samba and swat to try if you find webmin too difficult.

---

### Post by binbash on 2009-02-03
If you are going to use a GUI, then choose desktop.You can do what you need easily with desktop.

@handydan918

It is not about space.I never saw a system admin who uses any kind of GUI, especially crap KDE tools.And it is not about resources.On heavy production servers, every software is a BIG security risk to gain local access.That is why ;)

---

### Post by Neural oD on 2009-02-03
handydan918 - I thought that in ubuntu the runlevels 2-5 were the same thing basically - well I know in the past they were - have things changed?

---

### Post by tomsimmons on 2009-02-03
Space is not an issue, nor is performance really.  In the long term I was thinking of setting it up not to auto start the GUI.

Sounds like eBox is warned against, no problem.

System-Config-Samba and SWAT, these are for Samba config only?  Are there similar app tools for the rest of config?

Sounds like there is more in the way of tools in KDE, but a bigger following here for Gnome?

I would just like to say thanks to all you folk for quick replies, and no flaming/insults which has been my experience on most forums when it comes to Linux.


Tom

---

### Post by Neural oD on 2009-02-03
> **tomsimmons said:**
> This is some of the best news I've heard.  Sorry to push the point, but could you give some pointers as to where I'd find them?  A How To or guide would be more than sufficient.

Sounds like I'll swap to another spare drive and try again on Ubuntu desktop tonight.


Tom

one of the best ways is to google - also you can search the repositories - either the graphic tool(synaptic package manager) - or command line - something like this: apt-cache search xxx

---

### Post by albinootje on 2009-02-03
> **tomsimmons said:**
> Space is not an issue, nor is performance really.  In the long term I was thinking of setting it up not to auto start the GUI.

Securing your server eventually also means installing only the needed software, and do reading/research about computer security.
> 
System-Config-Samba and SWAT, these are for Samba config only?  

Yes.
> 
Are there similar app tools for the rest of config?

Try webmin, and just play with it, without trying to read the whole manual first ;-)
See also here to get a bit more understanding of what is Samba about :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
> 
Sounds like there is more in the way of tools in KDE, but a bigger following here for Gnome?


I've seen a groupware-wizard tool in KDE (which might be just focusing on the desktop part of that), but for the rest I don't think that KDE has more server related GUI tools by default.

---

### Post by albinootje on 2009-02-03
> **Neural oD said:**
> one of the best ways is to google - also you can search the repositories - either the graphic tool(synaptic package manager) - or command line - something like this: apt-cache search xxx

In my opinion for searching for GUI apps for managing your server, the last thing to use is to use a search engine to find a GUI.
It's imho better to first ask on a forum like this which software people recommend before losing yourself in a labyrinth of software choices.

My MS-Windows sysadmin at work, who uses Linux and who really wants to become a Linux sysadmin in the end, got lost in a Samba configuration several months ago.
He started installing all kind of Samba config GUIs and trying them, besides the manual configuration and several different howtos, ran into trouble, then asked me to help him, I've then removed all of the GUIs and tried to explain to him that it's better to stick to one howto or to one GUI. In the end we finally got a working solution after cleaning up the various "mess" of all the different GUIs.

---

### Post by handydan918 on 2009-02-03
> **binbash said:**
> If you are going to use a GUI, then choose desktop.You can do what you need easily with desktop.

@handydan918

It is not about space.I never saw a system admin who uses any kind of GUI, especially crap KDE tools.And it is not about resources.On heavy production servers, every software is a BIG security risk to gain local access.That is why ;)
Phooey. "Every software" is not a risk. Every service may be, if incompetently configured. And we are not talking about enterprise level production servers and professional sysadmins. We're talking about old pentiums stuck in a closet for file servers under somebody's stairwell. 
Context, people.

---

### Post by albinootje on 2009-02-03
> **handydan918 said:**
> Phooey. "Every software" is not a risk. Every service may be, if incompetently configured. And we are not talking about enterprise level production servers and professional sysadmins. We're talking about old pentiums stuck in a closet for file servers under somebody's stairwell. 
Context, people.

I think it's always very good to inform people properly.

I wouldn't want Linux to get a majority of server *and* desktop market share, while most of the users are still completely clueless or misinformed. :)

---

### Post by tomsimmons on 2009-02-03
> **albinootje said:**
> In my opinion for searching for GUI apps for managing your server, the last thing to use is to use a search engine to find a GUI.
It's imho better to first ask on a forum like this which software people recommend before losing yourself in a labyrinth of software choices.

It was through Google that I came by eBox and Webmin, and heard of one or two others.  And exactly as you say you can spend an age trying these.  I, mayeb navely, was hoping for some system supplied apps rather than webmin or similar.

However if the general opinion is that Webmin is best, then that's what I'll stick with, though if anyone has details of an update to guide rather than older ones that would be good.


Tom

---

### Post by albinootje on 2009-02-03
> **tomsimmons said:**
>  However if the general opinion is that Webmin is best, then that's what I'll stick with, though if anyone has details of an update to guide rather than older ones that would be good.


Webmin is good if you want all config/management modules in one interface.
One more advantage of webmin is that you don't need a desktop install to be able to use webmin, you can use webmin on a minimal server installation.

What I don't like about webmin is that it's not in the repositories, and the webmin deb repositories seem to be very outdated.

I think it's also a personal thing, I prefer to learn the basics so that I also know where to find the configuration files when I'm in a text console without any GUI tools. YMMV.. Good luck!

---

