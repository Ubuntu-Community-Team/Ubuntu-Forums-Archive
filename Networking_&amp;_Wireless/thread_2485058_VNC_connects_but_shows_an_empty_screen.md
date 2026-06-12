---
title: "VNC connects but shows an empty screen"
date: 2023-03-18
forum: Networking &amp; Wireless
---

### Post by Nounours18200 on 2023-03-18
Hello,

I have installed Tightvncserver on Ubuntu 22, installed on a VM on my NAS.

Tightvncserver starts normally as shown by the screen capture: 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291922&stc=1[/IMG]

From my PC I start tightvncviewer and I get the usual connection screen: 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291923&stc=1[/IMG]


but after entered the password, I am connected to the VM but the screen is empty:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291924&stc=1[/IMG]

What can I do to solve this issue ?

Thank you

---

### Post by TheFu on 2023-03-18
That is a default, empty X/Windows root window.  You need to setup the WM [https://en.wikipedia.org/wiki/Window_manager](https://en.wikipedia.org/wiki/Window_manager) to be run in the startup file.  For normal vnc, that is usually the last command at the bottom of the server initialization script.  Since the name of that startup script can be all sorts of things, I don't know the name for it on your system. Sorry.

From the client, you could ssh into the remote system, manually set your DISPLAY environment variable (0:5901), then manually run the WM too.

There are faster, more secure, tools possible than VNC if the client is a Linux workstation and you are on the same LAN, I'd use **ssh -X** to run remote commands.  Over the internet, I'd use x2go, which is based on a more efficient version of VNC called NX.  If the client machine (the one you are sitting at) is Windows or MacOS, I'd use x2go.

---

### Post by Nounours18200 on 2023-03-19
Thank you very much, but I am a newbie in the Linux world, so my knowledge is very, very small ! (close to zero !)

I have to chose the simplest route to get an access to this Linux VM...

Provided that my PC (the client) is under Windows, your recommandation seems to install "**x2go**" on the PC ? I install it and wait for your next reply.

What else should I do ? should I also install x2go server on the Linux VM ? (maybe this would work in a simpler way than Tighvncserver?).

Thank you very much

P.S.: your first sentence is unclear for me, as I don't know anything about Linux...

---

### Post by TheFu on 2023-03-19
If you are really new to Unix-like OSes, then start here:
[https://blog.jdpfu.com/2017/03/31/learning-linux-condensed](https://blog.jdpfu.com/2017/03/31/learning-linux-condensed)

You're gonna need to learn to use google for answers to things you don't know.  If you don't know about x2go, then use google.  You'll find a "start" webpage. [https://wiki.x2go.org/doku.php/download:start](https://wiki.x2go.org/doku.php/download:start) **Read it.**
It will explain that no remote desktop works well with a heavy DE (see that first link above), so the remote system will need one of the lighter DEs.  XFCE, Mate, LXQt are the normal "lite" DEs.  KDE and Gnome won't work. I won't bore you with the reasons.

x2go has a client and a server.  Install the client on the MS-Windows computer. Install the server on the remote Linux computer.  I think Windows doesn't have all the fonts, so when you are installing on the client, also find the x2go font package and install it too.  When you run the client,x2goclient, there is a setup/settings "Session Preferences" page for each remote system you want to connect.  On that tab, near the bottom is a "Session Type" area. That lists most of the different DEs and WMs.  The one selected here has to be installed on the remote system.  If you don't know any better, install XFCE. It is a simple, fast, light, DE that is pretty popular.

But having a full remote desktop is pretty wasteful when all you need to a text interface ... in the 1980s, we used telnet and rlogin and rsh for this. In the 1990s through to today, we use ssh, aka Secure Shell. 

BTW, all x2go traffic between the client and the server goes over an ssh encrypted tunnel.  ssh encryption can be extremely secure, if setup correctly.  You'll need to have ssh setup between the client and server anyway.  On the server, just do this:
```
sudo apt install ssh fail2ban
```
to install ssh and a tool that prevents brute force attacks.  If you haven't run **sudo apt update** today, run that first.

Linux desktops need to be maintained.  Here's what that means: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

VNC really should die.  It isn't secure.  If you still want to use it, clearly say you won't be installing x2go and hopefully, someone else will come by and help you get the DE you want started with VNC.  Actually, the connection **is** already working, the issue is that you either missed the part where the install instructions said to edit a specific line at the bottom of the server startup script or their instructions didn't say it at all.  IDK.  x2go is a more efficient, more secure, faster, solution than VNC.  I really wish all the VNC stuff would die out.  It is an inferior option.

And not to make things more complicated, but Ubuntu tries to default to using Wayland for the display server.  You need to ensure that X/Windows is used.  This is a pre-logon choice.  Google for how.  In another 10 yrs, hopefully, Wayland will be a great option.  X/Windows has been the way Unix-like OSes have GUIs since before I started using Unix 30 yrs ago.  X/Windows is a mess, but it works.

---

