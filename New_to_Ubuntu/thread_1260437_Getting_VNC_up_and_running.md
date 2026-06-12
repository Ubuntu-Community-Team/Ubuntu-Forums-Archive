---
title: "Getting VNC up and running"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by bunorama on 2009-09-07
I've been trying to get VNC up for a while now, google'd lots, hope to find some more direct answers.
I think prolly #3 is the best bet, but any help with any of these would be great :)

1. I've installed and reinstalled tightvncserver,, vnc4server, vino, x11vnc, directvnc, and not one of these shows up in the gnome menu... are they all command line only?  (I'd kinda like to know why a xwindows application doesnt install itself into the xwindows / gnome menus heh)

2. I've also downloaded realvnc.  It doesnt 'instal' it just extracts to the bin folder, then you run vncconfig, but mine says 
```
$ vncconfig
vncconfig: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```I have libstc++6 4.3.3-5  installed... should I get a differrent version of libc6?  
Also, I'm running 64bit, and the download for vnc shows **VNC Free Edition for Linux (x86)** so maybe I'm better off with something else.

3. Ubunto came with vino installed.  II found that 'remote desktop' in the system / preferences IS vino-preferences (it doesnt state what it is, I had to make a shortcut on the quick launch and check the properties to find out what in the world remote desktop is).   

Vino-preferences shows some options, but it doesnt have a 'start / stop' the server button, and although it says 'always display icon' in the notification area, it has no icon on my system.... so... how do I tell if it is running?  And on which port?  5900?

---

### Post by NESFreak on 2009-09-07
these don't run from any menus. They're servers. Which sort of means they run in the background. If you had just enabled remote desktop from the preferences --> remote desktop menus, you could access your pc from any other by typing in your ip on one of the other computers VNC viewers.

See VNC is made of two parts. The server and the client.
usually the server runs in the background, while a second program, a client, is used to access that server from another pc(or ipod or whatever).

once vino is configured, it always runs in the background.
thats why its wise to set a password. Also it's possible to show a dialog whenever someone tries to connect, forcing you to physically allow the connection everytime

---

### Post by krunge on 2009-09-07
> **bunorama said:**
> 1. I've installed and reinstalled tightvncserver,, vnc4server, vino, x11vnc, directvnc ...When troubleshooting the problems you are having be sure to completely disable (e.g. uninstall and kill any remaining processes, or reboot) the other VNC servers. I've seen people install a lot of VNC servers trying to get it to work; however things get messed up and the one currently listening on the default port (5900) is not the one they think is running, and similar confusing things.

---

### Post by bunorama on 2009-09-07
I've used vnc and pca quite a bit in windows.

I did set a password.

I'm still not getting an icon in the notification area.  I was hoping that would give access to start / stop and port info.  Since there is no icon, I guess it isnt vino working.  

Using ps -A I found Xvncserver running.  I'm working with vino right now so I better remove that.  Xvncserver does not show in services.  I looked in synaptic, it showed xtightvnc not installed.  So I killed the process.

ps -A | grep vino ... nada. 

Whats going on here?  I just want to run vnc, feels like I'm trying to compile a kernel or something.

---

### Post by bunorama on 2009-09-07
> **krunge said:**
> When troubleshooting the problems you are having be sure to completely disable (e.g. uninstall and kill any remaining processes, or reboot) the other VNC servers. I've seen people install a lot of VNC servers trying to get it to work; however things get messed up and the one currently listening on the default port (5900) is not the one they think is running, and similar confusing things.

From what I can see in the services / synaptic, vino is the only one installed now. 
I'm not sure how to restart it other than to reboot, sooo
Rebooting....

---

### Post by bunorama on 2009-09-07
Still nothing. 
There's no ps -A for vino (ran as root ofc) and none for vnc.
I searched message and syslog for vino, nada.

---

### Post by krunge on 2009-09-07
> **bunorama said:**
> Still nothing. 
There's no ps -A for vino (ran as root ofc) and none for vnc.
I searched message and syslog for vino, nada.
I think vino will only start up when the user (who activated vino via that preferences panel) logs into his desktop.  Did you log into your desktop session before checking with 'ps -A'?

If you want to run a VNC server before anyone logs in to a session let me know. I can show you how to do this with x11vnc.

---

### Post by bunorama on 2009-09-08
I found some drive errors in the system log.  
I'll probably have to replace the drive.  
Maybe better luck on the new install.
Thanks ;)

---

### Post by NESFreak on 2009-09-09
> **bunorama said:**
> I found some drive errors in the system log.  
I'll probably have to replace the drive.  
Maybe better luck on the new install.
Thanks ;)

too bad your harddrive got screwed.
Anyway after the reinstall it should just work with vino. However, as krunge said, vino only works when 1. enabled from preferences 2. the user that enabled it has logged in.

P.S. 1. Vino's server process is called "vino-server". 2. There is no notification icon it just runs.

---

