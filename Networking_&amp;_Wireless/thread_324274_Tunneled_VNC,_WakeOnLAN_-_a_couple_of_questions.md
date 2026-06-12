---
title: "Tunneled VNC, WakeOnLAN - a couple of questions"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by Crakie on 2006-12-23
I have a working SSH connection setup, which I now want to use as a VNC tunnel from Windows machines. But I have some special needs:
1) I want to walk around with a USB stick that contains everything I need *without* having to install anything on a computer I come across and wish to use as a client. These computers are generally Windows, of course... such is life :)
2) In addition, I also want my computer to be off, only to powerup when I need it. I think it got this done, but I haven't been able to test it yet. 

Reading up on several wikis, fora (including this one) and what not, I think I got the VNC tunnel down. Especially [this]("http://johnny.chadda.se/2006/10/24/access-your-linux-computer-graphically-and-securely-using-ssh-and-vnc/") link proved very useful. Thanks, Johnny!

So this got me the following software:
1) SSH server, authenticated by keyfiles + password - check (installed on my Kubuntu system)
2) Putty with private key - check (put on USB stick; works with SSH server, can be used to tunnel)
3) WoL from Depicus - check (put on USB stick, hope it'll work)

What I still need is:
a) a VNC client for Windows. I think I got a standalone application, UltraVNC Viewer. I could use some advice here though.
b) a VNC server. Here's where I get in trouble. Suppose I manage to wake up my computer remotely and it boots (by default) to Kubuntu. The bootprocedure ends at the login screen of course. I am told that at this point the SSH server will be operational, which I will get to test soon. However, will the VNC server also be operational? My choice of VNC server may depend on that!
My concern is that, at the login stage, there is no 'desktop environment' yet. Can I remotely start it and then see it through the VNC tunnel? Do I need to start X manually?

Any help is appreciated!

---

### Post by Crakie on 2006-12-23
Com'on guys, I know you want to... :p

---

### Post by dbott67 on 2006-12-23
> **Crakie said:**
> I have a working SSH connection setup, which I now want to use as a VNC tunnel from Windows machines. But I have some special needs:
1) I want to walk around with a USB stick that contains everything I need *without* having to install anything on a computer I come across and wish to use as a client. These computers are generally Windows, of course... such is life :)
2) In addition, I also want my computer to be off, only to powerup when I need it. I think it got this done, but I haven't been able to test it yet. 

Reading up on several wikis, fora (including this one) and what not, I think I got the VNC tunnel down. Especially [this]("http://johnny.chadda.se/2006/10/24/access-your-linux-computer-graphically-and-securely-using-ssh-and-vnc/") link proved very useful. Thanks, Johnny!

So this got me the following software:
1) SSH server, authenticated by keyfiles + password - check (installed on my Kubuntu system)
2) Putty with private key - check (put on USB stick; works with SSH server, can be used to tunnel)
3) WoL from Depicus - check (put on USB stick, hope it'll work)

What I still need is:
a) a VNC client for Windows. I think I got a standalone application, UltraVNC Viewer. I could use some advice here though.
b) a VNC server. Here's where I get in trouble. Suppose I manage to wake up my computer remotely and it boots (by default) to Kubuntu. The bootprocedure ends at the login screen of course. I am told that at this point the SSH server will be operational, which I will get to test soon. However, will the VNC server also be operational? My choice of VNC server may depend on that!
My concern is that, at the login stage, there is no 'desktop environment' yet. Can I remotely start it and then see it through the VNC tunnel? Do I need to start X manually?

Any help is appreciated!

I use WoL at work, plus UltraVNC, UVNC-Single-click, SSH, PuTTY.

WoL should be able to do the trick, although you need to make sure that the ports are forwarded through any routers.  I've tried a few different WoL utils and had various levels of success from the outside.

VNC viewer is a standalone app, so you should be able to run it from your USB (if your USB thumb drive support [U3]("http://www.u3.com/") then even better).

VNC server does not normally start before your are logged in.  If you want to be able to connect via VNC before you are logged in you need to do the following:

I've borrowed all of the details from [emperor's]("http://www.ubuntuforums.org/member.php?u=115") [HOWTO]("http://www.ubuntuforums.org/showthread.php?p=1627716") and summarized them below:

1. Install vnc4server:
```
sudo apt-get install vnc4server
```

2. Edit **/etc/X11/xorg.conf** file (for secure access with password):
```
sudo gedit /etc/X11/xorg.conf
```

3. Add the [COLOR="Red"]Load "vnc"[/COLOR] line to the **Module Section**:
```
Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	**[COLOR="Red"]Load "vnc"[/COLOR]**
EndSection
```

4. Add the [COLOR="Red"]Option[/COLOR] lines to the end of the **Screen Section**:

```
Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
	[B][COLOR="Red"]Option "SecurityTypes" "VncAuth"
	Option "UserPasswdVerifier" "VncAuth"
	Option "PasswordFile" "/root/.vnc/passwd"[/COLOR][/B]
EndSection
```

