---
title: "What's safest for SSH &amp; VNC?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by D1Knight on 2009-11-08
[COLOR=Purple]**So, what is the safest for these 2-SSH & VNC?  :?I currently have them both set up as deny in firewall.  Can I remove them both without messing up dependencies?:-kP**[/COLOR]

---

### Post by Tyke91 on 2009-11-08
1) please don't post in purple. it's quite offputting :)

2) If you're not connecting to anything remotely, you can safely remove ssh and vnc. though i would just turn off the sshd daemon (and whatever vnc uses) instead of uninstalling them. I find ssh is useful to have for copying things over a network (transfering files from one computer to another via scp)

---

### Post by D1Knight on 2009-11-08
> **Tyke91 said:**
> 1) please don't post in purple. it's quite offputting :)

2) If you're not connecting to anything remotely, you can safely remove ssh and vnc. though i would just turn off the sshd daemon (and whatever vnc uses) instead of uninstalling them. I find ssh is useful to have for copying things over a network (transfering files from one computer to another via scp)

Tyke91,

1) OK.....I had no idea a font color would easily offend/offput someone?:confused: It is no big thing to me, consider it changed.;)

2) I openssh-client installed, if I try to remove it, Ubuntu desktop (dependency)will be removed too.? I believe VNC is similar with dependancy.  I am new, so maybe I have mixed up, as far as names go?  The main reason, I was asking if I can remove SSH & VNC was to avoid any Bashing attacks.

Thanks for your responses.:DP.

---

### Post by Tyke91 on 2009-11-08
ubuntu desktop is just a metapackage. installing ubuntu desktop will install all the rest of those packages (vnc included), but removing ubuntu-desktop will not uninstall all of those programs (I don't think... someone should check me on that).


but like I said, you don't really need to uninstall them. you can just disable them. :)

---

### Post by .nedberg on 2009-11-08
> **Tyke91 said:**
> ubuntu desktop is just a metapackage. installing ubuntu desktop will install all the rest of those packages (vnc included), but removing ubuntu-desktop will not uninstall all of those programs (I don't think... someone should check me on that).


correct!

---

### Post by Tyke91 on 2009-11-08
> **.nedberg said:**
> correct!

thanks! :D

---

### Post by D1Knight on 2009-11-08
> **Tyke91 said:**
> ubuntu desktop is just a metapackage. installing ubuntu desktop will install all the rest of those packages (vnc included), but removing ubuntu-desktop will not uninstall all of those programs (I don't think... someone should check me on that).


but like I said, you don't really need to uninstall them. you can just disable them. :)

Tyke91, ok, how do I disable them?  Sorry so noobish.:oops:

Thanks again for your advice/help.:)

---

### Post by The Cog on 2009-11-08
For SSH, don't confuse the client with the server. The client, which is installed by default, allows you to try to connect to other computers. I see no reason to remove or disable the client. 

The SSH server (openssh-server) is the program that listens for incoming connect requests and (if they give the right password) allows other computers to log into yours. You should not install this unless you have good reason and know how to secure it. If you have installed it and don't actually intend to use it then ininstall it again (sudo apt-get remove openssh-server).

As for VNC, again the client program that lets you view remote desktops shoudln't be an issue. The VNC server is also installed by default but disabled. You can enable/disable it from the confgiuration page System->Preferences->Remote Desktop. Checking "Allow others to view your desktop" will enable the VNC server. Only enable this when you really need to, and **never** let it accept connections without getting your approval first. Several people have posted here after doing so and then finding that other people have been messing with their PCs. Mostly it's a bot that tries to use commands that would compromise a windows PC, but sometimes the intruder realises what they have connected to and starts doing things what could harm Linux.

---

### Post by D1Knight on 2009-11-08
> **The Cog said:**
> For SSH, don't confuse the client with the server. The client, which is installed by default, allows you to try to connect to other computers. I see no reason to remove or disable the client. 

The SSH server (openssh-server) is the program that listens for incoming connect requests and (if they give the right password) allows other computers to log into yours. You should not install this unless you have good reason and know how to secure it. If you have installed it and don't actually intend to use it then ininstall it again (sudo apt-get remove openssh-server).

As for VNC, again the client program that lets you view remote desktops shoudln't be an issue. The VNC server is also installed by default but disabled. You can enable/disable it from the confgiuration page System->Preferences->Remote Desktop. Checking "Allow others to view your desktop" will enable the VNC server. Only enable this when you really need to, and **never** let it accept connections without getting your approval first. Several people have posted here after doing so and then finding that other people have been messing with their PCs. Mostly it's a bot that tries to use commands that would compromise a windows PC, but sometimes the intruder realises what they have connected to and starts doing things what could harm Linux.

The Cog, I thank you kindly, you have been most helpful.:) The openssh-server is not installed, thankfully.  The VNC server is installed, I believe it is called Vino. Would it be OK to remove Vino, if I do not plan on using this program (I do not want mess anything else up)? I appreciate you. Have a good week.:)

---

### Post by The Cog on 2009-11-09
> **D1Knight said:**
> The Cog, I thank you kindly, you have been most helpful.:) The openssh-server is not installed, thankfully.  The VNC server is installed, I believe it is called Vino. Would it be OK to remove Vino, if I do not plan on using this program (I do not want mess anything else up)? I appreciate you. Have a good week.:)

You are welcome. 
I think it's probably OK to remove vino, but to be honest I've never tried to do so. I suggest you try to remove it and see what else the package manager wants to remove along with it. If it wants to remove ubuntu-desktop, that's OK because it's just a virtual package like a list of all the packages that should be installed by default - removing ubuntu-desktop won't remove your entire GUI.

---

### Post by D1Knight on 2009-11-11
> **The Cog said:**
> You are welcome. 
I think it's probably OK to remove vino, but to be honest I've never tried to do so. I suggest you try to remove it and see what else the package manager wants to remove along with it. If it wants to remove ubuntu-desktop, that's OK because it's just a virtual package like a list of all the packages that should be installed by default - removing ubuntu-desktop won't remove your entire GUI.

Thanks again!:)  That is a good reminder about the "ubuntu-desktop" virtual package. Time to give it a go. Have a good one.:)

---

### Post by D1Knight on 2009-11-12
> **D1Knight said:**
> Thanks again!:)  That is a good reminder about the "ubuntu-desktop" virtual package. Time to give it a go. Have a good one.:)

OK, this is just an FYI-follow up.:)  I removed the vino package, without any other dependencies, whew.;)  Thanks again to The Cog. Peace

---

