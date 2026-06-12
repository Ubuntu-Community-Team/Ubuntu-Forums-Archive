---
title: "Running Desktop and Server on Same Box"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by jfluckey on 2010-05-27
I have a (2) part question concerning the running a desktop (Lucid) and server at the same time.  I have read that the easiest way to do this is install the server and then apt-get the gnome-desktop, etc.  I also read that the server kernel and desktop kernel differ in how they handle the memory (I will probably install the 64 bit version if that matters).  So:

1.)  I want to install the desktop first and configure the server.  I tried this but was unsuccessful, such that I must of changed a config file along the way that rendered my internet useless, and I will do a reinstall.  How do I (with detailed instructions because I am a noob please) add a webserver, file server, and SSH to the desktop version?  

2.)  I currently have a FreeBSD server which stays on all the time, but I was thinking of running everything on one machine.   After I get my server and desktop up and running, I would like to toggle the gui on and off, so once I am done working on the desktop I can turn off anything that needlessly uses resources.  Is it just gnome that I would have to toggle and how would I go about doing that?

Thank you to whoever takes the time to respond.
-jfluckey

---

### Post by Gone fishing on 2010-05-27
I would have thought it was best to keep them apart, I wouldn't want people doing Desktop stuff on my server, but you haven't said what the server does.

You could just install the desktop Ubuntu and add the server packages. This might be easier with Opensuse.

You could run your freeBSD sever and run Ubuntu in a VM

---

### Post by halitech on 2010-05-27
this should help with the webserver: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

file sharing: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

ssh: [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by jfluckey on 2010-05-27
@ Gone Fishing - Sorry, the purpose of the server is primarily for personal use.  Only I will file share or ssh when at work or via my phone. Some times I need to have a torrent or nzb download while I am work so it is done when I get home.  The webserver is for a website that should get very little traffic (I want to put all of my wife's recipes on a site so when people go "OOOH, can I get the recipe?" I can just give them the website so they can print it off.)  The desktop is for audio and video playing.  Having the (2) in (1) will also save me from having to run wires to hide my server as it is currently out in the open in my basement.

@ halitech - Thank you for those links, I will look through them now!

---

