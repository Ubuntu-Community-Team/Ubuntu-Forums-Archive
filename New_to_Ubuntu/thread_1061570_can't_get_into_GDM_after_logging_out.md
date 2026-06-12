---
title: "can't get into GDM after logging out"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Milov on 2009-02-05
I'm very new to Ubuntu and Linux. I've used Fedora a little bit on some of the servers at my work, but I really have no idea what I'm doing. I'm a Windows guy.

I've got an Ubuntu 8.10 Live CD, from which I have installed Ubuntu to my harddrive. The live CD works fine, and the install worked fine, and booting up after the install worked fine.

While booted up, I didn't change anything except my firefox homepage. However, at some point I decided to logout using the icon in the top right corner of the Gnome interface. I didn't expect it to kick me out to text mode, but that's what it did, followed by it prompting me to enter my login details. So, I logged back in, but nothing happened. It just stayed right there at tty1, whereas I was hoping I would go back to Gnome. I don't know how to get back into gnome from text mode. I tried restarting the computer, by pressing ctrl+alt+del, but every time it starts, It asks me to login again, and then it stays at tty1.

(I'm multi-booted on the same machine into Vista to use these forums right now)

I've been Googling for hours trying to find a solution to this, but nothing has worked. Here's a list of things I've tried:

startx
- this seems to fail, saying "no screens found", then it logs me out

Ctrl+Alt+F7
- this just goes to a blank screen with a little text cursor in the top left corner. Luckily I figured out that I can use alt+left/right to get back to tty1.

sudo /etc/init.d/gdm start
- This tells me that it is starting up gdm, but nothing happens after that. If I try to startx afterwards, startx still tells me "no screens found"

sudo gdm
- This tells me gdm is already running, even if I didn't already run 'sudo /etc/init.d/gdm start'

sudo dpkg-reconfigure -phigh xserver-xorg
-Threads I've read seem to imply that this asks you for information to configure X, but it didn't do that. It output a couple lines about using the defaults, and telling me the path where it put a backup.

I think that is it. It seems like this shouldn't be such a difficult problem, since it was working fine and I didn't change anything, all I did was log out. But, I'm about ready to reinstall Ubuntu and just hope that I don't have to logout again anytime soon, even though I know this is bound to come back up if I don't find a solution to it.

Any ideas would be appreciated. I'm going to continue fiddling around with ideas.

---

### Post by taseedorf on 2009-02-06
sounds like you need a drive installed maybe.... or something got VERY messed up with your install

try

sudo /etc/init.d/gdm stop
than try to do
startx
or dpkg-reconfigure xserver-xorg
or even try
sudo /etc/init.d/gdm start

try alt+F7.... and different numbers after

---

### Post by Milov on 2009-02-06
I thought no one was going to reply. Thank you for taking the time to reply.

I kind of have trouble believing that the problem is a missing driver since it was working fine before I logged out. Also doesn't seem like my install should be messed up since I didn't change anything.

Anyway, I tried what you said, but none of it worked.

I get off work right about now (I work at home, so the time doesn't matter so much...) so I'm going to boot it up again in a minute and try some things, and I'll put more detailed results of the commands here, so hopefully someone here can identify what's wrong.

---

### Post by Milov on 2009-02-06
Right now I'm using my other computer to use these forums so I can be on Ubuntu at the same time on my main computer

Starting off:

When I boot up, it gets to the graphical Ubuntu loading screen with the little orange bar. After it fills up all the way, the screen goes blank except for a little blinking text cursor in the top left. It stays like that for a few seconds and then outputs some stuff on my screen:

```

Boot from (hd1,4) ext3   c3257f74-458a-4dfc-aa2b-94500b84462a
Starting up ...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/cbbfaf64-dfae-4320-a25a-92a58a024
8d1
kinit: No resume image, doing normal boot...

Ubuntu 8.10 Zak-Ubuntu tty1

```

...and then the login prompt. I don't know if the "No resume image" means anything or if that is normal.

After typing in my log in details, and it displays Ubuntu's short disclaimer, I can then enter commands.

I type in

```

startx

```

and it starts with "X.Org X Server 1.5.2" followed by some info about the release and build, "Module Loader present", a description of different markers, and finally this:

```

(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  6 16:49:37 2009
(==) Using config file: "/etc/X11/xorg.conf"
Primary device is not PCI
(EE) No devices detected.

Fatal server error:
no screens found
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

And then I'm back at the prompt. That is all that startx ever does.

Now, if I try something else...

```

sudo /etc/init.d/gdm start

```

it says:

```

 * Starting GNOME Display Manager...          [ OK ]

```

Although, I'm pretty sure it was already started.

Another command that lots of people say to try is:

```

sudo dpkg-reconfigure xserver-xorg

```

which goes through a series of screens mostly asking about various keyboard options, after which it displays:

```

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090206171110

```

I've also read about a variation which is:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

This skips all of the screens asking for options, but it still ends in the same message.

The Ctrl+Alt+F7 or Alt+F7 always goes to a blank screen with a blinking text cursor, no matter what commands I have previously used. changing F7 to any of the other function keys, just switches between 6 tty screens, the F7 screen, a screen that appears to indicate the status of the non-existent battery, and another blank blinking cursor screen. F10+ don't do anything.

So those are the results of all of the ideas I've seen.

---

### Post by Milov on 2009-02-06
I'm getting impatient now. I've also noticed that a lot of people have had problems with nvidia drivers.

I'm kind of wondering about that.

When I'm in gnome, the screen tends to flicker on and off a lot, and also everything renders slow. I figured this was due to not having drivers for my video cards. So I went to install those infamous 177 nvidia drivers, but the download stayed frozen at 0%, and I eventually canceled it since it wasn't doing anything. I thought nothing changed, but maybe it did download something, and mess up the X config.

So, I'm going to try first reinstalling Ubuntu, and then do absolutely nothing and logout, to make sure I'm not insane. And if I can log back in without problems, then I'm going to download the new 180-something drivers form nvidias website, which hopefully aren't as crappy as the 177 version. I definitely need drivers because the screen-flickering is annoying as hell.

I'll post with my results soon.

---

### Post by carml on 2009-02-06
Just for your info,when your PC tells kinit no resume image,it's not a normal boot,did you try to boot in recovery mode and select fix x config or repair broken packages?It could help to solve the problem,because the first option will give a graphical and functional environment without special effects,the other one should reinstall any corrupted package if there are any.

---

### Post by Milov on 2009-02-06
I determined that logging out after a fresh install goes to the gnome login screen. After that I tried installing the nvidia 180.9 drivers from their website. The installation requires X to be stopped, and after they were installed, I couldn't start X back up.

startx said almost the same thing as usual except it didn't say "Primary device is not PCI" I think it said something else, but I didn't write it down. After that I tried sudo /etc/init.d/gdm start which said "starting gnome" as usual, then I tried startX again and it said another slightly different message but it was pretty much the same. It still said "no screens found".

I thought maybe it was as simple as fixing xorg.conf, but I replaced xorg.conf with all of the backups I had and none of them worked. All of them did the usual "Primary device is not PCI" and "no screens found". I even tried copying the xorg.conf off of the live CD filesystem, but that didn't work either.

As for the "no resume image", I watched the boot after the fresh install and it said "Boot from (hd1,4) ..." and "Starting up ..." and then gnome started, without any of those other messages being displayed. However, later when I went back to the tty to stop X for the driver installation, I noticed that the rest of those messages had appeared (probably in the background while gnome was loading). So that's off a completely new install.

I tried the recovery mode a few days ago when I first had this problem, but I reinstalled Ubuntu between then and when I made this thread, and hadn't tried it again (I also think I didn't try the "fix X server" option, since I had no idea what X was at the time). So I tried it again just a few minutes ago. First choosing the "recover packages" option, and then the "fix X server" option. Then I chose to continue with normal booting, but nothing changed.

So.... now I think I'm going to reinstall again, seeing as I am clueless as to what to do. After installing I'm going to try shutting down X and immediately restarting it just to see if installing the nvidia drivers messed it up, or if it was just the fact that I stopped X that messed it up. If I can successfully restart X on a fresh install, then I'm going to try using those old nvidia 90 something drivers. Apparently people have had more luck with those, even though they are way out of date. I definitely need drivers though so that my screen stops flashing and firefox doesn't take years to scroll down the page, but I doubt I'll be installing any intense games that need up-to-date drivers, so I should be good if I can get the legacy drivers to work. ...If I can't restart X on a fresh install then that would puzzle me, because how does it start in the first place? Enough rambling... time to fix my computer... some more.

---

