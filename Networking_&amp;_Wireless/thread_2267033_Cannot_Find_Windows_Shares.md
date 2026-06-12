---
title: "Cannot Find Windows Shares"
date: 2015-02-26
forum: Networking &amp; Wireless
---

### Post by HonestRepair8 on 2015-02-26
I'm running a web server on a Ubuntu Virtualbox and I'm having trouble accessing my Windows Workgroup. It seemed to work fine (Albeit a bit slower than it should be) for as long as I can remember. Just the other day it completely stopped trying to connect to one machine in particular on my Workgroup. When you select this one machine it will say "Loading" but will never load or time out or anything. It will just sit there with an empty window. Just tonight I've lost access to the rest of the Workgroup. My Virtualmachine is alone, which renders it completely useless to me. 

It is extremely frustrating. The machine is accessible on every other platform I can possibly try, except for Ubuntu. I've looked into it and all I can find is that they seemed to create some issues after 11.04 with Samba. Not sure if that could be related, but I'm running 14.10 at the moment. 

I need to figure this out. I'm not interested in doing this mediocre work with the Terminal. If there's anything I can do to fix this please let me know! I'm at the end of my rope and I'm not interested in trying any more convoluted work-arounds to move my files from two simple network locations. If there is no solution I need to know so I can find a distro that can accomplish this goal. This is pretty standard stuff we're talking about, here. Call me simple for not wanting to use the Terminal for this, but I'm seriously tired of working in terminal. There's a perfectly good GUI that I should be able to drag and drop my files with.

---

### Post by TheFu on 2015-02-26
Is virtualbox NAT or bridged or host-only networking?
Also - what is the hostOS and what is the clientOS - it isn't clear to me.

---

### Post by HonestRepair8 on 2015-02-26
Sorry, Host is Windows 7 and client is Ubunty 14.10. The host is using a gigabit Intel Ethernet adapter and the client is bridged.
*Edit: Still doesn't appear to be working. *
I actually figured out a possible solution but it had nothing to do with Ubuntu. I had to turn on promiscuous mode and drag and drop on Oracle Virtualbox. This won't help anyone who's using Ubuntu as a standalone OS but it worked for me. I worked for hours reinstalling all sorts of packages and messing with permissions to no avail. 

Should I mark it solved anyway?

---

### Post by deadflowr on 2015-02-26
> Should I mark it solved anyway?

Sure, if you feel the solution you found is best or satisfying. 
Workarounds and re-installs are solutions, too. Even if totally unintentional...

---

### Post by HonestRepair8 on 2015-02-26
Unfortunately it appears I can drag and drop folders but not files. Not having much luck yet. 

I was hoping to eventually be able to run Unison between the virtual client and the rest of the network through Gnome Schedule from a command line. Manually dragging/dropping isn't really a long-term solution. For now I'll take anything to get data between computers. External 3rd parties are out of the question. 

The virtual client has no problems connecting to the internet. Samba and Ubuntu both don't see a Workgroup. The Ubuntu GUI will allow me to set the parameters for a Local Network Share, but I get an error when I try to create the share...

> 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/ usershares. Error Permission denied. You do not have permission to create a usershare. Ask your administrator to grant you permission to create a share.

The current owner of my /var/lib/samba is root, and I'm nervous about using "sudo chown" because the last time I played with that I somehow removed myself from root users (long story).

---

