---
title: "Was I hacked?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by phosphide on 2009-05-07
I signed on to my computer today and had three random .docx files on the desktop somehow downloaded at 5:30 this morning, which my computer was in sleep mode (We all know what .docx is). Each file contained some weird information in them and the last file said, "Do a research paper on virus hoaxes" Makes you feel all cozy inside huh? Nonetheless, how can I make sure my system is secure? What is the easiest way to check and see if any other files were downloaded elsewhere besides the desktop?

---

### Post by cody50 on 2009-05-07
I guess first of all, do you have any open ports, or ways that somebody could have accessed your machine? SSH, for example?

---

### Post by phosphide on 2009-05-07
> **cody50 said:**
> I guess first of all, do you have any open ports, or ways that somebody could have accessed your machine? SSH, for example?

I never adjusted any ports, they should all be closed from the start, yes? I don't have any network sharing of any kind, no SSH, nada. This is just my personal laptop.

---

### Post by albinootje on 2009-05-07
> **phosphide said:**
> I signed on to my computer today and had three random .docx files on the desktop somehow downloaded at 5:30 this morning, which my computer was in sleep mode 

Which Ubuntu release is this ?
What services are you running (ssh,telnet,http, ftp etc.) ?
Are you behind a firewall on your router ?
Do other people have physical access to your computer ?
> 
(We all know what .docx is).
Erhm, no, what is .docx ?

---

### Post by Joeb454 on 2009-05-07
> **albinootje said:**
> Erhm, no, what is .docx ?

The default file format for Word 2007 documents

---

### Post by cody50 on 2009-05-07
You could check the auth log to see if anyone logged into your machine in the night.

```
sudo less /var/log/auth.log
```


with a little bit of reading it you could see who has been logging in. if there are failed password attempts it will tell you **Possible break in attempt** or something like that.

---

### Post by Sef on 2009-05-07
> Erhm, no, what is .docx ?

It is Microsoft's latest format for Word 2007.

---

### Post by phosphide on 2009-05-07
> **albinootje said:**
> Which Ubuntu release is this ?
What services are you running (ssh,telnet,http, ftp etc.) ?
Are you behind a firewall on your router ?
Do other people have physical access to your computer ?
Ubuntu 8.10 Intrepid
Kernel Linux 2.6.27-11-generic
GNOME 2.24.1
Not running any services.
I would assume so, when I get back home I will recheck the router settings. Though I would assume all NetGear Routers are protected by a firewall?
My girlfriend as access to my computer, I will question her when I get home, but the only thing she knows how to do is bring up firefox and get on myspace. Is there anyway to check or see the tasks processing at 5:30 this morning?

> **albinootje said:**
> Erhm, no, what is .docx ?
Vista Word Document.

---

### Post by SunnyRabbiera on 2009-05-07
Well maybe its time to add firewall, and also try to rotate your passwords.
Careful browsing habits and personal habits can matter a lot, no OS is 100% immune to being infiltrated.
Ubuntu has a firewall client preinstalled but it needs to be configured, firestarter is a good tool for this.

---

### Post by phosphide on 2009-05-07
> **cody50 said:**
> You could check the auth log to see if anyone logged into your machine in the night.

```
sudo less /var/log/auth.log
```


with a little bit of reading it you could see who has been logging in. if there are failed password attempts it will tell you **Possible break in attempt** or something like that.

Did and done. This is the activity for this morning.

```
May  7 02:37:22 USERNAME-laptop sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=USERNAME ; COMMAND=/usr/bin/pacmd
May  7 05:12:58 USERNAME-laptop sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=USERNAME ; COMMAND=/usr/bin/pacmd
May  7 05:13:12 USERNAME-laptop gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  7 05:17:01 USERNAME-laptop CRON[558]: pam_unix(cron:session): session opened for user root by (uid=0)
May  7 05:17:01 USERNAME-laptop CRON[558]: pam_unix(cron:session): session closed for user root
May  7 05:24:49 USERNAME-laptop sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=USERNAME ; COMMAND=/usr/bin/pacmd
May  7 08:57:38 USERNAME-laptop sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=USERNAME ; COMMAND=/usr/bin/pacmd

```

---

### Post by phosphide on 2009-05-07
> **SunnyRabbiera said:**
> Well maybe its time to add firewall, and also try to rotate your passwords.
Careful browsing habits and personal habits can matter a lot, no OS is 100% immune to being infiltrated.
Ubuntu has a firewall client preinstalled but it needs to be configured, firestarter is a good tool for this.
Well, I did do that.

---

### Post by b@sh_n3rd on 2009-05-07
Hey I'm just wondering, Is there a way of tracking down IP addresses in the same method shown above? I mean the auth.log file? Now wouldn't that be some kind of advantage to track a hacker? I was hunting for something like the auth.log file in winblows and finally I found it on Ubuntu! :D. Thanks guys :D.

---

### Post by albinootje on 2009-05-07
> **phosphide said:**
> Ubuntu 8.10 Intrepid
Kernel Linux 2.6.27-11-generic
GNOME 2.24.1
Not running any services.

Okay, thanks.
If you're not running any services (Also not vnc ?), and it's only your laptop in the LAN, then we might as well forget about firewalls.

Can you then boot into "recovery mode", choose "root prompt" and do the following :
```

dhclient
apt-get update
apt-get install rkhunter chkrootkit
rkhunter -c
chkrootkit

```
Post any irregular/error signs from that here.

