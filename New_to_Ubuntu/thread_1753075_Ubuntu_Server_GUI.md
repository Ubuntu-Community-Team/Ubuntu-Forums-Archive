---
title: "Ubuntu Server GUI"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2011-05-08
Hey,

I have a machine running Ubuntu server, and I would like to be able to watch videos on it using either mplayer or VLC. Anyone know what packages I need to get this to work?

If I could eventually get Firefox to work, that would be nice as well.

All help is appreciated.

Thanks,
Kurt

---

### Post by dniMretsaM on 2011-05-08
You could try the LXDE interface.

---

### Post by wojox on 2011-05-08
For all that you need x-server installed. So +1 for lxde.

---

### Post by K_45 on 2011-05-08
This defeats the whole point of a server, and introduces possible security risks. If you are using a server to serve whatever, why are you putting a GUI on it?

---

### Post by jkurtisr32 on 2011-05-08
Thanks for the replies. I'm going to give LXDE a try.

> **K_45 said:**
> This defeats the whole point of a server, and introduces possible security risks. If you are using a server to serve whatever, why are you putting a GUI on it?

This computer is old as **** and will not run the full Ubuntu GUI. Setting it up as a media client to play movies and music.

I wouldn't mind figuring out how to run the programs I mentioned without a full desktop environment, as everyone in my house would be able to use a device with CLI only.

-Kurt

---

### Post by K_45 on 2011-05-08
> **jkurtisr32 said:**
> Thanks for the replies. I'm going to give LXDE a try.



This computer is old as **** and will not run the full Ubuntu GUI. Setting it up as a media client to play movies and music.

I wouldn't mind figuring out how to run the programs I mentioned without a full desktop environment, as everyone in my house would be able to use a device with CLI only.

-Kurt

 Then you should go for an Ubuntu minimal install and install what you need or a Debian net install which is similar. Then you can use something like Mediatomb to stream your files. Alternatively you could buy a NAS to stream your media. For the command line, some programs need a GUI. For music at least I'd look at an MPD server, or, as I mentioned, a NAS box.

---

### Post by jkurtisr32 on 2011-05-08
> **K_45 said:**
> Then you should go for an Ubuntu minimal install and install what you need or a Debian net install which is similar. Then you can use something like Mediatomb to stream your files. Alternatively you could buy a NAS to stream your media. For the command line, some programs need a GUI. For music at least I'd look at an MPD server, or, as I mentioned, a NAS box.

Haha, I had originally created this thread with the "Ubuntu minimal install and install what you need" method in mind. The problem is that I have no idea what I need to make these things work. I tried setting it up this way yesterday, but... fail.

I have installed the LXDE, and it seems to be pretty stable on this machine. This definitely is packaged with the things that I need to get my programs running, even though I don't need the full environment. I might just end up booting into CLI and running GUI-based programs from there (if possible).

Let me know what you think, and again, thanks for all the help.

-Kurt

---

### Post by K_45 on 2011-05-08
For the Debian minimal install on my machines I run:

```
sudo apt-get install slim xfce4 xfce4-taskmanager xfce4-terminal xorg wicd
```

From this you can boot into XFCE4, then install the rest of the apps you need via terminal. To keep the bloat down there is no synaptic or gdebi so installing apps is via the command line. From there you can explore the command line alternatives, I would recommend MPD to serve music, and I've heard good things about mediatomb as a media server. As I also mentioned everything will be simplified with a NAS box serving your media to wherever, although that may not be practical.

---

### Post by jkurtisr32 on 2011-05-08
> **K_45 said:**
> For the Debian minimal install on my machines I run:

```
sudo apt-get install slim xfce4 xfce4-taskmanager xfce4-terminal xorg wicd
```

From this you can boot into XFCE4, then install the rest of the apps you need via terminal. To keep the bloat down there is no synaptic or gdebi so installing apps is via the command line. From there you can explore the command line alternatives, I would recommend MPD to serve music, and I've heard good things about mediatomb as a media server. As I also mentioned everything will be simplified with a NAS box serving your media to wherever, although that may not be practical.

