---
title: "How do I get Ubuntu to run in normal graphics mode without a monitor"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by diablo75 on 2009-06-08
I have a computer that I want to use as a server of sorts.  I have a monitor attached to it for the time being but this is going to be used as a stand alone PC with no keyboard, mouse or monitor attached.  It's sole purpose is to sit there and await VNC remote desktop session requests.

Now, anytime I restart and disconnect the monitor, it appears to boot but I couldn't VNC into it.  Plugging the monitor back in, I get this stupid "Ubuntu wants to boot into safe graphics mode" because, apparently, it doesn't want to screw up a monitor that's not even plugged in.

So how do I force Ubuntu to boot into a plain-jane 1024x768 resolution with no fuss during startup and no complaints about there being no monitor attached?

---

### Post by SteveDee on 2009-06-09
> **diablo75 said:**
> I have a computer that I want to use as a server of sorts.  I have a monitor attached to it for the time being but this is going to be used as a stand alone PC with no keyboard, mouse or monitor attached.  It's sole purpose is to sit there and await VNC remote desktop session requests.

Now, anytime I restart and disconnect the monitor, it appears to boot but I couldn't VNC into it.  Plugging the monitor back in, I get this stupid "Ubuntu wants to boot into safe graphics mode" because, apparently, it doesn't want to screw up a monitor that's not even plugged in.

So how do I force Ubuntu to boot into a plain-jane 1024x768 resolution with no fuss during startup and no complaints about there being no monitor attached?

Not sure why you are having a problem as I have a similar setup. But here are a couple of suggestions.

