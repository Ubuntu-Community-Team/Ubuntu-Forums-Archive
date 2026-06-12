---
title: "Running Ubuntu 9.10 (x86) with no monitor?"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by Kerrisis on 2010-03-19
Hi all, I wonder if someone could help me out, please.

I'm trying to run an Ubuntu box as a small fileserver I can have sat off to one side with just power and ethernet attached. I've managed to get the system installed and networked, and set up the share with the right permissions etc. I've run into a small problem, however.

Whenever I turn the system on with no VGA cable attached, I get an error box that says:
```
**Ububto is running in low-graphics mode**

The following error was encountered. You may need to update your configuration to solve this.

(EE) Failed to load module "i810" (module does not exist, 0)
(EE) open /dev/fb0: No such file or directory
(EE) intel(0): No cald modes.
(EE) Screen(s) found, but none have a usable configuration.
```

As the OS stops here, I'm unable to use the file shares, remote in with VNC etc. 

I've hunted through the forum here for several hours now. he only thing I could find was to add the line:
xrandr --output VGA --mode 1024x768 --rate 75
to the file:
/etc/X11/Xsession.d/45custom_xrandr-settings (which I had to make as it didn't exist).

This makes the system work without a screen once, but on the following reboot it just throws up the same error message again. I'm using an old P4 box with an Intel 865 chipset, using the onboard graphics when necessary.

Can anyone offer me any advice please?
Thanks in advance.

---

### Post by Mighty_Joe on 2010-03-19
How are you seeing the error without a monitor? ;)
Is the error coming from GDM (the graphical log in prompt) or after you log in?
I use Ubuntu Server for my headless "home server appliance".  No GUI, no problem.

---

### Post by abohsin on 2010-03-19
If this command works once, but doesn't work on reboot, then place this command in a <script_name>.sh, then add it in startup programs, System > Preferences > Startup Applications. See if that works.

---

### Post by Kerrisis on 2010-03-19
Joe:
If I plug the screen in after a minute or so, that's what I see. It's obviously sticking at that message rather than booting straight to the desktop. The problem crops up before any graphical login prompts. If it helps, at the point of sticking the shares I've set up are visible from my W7 box but don't allow me to view the contents at that point. They work fine when the system boots properly.

Aboshin:
Unfortunately that made no appreciable difference. 


Thanks to you both for your replies BTW. =)

---

### Post by Mighty_Joe on 2010-03-19
Easiest thing to do: plug in a monitor, boot up, unplug monitor. You shouldn't be booting a server that often (it should be on a UPS) so it shouldn't be *that *inconvenient. 
Probably the "correct" thing to do: install Ubuntu Server.  No GUI, no problem.  
If that's unacceptable, I'd try disabling GDM and X so they don't start up automatically.  That way, if you really need a GUI, you can always run startx and get the familiar desktop, but it wouldn't be looking for those drivers at startup.

---

### Post by 3rdalbum on 2010-03-19
I have the same issue and I plug in the monitor when starting up, and unplug it afterwards. It's not really a good solution.

I really want to have a GUI server that I can VNC into, so I can start a download in Firefox on the server and have it running overnight. For certain things, I can't just wget or torrent them - and if I tried to wget anyway I'd need to leave my other computer on just to maintain the SSH connection.

---

### Post by Kerrisis on 2010-03-19
Mighty_Joe:
In the interests of keeping my power bills down (at £0.16 per kWh it mounts up fast) I'd like to be able to turn the unit off when I'm not using it. I'm a Windows refugee attempting to find asylum with Ubuntu, so I can't work without a GUI (BASH prompts are highly intimidating for someone who only knows DOS commands!). I was also hoping to be able to VNC into said GUI at will to make changes, have a play around and get used to Linux etc. While your workarounds may work, they're not exactly ideal (not that I don't appreciate you taking the time to answer, though; I do! ).

Is there really no way to run a screenless Linux box without disabling the GUI or having to fumble around with VGA cables every time I turn it on?

---

