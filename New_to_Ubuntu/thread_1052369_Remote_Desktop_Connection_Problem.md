---
title: "Remote Desktop Connection Problem?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Synt4xError on 2009-01-27
Hello,

I am trying to setup my Remote Desktop on linux so I can use windows to login. I need a bit of help to do so. I have found very useless threads in some forums.


I see some people have VNC-viewer under there remote desktop connection command you need to use in-order to take control. Mine says vingare. 

I have forwarded the port 3389, I am not able to remote in. Can anyone help me out with this one?

Please!! :) Thank you!

---

### Post by pytheas22 on 2009-01-27
Go to System>Preferences>Remote Desktop and enable desktop sharing with the options that you want (you should definitely set a password if you're going to allow remote users to control the desktop).  Then, while still logged into your Ubuntu computer, go to the Windows machine and, using a client like [tightvnc]("http://www.tightvnc.com/download.html"), launch the viewer (*not* the server) and connect to:
```

your-ubuntu-ip-address:1
```

If both the Windows and Ubuntu computers are on the same local network (e.g. they're both in your house and have IP addresses in the 192.168.X.X range), then you should not need to worry about port forwarding.  If your Windows computer is at a remote location, you will need to tell your router to forward the VNC ports to your Ubuntu computer.  By default, these should be ports 5900-5910, but you can specify a different port under the 'Advanced' tab of the 'Remote Desktop' window that you opened earlier.

I'm not sure where you got port 3389 from; 5900 is the default VNC port.

Note that this only works when you are logged into your Ubuntu computer.  If you log out and then try to connect from Windows, you'll get rejected.  There is a way to configure the VNC server on Ubuntu to allow remote users to log into new desktop sessions, but I don't know how off the top of my head.  I set it up last week and could find the tutorial that I used if you need, though.

You can find more information on VNC [here]("https://help.ubuntu.com/community/VNC").

---

### Post by Synt4xError on 2009-01-27
Remote Desktop Preferences:

Allow other users to view your desktop - Checked
Allow other users to control your desktop - Checked
The command is Vinagre XXX-XXX:0

Security:
Reuire the user to enter this password - Checked

Advanced Tab:
Require Encryption.

I have forwarded the port 5900 (3389 is windows I guess) on my router. The router has no firewall on it.

I have changed my IP to the desktop which I would like to remote in and forwarded the port to that IP.

I only have 1 computer, so I am asking a friend to log in for me using remote desktop on a windows machine. Also, another friend of mine was trying to use TightVNC to log into my desktop. 

both have failed to connect. 

Any ideas?

---

### Post by cariboo on 2009-01-27
Your friends is going to have  to install vncviewer on his windows computer in order for him to connect to your computer remotely. To make sure you have setup the port forwarding correctly go to [canyouseeme]("http://www.canyouseeme.org/") and check to see if port 5900 is open.

Jim

---

### Post by pytheas22 on 2009-01-27
Yes, check out canyouseeme.org to verify that port 5900 is open, and tell your friend to make sure that his client is set to connect on port 5900.

You might also want to disable the 'require encryption' option for now.  I'm not sure how it works, but I would guess that it operates over ssh, which would complicate matters if your friend has a Windows machine.

Also, to check that you can connect to your own desktop, go to Applications>Internet>Remote Desktop Viewer and connect to:
```

localhost:1
```

You should see your own desktop in the viewer; does that work?  If not, try with just 'localhost' or 'localhost:2'.

---

### Post by Synt4xError on 2009-01-27
I guess turning off the Require Exrpytion made it work. I did that first and tried.

Thank you much!

---

### Post by pytheas22 on 2009-01-27
I'm glad that did it.

FYI if you wanted to use it with encryption, you would probably need to install an ssh server on Ubuntu ('sudo apt-get install ssh'), then have your friend use [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") to log into your Ubuntu computer on the command-line before launching vncviewer.  This is just a guess though; I'm not actually sure how the VNC communication would be encrypted, and unless you're paranoid about security, there's probably no reason to worry about this.

---