After that reboot.
(to not let the "dhclient" process conflict with Network Manager)

And can you then post the output of the following :
```

ls -latr /var/log/
history | tail
ls -latr /etc|tail
ls -latr ~/|tail
ls -latr ~/Desktop/tail
cat /etc/resolv.conf

```

By the way, is "ifconfig" showing you a LAN address, like 192.168.1.2 or 10.0.0.2 ?

---

### Post by albinootje on 2009-05-07
> **phosphide said:**
> Did and done. This is the activity for this morning.

```
May  7 02:37:22 USERNAME-laptop sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=USERNAME ; COMMAND=/usr/bin/pacmd
May  7 05:12:58 USERNAME-laptop sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=USERNAME ; COMMAND=/usr/bin/pacmd
May  7 05:13:12 USERNAME-laptop gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  7 05:17:01 USERNAME-laptop CRON[558]: pam_unix(cron:session): session opened for user root by (uid=0)
May  7 05:17:01 USERNAME-laptop CRON[558]: pam_unix(cron:session): session closed for user root
May  7 05:24:49 USERNAME-laptop sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=USERNAME ; COMMAND=/usr/bin/pacmd
May  7 08:57:38 USERNAME-laptop sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=USERNAME ; COMMAND=/usr/bin/pacmd

```
Interesting, at about 05:15 someone unlocked your screensaver lock.

And on my Ubuntu Hardy I cannot find any references to pacmd here :
```

# grep -r -i pacmd /var/log/
# grep -r -i pacmd /usr/lib/hal/scripts/

```
No results.
Can you issue the same commands to see where a reference to "pacmd" can be found ?

---

### Post by mcduck on 2009-05-07
> **albinootje said:**
> Interesting, at about 05:15 someone unlocked your screensaver lock.

And on my Ubuntu Hardy I cannot find any references to pacmd here :
```

# grep -r -i pacmd /var/log/
# grep -r -i pacmd /usr/lib/hal/scripts/

```
No results.
Can you issue the same commands to see where a reference to "pacmd" can be found ?

pacmd is related to PulseAudio, if I remember right it's used for reconfiguring PulseAudio server while running.

Anyway, the log entry showing unlocking the screensaver is a sign that who ever used the machine, did it with local access instead of connecting through network. Which means that you can pretty much stop worrying about being hacked, and instead ask your girlfriend about it when she gets home.

---

### Post by Niniel on 2009-05-07
Or the OP is sleepwalking. :D

---

### Post by b@sh_n3rd on 2009-05-07
> **Niniel said:**
> Or the OP is sleepwalking. :D

Hehe, good one :D. But, it kinda makes sense :D. The way it goes only 2 ppl have access...it should be one of 'em if it's not a remote hack. right? no offense, if any k?

---

### Post by phosphide on 2009-05-07
Me sleep walking and getting on the computer scares me more than being hacked.

---

