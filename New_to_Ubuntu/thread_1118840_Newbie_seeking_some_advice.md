---
title: "Newbie seeking some advice"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Paidhima on 2009-04-07
I've been playing with Ubuntu on and off since the release of 5.10, but this past weekend I finally made the jump to a permanent Ubuntu solution w/ 8.10.  It's running on a headless machine that I want to use for several purposes:

1.  NUT or apcupsd.  Specifically, I need the ability to remotely shut down a number of Windows machines (XP, Vista, Server 2k3 and 2k8) after a power failure without having to resort to pricey network interfaces for UPS units or a UPS for each machine.  The Linux machine will be on either a Cyberpower 425 USB or APC Back-UPS ES 550 USB.  I've had no end of trouble getting UPS support.  Does anyone that has gotten this working have any tips?  My #1 requirement, as I mentioned, is remote shutdown of Windows machines on the network.

2.  Torrents.  I need bandwidth scheduling, folder scanning, UPnP and a solid web interface.  uTorrent runs almost perfectly in Wine, but I'd like a native solution.  KTorrent seems to be the best option, but it's a KDE app.  Right now I've got my machine configured headless w/ CLI at boot and VNC server running for management (gives me GDM when I remote in).  Can I install KDE and still remain headless?

3.  FTP server.  I'd prefer something with a GUI, just for ease of use, but my main requirements are granular control over user access per folder and the ability to use mounted network volumes.  I've got Pure FTP installed right now with Pure Admin.  It's great, but doesn't provide granular support for folder permission.  If I need greater control, is my only option something like ProFTP/CLI solution?

4.  Switching gears a bit, how does the desktop distro differ from server?  Specifically, could I use the server distro but install KDE over it for KTorrent while keeping it headless?  I would love to integrate this system with AD in my home network, but my attempt (using likewise-open) on 8.10 desktop got borked so bad I had to reinstall the OS and it seems like I may have a better time of it with server.

Sorry for the rapid fire questions, but four days of serious tinkering have left me with more ideas than I have knowledge of implementing them.

---

### Post by simtaalo on 2009-04-07
> **Paidhima said:**
>  KTorrent seems to be the best option, but it's a KDE app

i use Ktorrent in gnome without any problem, in fact i use a few different kde apps inside gnome and never had any issues.

---

### Post by BDNiner on 2009-04-07
By headless do you mean that there is no monitor or you are not going to install a desktop environment. You can install gnome and kde and not connect a monitor and still VNC to the machine.

You can install KDE on the server distro
```

sudo apt-get install kubuntu-desktop

```

but that would install all the desktop applications that come with kubuntu that you may not want.

---

### Post by kanikilu on 2009-04-07
For remote shutdown, check out this thread for some suggestions (I haven't tested it, but the last one suggested looks pretty straight forward):

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/60324-remote-shutdown-windows-linux-box.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/60324-remote-shutdown-windows-linux-box.html)

For torrents, check out rtorrent in the repositories. Again, I haven't used it, but here's a tutorial:

[http://polishlinux.org/apps/p2p/rtorrent-console-p2p/](http://polishlinux.org/apps/p2p/rtorrent-console-p2p/)

I haven't setup an FTP server in over 5 years since moving to SSH, so can't really help there. Can you not use SSH and just connect from your Windows clients using a GUI like WinSCP? I'm not sure exactly what you are trying to accomplish with the FTP server, so I can't say for sure that will work, but it's something to consider...

---

### Post by Paidhima on 2009-04-07
Wow, thanks for the replies!

> By headless do you mean that there is no monitor or you are not going to install a desktop environment. You can install gnome and kde and not connect a monitor and still VNC to the machine.

Sorry, by headless I mean no monitor.  With gnome, booting to GDM with no monitor gave me that "low graphics" issue where it wouldn't continue to boot without one plugged in.  I could always make a monitor loopback, but I'd prefer to just do it straight.

> You can install KDE on the server distro but that would install all the desktop applications that come with kubuntu that you may not want. 

Exactly - I was trying to avoid adding more than I need in terms of applications.  I may still mess around with it, though.

> i use Ktorrent in gnome without any problem, in fact i use a few different kde apps inside gnome and never had any issues. 

Well, now I know what I'm doing when I get some spare time to remote into my home network.

> I haven't setup an FTP server in over 5 years since moving to SSH, so can't really help there. Can you not use SSH and just connect from your Windows clients using a GUI like WinSCP? I'm not sure exactly what you are trying to accomplish with the FTP server, so I can't say for sure that will work, but it's something to consider...

I should have been more clear, sorry.  I frequently need access to some of the files on my home server (software tools, etc).  I previously had Filezilla server set up on my file server so I could jump in and grab what I need.  I also allow a few other people (friends and colleagues) to get in and grab files they may need.  I was able, in Filezilla, to restrict access the way you might with regular ntfs user and group file permissions.  I'd like to keep my file server a bit less exposed, so I want to move the FTP server onto Linux - preferably without giving up the level of control Filezilla gave me.

---

### Post by kanikilu on 2009-04-07
For FTP, have you already checked out the relevant section of the server guide?

[https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html)

Sorry I don't have more specific advice...it's been way too long since I've set FTP up, that I'm pretty much useless on the topic. 8-[

---

### Post by batharoy on 2009-04-07
Filezilla is in the repos, I can't remember which one though.
EDIT: Universe ropo

---

### Post by Paidhima on 2009-04-07
Thanks for the suggestion.  I actually did read that a few days ago, but looking at it again now gives me a few more ideas.

---

### Post by BDNiner on 2009-04-07
You could download the source code for KDE and complie it depending on how much control you want over the application that are installed.

---

### Post by Paidhima on 2009-04-07
> **batharoy said:**
> Filezilla is in the repos, I can't remember which one though.

The client, or server?  I've got the client installed, but so far as I've seen they've never released an updated server.  There's been talk of one for a while, but I was under the impression it won't make an appearance until the author completely rewrites the server code.  I'll have to check some repositories, though.

---

### Post by Paidhima on 2009-04-07
> **BDNiner said:**
> You could download the source code for KDE and complie it depending on how much control you want over the application that are installed.

Man, my list of "Ubuntu Things to Do" just keeps getting longer.  It's a bit daunting, but so far I'm quite enjoying the experience.  It's a nice change of pace as well, seeing as how my day is generally spent supporting Windows networks.

---

### Post by BDNiner on 2009-04-07
> **Paidhima said:**
> Man, my list of "Ubuntu Things to Do" just keeps getting longer.  It's a bit daunting, but so far I'm quite enjoying the experience.  It's a nice change of pace as well, seeing as how my day is generally spent supporting Windows networks.

I completely agree, I have been meaning to for about 6 months to compile XFCE for an older laptop that i have but have not gotten around to it yet. still working on that home server!!
:lolflag:

---