This machine will be used as a client that simply plays media pulled over my network. I think that for video players, I was either going to use vlc or mplayer. For music, I was definitely going to use MPD.

I have the audio all working, but I could not get mplayer or vlc to play movies through the X11 installation that I did. I thought that that would be enough to play video, but I think I'm still a little bit confused at how these kinds of things work.

I got everything to work under the LXDE installation, but I would really like to get this working without having to always use a desktop environment. Is that possible to do?

-Kurt

---

### Post by K_45 on 2011-05-08
If it will serve media, use mediatomb, if you don't need local playback. If you want to stream media, then use VLC which uses Xorg for the GUI. Command line requirements are different. You'll also need a fairly decent media to stream.

---

### Post by jkurtisr32 on 2011-05-08
> **K_45 said:**
> If it will serve media, use mediatomb, if you don't need local playback. If you want to stream media, then use VLC which uses Xorg for the GUI. Command line requirements are different. You'll also need a fairly decent media to stream.

Well it will only be playing back local media. I think it would be nice to get vlc working for local palyback without having to use any desktop environment. If starting with a fresh install of Ubuntu server, would I just have to install vlc and then get the xorg package?

-Kurt

---

### Post by Paqman on 2011-05-08
> **jkurtisr32 said:**
> If starting with a fresh install of Ubuntu server, would I just have to install vlc and then get the xorg package?


I'd use the minimal image rather than the server one. Installing just xorg and your video player will mean that you're missing a lot of stuff, such as a graphical way to log into the machine and manage files. Exactly what DE you choose is mostly personal preference. There are a range of packages available in the Ubuntu repos for lightweight systems. You can even have a Gnome desktop that will only take up about 100MB of RAM.

Generally speaking, the minimum usable desktop system will consist of:
[LIST]
[*]xorg
[*]A DE package such as lxde, xfce4 or gnome-core
[*]A network manager such as network-manager or wicd
[*]A login screen such as gdm or lxdm
[/LIST]

You may also want to install some other bits and pieces like session managers, better themes and panel applets, but they are more for convenience.

---

### Post by jkurtisr32 on 2011-05-08
> **Paqman said:**
> I'd use the minimal image rather than the server one. Installing just xorg and your video player will mean that you're missing a lot of stuff, such as a graphical way to log into the machine and manage files. Exactly what DE you choose is mostly personal preference. There are a range of packages available in the Ubuntu repos for lightweight systems. You can even have a Gnome desktop that will only take up about 100MB of RAM.

Generally speaking, the minimum usable desktop system will consist of:
[LIST]
[*]xorg
[*]A DE package such as lxde, xfce4 or gnome-core
[*]A network manager such as network-manager or wicd
[*]A login screen such as gdm or lxdm
[/LIST]

You may also want to install some other bits and pieces like session managers, better themes and panel applets, but they are more for convenience.

This is definitely good information to have, as I am a fan of minimalism when talking about computers. However, for this particular machine, I only need it to play movies and music. All file management is already being done on one of my other machines.

Is it possible to just install the player and xorg and have it work from terminal?

-Kurt

---

### Post by Paqman on 2011-05-09
> **jkurtisr32 said:**
> 
Is it possible to just install the player and xorg and have it work from terminal?


Don't know because i've not tried it, but I know one way to find out! There may be some little snags that you only discover when you try it.

You could add VLC to that startup applications and have it launch full screen. Set your user account to log in automatically. In effect, VLC would be your interface.

Interesting little project, let us know if it works. I might open up a new VM and try it myself, too.

---

### Post by nothingspecial on 2011-05-09
> **jkurtisr32 said:**
> Hey,

I have a machine running Ubuntu server, and I would like to be able to watch videos on it using either mplayer or VLC. Anyone know what packages I need to get this to work?