### Post by nezik on 2009-05-31
Hi to All.
I have the same problem, but little bit worst.
My Auth.log finished with following text:
> May 31 10:37:34 notes sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=chita ; COMMAND=/usr/bin/pacmd
May 31 10:39:24 notes sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=chita ; COMMAND=/usr/bin/pacmd
May 31 10:39:30 notes gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May 31 10:39:57 notes polkit-grant-helper[18898]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 18890 [uid=1001] [auth=chita]
May 31 10:41:51 notes groupdel[18937]: remove group `adm' 
May 31 10:41:51 notes groupdel[18943]: remove group `admin' 
May 31 10:41:51 notes groupdel[18949]: remove group `audio' 
May 31 10:41:52 notes groupdel[18963]: remove group `cdrom' 
May 31 10:41:52 notes groupdel[18971]: remove group `crontab' 
May 31 10:41:53 notes groupdel[18979]: remove group `dialout' 
May 31 10:41:53 notes groupdel[18985]: remove group `dip' 
May 31 10:41:53 notes groupdel[18991]: remove group `disk' 
May 31 10:41:53 notes groupdel[18997]: remove group `fax' 
May 31 10:41:53 notes groupdel[19003]: remove group `floppy' 
May 31 10:41:53 notes groupdel[19009]: remove group `fuse' 
May 31 10:41:54 notes groupdel[19029]: remove group `kmem' 
May 31 10:41:55 notes groupdel[19041]: remove group `lpadmin' 
May 31 10:41:55 notes groupdel[19053]: remove group `mlocate' 
May 31 10:41:56 notes groupdel[19064]: remove group `netdev' 
May 31 10:41:56 notes groupdel[19076]: remove group `nvram' 
May 31 10:41:56 notes groupdel[19082]: remove group `operator' 
May 31 10:41:56 notes groupdel[19088]: remove group `plugdev' 
May 31 10:41:57 notes groupdel[19100]: remove group `pulse-access' 
May 31 10:41:57 notes groupdel[19106]: remove group `pulse-rt' 
May 31 10:41:57 notes groupdel[19114]: remove group `sambashare' 
May 31 10:41:58 notes groupdel[19122]: remove group `sasl' 
May 31 10:41:58 notes groupdel[19128]: remove group `scanner' 
May 31 10:41:58 notes groupdel[19134]: remove group `shadow' 
May 31 10:41:58 notes groupdel[19140]: remove group `src' 
May 31 10:41:58 notes groupdel[19146]: remove group `ssh' 
May 31 10:41:58 notes groupdel[19152]: remove group `ssl-cert' 
May 31 10:41:58 notes groupdel[19158]: remove group `staff' 
May 31 10:41:59 notes groupdel[19164]: remove group `sudo' 
May 31 10:41:59 notes groupdel[19174]: remove group `tape' 
May 31 10:41:59 notes groupdel[19180]: remove group `tty' 
May 31 10:41:59 notes groupdel[19186]: remove group `users' 
May 31 10:41:59 notes groupdel[19192]: remove group `utmp' 
May 31 10:42:00 notes groupdel[19200]: remove group `video' 
May 31 10:42:00 notes groupdel[19206]: remove group `voice' 
May 31 10:42:00 notes userdel[19220]: delete user `avahi' 
May 31 10:42:00 notes userdel[19220]: removed group `avahi' owned by `avahi' 
May 31 10:42:01 notes userdel[19230]: delete user `avahi-autoipd' 
May 31 10:42:01 notes userdel[19230]: removed group `avahi-autoipd' owned by `avahi-autoipd' 
May 31 10:42:01 notes userdel[19239]: delete user `backup' 
May 31 10:42:01 notes userdel[19239]: removed group `backup' owned by `backup' 
May 31 10:42:01 notes userdel[19248]: delete user `bin' 
May 31 10:42:01 notes userdel[19248]: removed group `bin' owned by `bin' 
May 31 10:42:01 notes userdel[19262]: delete user `daemon' 
May 31 10:42:01 notes userdel[19262]: removed group `daemon' owned by `daemon' 
May 31 10:42:01 notes userdel[19271]: delete user `games' 
May 31 10:42:01 notes userdel[19271]: removed group `games' owned by `games' 
May 31 10:42:02 notes userdel[19280]: delete user `gdm' 
May 31 10:42:02 notes userdel[19280]: removed group `gdm' owned by `gdm' 
May 31 10:42:02 notes userdel[19289]: delete user `gnats' 
May 31 10:42:02 notes userdel[19289]: removed group `gnats' owned by `gnats' 
May 31 10:42:02 notes userdel[19298]: delete user `haldaemon' 
May 31 10:42:02 notes userdel[19298]: removed group `haldaemon' owned by `haldaemon' 
May 31 10:42:02 notes userdel[19307]: delete user `hplip' 
May 31 10:42:02 notes userdel[19316]: delete user `irc' 
May 31 10:42:02 notes userdel[19316]: removed group `irc' owned by `irc' 
May 31 10:42:02 notes userdel[19325]: delete user `klog' 
May 31 10:42:02 notes userdel[19325]: removed group `klog' owned by `klog' 
May 31 10:42:02 notes useradd[19334]: new user: name=klop, UID=1002, GID=0, home=/home/klop1, shell=/bin/bash
May 31 10:42:03 notes usermod[19341]: change user `klop' password
May 31 10:42:03 notes chfn[19346]: changed user `klop' information
May 31 10:42:03 notes usermod[19351]: change user `klop' password
May 31 10:42:03 notes userdel[19366]: delete user `libuuid' 
May 31 10:42:03 notes userdel[19366]: removed group `libuuid' owned by `libuuid' 
May 31 10:42:03 notes userdel[19375]: delete user `list' 
May 31 10:42:03 notes userdel[19375]: removed group `list' owned by `list' 
May 31 10:42:03 notes userdel[19384]: delete user `lp' 
May 31 10:42:03 notes userdel[19384]: removed group `lp' owned by `lp' 
May 31 10:42:03 notes userdel[19393]: delete user `mail' 
May 31 10:42:03 notes userdel[19393]: removed group `mail' owned by `mail' 
May 31 10:42:04 notes userdel[19402]: delete user `man' 
May 31 10:42:04 notes userdel[19402]: removed group `man' owned by `man' 
May 31 10:42:04 notes userdel[19411]: delete user `messagebus' 
May 31 10:42:04 notes userdel[19411]: removed group `messagebus' owned by `messagebus' 
May 31 10:42:04 notes userdel[19420]: delete user `mysql' 
May 31 10:42:04 notes userdel[19420]: removed group `mysql' owned by `mysql' 
May 31 10:42:04 notes userdel[19429]: delete user `mythtv' 
May 31 10:42:04 notes userdel[19438]: delete user `news' 
May 31 10:42:04 notes userdel[19438]: removed group `news' owned by `news' 
May 31 10:42:04 notes userdel[19447]: delete user `nobody' 
May 31 10:42:04 notes userdel[19456]: delete user `ntp' 
May 31 10:42:04 notes userdel[19456]: removed group `ntp' owned by `ntp' 
May 31 10:42:05 notes userdel[19465]: delete user `polkituser' 
May 31 10:42:05 notes userdel[19465]: removed group `polkituser' owned by `polkituser' 
May 31 10:42:05 notes userdel[19474]: delete user `proxy' 
May 31 10:42:05 notes userdel[19474]: removed group `proxy' owned by `proxy' 
May 31 10:42:05 notes userdel[19483]: delete user `pulse' 
May 31 10:42:05 notes userdel[19483]: removed group `pulse' owned by `pulse' 
May 31 10:42:05 notes userdel[19494]: delete user `saned' 
May 31 10:42:05 notes userdel[19494]: removed group `saned' owned by `saned' 
May 31 10:42:05 notes userdel[19503]: delete user `sync' 
May 31 10:42:06 notes userdel[19513]: delete user `sys' 
May 31 10:42:06 notes userdel[19513]: removed group `sys' owned by `sys' 
May 31 10:42:06 notes userdel[19522]: delete user `syslog' 
May 31 10:42:06 notes userdel[19522]: removed group `syslog' owned by `syslog' 
May 31 10:42:06 notes userdel[19531]: delete user `uucp' 
May 31 10:42:06 notes userdel[19531]: removed group `uucp' owned by `uucp' 
May 31 10:42:06 notes userdel[19540]: delete user `www-data' 
May 31 10:42:06 notes userdel[19540]: removed group `www-data' owned by `www-data' 
May 31 10:42:06 notes groupdel[19551]: remove group `mythtv' 
May 31 10:42:06 notes groupdel[19557]: remove group `nogroup' 
May 31 10:58:56 notes sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=chita ; COMMAND=/usr/bin/pacmd
May 31 12:06:47 notes sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=chita ; COMMAND=/usr/bin/pacmd
May 31 12:07:40 notes sudo: cannot execute /usr/sbin/sendmail: No such file or directory
May 31 12:07:40 notes sudo:    chita : user NOT in sudoers ; TTY=unknown ; PWD=/home/chita ; USER=root ; COMMAND=/usr/bin/nautilus
May 31 12:08:35 notes sudo: cannot execute /usr/sbin/sendmail: No such file or directory
May 31 12:08:35 notes sudo:    chita : user NOT in sudoers ; TTY=pts/0 ; PWD=/home/chita ; USER=root ; COMMAND=/usr/bin/nautilus
May 31 12:08:48 notes gdm[4706]: pam_unix(gdm:session): session closed for user chita
May 31 12:09:07 notes gdm[20060]: pam_unix(gdm:session): session opened for user klop by (uid=0)
May 31 12:09:07 notes gdm[20060]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
May 31 12:09:07 notes gdm[20060]: gnome-keyring-daemon: couldn't lookup keyring component setting: Nelze kontaktovat server nastavení; p&#345;í&#269;inou m&#367;&#382;e být nutnost povolení sít&#283; TCP/IP pro ORBit, nebo existují staré zámky NFS po pádu systému. Více informací viz [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/). (Podrobnosti -  1: Nelze se p&#345;ipojit k sezení: dbus-launch failed to autolaunch D-Bus session: No protocol specified
May 31 12:09:07 notes gdm[20060]: Autolaunch error: X11 initialization failed.
May 31 12:09:07 notes gdm[20060]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Nelze kontaktovat server nastavení; p&#345;í&#269;inou m&#367;&#382;e být nutnost povolení sít&#283; TCP/IP pro ORBit, nebo existují staré zámky NFS po pádu systému. Více informací viz [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/). (Podrobnosti -  1: Nelze se p&#345;ipojit k sezení: dbus-launch failed to autolaunch D-Bus session: No protocol specified
May 31 12:09:07 notes gdm[20060]: Autolaunch error: X11 initialization failed.
May 31 12:09:07 notes gdm[20060]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Nelze kontaktovat server nastavení; p&#345;í&#269;inou m&#367;&#382;e být nutnost povolení sít&#283; TCP/IP pro ORBit, nebo existují staré zámky NFS po pádu systému. Více informací viz [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/). (Podrobnosti -  1: Nelze se p&#345;ipojit k sezení: dbus-launch failed to autolaunch D-Bus session: No protocol specified
May 31 12:09:07 notes gdm[20060]: Autolaunch error: X11 initialization failed.
May 31 12:09:07 notes gdm[20060]: )
May 31 12:09:50 notes sudo: cannot execute /usr/sbin/sendmail: No such file or directory
May 31 12:09:50 notes sudo:     klop : user NOT in sudoers ; TTY=unknown ; PWD=/home/klop1 ; USER=root ; COMMAND=/usr/bin/nautilus
May 31 12:10:14 notes gdm[20060]: pam_unix(gdm:session): session closed for user klop
May 31 12:10:29 notes gdm[20060]: pam_unix(gdm:session): session opened for user chita by (uid=0)
May 31 12:10:29 notes gdm[20060]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
May 31 12:10:29 notes gdm[20060]: gnome-keyring-daemon: couldn't lookup keyring component setting: Nelze kontaktovat server nastavení; p&#345;í&#269;inou m&#367;&#382;e být nutnost povolení sít&#283; TCP/IP pro ORBit, nebo existují staré zámky NFS po pádu systému. Více informací viz [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/). (Podrobnosti -  1: Nelze se p&#345;ipojit k sezení: dbus-launch failed to autolaunch D-Bus session: No protocol specified
May 31 12:10:30 notes gdm[20060]: Autolaunch error: X11 initialization failed.
May 31 12:10:30 notes gdm[20060]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Nelze kontaktovat server nastavení; p&#345;í&#269;inou m&#367;&#382;e být nutnost povolení sít&#283; TCP/IP pro ORBit, nebo existují staré zámky NFS po pádu systému. Více informací viz [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/). (Podrobnosti -  1: Nelze se p&#345;ipojit k sezení: dbus-launch failed to autolaunch D-Bus session: No protocol specified
May 31 12:10:30 notes gdm[20060]: Autolaunch error: X11 initialization failed.
May 31 12:10:30 notes gdm[20060]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Nelze kontaktovat server nastavení; p&#345;í&#269;inou m&#367;&#382;e být nutnost povolení sít&#283; TCP/IP pro ORBit, nebo existují staré zámky NFS po pádu systému. Více informací viz [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/). (Podrobnosti -  1: Nelze se p&#345;ipojit k sezení: dbus-launch failed to autolaunch D-Bus session: No protocol specified
May 31 12:10:30 notes gdm[20060]: Autolaunch error: X11 initialization failed.
May 31 12:10:30 notes gdm[20060]: )
May 31 12:11:20 notes gdm[20060]: pam_unix(gdm:session): session closed for user chita

