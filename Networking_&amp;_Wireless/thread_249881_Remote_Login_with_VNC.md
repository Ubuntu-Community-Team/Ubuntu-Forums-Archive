---
title: "Remote Login with VNC"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by m.h.shams on 2006-09-03
dear friends,

i want to use my ubuntu remotely. i active remote desktop for a user.  but when i want to connect ubuntu remotely, i most first login to ubuntu locally, and then use remote connection.

i want to login to my ubuntu, remotely with VNC from WIN XP.

help me plz, 
Thanks All.

---

### Post by Threbus5 on 2006-12-23
Hi,

Does "Log in" mean that you want to use the computer as if you were sitting at it?

You seem moving in the right direction.

So, do that. Login to the Ubuntu locally, make sure that remote desktop is enabled, and walk away from it leaving it running. 

Install and use UltraVNC or tightVNC on your windows machine to access the Ubuntu.

You will have to have enabled port forwarding through your router and firewall and if connecting through the internet, should consider secure tunelling.

But if you don't care about security, from UltraVNC you could type (after port forwarding) your ISP IP that connects to your LAN (for example 68.35.111.32:0) as the vnc address.

Quick and Dirty:
Configure the Ubuntu remote desktop via: menu - system - preferences - remote desktop and select to allow other users to view your desktop, control your desktop, and require the user to enter a password. But Do Not select "ask for confirmation".  A windows VNC viewer/client will access the desktop through a port forwarded router.

Hope this helps.

---

### Post by dbott67 on 2006-12-23
> **m.h.shams said:**
> dear friends,

i want to use my ubuntu remotely. i active remote desktop for a user.  but when i want to connect ubuntu remotely, i most first login to ubuntu locally, and then use remote connection.

i want to login to my ubuntu, remotely with VNC from WIN XP.

help me plz, 
Thanks All.

This HOWTO is probably what you need to do:
[http://www.ubuntuforums.org/showthread.php?p=1627716](http://www.ubuntuforums.org/showthread.php?p=1627716)

I've summarized [emperor's]("http://www.ubuntuforums.org/member.php?u=115") steps below:

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

### Post by dbott67 on 2006-12-29
Please read this important security vulnerability regarding **vnc4server**:

[http://www.ubuntuforums.org/showthread.php?t=327275](http://www.ubuntuforums.org/showthread.php?t=327275)

-Dave

---

