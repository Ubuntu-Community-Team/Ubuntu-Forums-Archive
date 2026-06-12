---
title: "Remmina installation"
date: 2022-01-24
forum: Networking &amp; Wireless
---

### Post by jgw on 2022-01-24
I just installed Remmina.  I am not convinced I didn't screw up.  I now think that I don't really need Remmina on any drive but the one that I will use to access the other drives.  Before I goto the other drives to delete all Remmina stuff I thought I had better ask if I should.   Anyway, I got Remmina up and defined two other drives.  Remmina tells me that I can connect to those two drives.  It tells me its connecting and then goes to a black screen.  I started investigating that one and found a bunch of different answers but I am not sure what applies to what. 

The Remmina I install was version 1.4.2   I checked if that was current and found that there is a version of something like 1.7.2 out there.  I then figured that I should get a repository that would allow me to ujpdate the program but also read that would probably not be a good idea.  

Anyway, can anybody help me with this stuff or aim me in the right direction?

Thank you.....................

---

### Post by schragge on 2022-01-24
> **jgw said:**
> I checked if that was current and found that there is a version of something like 1.7.2 out there.
Where did you get that info from? As of now, the latest tag in [their Git repo]("https://gitlab.com/Remmina/Remmina/-/tags") is v1.4.23.
> **jgw said:**
> I should get a repository that would allow me to update the program
There are two PPAs with the latest Remmina: [ppa:remmina-ppa-team/remmina-next]("https://launchpad.net/~remmina-ppa-team/+archive/ubuntu/remmina-next") (currently at 1.4.23) and [ppa:remmina-ppa-team/remmina-next-daily]("https://launchpad.net/~remmina-ppa-team/+archive/ubuntu/remmina-next-daily") (daily snapshot).
> **jgw said:**
> I now think that I don't really need Remmina on any drive but the one that I will use to access the other drives.
Sorry? I always thought Remmina is used to access other *hosts.* What has it to do with drives?

BTW, what protocol are you using with Remmina. When I start it, it lets me select between RDP, VNC, SSH, and NX. OTOH, description of the package says
> Currently RDP, VNC, SPICE, WWW, NX, XDMCP, EXEC and SSH are supported.
This obviously depends on what Remmina plugins are installed
```
[COLOR=green]$[/COLOR] apt-cache pkgnames remmina-plugin[COLOR=green]
remmina-plugin-nx
remmina-plugin-exec
remmina-plugin-kwallet
remmina-plugin-xdmcp
remmina-plugin-spice
remmina-plugin-rdp
remmina-plugin-secret
remmina-plugin-vnc
remmina-plugin-www[/COLOR]
```

---

### Post by jgw on 2022-01-27
Thank you for the reply.

Its strange - I answered this a while ago and thought I would check and see if there were any other responses and found that it didn't take.  Will try again.

Where did you get that info from? As of now, the latest tag in their Git repo is v1.4.23.
I got it from my own head and you are right - sorry......

"BTW, what protocol are you using with Remmina. When I start it, it lets me select between RDP, VNC, SSH, and NX. OTOH, description of the package says"
I have no idea.  When I installed I used the suggestions.  in this case:  Remmina VNC plugin    I will run through the list and see what happens.

I think I am going to have to study up on plugins, obviously, I am clueless.......

thanks again!


This is a place.  There are others.  
people also ask:
What is the latest version of Remmina?
Remini Mod APK 1.7.5 (Unlimited Pro Cards, No Ads)
Name	Remini
Updated	Jan 3, 2022
Compatible with	Android 4.4+
Last version	1.7.5
Size	65.38 Mb

"There are two PPAs with the latest Remmina: ppa:remmina-ppa-team/remmina-next (currently at 1.4.23) and ppa:remmina-ppa-team/remmina-next-daily (daily snapshot)."
I installed using ppa - thank you..........

Sorry? I always thought Remmina is used to access other hosts. What has it to do with drives?
Absolutely nothing - I meant host.

BTW, what protocol are you using with Remmina. When I start it, it lets me select between RDP, VNC, SSH, and NX. OTOH, description of the package says
VNC

I do get connected - to a black screen but, still, it says its connected.

Doing something wrong.

---

### Post by schragge on 2022-01-27
> **jgw said:**
> 
What is the latest version of Remmina?
Remini Mod APK 1.7.5 (Unlimited Pro Cards, No Ads)
Name    Remini
Updated    Jan 3, 2022
Compatible with    Android 4.4+
Last version    1.7.5
Size    65.38 Mb
[Remini]("https://remini.ai") (AI photo enhancer) has nothing whatsoever to do with [Remmina]("https://remmina.org") (remote destop client).

---

### Post by jgw on 2022-01-27
thanks for the reply...........

I now realize that the version thing was just something to confuse me (easy thing sometimes) but I now know that I am using 1.4.23

Now I have to figure out what to do with the black screens.  I have two connections and they are both black.

---

### Post by schragge on 2022-01-27
Well, my setup is a CentOS 8 Stream computer running **Remmina** 1.4.11 and a Xubuntu 20.04 computer running **xrdp**+**xorgxrdp**, and I have no problems connecting from CentOS to Xubuntu via RDP protocol.

---