Any Ideas how to repair it?
Thanks

---

### Post by steeleyuk on 2009-05-31
You'd probably be better reinstalling from scratch... with the amount of 'damage' done there a reinstall with complex passwords would be best in my opinion.

---

### Post by lisati on 2009-05-31
> **phosphide said:**
> I would assume so, when I get back home I will recheck the router settings. Though I would assume all NetGear Routers are protected by a firewall?

Apologies for the delay jumping in: I have two routers, one of which is one by Netgear. If left with the factory settings, it's firewall features are turned on by default, but wireless encryption and MAC filters are switched off by default.

---

### Post by mcduck on 2009-05-31
> **nezik said:**
> Hi to All.
I have the same problem, but little bit worst.
My Auth.log finished with following text:

Any Ideas how to repair it?
Thanks

Only thing visible from that log is that user "chita" removed pretty much all users & groups from the system. Using the GUI tool, not command -line user management tools.

Since the part where that user logs in is not visible in the output you posted there's no reason to assume any cracker was involved. If your system was cracked, you'd most likely see a bunch of failed login attempts in auth.log. Without those, it could just as well be that user "chita" was the one who did the damage.

Also, unless you ave installed any server software on the machine there's no tasks running that would respond to incoming network connections. That makes it very unlikely that you'd really get cracked. And also crackers don't usually break into some random person's system just to destroy it, there wouldn't be much benefits from that. In case somebody really cracks into your computer he would most likely leave it working, hide his tracks and use the system for some purpose like as a part of a botnet.

