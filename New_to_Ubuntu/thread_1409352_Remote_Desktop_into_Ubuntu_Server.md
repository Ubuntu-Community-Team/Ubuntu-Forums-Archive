---
title: "Remote Desktop into Ubuntu Server"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by nitrusoxide on 2010-02-17
Hello,

I have an old PC set up with Ubuntu Server edition, and it works fine on my home LAN.  I can connect to it via ssh through a terminal session on my Macbook, and I set up a few directories for backing up files.  This PC is headless.

Now I know that this may be taboo, but I wanted to install a GUI so that I can actually see Ubuntu.  I installed Gnome, and now I'm interested in setting up remote desktop access.  I downloaded and installed tightvnc server and set that up.  I forwarded port 5600 on my Airport, and installed Chicken of the VNC on my Mac.

This is the part that I don't know how to do.  I'm assuming I need to start Gnome, then start tightvnc, right?  So far I've been starting gdm, starting the vnc session, then typing startx to load Gnome.  Then I go to my Mac and fire up Chicken of the VNC and type in the IP address followed by the display number.  It connects, but all I see is a gray screen with one quadrant black.  What am I doing wrong?

Thanks!

---

### Post by mk1w86 on 2010-02-17
I know it doesn't solve your problem, but out of interest is there a particular reason you need a GUI on the server? :-k

---

### Post by bodhi.zazen on 2010-02-17
If you want a gui for server management I advise you go with something more like webmin.

Honestly, IMO, GNOME or KDE or XFCE or a window manager is of little use as 99.99 % of managing a server is either editing text files or issuing commands, neither of which is particularly enhanced by X Windows desktops.

---

### Post by pirateghost on 2010-02-17
> **bodhi.zazen said:**
> if you want a gui for server management i advise you go with something more like webmin.

Honestly, imo, gnome or kde or xfce or a window manager is of little use as 99.99 % of managing a server is either editing text files or issuing commands, neither of which is particularly enhanced by x windows desktops.
+1

---

