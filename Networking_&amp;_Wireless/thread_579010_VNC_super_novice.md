---
title: "VNC super novice"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by realillusions on 2007-10-17
I have some good news and some bad news.

Good news: I've convinced my girl that she should use Linux, and I'm going to start her with Ubuntu just so we're both in the same boat.

Bad news: She's not the most tech savvy lass out there, and I'm three hours away from her.

In light of this, I figured VNC would be a good way for me to be able to access her machine and help her figure things out if she has a panic attack, or her machine does something weird. Unfortunately, I have no idea how to go about accessing her machine.

Once I get VNC installed on both boxes, where do I go from there? I thought at first it would be fairly simple, but we're both on university dormitory connections, ie: behind routers. What information do I need to get in order to access her machine, and how do I get it.

I'm completely new to the world of VNC and remote connections like this, despite all the time I've been using computers, so I have absolutely no idea where to begin. Step-by-step instructions are preferred!

Thanks in advance!

---

### Post by eldragon on 2007-10-17
if you are comfortable with the CLI, then i would setup a SSH server on her pc, that will give you complete access to her box even if Xorg fails. thats what ive done with a friend on the other side of South america. works like a charm.

to set up vnc...... i would use x11vnc, since ive had problems with the vnc server that comes with Ubuntu.
```
 $ sudo apt-get install x11vnc 
```

then i would set a password somewhere noone can touch it and allow everyone to read the encrypted file
```
 $ sudo vncpasswd /root/.vnc/vncpassword 
$ sudo chmod a+r /root/.vnc/vncpassword 
```


then create a script that will run the server everytime your gf logs into her X session
```

#!/bin/bash
x11vnc -display :0 -shared -forever -rfbauth /root/.vnc/vncpassword

```
save that file to /usr/bin/startvnc

and set its execute flag
```
 $ sudo chmod a+x /usr/bin/startvnc
```
then create the gnome entry to autostart it
```

$gedit ~/.config/autostart/startvnc.desktop

```
and fill it with
```

[Desktop Entry]
Name=No name
Encoding=UTF-8
Version=1.0
Name[en_US]=vnc server
Exec=/usr/bin/startvnc
X-GNOME-Autostart-enabled=true

```


the next time she logs into her account, she should have the server up and running.

remember to open port 5900 at her router (if she has one). otherwise this wont work.



cheers

---

### Post by realillusions on 2007-10-17
She doesn't have a router for her room, but I believe the whole building and/or floor runs off of a router (logically). How can I have her check to see if that port is open? And if it's not (which I assume will be the case), is there a neat trick to open it from her computer for just her, or will we have to talk to the campus' IT folks?


Also, could you inform me on SSH? I didn't find anything on the web that really helped out. I just opted for VNC for the graphical aspect, so she could see what I was doing. SSH would make "quick fixing" really easy, but I still don't know how I'd actually get to her computer through the router. That's really my big question in all of this.

---

### Post by Synflux on 2007-10-18
Hi,

I think what you're going to need is something that makes active outgoing connections from her computer, this will get round the need for port forwards and avoid SPI firewalls. Something like [[color=red]Hamachi[/color] ]("https://secure.logmein.com/products/hamachi/list.asp"),which is a bit of software that creates a vpn by using proxy servers, _might_ do what you need.  There is also a linux forum for it with install instructions.

Once you have it up and running you should be able to run vnc/ssh/freeNX over it as normal.  I'm sure there are other options that will do the same job but that's one I know of.

Unfortunately I've not used it on Linux myself so can't really help with the install/configuration of it :(

Hope it's a usefull suggestion though. :)

---

### Post by krunge on 2007-10-18
> **realillusions said:**
> 
Also, could you inform me on SSH? I didn't find anything on the web that really helped out. I just opted for VNC for the graphical aspect, so she could see what I was doing. SSH would make "quick fixing" really easy, but I still don't know how I'd actually get to her computer through the router. That's really my big question in all of this.

You might want to have a look at  x11vnc's simple attempt at emulating UltraVNC (windows) "Single Click" connections for naive users. [http://www.karlrunge.com/x11vnc/#faq-singleclick]("http://www.karlrunge.com/x11vnc/#faq-singleclick")

The basic idea is the naive user's x11vnc initiates a reverse connection (-connect or -connect_or_exit option) to your vncviewer running in "listening mode".  That way the naive user's router/NAT doesn't matter.  The "Single Click" aspect  simply involves a wrapper for this to make it easier for the user. The above link also shows how to encrypt this reverse connection via SSL (headsup: the ubuntu x11vnc is way too old to do that).

You could rig up a similar encrypted tunnel via SSH ([http://www.karlrunge.com/x11vnc/#tunnelling]("http://www.karlrunge.com/x11vnc/#tunnelling")) but, again, she would have to initiate the ssh from her machine to yours. E.g.
```
ssh -R 5900:localhost:5900 herusername@your.ip.address
```
Then in another terminal window she types "x11vnc" and then you type "vncviewer :0" (or "vncviewer localhost:0")

BTW, in all of the above I assume you are not NAT'd by a router/firewall or you know how to redirect ports from it to your PC.

If you have any questions just ask.

---

### Post by eldragon on 2007-10-18
what i said to set her vnc server + what krunge said to set the tunnel, will bypass her internet nat / firewall, etcetera. but some extra effort from you is required.

you have to install in your pc a ssh daemon.
```
 $sudo apt-get install openssh-server 
```

then you will need to open your 22 port on your nat / router + firewall (if you have any of those)

and third. you need to setup a nonpriviledged account for your girlfriend to connect through.
```
 $sudo adduser girlfriends_account 
```

she should start the tunnel with
```
 $ ssh -R 5900:localhost:5900 -p 22 girlfriends_account@your.ip 
```

the first time, she runs, she will be asked for confirmation about adding your computer to her known hosts list.

just remember to use STRONG passwords, since, anyone scanning your network, and being able to get in, could make a mess. another good idea is to change the default port from 22 to something else (maybe 2222) that can be done editing /etc/ssh/sshd_config in your computer.

once this is done, the tunnel started from your g/f's end, you will connect to her box with the following command
```
 $ vncviewer localhost 
```

hope this helps a bit more.

---

