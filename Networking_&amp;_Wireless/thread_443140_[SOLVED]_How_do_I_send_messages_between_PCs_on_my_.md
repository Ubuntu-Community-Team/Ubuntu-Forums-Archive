---
title: "[SOLVED] How do I send messages between PCs on my home network?"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by ridgeland on 2007-05-14
I've never used GAIM or Instant Messaging or Chat Rooms.  So very newbee.
What I want is just a way to send a message from one PC in the house to another PC on a different floor.  Like Web IM maybe but local router only, no Web.
I guess I could use GAIM or Kopete and set up an account with a web-based system, but that seems such a waste to send a note to a URL to have it echoed back to the house.  Is there a simple tool to send a message straight from 192.168.123.111 to 192.168.123.112 both on the same router.  Does a GAIM option do this?  I have yet to find good support documentation/wiki for GAIM.
Wall seems to be if the users are logged into the same computer which is not the case.
Thanks,
Ridgeland

---

### Post by misconfiguration on 2007-05-14
Use ytalk, you can communicate via shell from PC to PC.

[http://www.impul.se/ytalk/](http://www.impul.se/ytalk/)

---

### Post by ridgeland on 2007-05-14
Thanks misconfiguration.
I got ytalk to work on two PCs.  I used synaptics to load ytalk on each PC.  Took me awhile to figure out how to get it to work.
Nothing worked without the full LAN addresses.  192.168.123.xxx is local only.  These numbers are probably unique to our PCs
On both PCs we open a terminal window.
On PC 2 enter:
$ ytalk -h 192.168.123.111 pc1@192.168.123.100
the ytalk window opens and PC 1 gets a text prompt in the terminal window saying to enter
talk pc2@192.168.123.111
this doesn't work.  It needs to be:
talk -h 192.168.123.100 pc2@192.168.123.111
Enter that and PC2 has a split ytalk screen - all set.
But PC 1 has a prompt about rering? say 'n' 
Now PC1 also has a split ytalk screen and communications work.
When either one hits [Ctrl]+C both ytalk windows close.

Now some improvements for pc2:
$ gedit /home/pc2/.ytalkrc  (it doesn't exist yet)
   localhost 192.168.123.111
   alias pc1 pc1@192.168.123.100

Now to talk is just $ ytalk pc1

It does what I requested. :) 

Anything better out there?  A way to just send a pop-up window and a beep tune.
Maybe what I need is Apache to make my PC a server then use GAIM with my PC being the host for the messages.  Anyone go that route already?  I'll search the forums some more.

---

### Post by misconfiguration on 2007-05-15
Great news I'm glad you got it working, I don't know anything off of the top of my head for exactly what you're looking for. I've just used ytalk for the same reasons for a few years now.

---

### Post by 655 on 2008-06-10
Hi ridgeland,

I came across this post while trying to troubleshoot my own unworking ytalk configuration.

In Ubuntu 8.04, the program does not seem to configure itself correctly upon install.   Whenever we try to connect to each other, it says that the talk daemon is not running.

I realize that this post is old, but are you still able to use ytalk successfully?
I'd be interested to know about your configs in detail.

Thanks for any help you could provide.

---

### Post by ridgeland on 2008-06-12
Hi 655,
We don't use ytalk.
We have:
NFS for common folders (Images, Music,...)
ssh for remote terminal 
vncviewer to take over the other PC's screen
places->connect to ssh server to use Nautilus to see the full file structure of both PCs.
With vncviewer I could connect to her PC, she would see a pop-up window saying someone wants to take over.  Once she clicks OK then we both control her screen.  I could open a gedit screen and we could both type in it like a chat room.
But we just get up and go talk to the other one or use the telephone's intercom feature.
I stayed with Ubuntu 7.04.  I didn't like 7.10.  I will switch to 8.04 once all my other distros are using Firefox 3.  Now I use Mandriva 2008.1 most all the time.

---

### Post by 655 on 2008-06-16
Thanks for your reply.

All of those are good alternatives.  Nevertheless, I'll keep hacking at the ytalk angle.

---

### Post by ridgeland on 2008-06-16
I like having lots of options and the freedom to choose.  Post back again when you get ytalk like you want it.  Others may come later asking how-do-I...

---

