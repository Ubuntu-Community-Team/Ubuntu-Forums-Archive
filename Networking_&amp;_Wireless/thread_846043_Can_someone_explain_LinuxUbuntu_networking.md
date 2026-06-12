---
title: "Can someone explain Linux/Ubuntu networking?"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by kcy29581 on 2008-07-01
Hi all,

I am very confused regarding networking with Ubuntu and Linux in general at the moment. I would appreciate if someone explained it plainly, as I can see many threads asking similar questions and very contradicting replies appear. It is clear that people want similar results from Windows: you change the domain name of the Windows machines, and they can interact/see eachother on the network domain.

*Please do not reply by saying "this does not always work in Windows". I am not here to discuss the success of Windows machines connecting to domains; I want to see Linux machines successfully connecting to domains.*

**To make things absolutely clear, the end result I want is to have multiple machines connecting to the same domain, so they can file share etc. A typical home network & enterprise network scenario.**

As I understand it, there are three ways to connect Linux machines to a network:

[LIST]
[*]SSH
[*]Samba
[*]NFS
[/LIST]
Can someone explain what Ubuntu uses by default in the following scenarios, and what the best implementation would be, as in, which networking protocol should I be using and why.
For clarity, I would appreciate steps for how to get SSH, Samba and NFS to actually work, not just "SSH is used for ...":

[LIST=1]
[*]I only have a network with Linux machines
[*]I have a network where Linux/Windows machines will connect
[*]I have a network where Linux/Windows/OSX machines will connect
[/LIST]
I have two Ubuntu machines at home, and they cannot (by default) see eachother if I go to Places->Network. Due to a bug in the Gnome network configuration utility, after a reboot the domain name is set to blank; the user is forced to reselect the network location they have created on every boot, not a very user-friendly method (as an example, Windows and OS X always remember the default domain set, until the user explicitely changes it). Even when I do this, they still cannot see eachother.

Thanks

---

### Post by superprash2003 on 2008-07-01
SSH is usually used when you are trying to access your pc files from the internet.. in a more secure way.. 
NFS is used as file sharing for linux to linux machines.. so if you have an all linux network then NFS is the way
Samba is used with linux and windows machines

---

### Post by kcy29581 on 2008-07-01
> **superprash2003 said:**
> SSH is usually used when you are trying to access your pc files from the internet.. in a more secure way.. 
NFS is used as file sharing for linux to linux machines.. so if you have an all linux network then NFS is the way
Samba is used with linux and windows machines

Thanks for the reply. That explains when the protocols are used.

By default, should Ubuntu machines find eachother on the network when they are connected to the same router? Or are specific things needed to be done to accomplish this?

---

### Post by superprash2003 on 2008-07-01
find each other as in?? it would be able to ping.. but for file sharing etc it has to be configured

---

### Post by kcy29581 on 2008-07-03
> **superprash2003 said:**
> find each other as in?? it would be able to ping.. but for file sharing etc it has to be configured

Exactly. What is the easiest way to configure two Ubuntu machines to file share, be on the same domain, etc?

---

### Post by daRealScanMan on 2008-07-03
> **kcy29581 said:**
> Exactly. What is the easiest way to configure two Ubuntu machines to file share, be on the same domain, etc?Have you tried searching to find something like this?

NFS HOWTO:
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Or this?

SAMBA HOWTO:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by shad0w_walker on 2008-07-03
If you right click on a folder, you should see an option called 'Sharing Options' this will give you a basic menu to setup sharing of that folder. If memory serves it defaults to Samba, which is an opensource clone/implementation of the windows filesharing system. When you've setup the folder to share, it should be visible from Places > Network > Windows Network.

---

### Post by JC Cheloven on 2008-07-03
> **kcy29581 said:**
> Exactly. What is the easiest way to configure two Ubuntu machines to file share, be on the same domain, etc?

In MHO th easiest way is ssh. 

- First you have to install openssh-server from the repository in the computer(s) that contain files you want to share (the client counterpart of ssh is installed by default in ubuntu)
- I'd recommend to assign static IPs to your computers, so that you avoid mistakes.
- In a client computer, go to places -> connect to server (alternatively file -> connect to server in nautilus), give the server's IP, and that's it. You'll be presented with a window asking username&password in the server. Then you'll have the filesystem of the server into a nautilus folder.

Hope this is the kind of answer you were looking for ;-)
Greetings
____________________
EDIT: of course, choose ssh as "service type" on that window :-)

---

### Post by kcy29581 on 2008-07-03
> **JC Cheloven said:**
> In MHO th easiest way is ssh. 

- First you have to install openssh-server from the repository in the computer(s) that contain files you want to share (the client counterpart of ssh is installed by default in ubuntu)
- I'd recommend to assign static IPs to your computers, so that you avoid mistakes.
- In a client computer, go to places -> connect to server (alternatively file -> connect to server in nautilus), give the server's IP, and that's it. You'll be presented with a window asking username&password in the server. Then you'll have the filesystem of the server into a nautilus folder.

Hope this is the kind of answer you were looking for ;-)
Greetings
____________________
EDIT: of course, choose ssh as "service type" on that window :-)

That's cool, thanks :) Good thing I always assign static IPs to all my devices.

Another question if I may: when I click on Places->Network, what exactly does this do? As in, what type of devices does it show, and what requirements are needed for devices to show up here. The only time I have used it is at work but in a Windows network environment. Not sure how it works for purely Linux machines.

---

### Post by JC Cheloven on 2008-07-03
> **kcy29581 said:**
> That's cool, thanks :) Good thing I always assign static IPs to all my devices.

Another question if I may: when I click on Places->Network, what exactly does this do? As in, what type of devices does it show, and what requirements are needed for devices to show up here. The only time I have used it is at work but in a Windows network environment. Not sure how it works for purely Linux machines.

Places->network is pretty much the same as the "net servers" folder in nautilus. It is preconfigured for samba, I think. In my experience, it takes a while until it "sees" the win machines, but finally it works. Anyway I'm not very adept to networking with windows machines, so if you find something interesting about this, please come back and share your knowledge ;-)

EDIT: so in Madrid? Not so far from me. Greetings, and be prepared for the hot weather!

---

### Post by kcy29581 on 2008-07-11
JC Cheloven, thanks :)

I think one very annoying thing is that setting up a pure Linux network between two Ubuntu machines is not that straightforward. I'm all for getting every OS to network with eachother, but if we cater mainly for Windows networks then we are doing something wrong.

By that I mean, as an example, when you right click on a folder in nautilus and try to set up sharing, it does so by means of Samba. Also, 8.04 has removed an option in the Administration menu where you could install both NFS and Samba protocols graphically, and then choose what protocol you wanted to use for folder sharing. This has kicked NFS into the corner as far as I can see.

Also, the annoying (damn really annoying) bug in Gnome where it does not remember your domain name just adds to the feel of "non-networking".

Obviously, if I am very wrong about something, please correct me. I just want to learn more.

And yeah, Spain is getting hot, although I'm moving to the States soon! :)

---

