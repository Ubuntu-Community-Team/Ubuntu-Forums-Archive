---
title: "xdmcp, x11, osx, and ubuntu 6.06"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by somuchfortheafter on 2006-11-14
I have a macbook pro with x11 installed on it and virtual work spaces so I can switch between desktops(not that the desktop have anything to do with my question) I also have a server running ubuntu 6.06 with gnome installed. I have resumable vnc sessions now thanks to an tutorial on this forum. My question is this: "How do i configure xdmcp to allow me to login using x11 on the mac through my network without using vnc?" If this is not possible I understand but I knew with two linux boxes I could just point to the other one and login fine so I figured there would be a way to do this in osx as well. Thanks in advance.

---

### Post by joeschram on 2006-11-16
> **somuchfortheafter said:**
> I have a macbook pro with x11 installed on it and virtual work spaces so I can switch between desktops(not that the desktop have anything to do with my question) I also have a server running ubuntu 6.06 with gnome installed. I have resumable vnc sessions now thanks to an tutorial on this forum. My question is this: "How do i configure xdmcp to allow me to login using x11 on the mac through my network without using vnc?" If this is not possible I understand but I knew with two linux boxes I could just point to the other one and login fine so I figured there would be a way to do this in osx as well. Thanks in advance.

Hey somuch...I'm trying to do the same thing myself. I found [this guy's]("http://davidwinter.me.uk/articles/2005/12/08/setting-up-xdmcp-for-mac/") instructions for doing it from Tiger to Ubuntu 6.06, but it is not working with my fresh install of 6.10.

I'm on 10.4.8 with Apple's newest X11 installed, and when I type this into the Terminal.app:

```
/usr/X11R6/bin/X -query XXX.XXX.XXX.XX
```

Where XXX.XXX.XXX.XXX is the IP of the Ubuntu machine, I get this back:

```
XFree86 Version 4.4.0 / X Window System
(protocol Version 11, revision 0, vendor release 6600)
[DRI] screen 0 installation complete
Screen 0 added: 2720x1024 @ (0,0)
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!
```

At this point it just hangs.

I noticed in Dave Winter's instructions that his step in the Login Admin panel is not present in Ubuntu 6.10:

> Under the Security tab, Enable XDMCP

Maybe someone else here has an idea about what the correct options are here? What steps are we missing? :-k

---

### Post by joeschram on 2006-11-16
OK. I'm getting warmer...searches about my font error mentioned above talk about the Ubuntu box possibly needing xfs installed, a font serving system. I will try this and report back.

---

### Post by somuchfortheafter on 2006-11-17
Sweet, I am at work now so I cannot test this but I will at somepoint this weekend and I will report back as well.

---

### Post by ashram on 2006-11-17
There is always possibility to ssh or telnet the server, configure $DISPLAY and run any GUI app...

Sometimes it's even better not to run additional full session for one application

---

### Post by joeschram on 2006-12-10
Well, just for google searchers in the future, here's how I got it working:

1.) Installed xfs via apt-get. Who knows why, but it seemed to make a difference.

2.) Fiddled with my settings in the "Login Window Preferences" until I got something that worked - see the attached screenshots for specifics.

3.) Rebooted both machines (Ubuntu & OS X), then used this command in Terminal.app:

```
/usr/X11R6/bin/X -query YOUR.IP.GOES.HERE
```

Works like a champ and is fast as hell over my LAN - makes VNC looks like molasses!

---

### Post by dalziel_86 on 2007-04-03
I'm in the same situation described earlier in the thread, having the exact same issue, with the same feedback in Terminal:

```
XFree86 Version 4.4.0 / X Window System
(protocol Version 11, revision 0, vendor release 6600)
[DRI] screen 0 installation complete
Screen 0 added: 1280x800 @ (0,0)
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!
```

I've installed xfs on the Ubuntu machine, but this seems to make no difference. I got the error before, I still get it now.

Does anybody have any idea what else I can try to get this working?

---

### Post by dalziel_86 on 2007-04-03
Anyone? Should I have started a new thread instead of bumping this old one?

---

### Post by DeepBlade on 2007-07-21
Ok I'm having the same problem as dalziel_86.
I installed xfs in ubuntu and ensured that the font server is running but I get the same error message.

I did a lot of research and it maybe looks like I need to install the CID font in ubuntu?? How do I do that? Does anyone know how to fix this?? I would really prefer XDMCP over VNC.

---

### Post by DeepBlade on 2007-07-21
actually nevermind. It works..! Except...... when I log in, the keyboard is mapped differently. Things aren't coming up properly when I type..... so I can only use the mouse. The login screen maps the keyboard correctly, but once I log in, the keys are completed messed up.

Does anyone know what to do? How can I fix this? =(

---

### Post by ivotedforkodos on 2007-08-10
DeepBlade, what did you do to get it working? I'm in the same boat as dalziel_86, stuck on the font error in OS X. Does anyone know how to fix this???

---

### Post by DeepBlade on 2007-08-18
After I install xfs, it worked. Once you run the "X -query <ubuntu-machine>", you should see a new app called "XQuartz" show up on your dock. The keys when I type are not correct though... I haven't found a solution. I don't think anyone has.

---

### Post by ivotedforkodos on 2007-08-19
OK, I'm right there with you. My problem was that you have to use the actual IP address; using "hostname.local" didn't work. Anyway, yeah, the keyboard is mapped all screwy. Actually, I was able to login using two different accounts on the Ubuntu machine, but my login failed on another account. I think that it might be related to having a number in your password. (?)

But definitely let me know if you come up with any way to fix the keyboard mapping.

---

### Post by ivotedforkodos on 2007-08-21
I'm going to try this tonight:

[http://ubuntuforums.org/showthread.php?t=396308&highlight=xdmcp+keyboard+map](http://ubuntuforums.org/showthread.php?t=396308&highlight=xdmcp+keyboard+map)

---

### Post by blackpaw on 2007-09-01
try:

/usr/X11R6/bin/Xquartz :1 -query [IP address]

worked for me... also the X server has to be configured properly, talk about the DISPLAY variable.. but that is so long ago I don't quite remember.. I am happy it still works ;)

success


Andreas

---

### Post by allengeer on 2008-07-16
So to fix the keyboard issues (scrambled nonsense text, shift key not working) 

1. login to your Ubuntu box (U-Box) via SSH:
ssh -X <u-box-ip>

2. Generate your key map
xmodmap -pke > $HOME/.xmodmaprc

3. Log out of your SSH session

4. On your Mac OSX machine (O-Box) open the terminal and type
/usr/X11R6/bin/X -q <u-box-ip>

5. You will see Ubuntu's login come up. Log in as normal. A prompt will ask you if you want to load the .xmodmaprc. Add the file to the left hand box and hit okay. Your keys should now work normally.  Except for the Shift key.

6. On the U-Box run this command
gedit ~/.xmodmaprc

7. At the beginning of the file add this text
clear shift
clear lock
clear control
clear mod1
clear mod2
clear mod3
clear mod4
clear mod5

8. At the end of the file add this text
add shift   = Shift_L Shift_R
add lock    = Caps_Lock
add control = Control_L Control_R
add mod1    = Alt_L
add mod2    = Num_Lock
add mod3    = Mode_switch
add mod4    = Meta_L
add mod5    = Scroll_Lock

9. Save the file
10. Log out of Ubuntu and close the X session.
11. Run the /usr/X11R6/bin/X -q <u-box-ip> command again, login, and your shift keys should work.

---

