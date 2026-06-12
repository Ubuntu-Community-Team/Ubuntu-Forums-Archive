---
title: "[SOLVED] video over lan and how to setup lan?"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by secondstage on 2008-03-10
two questions

1. How to setup a lan?

2. Can I have the video that would usually go to a monitor go through the lan cable and be shown in a window on another computer?

Both computers will be running Gutsy, and one has scecs below, the other is an old AMD Duron. The reason for the second question is because I have limited desk space and the only place I could put a second moniter is on the floor :( .

ps Thanks in advance!

---

### Post by secondstage on 2008-03-10
*bump*

---

### Post by lespaul_rentals on 2008-03-10
A LAN is simply an interconnected network of computers and networking devices.  You can link your computers together in all sorts of ways, but probably the most common service for what you want to do would be Samba.

And yes, you can do that.  If you have a video of some sort on your server, you can connect using Samba and stream the video from the server just like you had it on your local hard drive.

Main computer sends request --> server --> "Please send me this video"

Server replies --> main computer --> "Here you go"

The main computer then plays the video using your favorite media player, say VLC Player.  The video still resides on the server, but the main computer is pulling the data from the server as the video plays.

---

### Post by secondstage on 2008-03-10
And what could i use to capture the _screen_video from the server?

The video isn't a file but rather it is a continuous screenshot of the server, because Istill want to be able to navigate the server as if it a regular computer.

---

### Post by lespaul_rentals on 2008-03-11
Oh, I get you now!  You want to have a GUI of the server, like remote desktop.  Use VNC.

---