If its just the initial boot screen that is giving problems, run Startup Manager (System > Administration > Startup-Manager) and under "boot options" set resolution to 640 x 480, colour depth 8 bits. (if you don't have Startup Manager either install it, or work out how to edit /boot/grub/menu.lst manually).

If the problem is post login, turn off any fancy visual effects and set to a modest resolution via System > Preferences > Display.

I hope this helps.

---

### Post by diablo75 on 2009-06-09
640x480?  Seriously?  The calculator app can barely fit on the screen at that resolution, much less any window with an OK button at the bottom of it.  With no monitor attached to the computer, why does this resolution matter?  Why can't it at least be 1024x768 or higher?

And I had already disabled all desktop effects before removing the monitor the first time.

It's freaking out because there's no monitor attached.  Perhaps theres a way to trick it into thinking there IS one attached, or tell it to skip whatever step tells it to check and see what kind of monitor there is in the first place and setup some sort of static, manual resolution for it to use no matter what is or is not attached?

---

### Post by dileepm on 2009-06-09
I almost have same problem with 8.04 which gives 1024 x 768 while my laptop screen is capable of 1366 x 768 but this did not happen in 8.10 or 9.04. Well i could not figure out the issue but you may be helped with this, i hope [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

---

### Post by nothingspecial on 2009-06-09
Not sure why it`s not working for you `cause I`ve got the same thing going on just fine.

I must say though that I find remoting in rather slow and annoying.

Why not ssh in with -X. You can run anything then even nautilus you just don`t get a desktop.

---

### Post by SteveDee on 2009-06-09
> **diablo75 said:**
> 640x480?  Seriously?  The calculator app can barely fit on the screen at that resolution, much less any window with an OK button at the bottom of it.  With no monitor attached to the computer, why does this resolution matter?  Why can't it at least be 1024x768 or higher?

And I had already disabled all desktop effects before removing the monitor the first time.

It's freaking out because there's no monitor attached.  Perhaps theres a way to trick it into thinking there IS one attached, or tell it to skip whatever step tells it to check and see what kind of monitor there is in the first place and setup some sort of static, manual resolution for it to use no matter what is or is not attached?

I can only repeat the main points of my post which were:-
 - I'm doing what you are doing with no problems.
 - The 640x480 resolution is just the initial boot resolution, which is used before you get to your desktop, and before you get a chance to run Calculator.
 - The final display resolution can be set higher (like 1024x768).

Your post indicated that the system had not successfully booted as far as your desktop...sorry if I've read that wrong. In addition, I don't know why 'buntu cares about a monitor previously connected.

---

### Post by diablo75 on 2009-06-09
> **nothingspecial said:**
> Not sure why it`s not working for you `cause I`ve got the same thing going on just fine.

I must say though that I find remoting in rather slow and annoying.

Why not ssh in with -X. You can run anything then even nautilus you just don`t get a desktop.

Huh!  I WILL have to try this.  I've been wanting something that could do what vnc does and shave bandwidth for me.  What do you say the command for this is again?  ssh -X [email]user@ip.add.res[/email].s ?

---

### Post by Cypher on 2009-06-09
For a standalone machine that isn't going to have keyboard/mouse/video, the thing I do is to have it boot up directly to the command prompt (disable GDM/KDM) and then in your user account, create the following file in in ~/bin
```

DISPNUM=2

vncserver :$DISPNUM -name <optional name> -nevershared -geometry 1500x950 &

```

Make it executable with
```

chmod 755 ~/bin/xvnc

```

You will have to play with the geometry to get the size right, the size I use here works nicely on my 1680x1050 widescreen monitor. The VNC window's height fit nicely between the taskbar and the top and the width leaves a little for me to move it around..

Now install the VNC server with
```

sudo apt-get install vnc4server

```

Run the 'vncpasswd' command to create your password which will also create the ~/.vnc directory. If a file called 'xstartup' doesn't exist in that directory, create it and add
```

#!/bin/sh

xrdb $HOME/.Xresources

# For Gnome
gnome-session &
vncconfig -iconic &

# For KDE
# startkde &

```

Now, from your remote machine you will ssh to your Ubuntu machine and once logged into your user accout, execute "xvnc" and wait for VNC to tell you that :2 was created, you probably won't see a whole lot of information. Now unceremousinly close the SSH window (if you are using PuTTY or something).

With the VNC Viewer, hit up <machine IP>:2 and you will be asked for your password, enter it and you will now see the standard Gnome window in all it's glory. You can close VNCViewer and re-open it to continue using the session..

The steps here are what I used to get my newly updated Jaunty machine accessible to the my XP machine at work..

---

### Post by nothingspecial on 2009-06-10
> **diablo75 said:**
> Huh!  I WILL have to try this.  I've been wanting something that could do what vnc does and shave bandwidth for me.  What do you say the command for this is again?  ssh -X [email]user@ip.add.res[/email].s ?

Here`s how I do it. First install openssh-server on your headless machine.

Then ```
ssh -X -C -c blowfish user@ipadress
```

-X fowards X to let you run guis, watch vids etc on your remote machine.
-C compresses it and -c encrypts. blowfish is the sort of encryption.

Put an alias in your .bashrc `cause you don`t want to be typing that in every time mine goes.

```
alias server='ssh -X -C -c blowfish me@192.168.2.10'
```
So I just have to type server to login.
I mostly just use it as a media server, for torrents, big downloads, media converting and backing up so it frees up my other machines.

I find screen essential. Ssh in to your headless box then run screen. Start your process going (rtorrent, wget or ffmpeg usually for me) Then press Ctrl + A then Ctrl + D. This detaches your session allowing you to logout and turn your laptop off. When you want to check the progress ssh back in. Then type ```
screen -r
```This will then give you a list of detached processes. Then type ```
screen -r process_id_number
``` and you can see how your torrent (or whatever) is going.

I use mt-daap to share my music so that the whole family can play it using rhythmbox or banshee.

Have a look at rsync too for backing up stuff.

---

### Post by diablo75 on 2009-06-10
That's a lot to digest but I'm sure I'll have time to get around to trying it out in the near future.  Thank you very much for going through the trouble of typing all that up!

Anyway, as for the VNC thing, as nice as it would be for the system to be completely headless, I've decided to leave the monitor attached.  Not for simplicity in solving the problem at hand, but for convenience in the event there's a technical problem with the system down the road and I need a monitor attached to see what's wrong with it.  The purpose of the system is for me and one other friend of mine to access via VNC and use it to accept reverse-VNC connections from customers/clients of ours who we assist with computer problems by remote.  The computer is located in my house and I am going to be leaving the country soon so in the unlikely event there's a problem it will make troubleshooting (via a phone call to my girlfriend who is not very computer savvy) easier.

---