### Post by Mighty_Joe on 2010-03-19
> **3rdalbum said:**
> if I tried to wget anyway I'd need to leave my other computer on just to maintain the SSH connection.

Let me introduce you to my friend [screen]("http://www.manpagez.com/man/1/screen/").  You can leave a terminal session running after terminating your SSH session.  When you log back in, you run "screen" again to resume.

---

### Post by Kerrisis on 2010-03-19
I guess the tumbleweed gently rolling past accompanied by the lonely, sonorous tolling of a churchbell in the distance means the answer to my question is "Yes, there is no way".

Guess I'm going back to XP. Ah well, it was a nice idea.

---

### Post by sailor2001 on 2010-03-19
[https://help.ubuntu.com/community/i810](https://help.ubuntu.com/community/i810)

---

### Post by Kerrisis on 2010-03-22
Thanks for the reply, sailor2001. Unfortunately that didn't seem to help - I'm still getting the same error. The page you linked me seems to rely on editing the xorg.conf file. That didn't exist in my system until I created it, implying that Ubuntu is storing/reading the information from somewhere else now.

Anyone have any ideas where that may be?

---

### Post by 3rdalbum on 2010-03-22
> **Mighty_Joe said:**
> Let me introduce you to my friend [screen]("http://www.manpagez.com/man/1/screen/").  You can leave a terminal session running after terminating your SSH session.  When you log back in, you run "screen" again to resume.

Ahh, I didn't know screen could do that. Thanks!

(I can't try it at the moment, the server's unplugged due to electrical storms)

Also, I'm thinking it might be possible to use a miniature X server like XVesa to run your graphical environment in - it might not need a monitor plugged in. I shall try this at some point; the server's going to get 10.04 soon so just before this happens will be a good time to make the attempt.

---

### Post by halitech on 2010-03-22
> **Kerrisis said:**
> Thanks for the reply, sailor2001. Unfortunately that didn't seem to help - I'm still getting the same error. The page you linked me seems to rely on editing the xorg.conf file. That didn't exist in my system until I created it, implying that Ubuntu is storing/reading the information from somewhere else now.

Anyone have any ideas where that may be?

when you created the /etc/X11/xorg.conf file, what did you put into it? If you just created the file and left it blank it would be the same as not having a file to start with. I'm not sure but I think hal is now autodetecting all hardware (someone correct me if I'm wrong) so xorg.conf isn't needed. It will be used if it is there and configured properly.

can you open a terminal and post the output of
```
cat /etc/X11/xorg.conf
```

---

### Post by Kerrisis on 2010-03-22
Halitech:
As requested, here's the results. It was basically copy-pasted from the link sailor2001 posted, with minor modifications for my system.

```
Section "Device"
        Identifier      "Intel Corporation 82865G Integrated Graphics Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

Edit:
Incidentally, after the fumbling around I've done, the start up error message with no monitor attached now only has 2 warning codes in it:
```
(EE) intel(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration.
```

---

### Post by halitech on 2010-03-22
that looks okay except 1 question. Did you confirm your card is actually on PCI Bus 0:2:0 with the lspci command?

---

### Post by Kerrisis on 2010-03-22
I did, and it seems to be, yes. The appropiate line from the lspci command is:
```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```

---

### Post by halitech on 2010-03-22
okay, that looks right then ... maybe try changing intel in the driver line to i810 as per the info here : [https://help.ubuntu.com/community/i810](https://help.ubuntu.com/community/i810)

---

### Post by Kerrisis on 2010-03-22
Setting the driver line to i810 just gives me more error messages, along the lines of "This driver module isn't installed", despite (to the best of my ability to tell) it should be installed as it's part of the same pack that the "intel" driver is in.

With the assistance of a friend via Jabber though, I think it's fixed. I changed the driver to "vesa", and it seems to be booting straight to Gnome without any errors now. I'm guessing this is substituting the optimised Intel drivers for the generic Vesa ones and won't use any of the card's capabilities beyond basic 2D display, but that's not a problem in my case really. =)

Thanks to everyone for your help, it's greatly appreciated! =D

---

