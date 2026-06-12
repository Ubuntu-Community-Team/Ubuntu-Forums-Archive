---
title: "working on making a home server"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by systemchris on 2010-06-01
hi there, i've posted before

anyway i'm trying to work how to approach my current home project

what i'm aiming to do is replace my NAS with a small computer i've put together so i can run torrents overnight, and use it an always on file server + network printer with my family's old yet trusty hp laserjet 4 plus which is almost certain to work with CUPS :)

my considerations are:
trying to decide between ubuntu server or desktop as starter, i'm thinking server
keeping it headless so SSH for CL or remote desktop/vnc
not fussy with usernames for file access
the other computers are using windows 7 (mine and my mums) - i downgraded the security policy to work with our old nas which was on an old version samba

i'm thinking for approach
- install the OS
- set up network address as i prefer static + openSSH so i can get command line access from my comfy chair
- install printer locally on it
- sort out file sharing with samba and add printer to samba share list
- add torrent software, probably set to download to shared folder, and see if i can webmin access to it, i heard torrentflux has this function

would this work? and what version would you recommend, the server mode with SSH already on or desktop version and go from there?

---

### Post by HereInOz on 2010-06-01
If you want to use Remote Desktop/VNC, you are going to have to use the desktop version.  Server with CLI only will provide SSH access but not VNC.

This is no great problem.  Just install the Desktop version then OpenSSH, Samba, System-Config-Samba (if you have a desktop you may as well use it).

Set your address static as you have said.

---

### Post by dustinmarlowe56 on 2010-06-01
I do something very similar to this, especially where the remote desktop is concerned. 

what i do is just log in with as an xterm session, connect to the internet and launch a vnc virtual desktop and then leave it alone. from there I control all of the torrents and such using the virtual desktops that i can view using vnc viewers. which when you log in you will get just a command line, but you can switch into graphical mode by running the command sudo start'GUIname' (sudo startxfce4 for me). this gives you the ability to run things with just the simplicity of the command line or being able to switch into a graphical environment

---

### Post by durand on 2010-06-01
For a torrent downloader, I strongly recommend deluge. It has a really neat WebUI but the client program can also be daemonised and you can connect to a daemon from anywhere on the network, including windows computers.

---

### Post by Jeroensum on 2010-06-01
There is no need to install vnc for remote desktopping, heck I would even reccomend you do not use vnc at all. It's had more leaks than BP :P

To get on with being helpfull here, I would reccomend you install ssh and freenx on top of that. It's lighter, tighter and works a lot faster than vnc and the big plus is that you don't need a graphical environment to run it! :) I've been using it for years now and loving it.

---

### Post by tom.swartz07 on 2010-06-01
> **Jeroensum said:**
> There is no need to install vnc for remote desktopping, heck I would even reccomend you do not use vnc at all. It's had more leaks than BP :P


HAHAHAHAHAHA!!!!!!


anyway, I havent had any problems with the standard torrent program for Ubuntu, Transmission. It too has a web interface, so you could log in and view it on the network anytime from any browser or OS.

Jeroensum has a good point, VNC is EXTREMELY laggy and slow. Many times you could get done what you want through command line SSH before you could even load up the desktop with VNC.

---

### Post by aeiah on 2010-06-01
rutorrent, a web frontend for rtorrent, is used a lot on seedboxes and such. that is another to consider.. i think the interface for rutorrent mimics utorrent (but on a web page)

but yea.. just install ubuntu server with ssh, samba etc. there's no reason to install a gui because you aren't going to be using gui programs to do any of the configuration anyway

---

### Post by systemchris on 2010-06-03
wow so many start points and stuff :) definetly a case of finding what works for me:

i can put the printer work on hold thankfully as the printer appears to be permenently jammed now so it's on it's last rusty legs lol

so far i've instaled the server version of 10.04 with ssh, samba and cups server, didn't do lamp but from looking on net it looks like i might need to? any truth to this?

i'm able to get CLI access from my windows comp now so i can work on it whilst listening to music :)

---

### Post by bodhi.zazen on 2010-06-03
> **systemchris said:**
> hi there, i've posted before

anyway i'm trying to work how to approach my current home project

what i'm aiming to do is replace my NAS with a small computer i've put together so i can run torrents overnight, and use it an always on file server + network printer with my family's old yet trusty hp laserjet 4 plus which is almost certain to work with CUPS :)

my considerations are:
trying to decide between ubuntu server or desktop as starter, i'm thinking server
keeping it headless so SSH for CL or remote desktop/vnc
not fussy with usernames for file access
the other computers are using windows 7 (mine and my mums) - i downgraded the security policy to work with our old nas which was on an old version samba

i'm thinking for approach
- install the OS
- set up network address as i prefer static + openSSH so i can get command line access from my comfy chair
- install printer locally on it
- sort out file sharing with samba and add printer to samba share list
- add torrent software, probably set to download to shared folder, and see if i can webmin access to it, i heard torrentflux has this function

would this work? and what version would you recommend, the server mode with SSH already on or desktop version and go from there?

I suggest server edition , you can ssh + X.

For torrents I would use rtorrent, but transmission has a web interface as well.

For file sharing , if you have all Linux clients, I would use NFS rather then samba.

Take a look at autofs, can be used with either samba or nfs. With autofs remote file systems are automatically mounted as needed, so it is invisible to your users and reduces the load on your server.

---

