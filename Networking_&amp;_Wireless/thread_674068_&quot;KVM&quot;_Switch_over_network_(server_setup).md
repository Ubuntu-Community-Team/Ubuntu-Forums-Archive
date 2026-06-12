---
title: "&quot;KVM&quot; Switch over network? (server setup?)"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by xptweakerntn on 2008-01-21
I have two computers, both running Ubuntu, and I was wondering if I could use both of them with one monitor over the network. Essentially what I am going to do is use one as a "server backup", and my newer computer to actually use. As I only  have one monitor/keyboard and mouse, I wanna use them on both. I've heard of [http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/) , but that is quite the opposite, isn't it? Will it allow me to only use one monitor as well? Also, how about this: Theoretically, couldn't I setup my older computer to autologin on boot, then set it to share one of the drives? I could then leave it on all the time as well. I'm wanting to essentially setup a media server, as well as to be used as a backup server. If anyone has any ideas that I haven't thought of, be sure to share them.

---

### Post by BrentC on 2008-01-21
> **xptweakerntn said:**
> I have two computers, both running Ubuntu, and I was wondering if I could use both of them with one monitor over the network. Essentially what I am going to do is use one as a "server backup", and my newer computer to actually use. As I only  have one monitor/keyboard and mouse, I wanna use them on both. I've heard of [http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/) , but that is quite the opposite, isn't it? Will it allow me to only use one monitor as well? Also, how about this: Theoretically, couldn't I setup my older computer to autologin on boot, then set it to share one of the drives? I could then leave it on all the time as well. I'm wanting to essentially setup a media server, as well as to be used as a backup server. If anyone has any ideas that I haven't thought of, be sure to share them.

I'm not sure I quite understand. Are you trying to figure out a way to use 1 keyboard/mouse with or without a KVM switch? With a KVM switch, it should be straight forward for what you want to accomplish, so I don't understand your problem.

---

### Post by xptweakerntn on 2008-01-21
I am wondering if I can use the network "as a KVM switch". I don't have a kvm switch, all I want to possibly do is use my keyboard/mouse/moniter for two computers OVER THE NETWORK, if possible, to control two computers. What I wish I could do is explained here:
[http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/)
"Support N computers on M monitors"
However, unless you can do this with some other software, I don't think I can do this. Another option would be "remote login" possibly, however I don't have any experience with that, so perhaps some questions:
I am planning on having the computer "server" downstairs, and my actual usable one upstairs. Downstairs it will have no moniter, so will this make remote login hard to do/impossible? I can hook up the older computer to a monitor to setup, but eventually it will have no keyboard/mouse or a moniter. It will only be hooked up to the network. From there, I would like to be able to not only share files between the two, but also "remote login", or synergy, or kvm over network, or whatever works best or whatever you want to call it, so that I can update the computer downstairs while I am upstairs. Performance isn't something I need to worry  about, meaning I don't care if I have to wait a few seconds for something to "respond". Essentially I want the downstairs computer to act as a server, but be able to be controlled from upstairs. Perhaps there is something that works better, so be free to explain.

---

### Post by BrentC on 2008-01-21
> **xptweakerntn said:**
> I am wondering if I can use the network "as a KVM switch". I don't have a kvm switch, all I want to possibly do is use my keyboard/mouse/moniter for two computers OVER THE NETWORK, if possible, to control two computers. What I wish I could do is explained here:
[http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/)
"Support N computers on M monitors"
However, unless you can do this with some other software, I don't think I can do this. Another option would be "remote login" possibly, however I don't have any experience with that, so perhaps some questions:
I am planning on having the computer "server" downstairs, and my actual usable one upstairs. Downstairs it will have no moniter, so will this make remote login hard to do/impossible? I can hook up the older computer to a monitor to setup, but eventually it will have no keyboard/mouse or a moniter. It will only be hooked up to the network. From there, I would like to be able to not only share files between the two, but also "remote login", or synergy, or kvm over network, or whatever works best or whatever you want to call it, so that I can update the computer downstairs while I am upstairs. Performance isn't something I need to worry  about, meaning I don't care if I have to wait a few seconds for something to "respond". Essentially I want the downstairs computer to act as a server, but be able to be controlled from upstairs. Perhaps there is something that works better, so be free to explain.

Are you trying to make the downstairs computer a file sharing server or ? If so, just configure the server upstairs with your monitor/keyboard/mouse up there. 

Assuming the server is going to be running Linux, so, just configure it with FTP, SSH, SAMBA(if you plan on having any Windows computers networked to it), remote access, etc. Then all you have to do once it's downstairs is turn it on and run back upstairs and use SSH to run all of your terminal commands, FTP or SAMBA to transfer files between computers(Although if you're using only Linux boxes on the network, SAMBA and/or FTP isn't required, but can help reduce time later on if expand your network and pre-install/set them up),

This is of course assuming you understand how to use SSH. If not, it is a very, VERY useful tool which I recommend learning how to use, regardless of whether you do anything I suggested. :)

EDIT: You'll be running almost everything from an ssh terminal on your upstairs client to send commands to the server. You can still use Nautilus between the 2 computers for file sharing assuming they are on the same network if you don't feel comfortable in a terminal. Just make sure permissions are set with the right users.

---

### Post by xptweakerntn on 2008-01-22
I actually spent most of last night doing this:
Setting the computer to auto login, then lock.
Setting up nfs, some sorta file server thing. 
Now every time it boots, it logins and now from the "client" i can view the drives i need and access them accordingly. However, I would like to setup ssh, is there a short guide I can have to setting it up? Learning it will be no problem, but do I really need it? All I really want is to be able to use the storage on the thing, just as I'm doing now.

---

### Post by BrentC on 2008-01-22
> **xptweakerntn said:**
> I actually spent most of last night doing this:
Setting the computer to auto login, then lock.
Setting up nfs, some sorta file server thing. 
Now every time it boots, it logins and now from the "client" i can view the drives i need and access them accordingly. However, I would like to setup ssh, is there a short guide I can have to setting it up? Learning it will be no problem, but do I really need it? All I really want is to be able to use the storage on the thing, just as I'm doing now.

The reason I suggested SSH is in case you ever wanted to modify, install, repair, etc anything on the server without having to bring the server case back upstairs and hook it upto your monitor and what have you. You can run all those terminal commands from an SSH client on the client upstairs. 

As for an SSH guide, I can't find the one I read here on the forums awhile back, but there are a lot of them out there. Could just google "ubuntu ssh guide(or tutorial)" and browse through the results. SSH isn't necessarily *mandatory*, but trust me, if there ever comes a time when you need to do something on the server(and there will), it's a lot easier to just run a command terminal upstairs rather than physically moving something(ie; monitor or the server box itself).

---