### Post by nitrusoxide on 2010-02-17
I know, I know, it's a noob move, but I'm not familiar with Ubuntu at all, so I wanted to get familiar with all facets of the OS (including the GUI's).  I probably should have installed Ubuntu Desktop on this PC from the start, but I didn't want to cut myself short if I ever wanted to take full advantage of all the features the Server edition offers (whatever they are).

---

### Post by bodhi.zazen on 2010-02-17
> **nitrusoxide said:**
> I know, I know, it's a noob move, but I'm not familiar with Ubuntu at all, so I wanted to get familiar with all facets of the OS (including the GUI's).  I probably should have installed Ubuntu Desktop on this PC from the start, but I didn't want to cut myself short if I ever wanted to take full advantage of all the features the Server edition offers (whatever they are).

You will not cut yourself short if you install the standard desktop.

Unlike Windows, the only difference between server and desktop editions are:

1. The server edition has a custom server kernel.
2. The set of default applications installed is different.

You can install server software, such as Apache, FTP, Samba, etc on a Desktop if you wish.

From what you describe, I would advise you simply :

```
sudo apt-get install ubuntu-desktop
```

As far as VNC server, it depends on which one you use. The default, vino, yes you need to be loged in.

But if you use an alternate VNC server, such as tight VNC, you do not.

You could also try FreeNX

---

### Post by kanikilu on 2010-02-17
This doesn't directly address your question about VNC, but I much prefer FreeNX as a means of remote desktop.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

The NX Client for Mac OS X can be found here:

[http://www.nomachine.com/select-package-client.php](http://www.nomachine.com/select-package-client.php)

---

### Post by pirateghost on 2010-02-17
> **nitrusoxide said:**
> <snip>
I ever wanted to take full advantage of all the features the Server edition offers (whatever they are).
lack of GUI.  you are looking at the advantage

try webmin out.  it gives you the ability to maintain and configure your server from a web browser.  the desktop gui CANNOT teach you anything about running a server, and as stated already, is basically useless for server administration because most of your server admin will come from editing files or running commands (which can be done via ssh)

dont think of a lack of a GUI as a setback, consider it a performance boost and a training aid.  if all you ever use is a desktop GUI for everything, you are learning basically nothing.
example:
compare folder sharing with windows clients;
in desktop gui, you right click on a folder and share.  done.  what have you learned?  that you can right click.
in command line gui, or even via webmin (which is basically a webgui that is wrapped around the basic commands, and config file editing) configuring SAMBA (you dont really need to know that term in desktop GUI) is much harder.
```
sudo nano /etc/samba/smb.conf
[global]
        guest account = nobody
        netbios name = nas
        server string = nas
        default = shares
        workgroup = WORKGROUP
        os level = 20
        null passwords = yes
        interfaces = lo eth0
        encrypt passwords = true
        security = share
        preferred master = no
        bind interfaces only = true
        max open files = 10240


[shares]
        comment = shares on nas
        path = /mnt/shares
        browseable = yes
        read only = no
        guest ok = yes
        ; recycler
                vfs object = recycle:recycle
                recycle:subdir_mode = 0770
                recycle:repository = .recycle bin
                recycle:keeptree = Yes
                recycle:touch = Yes
                recycle:versions = No
                recycle:maxsize = 100000000 ; 100 metric million bytes

```now which one are you more likely to LEARN from?  or have a better understanding when it comes to trying to troubleshoot issues?

---

### Post by nothingspecial on 2010-02-17
> **nitrusoxide said:**
> Hello,
 I can connect to it via ssh through a terminal 



If the object of the exercise is to learn, then I would install a gui (as it were) on your server. That`s how I learned.....I just unplugged the monitor and keyboard of my old desktop and stuck it under the stairs.

Anytime I couldn`t do something from the cli, I used X forwarding. Now I don`t bother with X much on my main system.

ssh -X user@ipadress

---

### Post by nitrusoxide on 2010-02-17
Thanks to all for the very helpful responses, they've given me much to consider.

I think I will try the webmin approach, and install the Desktop version when I want to mess around with the GUI, purely for exposure to it.

One final question though, relating to what bodhi.zazen said, will installing ubuntu-desktop like that overwrite the server install?  Meaning, will I then have Ubuntu Server edition and Desktop edition or just the Desktop version?  Sorry if that's a stupid question, but I just want to make sure I know what I'm working with.

---

### Post by pirateghost on 2010-02-17
> **nitrusoxide said:**
> Thanks to all for the very helpful responses, they've given me much to consider.

I think I will try the webmin approach, and install the Desktop version when I want to mess around with the GUI, purely for exposure to it.

One final question though, relating to what bodhi.zazen said, will installing ubuntu-desktop like that overwrite the server install?  Meaning, will I then have Ubuntu Server edition and Desktop edition or just the Desktop version?  Sorry if that's a stupid question, but I just want to make sure I know what I'm working with.
you would have server edition with a desktop gui.

---

### Post by bodhi.zazen on 2010-02-17
> **nitrusoxide said:**
> Sorry if that's a stupid question, but I just want to make sure I know what I'm working with.

It is a valid question, but as pirateghost indicated, ubuntu-desktop will install the default ubuntu (gnome) desktop and you keep the server stuff as well.

---

### Post by 3rdalbum on 2010-02-17
You didn't need to install a VNC server onto Gnome. It already has one built-in. On your server, go to System > Preferences > Remote Desktop to set it up.

---

### Post by gzur on 2010-02-22
Am I wrong in thinking that if he installs ubuntu-desktop - and then decides he doesn't need it, he can just apt-get remove it with no net loss? 

Right?

---

### Post by bodhi.zazen on 2010-02-22
It is not so easy to remove ubuntu-desktop, but it can be done.

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

