---
title: "Problems trying to VNC from my Macbook to my Ubuntu HTPC"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by knidsrok on 2010-05-07
Hi all!

So I've been trying to figure out how to set this up using prior posts from this support forum, and others, but I'm having trouble trying to sort out the current info from the obsolete as well as their varying degrees of relevance to what I'm trying to do.

I'm hoping someone here can provide me with a little direction.

My setup:

I've built myself a nice little HTPC on which I'm running Ubuntu 10.04.  I would like to be able to operate it from my Snow-Leopard-running macbook over my local network, ideally in its own X session, so that I can do some tinkering and content-hunting from my laptop even while the HTPC is playing a movie on the TV I'm using as a display.

The default remote desktop program that comes packaged with Ubuntu doesn't work with the Nvidia drivers my graphics card uses unless I turn off all compiz desktop effects.  I've tried various ideas from other support threads, and the closet I've come to getting something working is the one from [here, which goes something like]("http://superuser.com/questions/32455/virtual-vnc-screen-workspace"):

>  
If say your computer name is comp-user-01. You can VNC into a different session by using: comp-user-01:1

I believe you can set how many simultaneous users within the VNC server settings.

Edit: You can replace the last 1 with the number of the session you want to log into.

You'll need an xstartup script in ~/.vnc/xstartup. It may already be there. If not, the standard one looks like:

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &
Now, uncomment the two lines starting with "# unset " and "# exec " (yeah-- those two just below the comment that says "Uncomment the following two lines for normal desktop"

That should give you your normal, Gnome desktop.

This seems close to working, as I can then VNC from my mac into its own X session on the Ubuntu machine, but there's a fair bit of pixel artifacting, which isn't itself a dealbreaker, but the VNC server then crashes after about 10 minutes, and after that, I start getting weird error messages when I try to open up the synaptic package manager about not being able to open my xauthor profile or something to that effect.  Also, if I open up a browser in the VNC session, I end up losing all of my extensions and bookmarks when I next open it in the native x session.

So, yeah, I'm open to a suggestions of alternate ways of going about this, and I'm not expecting a step-by-step walkthrough or anything, but I could really use someone to point me in the right direction, and help me figure out what I need to be educating myself about, and where I can find the right resource.

---

