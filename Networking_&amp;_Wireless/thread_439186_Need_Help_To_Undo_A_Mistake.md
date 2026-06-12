---
title: "Need Help To Undo A Mistake"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by Wraith's Hand on 2007-05-10
On Saturday, I finally got the shell that allows me to connect to my university's VPN to work and I noticed that one of the lines in the shell stated that I didn't have dhcpcd and so the shell used a different package to complete its task.  Foolishly, I thought that if I downloaded dhcpcd I would get a better connection.  Afterwards, I could not seem to connect to any wireless router.  I believe that it deleted a package, I foolishly simply accepted the change without really looking at what happened.  I think it is dhcp3-client, but I wanted to check before I mess around with it some more.  Or does anyone have any suggestions to get dhcpcd to work?

Also, I updated libcurl3 and synaptic that day as well,  if that would effect my wireless connection.  I don't think either would, but I thought I'd mention this just in case.

---

### Post by aysiu on 2007-05-10
I don't know what package you might have deleted, but if you install *ubuntu-desktop* through Synaptic, you should get the default set of Ubuntu packages back.

---

### Post by dbott67 on 2007-05-10
All installed/removed packages are tracked in the **/var/log/dpkg.log** files.  The current changes are in [COLOR=black]**dpkg.log**[/COLOR], while the older ones may be in **dpkg.log.1**.

For example, on my system, when I type **ls -all | grep dpkg** from the **/var/log** directory, I see 2 files:
```
dbott@feisty:/var/log$ [COLOR=Blue]**ls -all | grep dpkg**[/COLOR]
-rw-r-----  1 root       adm        14130 2007-05-10 10:34 dpkg.log
-rw-r-----  1 root       adm       669591 2007-04-30 17:29 dpkg.log.1
```One is dated today (May 10, 2007) and another dated back to April 30 (probably the last time I installed any packages).

Everything prior to April 30th is contained in the [COLOR=Blue]**dpkg.log.1**[/COLOR] file:

```
dbott@feisty:~$ [COLOR=Blue]**less /var/log/dpkg.log.1**[/COLOR]
2007-04-22 18:50:20 install base-files <none> 4ubuntu2
2007-04-22 18:50:20 status half-installed base-files 4ubuntu2
2007-04-22 18:50:22 status unpacked base-files 4ubuntu2
2007-04-22 18:50:22 status unpacked base-files 4ubuntu2
2007-04-22 18:50:22 install base-passwd <none> 3.5.11
2007-04-22 18:50:22 status half-installed base-passwd 3.5.11
2007-04-22 18:50:22 status unpacked base-passwd 3.5.11
2007-04-22 18:50:22 status unpacked base-passwd 3.5.11
2007-04-22 18:50:22 status unpacked base-passwd 3.5.11
2007-04-22 18:50:22 status half-configured base-passwd 3.5.11
2007-04-22 18:50:22 status installed base-passwd 3.5.11
2007-04-22 18:50:22 status unpacked base-files 4ubuntu2
2007-04-22 18:50:22 status unpacked base-files 4ubuntu2
2007-04-22 18:50:22 status unpacked base-files 4ubuntu2
2007-04-22 18:50:22 status unpacked base-files 4ubuntu2
2007-04-22 18:50:22 status unpacked base-files 4ubuntu2
2007-04-22 18:50:22 status unpacked base-files 4ubuntu2
2007-04-22 18:50:22 status half-configured base-files 4ubuntu2
2007-04-22 18:50:22 status installed base-files 4ubuntu2
2007-04-22 18:50:23 upgrade dpkg 1.13.24ubuntu6 1.13.24ubuntu6
2007-04-22 18:50:23 status half-configured dpkg 1.13.24ubuntu6
2007-04-22 18:50:23 status unpacked dpkg 1.13.24ubuntu6
2007-04-22 18:50:23 status half-installed dpkg 1.13.24ubuntu6
2007-04-22 18:50:23 status half-installed dpkg 1.13.24ubuntu6
2007-04-22 18:50:23 status unpacked dpkg 1.13.24ubuntu6
2007-04-22 18:50:23 status unpacked dpkg 1.13.24ubuntu6
2007-04-22 18:50:23 status unpacked dpkg 1.13.24ubuntu6
2007-04-22 18:50:23 status unpacked dpkg 1.13.24ubuntu6
2007-04-22 18:50:23 status unpacked dpkg 1.13.24ubuntu6
2007-04-22 18:50:23 status unpacked dpkg 1.13.24ubuntu6
2007-04-22 18:50:23 status unpacked dpkg 1.13.24ubuntu6
[COLOR=Blue]*... <snipped for brevity> ...*[/COLOR]
2007-04-29 18:27:05 status unpacked rdesktop 1.5.0-1ubuntu1
2007-04-29 18:27:05 status half-configured rdesktop 1.5.0-1ubuntu1
2007-04-29 18:27:05 status installed rdesktop 1.5.0-1ubuntu1
2007-04-30 15:33:21 install gadminhttpd <none> 0.0.4-1
2007-04-30 15:33:21 status half-installed gadminhttpd 0.0.4-1
2007-04-30 15:33:21 status unpacked gadminhttpd 0.0.4-1
2007-04-30 15:33:21 status unpacked gadminhttpd 0.0.4-1
2007-04-30 15:33:21 status unpacked gadminhttpd 0.0.4-1
2007-04-30 15:33:21 status half-configured gadminhttpd 0.0.4-1
2007-04-30 15:33:21 status installed gadminhttpd 0.0.4-1
2007-04-30 15:35:10 upgrade gadminhttpd 0.0.4-1 0.0.4-1
2007-04-30 15:35:10 status half-configured gadminhttpd 0.0.4-1
2007-04-30 15:35:10 status unpacked gadminhttpd 0.0.4-1
2007-04-30 15:35:10 status half-installed gadminhttpd 0.0.4-1
2007-04-30 15:35:10 status half-installed gadminhttpd 0.0.4-1
2007-04-30 15:35:10 status unpacked gadminhttpd 0.0.4-1
2007-04-30 15:35:10 status unpacked gadminhttpd 0.0.4-1
2007-04-30 15:35:10 status unpacked gadminhttpd 0.0.4-1
2007-04-30 15:35:10 status half-configured gadminhttpd 0.0.4-1
2007-04-30 15:35:10 status installed gadminhttpd 0.0.4-1
2007-04-30 17:29:08 status installed gadminhttpd 0.0.4-1
2007-04-30 17:29:08 remove gadminhttpd 0.0.4-1 0.0.4-1
2007-04-30 17:29:08 status half-configured gadminhttpd 0.0.4-1
2007-04-30 17:29:08 status half-installed gadminhttpd 0.0.4-1
2007-04-30 17:29:08 status config-files gadminhttpd 0.0.4-1
2007-04-30 17:29:08 purge gadminhttpd 0.0.4-1 0.0.4-1
2007-04-30 17:29:08 status config-files gadminhttpd 0.0.4-1
2007-04-30 17:29:08 status config-files gadminhttpd 0.0.4-1
2007-04-30 17:29:08 status config-files gadminhttpd 0.0.4-1
2007-04-30 17:29:08 status config-files gadminhttpd 0.0.4-1
2007-04-30 17:29:08 status config-files gadminhttpd 0.0.4-1
2007-04-30 17:29:08 status not-installed gadminhttpd <none>

```So, you could just browse through that log file and look for the packages that were removed:
```
dbott@feisty:~$ [COLOR=Blue]**less /var/log/dpkg.log.1 | grep remove**[/COLOR]
2007-04-22 15:44:30 remove totem-mozilla 2.18.1-0ubuntu3 2.18.1-0ubuntu3
2007-04-22 15:45:45 remove totem-gstreamer 2.18.1-0ubuntu3 2.18.1-0ubuntu3
2007-04-22 16:10:02 remove xorg-driver-fglrx 7.1.0-8.34.8+2.6.20.5-15.20 7.1.0-8.34.8+2.6.20.5-15.20
2007-04-22 16:10:22 remove linux-generic 2.6.20.15.14 2.6.20.15.14
2007-04-22 16:10:22 remove linux-restricted-modules-generic 2.6.20.15.14 2.6.20.15.14
2007-04-22 16:10:22 remove linux-restricted-modules-2.6.20-15-generic 2.6.20.5-15.20 2.6.20.5-15.20
2007-04-26 11:40:11 remove winbind 3.0.24-2ubuntu1 3.0.24-2ubuntu1
2007-04-26 14:01:15 remove samba 3.0.24-2ubuntu1 3.0.24-2ubuntu1
2007-04-26 14:11:35 remove winbind 3.0.24-2ubuntu1 3.0.24-2ubuntu1
2007-04-30 17:29:08 remove gadminhttpd 0.0.4-1 0.0.4-1

```If you have any difficulties, just post the output of the last command here.

-Dave

---

### Post by Wraith's Hand on 2007-05-10
Hmm.  It appears that I was wrong and that I didn't delete another file when I installed dhcpcd.   I wonder why it stopped working all of the sudden.

---

### Post by Wraith's Hand on 2007-05-11
Quick update, I got my wireless card to work at a coffee shop last night, so I'm not completely without a wireless connection like I thought I was or reinstalling *ubuntu-desktop* helped. Anyways, it works now.  I hope that I can contact a friend of a friend to help me trouble shoot the VPN shell sometime soon.

ETA: Thanks for the suggestions.

---

