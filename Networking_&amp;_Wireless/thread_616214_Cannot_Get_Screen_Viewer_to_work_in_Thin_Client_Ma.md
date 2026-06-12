---
title: "Cannot Get Screen Viewer to work in Thin Client Manager"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by Dzenhax on 2007-11-18
I've been working with edubuntu all day trying to get the Thin Client Manager to work.  There are a dozen explanations on this spread throughout the web and it seems each one leaves a small but important detail out.

The most useful one was here: [https://wiki.edubuntu.org/InstallX11VncOnLtspClients](https://wiki.edubuntu.org/InstallX11VncOnLtspClients)  *Edit: This was taken down the day after I wrote this.  Do a search on google and see the cached page.*

However it barely mentioned updating the apt sources.list which should have been part of the text boxes.  It's also worth mentioning that in the chroot pico does not work, so have a vi command list ready if you are not familiar with it.

The second thing is that your /etc/resolf.conf file needs to match that of your server.  I just copied and pasted mine.

My problem is this one.  My thin client connects to the server and boots up and works fine.  In the Thin Client Manager I can see the client, send messages to it, blank and unblank the screen, execute commands on it and end processes.  However when I try to view the screen of the client I can't.

Following the above instructions I have installed the x11vnc package in the chroot and updated the client with ltsp-update-sshkeys && ltsp-update-image.

The screen viewer shows the correct user and IP address, but has not connected in bold print.  At the bottom it has "Unavailable" in red and "Install x11vnc on the client", which I already have.

I have tried running x11vnc with sudo from the client and it seems to start up.  I have also tried using the execute button to start it from TCM.  No luck.

One more thing, though not important yet, it will be later.  When I click Share Screen at the top of the GUI an error message pops up on the client saying "Opening password file failed."  I'm pretty sure this is to let students see what's on the server screen but don't know since I can't get it to work.

The product is awesome and I'm trying to introduce it to a school.  I think this is a winning point for the software if I can get it to work.  I'd hate for the school to be down on it because I can't figure it out.

Many thanks to all who offer help.

---

