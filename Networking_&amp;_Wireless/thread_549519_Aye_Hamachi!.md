---
title: "Aye Hamachi!"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by Jack Of Spades on 2007-09-12
OK here's the problem.  I have just installed hamachi and ghamachi on two computers running Kubuntu 7.04.  The PC is running a 32-bit version, and the laptop is running a 64-bit version.  I installed 0.8.1 and finally got the GUI to show itself.  Running the previous version would cause the gHamachi interface to show up and promptly disappear.  

So I setup a network for both machines, but there's a problem.  When I try to use VNC->Control this Machine, the pop-up for the network password appears and then promptly disappears with some error message on it.  I almost went insane trying to read it.  I found that it needed me to install a vnc client (duh).  So I installed xtightviewer, and tried VNC->Control this Machine.  Same thing as before, different error message.  After a lot of cursing and threats to inanimate objects, I got a screen shot of the message before it could vanish.  Here's what it said:

```
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
```

I'm a bit lost on what to do next.  Does it have anything to do with the hardware firewall on my router?

---

### Post by dmizer on 2007-09-12
don't know how to help you fix your problem, but for future reference ... most error messages can be found in text format in the /var/log directory.

something like:
```
tail /var/log/system
```
probably would have shown you what you needed.  you can also open the log as a text file, and view the whole thing.

---

### Post by Jack Of Spades on 2007-09-12
ooooooooooooooooooh... ^^; that would have been nice to know...

---

