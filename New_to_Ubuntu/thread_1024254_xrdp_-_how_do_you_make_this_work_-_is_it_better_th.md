---
title: "xrdp - how do you make this work - is it better than NoMachine?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by cwmoser on 2008-12-28
How do you get xrdp - X Remote Desktop to work?
Is it better than NoMachines NXServer?

I installed xrdpd and tried to run a Remote Desktop Client to connect but it would not connect.

When I tried to connect, I get this error:

ERROR: channel_register
WARNING:  Initializing sound-support failed!
X Error of failed request:  BadAtom (invalid Atom parameter)
Major opcode of failed request: 23(X_GetSelectionOwner)
Serial number of failed request: 53

Carl

---

### Post by MadMedis on 2009-06-05
I've been able to get xrdp working in Jaunty with limited success, although when it is working it is much better than NoMachine's FreeNX or any other remote login software IMHO.  

Here are a few things to keep in mind:
1) xrdp depends on the tightvncserver package even though apt-get won't pull it down automatically for you, so make sure you install that package on the server (the machine you are trying to connect to) using the command "sudo apt-get install tightvncserver".  I installed tightvncserver first, rebooted, then installed xrdp. 

2) When you finally get Xrdp working you may find that it stops working after you reboot the server.  There is something not-quite-right about Xrdp's startup procedure, so after a reboot you have to restart it manually.  It isn't even that simple, though.  Xrdp isn't always sure whether it is running, so even after you stop it you may have to manually browse to the xrdp.pid file and get rid of it before you restart xrdp.  I used these commands to get it working again:

     sudo sesman --kill
     sudo xrdp --kill
     sudo rm /var/run/xrdp/xrdp.pid
     sudo sesman
     sudo xrdp

After doing that I was able to start a remote desktop session which started X but gave me a command prompt.  I simly issued the command "gnome-session" and I was back up and running.  It's an ugly workaround but it worked for me.  If it works for you and you want to automate it, you might consider putting the commands in a bash script and calling it from rc.local.  HTH!

---

