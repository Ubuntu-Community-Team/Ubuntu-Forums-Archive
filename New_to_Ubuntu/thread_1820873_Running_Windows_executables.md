---
title: "Running Windows executables"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by Methus on 2011-08-08
Ok, somewhat new to Ubuntu, but for simplicity just treat me as a complete n00b when giving feedback please. :p

Ok, I have an Ubuntu 10.04 server, and I am wanting to host certain servers for a game I used to play. I can do this by giving arguments to the game's main EXE file. However, I am not sure what to do to get this working on Ubuntu. The server is remote and outside of my LAN.

Now, before you say anything about using WINE, I know I could do that. However, I don't want to have to run a VNC server, tunnel the traffic to my home computer, etc. All I want to do is have Ubuntu run the file with no displays or windows being created. Sort of "in the background" I guess. All the EXE does (with arguments passing through it to be a server) is open up a Command Line console anyways. Maybe a way to get it to export to the SSH console? Idk...:confused:

Any help on the matter is appreciated.

---

### Post by Mark Phelps on 2011-08-08
If you're asking, can you do this WITHOUT Wine, the answer simply put is no.  As to whether you can do it in the background, sorry -- have generally found Wine to be a waste of time, so I can't help you there.

---

### Post by haqking on 2011-08-08
> **Mark Phelps said:**
> If you're asking, can you do this WITHOUT Wine, the answer simply put is no.  As to whether you can do it in the background, sorry -- have generally found Wine to be a waste of time, so I can't help you there.

+1

.exe is a windows thing so you either use windows or you can use methods to run windows .exe such as WINE or virtualisation.

.exe run best in there native envronments, either dual boot or use virtualisation such as vmware or virtualbox

---

### Post by kaldor on 2011-08-08
Which game is it? Almost every game I can think of (that I currently play or have played) releases a Linux server package.

---

### Post by Methus on 2011-08-08
The game is called Starsiege. It was made back in 1998.

---

### Post by Methus on 2011-08-08
> **Mark Phelps said:**
> If you're asking, can you do this WITHOUT Wine, the answer simply put is no.  As to whether you can do it in the background, sorry -- have generally found Wine to be a waste of time, so I can't help you there.

So basically I'm going to have to install a GUI and WINE?

---

### Post by kaldor on 2011-08-08
> **Methus said:**
> So basically I'm going to have to install a GUI and WINE?

Unsure about the GUI (depends on the game). But yes, WINE is definitely a need. You need a Windows compatibility layer in order to run Windows software.

---

### Post by Methus on 2011-08-08
Ok, say I have WINE installed on the server then. If I try to install the software or run something, it yells at me about the X server not running and the DISPLAY not being set right.

---

### Post by anaconda on 2011-08-08
does it work in dosbox?

Just thought that if it is a console program it just might....

---

### Post by Methus on 2011-08-08
I got an error when trying it. Here's what I did:

```

user@server:~# apt-get install dosbox
user@server:~# dosbox

```

And this is what it spat at me:

```

DOSBox version 0.73
Copyright 2002-2009 DOSBox Team, published under GNU GPL.
---
init kbd.
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
CONFIG: Generating default configuration.
Writing it to /root/.dosbox/dosbox-0.73.conf
CONFIG:Loading primary settings from config file /root/.dosbox/dosbox-0.73.conf
Exit to error: Could not initialize video: Video mode smaller than requested

```

---

### Post by kaldor on 2011-08-08
Yeah, you're gonna need a GUI.

If you want to keep things super minimal, install fluxbox. It wil give you a very simple gui and you can use that to run the graphical stuff.

---

### Post by Paqman on 2011-08-08
Looks like DOSBox doesn't like running headless.

---

### Post by Methus on 2011-08-08
Ok, I installed it. This is what I get:

```

user@server:~# startfluxbox
xmodmap:  unable to open display ''
Error: Couldn't connect to XServer

```

---

