---
title: "remote desktop windows xp from ubuntu"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by orangedangila on 2006-12-30
does someone know how to remote desktop windows xp from ubuntu? i tried to use tightvnc but it doesnt work.. it worked when i want to remote desktop my ubuntu from windows xp... but not the other wayy...](*,)

---

### Post by psycho78 on 2006-12-30
on winXP you have to enable "remote help" or however it is called.. from the linux side you can use tsclient .... i use it regulary to connect to windows2003 servers....  XP Prof. and XP home do not have the "real" terminal services... ... you could also install vnc server on the xp machines and then use vnclient on linux....

---

### Post by psycho78 on 2006-12-30
> on winXP you have to enable "remote help" or however it is called.. from the linux side you can use tsclient .... i use it regulary to connect to windows2003 servers.... XP Prof. and XP home do not have the "real" terminal services... ... you could also install vnc server on the xp machines and then use vnclient on linux....

if you enabled windows firewall and want to use vnc server on the XP machine, open up tcp port 5900 to go through the firewall....
if you want to use the remote help thing you have to enable port 3389

---

### Post by PilotJLR on 2006-12-30
VNC is fine, if you want to install it... otherwise, use the built-in remote desktop.

Basically, right click on My Computer, click Properties. Choose the Remote tab, and click the checkbox for Remote Desktop.
Then go to Windows firewall and add an exemption for Remote Desktop, if it didn't already. If you have a Symantec firewall or something else, make sure to open the port there instead!

Then use the Terminal Server Client in Ubuntu and give it the XP machine's IP address. Choose RDP as the protocol.

---

### Post by Xyem on 2006-12-30
Though not a direct answer to your question, this may answer a future one if you decide to use the RDP protocol with XP. Plus other users may find it useful.

If you use remote desktop you will find XP will only let one user be logged in at a time. This is because of their license agreeement which states only one user can be using the computer at a time.

During one of the service pack builds, they actually enabled it so you can log in as multiple users simultaneously. If you wish to do this, it requires a replacement DLL which took me a while to find. If you are at all interested in it, let me know and I will provide it for you ( along with installation instructions ). Though remember, this would violate your license agreement..

---

### Post by borris.morris on 2006-12-30
what i did is use the "System->Preferences->Remote Desktop & Enabled it. Then I downloaded vnc viewer. [Here]("http://www.realvnc.com/cgi-bin/download.cgi") is an exe for it. Click "Proceed To Downloads" without entering your info. Next scroll down to vnc viewer. You don't need the server, just the viewer. Dowload it and enter your ip or hostname.

---

### Post by orangedangila on 2007-01-04
thanks i got this one works...

---

### Post by SilverWave on 2008-02-02
Got The Fix Here:
[http://www.steveneppler.com/blog/2005/12/07/full-screen-and-tsclient](http://www.steveneppler.com/blog/2005/12/07/full-screen-and-tsclient)

1. Press ctrl-alt-enter, then QUICKLY press ctrl-alt-(arrow left or right). 
>>>Took me a bit of messing around but it finaly got me out :)

2.Check your COMPIZ plugins for - “Workarounds” Check settings of this plugin for:
> Legacy Fullscreen support
If enabled disable it.
Fullscreen in rdesktop then works properly eg “CTRL ALT ENTER” works. 

Class!

Thanks Everyone.

---

