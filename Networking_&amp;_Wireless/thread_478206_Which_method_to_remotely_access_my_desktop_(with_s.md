---
title: "Which method to remotely access my desktop (with sound)?"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by SoulinEther on 2007-06-19
I've been thinking about setting up a thin-client (fat-client maybe? can the video processing be done client side?) to connect to my computer here upstairs from my home theater system in the main room.

Basically, my goals are to:

-Be able to fully control my computer.
-Be able to watch a movie or other video content at full resolution.
-Not change my LAN setup (max speed is 54 Mbps...well, this could be up'd, router and all)
-Be secure (SSH?)
-Be able to hear sound on the speakers attached to the client, and NOT on my computer upstairs.

I've looked into VNC, but that won't do sound, would it? What about doing something with X11? Remote X login? XDMCP?

A point in the right direction or an explanation would be greatly appreciated. Thanks!

---

### Post by Toet on 2007-06-19
I had a server/thin client setup using LTSP. Worked great. It is a real thin client. Sound should be possible via pulse audio drivers. Didn't have that at that time, was Edgy. Now it should be in there.

Could play movies. But mind you that the video driver on the thin client is vesa, at least that's what I had, so quality wasn't that great. Furthermore, the TV-out on the client couldn't be used.

The network connection was used 14Mbit max. 

There are solutions where you port your audio signal via the powerplugs through the house.

---

### Post by SoulinEther on 2007-06-19
Thanks for your reply.

I'll look into it. My thin client won't be THAT thin honestly.. it'll probably run a decent graphics card... or so I think.

The TV has VGA input, so video out will not be a problem.

---

### Post by EndPerform on 2007-06-19
Sounds like you want to rig up your 'thin client' as a home theatre-type machine and play media found on your desktop..  Why not share out the media from your desktop and just play it that way?  I do something similar:

File server has the following shares:
/music
/video

"Thin Client"
Mounts the shares, then plays them locally.

As far as security goes, you can lock down Samba with usernames / passwords.  Just another thought.

---

### Post by SoulinEther on 2007-06-19
> **EndPerform said:**
> Sounds like you want to rig up your 'thin client' as a home theatre-type machine and play media found on your desktop..  Why not share out the media from your desktop and just play it that way?  I do something similar:

File server has the following shares:
/music
/video

"Thin Client"
Mounts the shares, then plays them locally.

As far as security goes, you can lock down Samba with usernames / passwords.  Just another thought.
I was considering that method... but that won't give me control over my computer.

That could be one method though, since I'm not entirely limited to any one method, heh.

Thanks.

---

### Post by EndPerform on 2007-06-20
> **SoulinEther said:**
> I was considering that method... but that won't give me control over my computer.

That could be one method though, since I'm not entirely limited to any one method, heh.

Thanks.

This is true.  Just out of curiousity, what exactly do you want to control on your box?   I find SSH / Samba gives me just about anything I need.  You can do X forwarding via SSH and run programs from your desktop and have them display on the laptop.  I do that at work.  I'll SSH into my laptop from my work machine in case I need something.

---

### Post by Soarer on 2007-06-20
For complete control, I haven't found anything as good as NX from [NoMachine.]("http://NoMachine.com") There is a free version for home use, works great once set-up. Does Sound too...

For playing videos etc. you really need a client/server type configuration - as EndPerform says. I don't believe you will have enough bandwidth across the network to get quality video. Best to send or stream the file and do the video on the client.

---

### Post by Princey on 2007-06-20
> **Soarer said:**
> For complete control, I haven't found anything as good as NX from [NoMachine.]("http://NoMachine.com") There is a free version for home use, works great once set-up. Does Sound too...

For playing videos etc. you really need a client/server type configuration - as EndPerform says. I don't believe you will have enough bandwidth across the network to get quality video. Best to send or stream the file and do the video on the client.

I headed over to the NoMachine NX website as I'm too interested in accessing my computer remotely with full control. However, when I click on the Linux Free edition, it says i386 and AMD 64 but the tar and .deb file says i386. Which should I go with? I run AMD 64 Feisty.

---

### Post by timcredible on 2007-06-20
i use pxes for this, but it's a really, really, thin client (CD boot is all you need, and it runs xdmcp, citrix, rdp, and a couple others).  you'll want to use xdmcp for linux, rdp is windows.  you also need to enable xdmcp access from your server via System -> Administration -> Security -> uncheck 'Deny TCP connections to Xserver' and reboot.

---

### Post by Soarer on 2007-06-20
> **Princey said:**
> I headed over to the NoMachine NX website as I'm too interested in accessing my computer remotely with full control. However, when I click on the Linux Free edition, it says i386 and AMD 64 but the tar and .deb file says i386. Which should I go with? I run AMD 64 Feisty.

I used the .deb files, but am on a 32 bit machine. I expect the 'NX Free Edition DEB for Linux' would work for you too :)

---

### Post by Princey on 2007-06-20
> **Soarer said:**
> I used the .deb files, but am on a 32 bit machine. I expect the 'NX Free Edition DEB for Linux' would work for you too :)

Thanks I'll give it a try. By the way, is there a means of accessing your Linux machine without installing anything on the client computer? I'd prefer NOT installing anything on the computer at work seeing I work for a government agency, something close to what RMA does by simply using a browser?

---

### Post by jaspergreen on 2008-02-26
Hi I am trying to enable sound on a thin client using pulseaudio. The Problem I have is that when I run this command:

$ sudo chroot /opt/ltsp/i386/ apt-get install pulseaudio pulseaudio-esound-compat \
                                              pulseaudio-module-x11

I get this error message:
id: cannot find name for group ID 126
The Group that the  group Id belong to is fuse.
 Anybody have an idea?

---

### Post by A$h X on 2008-03-25
> **Princey said:**
> Thanks I'll give it a try. By the way, is there a means of accessing your Linux machine without installing anything on the client computer? I'd prefer NOT installing anything on the computer at work seeing I work for a government agency, something close to what RMA does by simply using a browser?

I doubt it bro, you need to have two apps that can talk to each other, so unless your work computer has remote access software already installed, then you need to get something like nomachine on there. BTW I know it's over a year old, but I'm just getting into virtualization myself so I'm trawling the forums for info on nomachine.

---

### Post by Princey on 2008-03-31
I realise that. I'm in the process of setting up NOMACHINE during the course of this week as there's now a native x86_64 version. I'll just have to figure a way of installing the client on my usb flash drive and run it that way.

---