### Post by Paqman on 2011-08-08
You'll need to install xorg as well.

---

### Post by Methus on 2011-08-08
I already have xorg installed. Do I need to run another command before startfluxbox?

---

### Post by amjjawad on 2011-08-08
I still believe in one thing, even if the otherwise is possible.

"Run everything on its native environment, period."

I have some reasons for that.

Good luck :)

---

### Post by Methus on 2011-08-08
Ok, I've tried the commands ' initx '  and  ' startx '  but neither seem to finish. They both throw this:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux server.com 2.6.32-22-generic-pae #33-Ubuntu SMP Wed Apr 28 14:57:29 UTC 2010 i686 
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-22-generic-pae root=/dev/sda3 ro
Build Date: 08 March 2011  08:22:50AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug  8 11:07:35 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
Fulfilled via DRI at 7683200
Freed 7683200 (pool 2)


```

and then it just kind of hangs there. I can still provide input, but it doesn't do anything. So I cancel it and it says:

```

waiting for X server to shut down xterm:  fatal IO error 11 (Resource temporarily unavailable) or KillClient on X server ":0.0"
Freed 7683200 (pool 1)
error setting MTRR (base = 0xf0000000, size = 0x01000000, type = 1) Inappropriate ioctl for device (25)
 ddxSigGiveUp: Closing log


xinit:  unexpected signal 2.

```

---

### Post by 3rdalbum on 2011-08-08
Wait a moment... doesn't Wine ship with a headless version called "winecmd" or something like that? Pretty sure I remember reading about it.

---

### Post by jimwill on 2011-08-08
I may be missing something here, but how are you accessing the server? Via ssh? Since it is remote you may have to install vnc or something similar, at least to get things up and running. I don't think you can run gui programs over a ssh connection. 
Someone better with ubuntu/linux would have to give help on that.

---

### Post by Methus on 2011-08-08
Yes, I am accessing the server via SSH. I do have VNC on the server as well. However, what I'm looking for is a way to execute a Windows EXE file without the need of having to VNC into the server to load a GUI just to run a window.

3rdalbum got me on the right track though: I search for winecmd and it eventually lead me to wineconsole. I tried it out and it did what I wanted it to: it ran the program through an emulated DOS command line prompt instead of having to open it in and X window. Now I guess I can try to use the screen command with it so it can be running in the background.

:D

---

### Post by Methus on 2011-08-08
Ok, new problem. I had ran winconsole fine until just a bit ago. The command emulated the DOS window fine, and displayed the information that the sever was giving, allowing me input and everything. But now when I try to run it I just get a blank screen. If I CTRL C then it stops it and returns me back to the screen where I typed in the command. I've also tried using the --backend=curses argument.

The only thing that I've done since then to now is:

[LIST]
[*]uninstall xrdp
[*]uninstall tightvncserver
[*]reboot server
[/LIST]
And now it won't work. Hmm....any ideas? Possibly that something within the programs I deleted was something wineconsole was dependent on? I've also tried reinstalling wine.

---

### Post by anewguy on 2011-08-08
Did you install a GUI?  Sounds to me like perhaps it wants a graphic environment in order to run the game - by default the server install is text based only.

Also, I'm sure about running a Wine app and having it available on the server (I'm assuming it's a multi-player game of some sort?).

---

### Post by Methus on 2011-08-08
I actually seemed to of found a work-around. If I use:

```

user@server:~# wineconsole cmd

```

then it emulates a Windows Command Line just fine. From there I can point it to the EXE fille and pass the arguments through, and then it runs fine. Weird...

---

### Post by CatKiller on 2011-08-09
> **jimwill said:**
> I don't think you can run gui programs over a ssh connection. 
Someone better with ubuntu/linux would have to give help on that.

You can. Network transparency is one of the nicest things about X. I do it all the time. You just need to forward X connections over SSH.

The OP seems to have got things working without it, though.

---

