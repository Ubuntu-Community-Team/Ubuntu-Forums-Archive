---
title: "Is Ubuntu right for me, or should I go FreeNAS?"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by busydoingnothing on 2010-01-24
Greetings...I'm a newbie here, thought this would be the best place to start. I want to build a server that will act mainly as a NAS, but will provide additional functionality, and despite FreeNAS appearing to be very easy to set up and maintain, I don't know if it can do more than just the basic stuff, so I started to consider Ubuntu, and here I am.

The server hardware ain't too bad (Athlon 2400+ I believe, 512MB RAM, Adaptec 2610SA hardware RAID card for a RAID-5). I want to install it to a CF card on an IDE adapter (which is in transit from Hong Kong). My CF card is 256MB...I think I have a 512MB somewhere, but I have a feeling if I go with Ubuntu, I will need more space.

Here's a list of my must haves (=), definitely would like (+), and maybe would like (-). Would you guys recommend I go Ubuntu or FreeNAS based on these requirements? I'm very computer literate but I haven't messed with Linux in years (last time I sort of played around was when Gentoo was king; the last time before that, Red Hat was king). 

= NAS
= Backup (WinXP desktop, Mac OSX laptop; must be able to set user permissions on folders so only I can see my backed up files, etc.)
= Media serving (audio, video; iTunes, Winamp, XBOX 360, HTPC)
= Relatively simple administration interface
+ Torrent
+ Newsgroup binary downloads
+ Video conversion/encoding (automated)
+ DVD ripping
- PVR (I have an extra digital cable box and a couple tuners lying around; might get an HDHomeRun if I actually use this functionality)
- Web streaming for audio (might be nice to access my music from anywhere)
- Print server

---

### Post by pirateghost on 2010-01-24
> **busydoingnothing said:**
> Greetings...I'm a newbie here, thought this would be the best place to start. I want to build a server that will act mainly as a NAS, but will provide additional functionality, and despite FreeNAS appearing to be very easy to set up and maintain, I don't know if it can do more than just the basic stuff, so I started to consider Ubuntu, and here I am.

The server hardware ain't too bad (Athlon 2400+ I believe, 512MB RAM, Adaptec 2610SA hardware RAID card for a RAID-5). I want to install it to a CF card on an IDE adapter (which is in transit from Hong Kong). My CF card is 256MB...I think I have a 512MB somewhere, but I have a feeling if I go with Ubuntu, I will need more space.

Here's a list of my must haves (=), definitely would like (+), and maybe would like (-). Would you guys recommend I go Ubuntu or FreeNAS based on these requirements? I'm very computer literate but I haven't messed with Linux in years (last time I sort of played around was when Gentoo was king; the last time before that, Red Hat was king). 

= NAS
= Backup (WinXP desktop, Mac OSX laptop; must be able to set user permissions on folders so only I can see my backed up files, etc.)
= Media serving (audio, video; iTunes, Winamp, XBOX 360, HTPC)
= Relatively simple administration interface
+ Torrent
+ Newsgroup binary downloads
+ Video conversion/encoding (automated)
+ DVD ripping
- PVR (I have an extra digital cable box and a couple tuners lying around; might get an HDHomeRun if I actually use this functionality)
- Web streaming for audio (might be nice to access my music from anywhere)
- Print server


FreeNAS is simple.  it performs a job, and you can make it perform other jobs, but the hassle involved is probably not worth the reward.

basically you can do nearly all of those things with ubuntu/debian/fedora/basically any distro:

NAS=samba
mediaserving=add mt-daapd = itunes share; mediatomb adds upnp support for xbox, etc
backups=i prefer an automated webbased solution so i use backuppc
webgui=webmin
torrents and newsgroup downloader can be rolled into one webbased app=torrentflux-b4rt
video conversion = im not sure about but i would think there are plenty of apps like mediatomb or similar that would do the task, but i dont know
dvd ripping = not sure about this one either, but i know there are packages designed for doing this exact thing
web streaming is easy = gnump3d, or set up an apache/lighttpd webserver and host a php based system on it, like ampache or jinzora
print server = check
pvr= could probably install mythtv backend, but i am not sure about this type of setup, my htpc runs windows 7 w/xbmc because no matter how hard i tried, i couldnt make xbmc standalone/mythbuntu, etc work well with the hardware....

you cant get that kind of flexibility with freenas...trust me i have tried

---

### Post by rbscairns on 2010-01-24
In your "must haves" you have included media serving iTunes. This is available with FreeNAS. My understanding is that it is not available when using Ubuntu (I could be wrong). FreeNAS meets all of your "must haves"

I have been using FreeNAS now for over a year in my home and office. It's one of my better software "investments".

FreNAS has a great web based GUI that is fairly intuitive for a non-Unix/Linux person like me. As for Ubuntu (and my limited understanding of it), I am now looking at my third complete wipe and re-install within the first few weeks of initial installation.

If you are very comfortable with Ubuntu, give it a go. If not, stick with FreeNAS.

---

### Post by pirateghost on 2010-01-24
> **rbscairns said:**
> In your "must haves" you have included media serving iTunes. This is available with FreeNAS. My understanding is that it is not available when using Ubuntu (I could be wrong). FreeNAS meets all of your "must haves"

the exact same package that FreeNAS uses to serve media to itunes is mt-daapd which is Firefly media server.  it is available to ubuntu no problem.  the only difference is the configuration of it.  its done via the webpage that it creates vs the webgui that FreeNAS uses (same configuration page as if you enable the module on FreeNAS and at the bottom of the page click on the ip: port that takes you to a Firefly page)

---

### Post by busydoingnothing on 2010-01-24
Thanks for the input, guys. Looks like Ubuntu is the way to go if I want a more robust feature set (as I expected). I'll spend some time with it until it either works the way I want, or I give up and settle for something more simple :)

Should I go with Ubuntu Server, then? I know it's frowned upon, but does Ubuntu Server include a desktop? And how much space should I need for my install?

---

### Post by NCLI on 2010-01-24
If you're going to install a desktop anyway, it's easier for you to just install the desktop version.

---

### Post by pirateghost on 2010-01-24
> **busydoingnothing said:**
> Thanks for the input, guys. Looks like Ubuntu is the way to go if I want a more robust feature set (as I expected). I'll spend some time with it until it either works the way I want, or I give up and settle for something more simple :)

Should I go with Ubuntu Server, then? I know it's frowned upon, but does Ubuntu Server include a desktop? And how much space should I need for my install?

i do things a little bit differently.

i run a couple of esxi servers here and i virtualize all my 'single job' servers, and use debian5 64bit for each one: backup server, mysql server (actually running arch on this one), downloader (torrentflux-b4rt), web server, upnp/itunes server, test servers, and servers used to compile and build packages.  none of them have a desktop, they are all command line only, but i have webmin installed on all of them so that i can maintain them all through a webmin cluster.

i do have a physical server for my storage.  it is running ubuntu server 9.10 64bit, again, with no gui/desktop.  it handles samba shares, iscsi targets for my esxi boxes, and a few other things.  i once had one server that did all those things but it seemed if one thing broke they all broke, so i thought i would split up the workloads, and if i screwed something up, everything else would work.  rebuilding a server for me is generally about a 30min to hour long job, depending on what server it was.

ubuntu server does not include a desktop by default, and if you really want to learn whats going on with your server, its best to hit the command line running.

one of the first installs you should make is getting webmin installed, as this will give you a "freenas feel" in that most of your configurations can be done via the webgui that webmin gives you.  it is merely a webgui to the config files in your system.

going CLI only is definitely a learning experience, but dont let it scare you...its worth it.

---

