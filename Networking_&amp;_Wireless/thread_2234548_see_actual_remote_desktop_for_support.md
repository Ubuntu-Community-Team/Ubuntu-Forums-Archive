---
title: "see actual remote desktop for support"
date: 2014-07-15
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2014-07-15
I have been able to access the remote desktops I want but it goes to a generic desktop. I need to see the actual desktop currently in use to provide remote support. The so called easy remote in Ubuntu doesn't seem to really give a remote desktop as teamviewer does. I volunteer for a library and people call with support questions.I can't legally use teamviewer for the library (I have asked them). Aeroadmin crashes when used through wine and won't connect in win 7 either. I want to remote to their machine when the library calls and says someone needs help on ubuntu #4 for example,  so I remote to it and see what they see to help them through a process like "how do I print this", help with a writer doc, etc. These are beginner computer users and need frequent help.I remote to each  machine and see a desktop as if no one is using it.I have been studying this a lot for weeks and have seen numerous tutorials and have tried so many. Now I have several vnc things installed, vino, xrdp, x11vnc, tightvnc etc. And I have no idea how to do this except with page long tutorials full of scripts I don't understand. I have to set this up on 12 computers and it has to work every time. I am running xubuntu 14.04 64 bit on all the machines through an asus  RT-AC68U router. I can access the system though the terminals windows vnc server program but would prefer a linux vnc server. I am fairly good at a graphical interface but this remote stuff has taken all my time this summer with little success. Thank you

---

### Post by steeldriver on 2014-07-15
There are different kinds of VNC servers - *a desktop sharing* server (Vino, x11vnc) is the type you want, and for Xubuntu it would be more usual to use x11vnc over Vino (for example, the Xubuntu-based mythbuntu uses x11vnc by default)

What kind of account setup do the library machines have? do all users log into a single guest-type (or kiosk-type) account, or do they have individual persistent accounts?

---

### Post by cmcanulty on 2014-07-15
each computer has a librarians account I use for updates, installs, etc. And a user account  for the public. I can access both accounts but don't see their work just an xfce4 desktop with shortcuts correct. I have installed vino and x11vnc and xrdp but don't know how to direct vino to x11vnc. The guest account is darcy and just for the public without admin privileges. I can access either account remotely but need to reach a live seesion they are already on. when i command vino-preferences I don't see an option to tie it to x11vnc. Sorry to be so dumb but I need to know what I need to install on my home machine and what to install on the library machines I support. Thanks

---

### Post by steeldriver on 2014-07-15
What client software are you using on your local machine, and how are you setting up the connection?

You don't "direct vino to x11vnc" - they are two different implementations of the same thing. Both x11vnc and vino-server connect to the 'real' X11 server on the remote machine and then accept incoming connections from VNC client software on your local machine in order to relay the contents of the running session to it

---

### Post by cmcanulty on 2014-07-15
[ATTACH=CONFIG]254745[/ATTACH] picture of the options in the terminals program

for now I am accessing the terminals server through either teamviewer or logmein either of which could cut me off I suppose our router has a free dyns service which I have as darcylibrary.asuscomm.com but I have never been able to connect to it that way. Perhaps something is set wrong. I have x2go, xrdp, vino, x11vnc, sslssh all installed and it is a complete mess as I have tried everything. Once I get to one machine in library I have the terminals vnc server program installed on a windows 7 and can access the win 7 and xubuntu machines either user. The win 7 through vnc and the xubuntu through rdp. But the xubuntu don't go to the active desktop so I can't help people doing things in real time. I maybe am not explaining this correctly. I also have x11vnc and x2go and xrdp and shh client and server on everything.
[URL="https://terminals.codeplex.com/"]https://terminals.codeplex.com/[/URL
Right now I have like 30 tabs open studying how to do this all with different instructions and apps. I have been working on this for weeks and it makes me feel really dumb.
Is it even possible to see what a user is doing and help them remotely in xubuntu? If so it is terribly difficult. Not opening a new desktop but seeing what they are on.

---