Anyway, steeleyuk is right about reinstall being the easiest way to solve that mess.

---

### Post by albinootje on 2009-05-31
> **mcduck said:**
>  Also, unless you ave installed any server software on the machine there's no tasks running that would respond to incoming network connections. That makes it very unlikely that you'd really get cracked.

Applications connecting to the internet (web browser, mail-client, instant messaging etc.) can theoretically be exploited.
And there's also the possibility of trojans for Linux in e.g. maliciously modified source code.
And let's not forget about social engineering.

In this specific case however it makes sense to assume that someone had physical access to that machine itself.

---

### Post by nezik on 2009-05-31
I thing, it wasn't attack, because I have local network behind modem with firewall.
User 'Chita' tryed to make new user, but it faild. Than the computer went to sleep, while Chita was in Job. When We wake up computer it was impossible to log in.
I post whole auth.log for more informations.
The system was installed yesterday, so there was no time to make some mystakes.
> May 31 09:47:16 notes sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=chita ; COMMAND=/usr/bin/pacmd
May 31 10:02:35 notes sudo:     root : TTY=unknown ; PWD=/ ; USER=chita ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
May 31 10:02:36 notes sudo:     root : TTY=unknown ; PWD=/ ; USER=chita ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
May 31 10:02:37 notes sudo:     root : TTY=unknown ; PWD=/ ; USER=chita ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
May 31 10:15:17 notes gdm[17732]: pam_unix(gdm:auth): check pass; user unknown
May 31 10:15:17 notes gdm[17732]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:20 ruser= rhost= 
May 31 10:15:32 notes gdm[17732]: pam_unix(gdm:auth): check pass; user unknown
May 31 10:15:32 notes gdm[17732]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:20 ruser= rhost= 
May 31 10:15:53 notes gdm[17732]: pam_unix(gdm:auth): check pass; user unknown
May 31 10:15:53 notes gdm[17732]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:20 ruser= rhost= 
May 31 10:16:48 notes gdm[17732]: pam_unix(gdm:auth): check pass; user unknown
May 31 10:16:48 notes gdm[17732]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:20 ruser= rhost= 
May 31 10:17:01 notes CRON[17818]: pam_unix(cron:session): session opened for user root by (uid=0)
May 31 10:17:01 notes CRON[17818]: pam_unix(cron:session): session closed for user root
May 31 10:19:06 notes gdm[17916]: pam_unix(gdm:auth): check pass; user unknown
May 31 10:19:06 notes gdm[17916]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:20 ruser= rhost= 
May 31 10:19:21 notes gdm[17916]: pam_unix(gdm:auth): check pass; user unknown
May 31 10:19:21 notes gdm[17916]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:20 ruser= rhost= 
May 31 10:19:40 notes gdm[17916]: pam_unix(gdm:auth): check pass; user unknown
May 31 10:19:40 notes gdm[17916]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:20 ruser= rhost= 
May 31 10:19:52 notes gdm[17916]: pam_unix(gdm:auth): conversation failed
May 31 10:19:52 notes gdm[17916]: pam_unix(gdm:auth): auth could not identify password for []
May 31 10:20:04 notes gdm[17916]: pam_unix(gdm:auth): check pass; user unknown
May 31 10:20:04 notes gdm[17916]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:20 ruser= rhost= 
May 31 10:20:18 notes gdm[17916]: pam_unix(gdm:auth): check pass; user unknown
May 31 10:20:18 notes gdm[17916]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:20 ruser= rhost= 
May 31 10:22:14 notes gdm[17916]: pam_unix(gdm:auth): check pass; user unknown
May 31 10:22:14 notes gdm[17916]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:20 ruser= rhost= 
May 31 10:23:41 notes polkit-grant-helper[18197]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 18168 [uid=1001] [auth=chita]
May 31 10:37:24 notes polkit-grant-helper-pam[18380]: pam_unix(polkit:auth): conversation failed
May 31 10:37:24 notes polkit-grant-helper-pam[18380]: pam_unix(polkit:auth): auth could not identify password for [chita]
May 31 10:37:34 notes sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=chita ; COMMAND=/usr/bin/pacmd
May 31 10:39:24 notes sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=chita ; COMMAND=/usr/bin/pacmd
May 31 10:39:30 notes gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May 31 10:39:57 notes polkit-grant-helper[18898]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 18890 [uid=1001] [auth=chita]
May 31 10:41:51 notes groupdel[18937]: remove group `adm' 
May 31 10:41:51 notes groupdel[18943]: remove group `admin' 
May 31 10:41:51 notes groupdel[18949]: remove group `audio' 
May 31 10:41:52 notes groupdel[18963]: remove group `cdrom' 
May 31 10:41:52 notes groupdel[18971]: remove group `crontab' 
May 31 10:41:53 notes groupdel[18979]: remove group `dialout' 
May 31 10:41:53 notes groupdel[18985]: remove group `dip' 
May 31 10:41:53 notes groupdel[18991]: remove group `disk' 
May 31 10:41:53 notes groupdel[18997]: remove group `fax' 
May 31 10:41:53 notes groupdel[19003]: remove group `floppy' 
May 31 10:41:53 notes groupdel[19009]: remove group `fuse' 
May 31 10:41:54 notes groupdel[19029]: remove group `kmem' 
May 31 10:41:55 notes groupdel[19041]: remove group `lpadmin' 
May 31 10:41:55 notes groupdel[19053]: remove group `mlocate' 
May 31 10:41:56 notes groupdel[19064]: remove group `netdev' 
May 31 10:41:56 notes groupdel[19076]: remove group `nvram' 
May 31 10:41:56 notes groupdel[19082]: remove group `operator' 
May 31 10:41:56 notes groupdel[19088]: remove group `plugdev' 
May 31 10:41:57 notes groupdel[19100]: remove group `pulse-access' 
May 31 10:41:57 notes groupdel[19106]: remove group `pulse-rt' 
May 31 10:41:57 notes groupdel[19114]: remove group `sambashare' 
May 31 10:41:58 notes groupdel[19122]: remove group `sasl' 
May 31 10:41:58 notes groupdel[19128]: remove group `scanner' 
May 31 10:41:58 notes groupdel[19134]: remove group `shadow' 
May 31 10:41:58 notes groupdel[19140]: remove group `src' 
May 31 10:41:58 notes groupdel[19146]: remove group `ssh' 
May 31 10:41:58 notes groupdel[19152]: remove group `ssl-cert' 
May 31 10:41:58 notes groupdel[19158]: remove group `staff' 
May 31 10:41:59 notes groupdel[19164]: remove group `sudo' 
May 31 10:41:59 notes groupdel[19174]: remove group `tape' 
May 31 10:41:59 notes groupdel[19180]: remove group `tty' 
May 31 10:41:59 notes groupdel[19186]: remove group `users' 
May 31 10:41:59 notes groupdel[19192]: remove group `utmp' 
May 31 10:42:00 notes groupdel[19200]: remove group `video' 
May 31 10:42:00 notes groupdel[19206]: remove group `voice' 
May 31 10:42:00 notes userdel[19220]: delete user `avahi' 
May 31 10:42:00 notes userdel[19220]: removed group `avahi' owned by `avahi' 
May 31 10:42:01 notes userdel[19230]: delete user `avahi-autoipd' 
May 31 10:42:01 notes userdel[19230]: removed group `avahi-autoipd' owned by `avahi-autoipd' 
May 31 10:42:01 notes userdel[19239]: delete user `backup' 
May 31 10:42:01 notes userdel[19239]: removed group `backup' owned by `backup' 
May 31 10:42:01 notes userdel[19248]: delete user `bin' 
May 31 10:42:01 notes userdel[19248]: removed group `bin' owned by `bin' 
May 31 10:42:01 notes userdel[19262]: delete user `daemon' 
May 31 10:42:01 notes userdel[19262]: removed group `daemon' owned by `daemon' 
May 31 10:42:01 notes userdel[19271]: delete user `games' 
May 31 10:42:01 notes userdel[19271]: removed group `games' owned by `games' 
May 31 10:42:02 notes userdel[19280]: delete user `gdm' 
May 31 10:42:02 notes userdel[19280]: removed group `gdm' owned by `gdm' 
May 31 10:42:02 notes userdel[19289]: delete user `gnats' 
May 31 10:42:02 notes userdel[19289]: removed group `gnats' owned by `gnats' 
May 31 10:42:02 notes userdel[19298]: delete user `haldaemon' 
May 31 10:42:02 notes userdel[19298]: removed group `haldaemon' owned by `haldaemon' 
May 31 10:42:02 notes userdel[19307]: delete user `hplip' 
May 31 10:42:02 notes userdel[19316]: delete user `irc' 
May 31 10:42:02 notes userdel[19316]: removed group `irc' owned by `irc' 
May 31 10:42:02 notes userdel[19325]: delete user `klog' 
May 31 10:42:02 notes userdel[19325]: removed group `klog' owned by `klog' 
May 31 10:42:02 notes useradd[19334]: new user: name=klop, UID=1002, GID=0, home=/home/klop1, shell=/bin/bash
May 31 10:42:03 notes usermod[19341]: change user `klop' password
May 31 10:42:03 notes chfn[19346]: changed user `klop' information
May 31 10:42:03 notes usermod[19351]: change user `klop' password
May 31 10:42:03 notes userdel[19366]: delete user `libuuid' 
May 31 10:42:03 notes userdel[19366]: removed group `libuuid' owned by `libuuid' 
May 31 10:42:03 notes userdel[19375]: delete user `list' 
May 31 10:42:03 notes userdel[19375]: removed group `list' owned by `list' 
May 31 10:42:03 notes userdel[19384]: delete user `lp' 
May 31 10:42:03 notes userdel[19384]: removed group `lp' owned by `lp' 
May 31 10:42:03 notes userdel[19393]: delete user `mail' 
May 31 10:42:03 notes userdel[19393]: removed group `mail' owned by `mail' 
May 31 10:42:04 notes userdel[19402]: delete user `man' 
May 31 10:42:04 notes userdel[19402]: removed group `man' owned by `man' 
May 31 10:42:04 notes userdel[19411]: delete user `messagebus' 
May 31 10:42:04 notes userdel[19411]: removed group `messagebus' owned by `messagebus' 
May 31 10:42:04 notes userdel[19420]: delete user `mysql' 
May 31 10:42:04 notes userdel[19420]: removed group `mysql' owned by `mysql' 
May 31 10:42:04 notes userdel[19429]: delete user `mythtv' 
May 31 10:42:04 notes userdel[19438]: delete user `news' 
May 31 10:42:04 notes userdel[19438]: removed group `news' owned by `news' 
May 31 10:42:04 notes userdel[19447]: delete user `nobody' 
May 31 10:42:04 notes userdel[19456]: delete user `ntp' 
May 31 10:42:04 notes userdel[19456]: removed group `ntp' owned by `ntp' 
May 31 10:42:05 notes userdel[19465]: delete user `polkituser' 
May 31 10:42:05 notes userdel[19465]: removed group `polkituser' owned by `polkituser' 
May 31 10:42:05 notes userdel[19474]: delete user `proxy' 
May 31 10:42:05 notes userdel[19474]: removed group `proxy' owned by `proxy' 
May 31 10:42:05 notes userdel[19483]: delete user `pulse' 
May 31 10:42:05 notes userdel[19483]: removed group `pulse' owned by `pulse' 
May 31 10:42:05 notes userdel[19494]: delete user `saned' 
May 31 10:42:05 notes userdel[19494]: removed group `saned' owned by `saned' 
May 31 10:42:05 notes userdel[19503]: delete user `sync' 
May 31 10:42:06 notes userdel[19513]: delete user `sys' 
May 31 10:42:06 notes userdel[19513]: removed group `sys' owned by `sys' 
May 31 10:42:06 notes userdel[19522]: delete user `syslog' 
May 31 10:42:06 notes userdel[19522]: removed group `syslog' owned by `syslog' 
May 31 10:42:06 notes userdel[19531]: delete user `uucp' 
May 31 10:42:06 notes userdel[19531]: removed group `uucp' owned by `uucp' 
May 31 10:42:06 notes userdel[19540]: delete user `www-data' 
May 31 10:42:06 notes userdel[19540]: removed group `www-data' owned by `www-data' 
May 31 10:42:06 notes groupdel[19551]: remove group `mythtv' 
May 31 10:42:06 notes groupdel[19557]: remove group `nogroup' 
May 31 10:58:56 notes sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=chita ; COMMAND=/usr/bin/pacmd
May 31 12:06:47 notes sudo:     root : TTY=unknown ; PWD=/usr/lib/hal/scripts ; USER=chita ; COMMAND=/usr/bin/pacmd
May 31 12:07:40 notes sudo: cannot execute /usr/sbin/sendmail: No such file or directory
May 31 12:07:40 notes sudo:    chita : user NOT in sudoers ; TTY=unknown ; PWD=/home/chita ; USER=root ; COMMAND=/usr/bin/nautilus
May 31 12:08:35 notes sudo: cannot execute /usr/sbin/sendmail: No such file or directory
May 31 12:08:35 notes sudo:    chita : user NOT in sudoers ; TTY=pts/0 ; PWD=/home/chita ; USER=root ; COMMAND=/usr/bin/nautilus
May 31 12:08:48 notes gdm[4706]: pam_unix(gdm:session): session closed for user chita
May 31 12:09:07 notes gdm[20060]: pam_unix(gdm:session): session opened for user klop by (uid=0)
May 31 12:09:07 notes gdm[20060]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
May 31 12:09:07 notes gdm[20060]: gnome-keyring-daemon: couldn't lookup keyring component setting: Nelze kontaktovat server nastavení; p&#345;í&#269;inou m&#367;&#382;e být nutnost povolení sít&#283; TCP/IP pro ORBit, nebo existují staré zámky NFS po pádu systému. Více informací viz [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/). (Podrobnosti -  1: Nelze se p&#345;ipojit k sezení: dbus-launch failed to autolaunch D-Bus session: No protocol specified
May 31 12:09:07 notes gdm[20060]: Autolaunch error: X11 initialization failed.
May 31 12:09:07 notes gdm[20060]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Nelze kontaktovat server nastavení; p&#345;í&#269;inou m&#367;&#382;e být nutnost povolení sít&#283; TCP/IP pro ORBit, nebo existují staré zámky NFS po pádu systému. Více informací viz [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/). (Podrobnosti -  1: Nelze se p&#345;ipojit k sezení: dbus-launch failed to autolaunch D-Bus session: No protocol specified
May 31 12:09:07 notes gdm[20060]: Autolaunch error: X11 initialization failed.
May 31 12:09:07 notes gdm[20060]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Nelze kontaktovat server nastavení; p&#345;í&#269;inou m&#367;&#382;e být nutnost povolení sít&#283; TCP/IP pro ORBit, nebo existují staré zámky NFS po pádu systému. Více informací viz [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/). (Podrobnosti -  1: Nelze se p&#345;ipojit k sezení: dbus-launch failed to autolaunch D-Bus session: No protocol specified
May 31 12:09:07 notes gdm[20060]: Autolaunch error: X11 initialization failed.
May 31 12:09:07 notes gdm[20060]: )
May 31 12:09:50 notes sudo: cannot execute /usr/sbin/sendmail: No such file or directory
May 31 12:09:50 notes sudo:     klop : user NOT in sudoers ; TTY=unknown ; PWD=/home/klop1 ; USER=root ; COMMAND=/usr/bin/nautilus
May 31 12:10:14 notes gdm[20060]: pam_unix(gdm:session): session closed for user klop
May 31 12:10:29 notes gdm[20060]: pam_unix(gdm:session): session opened for user chita by (uid=0)
May 31 12:10:29 notes gdm[20060]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
May 31 12:10:29 notes gdm[20060]: gnome-keyring-daemon: couldn't lookup keyring component setting: Nelze kontaktovat server nastavení; p&#345;í&#269;inou m&#367;&#382;e být nutnost povolení sít&#283; TCP/IP pro ORBit, nebo existují staré zámky NFS po pádu systému. Více informací viz [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/). (Podrobnosti -  1: Nelze se p&#345;ipojit k sezení: dbus-launch failed to autolaunch D-Bus session: No protocol specified
May 31 12:10:30 notes gdm[20060]: Autolaunch error: X11 initialization failed.
May 31 12:10:30 notes gdm[20060]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Nelze kontaktovat server nastavení; p&#345;í&#269;inou m&#367;&#382;e být nutnost povolení sít&#283; TCP/IP pro ORBit, nebo existují staré zámky NFS po pádu systému. Více informací viz [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/). (Podrobnosti -  1: Nelze se p&#345;ipojit k sezení: dbus-launch failed to autolaunch D-Bus session: No protocol specified
May 31 12:10:30 notes gdm[20060]: Autolaunch error: X11 initialization failed.
May 31 12:10:30 notes gdm[20060]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Nelze kontaktovat server nastavení; p&#345;í&#269;inou m&#367;&#382;e být nutnost povolení sít&#283; TCP/IP pro ORBit, nebo existují staré zámky NFS po pádu systému. Více informací viz [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/). (Podrobnosti -  1: Nelze se p&#345;ipojit k sezení: dbus-launch failed to autolaunch D-Bus session: No protocol specified
May 31 12:10:30 notes gdm[20060]: Autolaunch error: X11 initialization failed.
May 31 12:10:30 notes gdm[20060]: )
May 31 12:11:20 notes gdm[20060]: pam_unix(gdm:session): session closed for user chita


