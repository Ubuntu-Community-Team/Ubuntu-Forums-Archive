---
title: "TLSP 5 and login confusion."
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by mvip on 2007-08-26
This past weekend I've set up an LTSP environment that will be deployed at a company as soon as possible. The setup went fine, and I'm almost done. However, I'm confused over how the users are logged in. 
[LIST]
[*]When I login from one of the clients using the graphical interface (GDMish), I'm getting logged in to the main system, and not the chrooted environment.
[*] When I login using the console I do get logged in to the chrooted environment.
[/LIST]
My question regards what the proper LTSP5 setup should be, rather then to solve the problem. I do see benefits of using both chrooted users as well as local users, but I'm confused about how the proper setup is supposed to be. I thought this chroot environment was what distinguished LTSP <4 from 5.

If the users  are not supposed to be using the chrooted environment (and it's just used during the boot-up process), I don't see why OpenOffice, Gnome etc. are installed into the chrooted envirnment.

(The system runs 6.06.1 LTS Server and the LTSP setup is very similar to [this]("http://developer.novell.com/wiki/index.php/HOWTO:_Install_MueKow_on_Ubuntu") guide.)

---

### Post by jaspergreen on 2007-09-17
Hi Did you ever solve the problem I have the exact same confusion. The only thing I did that   made some sence was to chroot /opt/ltsp/i386 and installed gdm into that. It gace me a different login screen but I was not able to login as a ltsp user.

---

### Post by RudeIota on 2007-09-17
> **mvip said:**
> This past weekend I've set up an LTSP environment that will be deployed at a company as soon as possible. The setup went fine, and I'm almost done. However, I'm confused o systemver how the users are logged in. 
[LIST]
[*]When I login from one of the clients using the graphical interface (GDMish), I'm getting logged in to the main system, and not the chrooted environment.
[*] When I login using the console I do get logged in to the chrooted environment.
[/LIST]

I'm having the same issues, only with Fiesty (Xubuntu) and LTSP 5. I'm actually posting this from a client which is logged in under the main system, but not under the chrooted system it is *supposed *to be logged in under.
[LIST]
[*]Installed ltsp-server-standalone
[*]Used ltsp-build-client to build the client environment under /opt/ltsp/i386
[*]Configured my dhcpd.conf to get clients booting
[*]On the server, I did: chroot /opt/ltsp/i386 and adduser test.
[*]Client boots with a 'Xubuntu' splash screen
[*]Upon successful OS loading, a Ubuntu login screen appears
[*]When I tried logging in using 'test', it did not work
[*]When I adduser test to the main system (not using chroot /opt/ltsp/i386), I was able to login... to the main system, of course! I was surprised. :)[/list]
I'm going to continue my investigation, but I cannot see why this is happening at the moment. I'm quite a linux scrub though, so maybe someone can shed some light on this issue.

---

### Post by RudeIota on 2007-09-18
After a night to investigate, I have found no solution. I'm beginning to wonder if this is by design (I find it hard to believe because the /opt/ltsp/i386 directory is so complete, with office.org, firefox etc..). 

As the post above, I've attempted to chroot /opt/ltsp/i386 and aptitude install ubuntu-desktop, but that doesn't seem to work. I've tried ltsp-build-client using a live Edubuntu CD and mounting /ltsp/opt/i386 as an NFS drive from another PC with simliar results. Using this technique, I will see the Ubuntu splash logo instead of Kubuntu and get an Edubuntu login screen. When logging in through, it goes back to Kubuntu and logs in under my server's root file system.

Another thought I had is maybe the /opt/ltsp directory contains applications, settings and the initial boot environment etc.. for clients, but somehow clients are supposed to use the main system to run? This sounds very 'dumb' though both from a practical and security stand point.

In my opinion, ltsp-build-client's $ROOT should be equal to /opt/ltsp/$ARCH. But I don't know enough about LTSP & linux to figure out if this is a configuration error, bug or by design. During client boot, the 'root file system is /root. This is supposed to switch over to / via initramfs. I REALLY think / should be relative to the /opt/ltsp/$ARCH directory and NOT the actual / partition. Is this wrong of me to think?

---

### Post by RudeIota on 2007-09-18
After much self-doubting, I believe I can confirm this is NOT by design. **This is a bug or configuration error**... Check it out: > _The root file system mounted by the thin client is not the same root file system the server itself uses_, but is specially prepared for thin clients, and is shared by all thin clients connected to the server (located in /opt/ltsp/<arch> on the server) . [https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)
[SIZE="3"]Now... does anyone know why our clients are sharing the server's root file system?[/SIZE]:confused:

---

### Post by RudeIota on 2007-09-19
The ltsp-discuss mailing list has shared that this **is** by design, so I'll let this topic rest. Here's the reply I received.

> 
LTSP provides a terminal to get you logged into a server.

Once logged in, your session is running ON THE SERVER. It's no surprise
that if you start snooping around the filesystem, it looks just like the
servers filesystem. that's because IT IS the servers filesystem.

the stuff in /opt/ltsp/$ARCH is just what is needed by the thin client
to get booted up and launch an Xserver. From that point on, all
processing takes place on the server.

installing ubuntu-desktop or anything else in the chroot isn't gonna
magically make it run there.

We are working on the ability to run arbitrary applications on the thin
client, but that's a big issue, because we have to deal with things like:

a) How to get the app launched on the client, when you are logged into
the server.

b) How to make the users home directory available to the thin client
when it exists on the server

c) How to deal with multiple architectures. some apps should run
localy on some clients, but not all apps and not all clients.

I hope that helps,

Jim McQuillan

---

### Post by mredmond on 2007-10-29
I am actually looking for a method to use LTSP to build thin clients that depend less on the server for the local interface. The goal is to use modern, low-energy-use thin clients with large memory (1G to 2G) to run a local diskless image, essentially as a kiosk. From there, to use ssh X sessions and gftp/sftp for access to user selected remote servers for applications and to transfer files to/from local thin-client storage (USB and CD/DVD). I want the load on the thin-client server to be minimal, consisting mainly of the initial transfer of the image to the memory/large RAMDISK of the thin client. 

It appears that the LTSP kiosk option can provide this to a limited extent. In this example, firefox is installed and executed as chroot on the thin client:

[https://wiki.edubuntu.org/HowtoWriteLTSP5Plugins](https://wiki.edubuntu.org/HowtoWriteLTSP5Plugins)

It also seemed to be the case when I installed gdm on feisty where I could open my own X session on the thin client (though this did not fix the problem of access to the thin-client USB and CD-ROM drives):

[https://help.ubuntu.com/community/Updated_Version_For_Feisty](https://help.ubuntu.com/community/Updated_Version_For_Feisty)

There is also someone that put this together some time ago without using LTSP:

[http://www.dnalounge.com/backstage/src/kiosk/](http://www.dnalounge.com/backstage/src/kiosk/)

It seems that the kiosk and local gdm options no longer work under gutsy. When I use the above method to install gdm, the thin client continues to insist on starting with ldm. For the kiosk option, I found a few threads talking about the problem, though I haven't tried the kiosk install myself:

[https://lists.ubuntu.com/archives/edubuntu-users/2007-July/001411.html](https://lists.ubuntu.com/archives/edubuntu-users/2007-July/001411.html)

So I am looking for reasons why these options aren't working on gutsy. Something has changed and so far I haven't had enough time to find out what. 

I am also looking for a general discussion of large-memory, stand-alone thin clients I will likely open this as a new topic soon, but I thought I would start in this thread to see if it is the right place to check.

---

