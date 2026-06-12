---
title: "Access Ubuntu from Windows..."
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by hellmet on 2006-09-08
In the second series of my questions..

How do I control(VNC..) Ubuntu from my XP machine..
I have another thread..."Access Windows from Ubuntu"
which was solved..I posted it for a purpose..

I post this thread out of curiosity...

I wanto access Ubuntu completely..not only CLI..
thru LAN on my Mom's system...

I tried TightVNC...but somehow..I cud see
only the Terminal that was open here..
Nothing else..I don't need security..so ssh not needed..

many thanks..
-hellmet

---

### Post by tbonius on 2006-09-08
I assumne you want your Gnome desktop when you connect with VNC..

this is pretty simple.

Install tightvncserver on your Ubuntu computer.  Got to your ~/.vnc directory and edit the xstartup file.

It might have entries like the following:

```
xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
```

Simply comment these out and put in:

```
gnome-session
```

Now start the tightvnc server

```
user@host# tightvncserver
New 'X' desktop is host:1

```

And connect with a tightvnc client from your Windows computer by using the IP address and session ID

192.168.0.5:1

Or whatever the IP address and session number is

You should be good to go

T

---

### Post by hellmet on 2006-09-08
hmm...same problem....I can only see a terminal when it is open here..
i can't see any other thing..like the GUI..etc

---

### Post by tbonius on 2006-09-08
Do you even get a Window Manager?  Is it an xterm within a Window?  Try to startx

user@host# startx

T

---

### Post by hellmet on 2006-09-10
tiz working fine now
thnks man

---

