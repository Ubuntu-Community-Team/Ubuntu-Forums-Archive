---
title: "vnc setup issues"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by Cellwind929 on 2008-08-23
I'm trying to setup vnc so I can manage my server completely headless.

My laptop and desktop are vista and xp so I want to use tightvnc viewer. I have mythtv control center setup on the server and told it to install the vnc service. After it did that I rebooted and tried to vnc in with no luck. I checked the processes running and there appears to be nothing vnc related running.

I looked through the howto's on vnc and found x11vnc to have a lot of guides. I tried that but could not get it set up how I wanted. I was also pretty overwhelmed by x11vnc.

I want to be able to have the vnc program prompt me for a password, then let me into an 800x600 desktop. Right now the server is connected to my monitor at 1680x1050, which is too much for vnc. I don't need it to be my current session or anything because the server just sits at the login screen usually. I just need it secure and the vnc service to start at boot.

Should I be using x11vnc or is there an easier solution like Playskool's my first vnc server?

If anyone can point me at the right document to get me going I'd greatly appreciate it.

---

### Post by HermanAB on 2008-08-23
Hmm, VNC is almost always the wrong solution on a Linux system.

You would have better luck if you install Cygwin on Windows with OpenSSL.  Then you can control your headless server using SSH.  You can run any command line or graphical program over SSH. 

An alternative to Cygwin is to install only a subset of it using Xming and Putty:
[http://element14.wordpress.com/2007/06/29/xming-putty-run-your-home-linux-apps-on-a-remote-windows-machine/](http://element14.wordpress.com/2007/06/29/xming-putty-run-your-home-linux-apps-on-a-remote-windows-machine/)

For example:
ssh -C -c blowfish user@server gnomepanel

after which you can go click crazy in the Gnome GUI.

Or you can run a specific program directly:
ssh -C -c blowfish user@server "gedit /etc/fstab"

Cheers,

Herman

---

### Post by Cellwind929 on 2008-08-23
Thanks, I'll check those out. I'd just go straight SSH only, but since I'm running this as my media server thing, I have album art and easytag setup to tag the mp3's before adding them to my library because I'm anal retentive. I just need to be able to run those two programs since they tag how I like them. This seems like it will do the trick.

---