You don't need X, you just need to enable the framebuffer.

First, create a udev rule to allow you to use it

```
sudo mkdir /etc/udev/my-rules.d
```

```
sudo nano /etc/udev/my-rules.d/framebuffer.rules
```

Put this line in it then press Ctrl-O to save it and Ctrl-X to exit

```
KERNEL=="fb0",  OWNER="root", MODE="0660"
```

Then add yourself to the video group

```
sudo usermod -a -G video $USER
```

Then restart and you can watch videos on the console :guitar:

---

### Post by alexan on 2011-05-09
**sudo apt-get install tinywm pcmanfm menu**

---

### Post by bodhi.zazen on 2011-05-09
> **jkurtisr32 said:**
> Thanks for the replies. I'm going to give LXDE a try.



This computer is old as **** and will not run the full Ubuntu GUI. Setting it up as a media client to play movies and music.

I wouldn't mind figuring out how to run the programs I mentioned without a full desktop environment, as everyone in my house would be able to use a device with CLI only.

-Kurt

Install a minimal window manager such as openbox (which is what LXDE uses), fluxbox, or awesome.

---

### Post by nothingspecial on 2011-05-09
You won't be able to use firefox in the framebuffer but if you install links2 and run it with ```
links2 -g
```

You will be able to see images in web pages. Unfortunately links2 doesn't support cookies which means you have to enter your username and password every time you log on to ubuntuforums.org........

...... but since this is a server, you could just stay logged on.

Also, bear in mind that the framebuffer doesn't work with terminal multiplexers such as screen or dvtm so you would need to log in to a different tty if you use them.

You can even take screenshots using fbgrab in the framebuffer

Watching a Snoopy video on the console

[ATTACH]191682[/ATTACH]

Viewing images of butterflies on google images on the console

[ATTACH]191683[/ATTACH]

---

### Post by nothingspecial on 2011-05-09
Sorry for multiple posts in your thread but ......

..... vlc will not work

Use mplayer

---

### Post by jkurtisr32 on 2011-05-10
> **nothingspecial said:**
> You don't need X, you just need to enable the framebuffer.

First, create a udev rule to allow you to use it

```
sudo mkdir /etc/udev/my-rules.d
```

```
sudo nano /etc/udev/my-rules.d/framebuffer.rules
```

Put this line in it then press Ctrl-O to save it and Ctrl-X to exit

```
KERNEL=="fb0",  OWNER="root", MODE="0660"
```

Then add yourself to the video group

```
sudo usermod -a -G video $USER
```

Then restart and you can watch videos on the console :guitar:

Thanks for this. I think I'm getting close. I followed the steps above to try and enable the framebuffer, but I got this output when I tried to run the 'links2 -g' command:
```
$ links2 -g

   ~~~~~~~~~~~~~~~~~~~~~~~~~~| DirectFB 1.2.8 |~~~~~~~~~~~~~~~~~~~~~~~~~~
        (c) 2001-2008  The world wide DirectFB Open Source Community
        (c) 2000-2004  Convergence (integrated media) GmbH
      ----------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2010-04-09 11:08) 
(!) DirectFB/core/vt: Error opening `/dev/tty0'!
    --> Permission denied
(!) DirectFB/Core: Could not initialize 'system_core' core!
    --> Initialization error!
svgalib: Cannot get I/O permissions.
```

I am also still not able to watch videos in the console using mplayer. I assume that issues with mplayer are being caused by whatever is stopping links2 from working.

-Kurt

---

### Post by jkurtisr32 on 2011-05-10
> **bodhi.zazen said:**
> Install a minimal window manager such as openbox (which is what LXDE uses), fluxbox, or awesome.

Thanks for the reply. I did get everything working under LXDE, but it is definitely overkill for what I need. In a perfect world, I would just turn the machine on and it would load VLC in fullscreen mode. The machine will be connected to a TV and will be used only for movies (and MPD for music).