4. Set the vnc password as root user:
```
sudo su
vncpasswd
Password:
Verify:
```

5. Restart X Windows (**CTRL-ALT-BACKSPACE**)

-Dave

---

### Post by dbott67 on 2006-12-23
Another thing I've found about PuTTY (Linux version).  

I tried using PuTTY between my laptop (running Dapper) and desktop PC (also running Dapper and both behind the router) and it didn't work.  I tried using PuTTY from my Windows XP PC at work and it works (going through my D-Link router).

Then I found this post:
[http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/)
On page 2, they suggest using openssh & this command on the remote machine:
```
ssh xx.xxx.xx.xx -L 5900:localhost:5900
```
So, on my laptop (192.168.1.105) I tried to connect to my desktop (192.168.1.106) using this command to establish the SSH tunnel:
```
ssh 192.168.1.106 -L 5900:localhost:5900
```
Followed by this command to connect to the VNC server:
```
vncviewer localhost:0
```
Hey! It works!!! These also work:
```
vncviewer localhost
vncviewer 127.0.0.1
```
But here's the strange part:

My laptop multi-boots between XP, Dapper, 2003 & MCE.  On Dapper, PuTTY doesn't work but openssh does when creating the VNC tunnel.  I am able to login to my desktop using PuTTY and then when I try to run **vncviewer localhost:X** I get this message:
```
dbott@dapper:~$ vncviewer localhost:0
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

```
I've tried every screen number (0-7), I've changed ports 5900, 5901, etc. but it doesn't work.  When I use openssh (**ssh 192.168.1.106 -L 5900:localhost:5900**) it works.

However, if I boot into Windows PuTTY works as it should using the exact same configuration!  

So, if you're trying from Linux-to-Linux, PuTTY may not work (I couldn't get it working), but it does work just using the command line.

If you have success with PuTTY (in Linux), please post how you did it.

**Screenshot 1:** WinXP connecting to Dapper 6.06 using PuTTY & VNC running over secure tunnel connected to Dapper 6.06.
**Screenshot 2:** Dapper 6.06 connecting to Dapper 6.06 using openssh & VNC running over secure tunnel connected to Dapper 6.06.


-Dave

---

### Post by Crakie on 2006-12-23
> **dbott67 said:**
> If you have success with PuTTY (in Linux), please post how you did it

Thanks alot for your help Dave! I'm sorry I probably won't be able to return the favour - your problem is weird indeed. It sounds like there might be a difference in the way Ubuntu and Windows handle network protocols. But then again, you seem to know more about this than I do. Perhaps you should post about it, if you didn't already? Apparently, there is a pretty helpful community on IRC as well.

---

### Post by dbott67 on 2007-01-17
[QUOTE=qujo86]Hi there.

U and your girlfriend/wife look happy together btw :-)
It seems i dont have any close friends that has the knowledge that people on this forum has. I could really need some help with remote desktop from my Ubuntu to my winxp that im supposed to access trough ssh from a 3:d winxp at work.
Been doing some reading on the forums and u seem to know a great deal about this. Would u be kind enough to hint me in the right direction, cause i cant get vnc to work between linux and windows.
The ssh is set so that was the easy part i guess.
Should u be "not interested" just ignore me ;)
Kind regards
Paul Zander (Sweden)[/QUOTE]

Hi Paul,

This thread should get you started for VNC and SSH:
[http://www.ubuntuforums.org/showthread.php?p=1923992#post1923992](http://www.ubuntuforums.org/showthread.php?p=1923992#post1923992)

Post any specific questions in the thread & I'll reply there rather than via PM (more people to help, plus it may provide answers for others that are looking for an answer).

I'll need to know a little bit about the network setup at home and work, as we may need to forward some ports on your router.  Can you explain your network setup, routers, bandwidth, etc. at both locations?

A summary of what you need to do:

1. Install SSH on both Windows & Ubuntu
    - [http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/) for XP
    - sudo apt-get install openssh for Ubuntu

2. Verify that you can SSH into the XP box from Ubuntu

3. Follow this thread on how to setup a secure tunnel in SSH:
[http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6155/1/)

You can also look at this thread I've posted in:
[http://www.ubuntuforums.org/showthread.php?p=1912795#post1912795](http://www.ubuntuforums.org/showthread.php?p=1912795#post1912795) for further elaboration.

4. Start VNCviewer on Ubuntu and point it to the localhost 127.0.0.1.  The tunnel that you created in SSH should redirect to the external IP of your work computer.

If all of this seems complex, don't worry... I'll help you through it.

-Dave

---

### Post by qujo86 on 2007-01-23
Thankyou very much.

This was very helpful and it solved my problems.
Im now running vncviewer trough a ssh tunnel to remotely control my Ubuntu and windows-xp at home from my work network.

Happy ;)
//Qujo86

---

