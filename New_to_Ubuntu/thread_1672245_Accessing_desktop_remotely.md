---
title: "Accessing desktop remotely"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by boldhoof on 2011-01-20
Hi

Last post seems to have gone off the rails, and not kept the message. What is the easiest way to access the Xubuntu 10.10 desktop over a network from a win xp machine.

Thanks

---

### Post by Foxheadz on 2011-01-20
Using a VNC server/client would probably be the easiest way. just download a vnc client on your computer something like [vinagre]("http://projects.gnome.org/vinagre/")and then download a client on your windows computer like [tight vnc]("http://www.tightvnc.com/") then startup vinagre and it should give you an adress like 192.168.2.21 and insert that into tight vnc and bam your using two computers on one. theres also some vnc client apps for ipod touch so you can use your computer from your ipod if you have one.

---

### Post by gagnz on 2011-01-20
Hi
 
I have the same question as Foxhead.
but without using VNC client?
 
I had something already installed on my winXP PC. It involved using puTTY.. I think, but then going through another client (?) to enable graphical interface with my GUI Ubuntu machine.
I upgraded my winXP PC, and can't remember what that other client is, to re-install it...
I have installed puTTY and it works, but I would like to run the UBUNTU with a non commmand-based interface.
Is it possible?
 
thanks

---

### Post by howefield on 2011-01-20
I like VNC, but I also like Teamviewer (free for personal use)

---

### Post by CharlesA on 2011-01-20
You can forward X over SSH as well.

---

### Post by boldhoof on 2011-01-21
> **Foxheadz said:**
> Using a VNC server/client would probably be the easiest way. just download a vnc client on your computer something like [vinagre]("http://projects.gnome.org/vinagre/")and then download a client on your windows computer like [tight vnc]("http://www.tightvnc.com/") then startup vinagre and it should give you an adress like 192.168.2.21 and insert that into tight vnc and bam your using two computers on one. theres also some vnc client apps for ipod touch so you can use your computer from your ipod if you have one.

Many thanks, will try it out this weekend.

---

### Post by nhtrader on 2011-03-12
PC1 = Xubuntu 10.10 (32bit) (koshi/xfce 4.8.0) with vnc4server
PC2 = winXP (32bit) using tightVNC

I'm trying to do the same thing. I am trying to access my xubuntu 10.10 from my winXP laptop using VNC.

I have edited my /home/user/.vnc/xstartup file as follows:

enter terminal mode:
sudo pico /home/user/.vnc/xstartup <E>

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

#doesn't work:  exec xfce4-session &
#doesn't work:  export VNCSESSION=TRUE


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
#vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop$
#x-window-manager &

#doesn't work:  startxfce4 &
#unnecessary:  xfwm4 --display :1.0 &
#unnecessary:  xfce4-panel --display :1.0 &

#works indirectly:  xfdesktop --display :28.25 &

xfdesktop --display :1.0 &

#doesn't work:  xfce4-session &

---END OF FILE---

Then start VNC...
$ vnc4server :1 -geometry 1024x768 <E>


Then I use PC2 and run tightVNC and input 10.0.0.10:1 and password and I'm connected.

Note that I can use PC2 to connect to PC1, but I can only see an unused desktop. The desktop that appears on PC2 is not what I see when I look at PC1's monitor. My workspace on PC1 is has many open windows that don't appear in the window of PC2. 

How can I view my active workspace from PC1 on PC2?

---