-Kurt

---

### Post by nothingspecial on 2011-05-10
Then you didn't do it correctly :)

Probably the way I explained it.  :P

You need to put this line

```
KERNEL=="fb0",  OWNER="root", MODE="0660"
```

in a file named /etc/udev/my-rules.d/framebuffer.rules

Then reboot.

Also, you need to be part of the video group, to check you did that correctly type

```
less /etc/group | grep $USER
```

You should see something like this

```
video:x:44:ns
```

except ns will be your username.

What does ```
cat /etc/udev/my-rules.d/framebuffer.rules
``` output?

To check it is possible to use the framebuffer (which it almost definitely will be) on your system try running mplayer with sudo on a video file.

Also, it might be that you need to install gpm for links2 -g to work

```
sudo apt-get install gpm
```

---

### Post by nothingspecial on 2011-05-10
> **jkurtisr32 said:**
> Thanks for the reply. I did get everything working under LXDE, but it is definitely overkill for what I need. In a perfect world, I would just turn the machine on and it would load VLC in fullscreen mode. The machine will be connected to a TV and will be used only for movies (and MPD for music).

-Kurt

I'm not sure on this but.........

For this senario, try installing slim

It should pull in just enough X stuff to play videos on your tv.

I'm assuming you have another {laptop,netbook} to control this with.

If that is the case, and you do install X, from the laptop

```
ssh user@ipaddress
export DISPLAY=:0.0
mplayer video_file
```

Press F and it will go fullscreen on your tv.

---

### Post by bodhi.zazen on 2011-05-10
If you are forwarding X over ssh:

You do not need to set the display and the display is :10

If you are ssh and displaying  X apps on the remove server:

1. X has to be running.
2. Usually you then need to run xhost. Then you can use :0

---

### Post by nothingspecial on 2011-05-10
> **bodhi.zazen said:**
> If you are forwarding X over ssh:

You do not need to set the display and the display is :10

If you are ssh and displaying  X apps on the remove server:

1. X has to be running.
2. Usually you then need to run xhost. Then you can use :0

I'm not talking about forwarding X

I'm talking about running X on the server connected to the tv, then using a remote box to control it.

I'm guessing this senario.........

Old, rubbish computer.

New tv with one of those blue input for monitor thingys.

OP would like to watch films/movies on the tv that reside,  on old computer connected to it, and start/stop/pause them from the remote box.

But I could be wrong.........

---

### Post by pi.boy.travis on 2011-05-10
Servers shouldn't have GUIs. And after setup they really don't need monitors either.

---

### Post by nothingspecial on 2011-05-10
> **pi.boy.travis said:**
> Servers shouldn't have GUIs. And after setup they really don't need monitors either.

This is linux, and as such, you can do whatever you like :popcorn:

---

### Post by pi.boy.travis on 2011-05-10
> **nothingspecial said:**
> This is linux, and as such, you can do whatever you like :popcorn:

True, true. But there are still best practices.

For streaming media, I took one of my old (~13 years) HP Pavilions, threw a gig of RAM in, a new gigabit Ethernet controller. and added a few TB of hard disk space. Ubuntu Server + SSH + Samba + NFS = Excellent file server.

---

### Post by pi.boy.travis on 2011-05-10
> **pi.boy.travis said:**
> True, true. But there are still best practices.

For streaming media, I took one of my old (~13 years) HP Pavilions, threw a gig of RAM in, a new gigabit Ethernet controller. and added a few TB of hard disk space. Ubuntu Server + SSH + Samba + NFS = Excellent file server.

It's been running for several years now, and I only attach a monitor to move from one version to Ubuntu to the next, upgrading over SSH makes me nervous. . . :shock:

If anyone would like to set this up, the Ubuntu Server Documentation is pretty good for all of these services:

[https://help.ubuntu.com/11.04/serverguide/C/index.html](https://help.ubuntu.com/11.04/serverguide/C/index.html)

---

### Post by bodhi.zazen on 2011-05-10
> **nothingspecial said:**
> I'm not talking about forwarding X

I'm talking about running X on the server connected to the tv, then using a remote box to control it.

I'm guessing this senario.........

Old, rubbish computer.

New tv with one of those blue input for monitor thingys.

OP would like to watch films/movies on the tv that reside,  on old computer connected to it, and start/stop/pause them from the remote box.

But I could be wrong.........

In that case you need to add xhost 

Nice discussion here:

[http://ubuntuforums.org/showthread.php?t=1553063](http://ubuntuforums.org/showthread.php?t=1553063)

In particular, this post outlines the process step-by-step

[http://ubuntuforums.org/showpost.php?p=10784779&postcount=9](http://ubuntuforums.org/showpost.php?p=10784779&postcount=9)

---

### Post by nothingspecial on 2011-05-10
> **bodhi.zazen said:**
> In that case you need to add xhost 

Nice discussion here:

[http://ubuntuforums.org/showthread.php?t=1553063](http://ubuntuforums.org/showthread.php?t=1553063)

In particular, this post outlines the process step-by-step

[http://ubuntuforums.org/showpost.php?p=10784779&postcount=9](http://ubuntuforums.org/showpost.php?p=10784779&postcount=9)

Strange.......

I'm sure I've never needed nohup for this.

Remote box is using ubuntu minimal (not server)

I just ssh in then change the display environment variable and away I go.

Is this a difference in the server/minimal set up?

---

### Post by nothingspecial on 2011-05-10
> **pi.boy.travis said:**
> True, true. But there are still best practices.

For streaming media, I took one of my old (~13 years) HP Pavilions, threw a gig of RAM in, a new gigabit Ethernet controller. and added a few TB of hard disk space. Ubuntu Server + SSH + Samba + NFS = Excellent file server.

I think, perhaps, that the op is not setting up a server as such.

I think he just wants a very very light system to watch movies on his tv.

I meant no offence :)

---

### Post by pi.boy.travis on 2011-05-10
> **nothingspecial said:**
> I think, perhaps, that the op is not setting up a server as such.

I think he just wants a very very light system to watch movies on his tv.

I meant no offence :)

Ahh, that's what I get for not reading all of the interim posts! :P

In that case, my recommendation would be MythTV.

[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

---

### Post by bodhi.zazen on 2011-05-10
> **nothingspecial said:**
> Strange.......

I'm sure I've never needed nohup for this.

Remote box is using ubuntu minimal (not server)

I just ssh in then change the display environment variable and away I go.

Is this a difference in the server/minimal set up?

Well, if it working as you expect, then no problem.

Some apps terminate when you close the X session and in that event you would need a tool (nohup, screen, dtach). Other apps do not stop running.

It is not often that I need to open an X application on the remote :0 screen, but last time I looked I did need xhost.

---

### Post by madjr on 2011-05-10
> **pi.boy.travis said:**
> Ahh, that's what I get for not reading all of the interim posts! :P

In that case, my recommendation would be MythTV.

[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

+1 for mythbuntu


@jkurtisr32

did you installed all the codecs to get your videos working?

---

### Post by nothingspecial on 2011-05-11
Just copied and pasted my instruction in a brand new install today and it works.

I can even watch youtube :wink:

[ATTACH]191825[/ATTACH]

---

### Post by jkurtisr32 on 2011-05-11
Finally got it working.

Just want to say thanks a lot to everyone who contributed to this thread, especially to "nothingspecial".

@nothingspecial:
This configuration is really legit. This is a great way to turn an old box into something useful. I'll probably be referring back to this in the future, as there is limited and scattered information out there on how to get something like this working. Thanks again.

Well, now I'm off to get my TVout interface working.

Peace,
Kurtis

---

### Post by nothingspecial on 2011-05-11
No problem, glad to have helped.  :D

---

