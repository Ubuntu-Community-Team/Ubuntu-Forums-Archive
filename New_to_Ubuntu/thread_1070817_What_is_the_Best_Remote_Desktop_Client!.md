---
title: "What is the Best Remote Desktop Client?!"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by birddog165 on 2009-02-15
I am trying to do remote desktop but I don't want to download every client to find the best one. I already use vinagre but what else is there?

---

### Post by jimreynold2nd on 2009-02-15
For MS's RDP, rdesktop is the best. It's on the command line but it has the most features (including SeamlessRDP)
For VNC, any client is the same to me. Vinagre is good, it has tabs.
But for a nice client with has lots of stuffs, try kde's krdc:tabbed, has both vnc and rdp, and a little control bar on top in fullscreen mode. Or if you don't like kde, try gnome's "terminal server client" (search for it in synaptic), which has both RDP and VNC

---

### Post by psychx on 2009-02-15
I had "Remote Desktop" already installed in System > Preferences. I just recently started using this to access my desktop from work, works wonderful. I use VNC viewer from work to access Remote Desktop at home. I was wondering if I could use VMware, because I have that installed here at work as well.

---

### Post by dro0g on 2009-02-19
I used to use Terminal Server Client, but it started doing this thing where it will occasionally freeze the screen for around 5 minutes (it may be related to compiz.)

Now I use Gnome-RDP. I like that I can save sessions, but it's kind of annoying to keep up to date and there's no way to set defaults so every time I setup a new connection I have to put the same settings in.

rdesktop works OK and I want to try it in seamless mode.

On the VNC side, I use UltraVNC through WINE or with the Java applet because none of the native Linux VNC clients support integrated AD logins.

I've also started heavily using psexec for shell-like access to Windows machines. ChrisControl is another great little util for doing a push install of VNC to machines that don't have it.

---

### Post by hellz99 on 2009-02-19
I use nxserver.  Have for a few years.  I find it's faster than vnc if you need encryption.

---

### Post by binbash on 2009-02-19
I am using rdesktop and vinagre

---

### Post by cb951303 on 2009-02-19
I always hear that VNC has latency problems. A lot of network admins choose nx over vnc. here is a open implementation: [http://freenx.berlios.de/](http://freenx.berlios.de/)

---