---

### Post by NHArticleTen on 2009-05-31
> **steeleyuk said:**
> You'd probably be better reinstalling from scratch... with the amount of 'damage' done there a reinstall with complex passwords would be best in my opinion.

DBAN the drive...
Reinstall everything...

And don't let the Chita back on your puter...

nuff said...

---

### Post by nezik on 2009-05-31
We reinstall the system, but, I want to know, what happend.
thx for answers.

---

### Post by NHArticleTen on 2009-05-31
> **nezik said:**
> We reinstall the system, but, I want to know, what happend.
thx for answers.

get your chita her own computer

---

### Post by albinootje on 2009-05-31
> **nezik said:**
> We reinstall the system, but, I want to know, what happend.

This was the new user ?
```

May 31 10:42:02 notes useradd[19334]: new user: name=klop, UID=1002, GID=0, home=/home/klop1, shell=/bin/bash

```
After you've reinstalled now, it is hard to say what happened, but something terribly went wrong. It looks imho pretty dodgy though.

---

### Post by nezik on 2009-05-31
> **albinootje said:**
> This was the new user ?
```

May 31 10:42:02 notes useradd[19334]: new user: name=klop, UID=1002, GID=0, home=/home/klop1, shell=/bin/bash

```
After you've reinstalled now, it is hard to say what happened, but something terribly went wrong. It looks imho pretty dodgy though.
Klop is the new user, which we tryed to make.
I have all logs saved, so I can give more infos if needed.

---

### Post by nezik on 2009-05-31
> **NHArticleTen said:**
> DBAN the drive...
Reinstall everything...

And don't let the Chita back on your puter...

nuff said...

It's Chita's comp. :D
I have my own, with only one user and no problems :D

---

### Post by dmizer on 2009-06-01
Have VNC server open to the web by chance?

---

