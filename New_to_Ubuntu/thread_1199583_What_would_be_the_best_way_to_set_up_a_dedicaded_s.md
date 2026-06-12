---
title: "What would be the best way to set up a dedicaded server"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Mick8882003 on 2009-06-29
I am tempted to set up a dedicated server. What I would like to do is set up a comp next to my router and use that as a server/backup unit.

Is it possible to remote into the box, using my current comp (saving on a screen and keyboard.)

Is it possible to use a low power pc or something that wakes up automatically?

Just curious if this if feasible.

Mick

---

### Post by Paqman on 2009-06-29
> **Mick8882003 said:**
> 
Is it possible to remote into the box, using my current comp (saving on a screen and keyboard.)


Absolutely. In fact that's how most servers are run. You can SSH into the server from the command line on your current box. Servers are normally administered from a command line rather than a graphical environment, although some people like to install a desktop while they're finding their feet.

> 
Is it possible to use a low power pc or something that wakes up automatically?


Totally. All modern systems will automatically power down to a certain degree when not under load. If you want to take it a step further you can look into using Wake-on-Lan. I'd suggest using a low-power CPU like the AMD 4850e, which only sucks 45W, which is impressive for a 2.5GHz dual-core.

---

### Post by 3rdalbum on 2009-06-29
> **Mick8882003 said:**
> I am tempted to set up a dedicated server. What I would like to do is set up a comp next to my router and use that as a server/backup unit.

Is it possible to remote into the box, using my current comp (saving on a screen and keyboard.)

Is it possible to use a low power pc or something that wakes up automatically?

Just curious if this if feasible.

Mick

It's definitely possible, I do this.

There are basically two ways to control the remote machine from your computer:

1. SSH - allows you to access a terminal prompt that is running on the remote computer. From that terminal, you can run any command-line program, and if you run SSH with the -X flag you can run any graphical program too.

2. VNC - you can access the running desktop remotely.

The one drawback with VNC is that, of course, it requires X to be running on the server - and if you don't have a monitor plugged in on startup, X won't run! You can plug in a monitor, start up the computer, log in to the desktop, and then unplug the monitor and X will stay running.

I use a small-ish, low-power computer. I bought a Mini-ITX motherboard off eBay, with an Intel Atom CPU. The case I bought contains a 200 watt power supply. Pretty low-power, except I used a 3.5 inch hard disk rather than the more expensive yet more efficient 2.5 inch disks. For a file server and backups, you don't need a processor anywhere near as powerful as what Paqman suggested - an Atom or a Via Nano will work fine. If you want the machine to do more heavy lifting, like transcoding media files, then the AMD 4850 would be a good choice (you can get Mini-ITX motherboards based around the AM2+ socket).

Basically, you install Ubuntu on the server as usual, turn on Remote Desktop (if you want VNC access) or install openssh if you want SSH access. Tell Network Manager to use a static IP address on the local network - I use 192.168.0.12 for my server.

Now you can ssh into the server from your computer:

```
ssh 192.168.0.12 -X
```

This requires you to have the same username on the server as on your local computer; see the SSH manual if you want to use different usernames.

Or you can Remote Desktop in - I've got a feeling you need to log out of Gnome and log in again before Remote Desktop will work. Once that's done, open Applications > Internet > Remote Desktop Viewer on your computer and it should automatically detect your server and list it in the left pane. Double-click that and you'll be in.

From there, you can install Samba, Rsync, or whatever server software you want.

---

### Post by Paqman on 2009-06-29
> **3rdalbum said:**
> For a file server and backups, you don't need a processor anywhere near as powerful as what Paqman suggested - an Atom or a Via Nano will work fine.

Actually on a headless file server, that's completely true. My little raid/torrent box runs really well on an ARM processor at about 15-20W.

---

