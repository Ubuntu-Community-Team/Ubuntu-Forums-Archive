---
title: "iptables error after latest upgrade"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by Turias on 2008-02-11
Hello.  I am running 7.10 "Gutsy Gibbon" and when my machine starts up I run the following iptables command:

iptables -t nat -A PREROUTING -p tcp -i eth0*-s 118.22.0.0/16 --dport 443*-j REDIRECT --to-ports 22

The purpose behind this command is to let me SSH into this machine over port 443 when I am at a location that blocks port 22.  This command worked fine until last night after I ran aptitude dist-upgrade and rebooted.  Now when I run it I get the following error:

Bad argument `118.22.0.0/16'
Try `iptables -h' or 'iptables --help' for more information.

Running a similar command without the IP mask works fine.

It's been a while since I last rebooted this machine, so a bunch of packages have changed.  All of the changes have occurred when running the command 'aptitude dist-upgrade'.  I do look through the list of proposed changes before accepting them, and nothing has ever looked out of the ordinary.  Searching through my aptitude log I can see that these packages have all been upgraded recently:

```

[UPGRADE] cupsys 1.3.2-1ubuntu7.1 -> 1.3.2-1ubuntu7.3
[UPGRADE] cupsys-bsd 1.3.2-1ubuntu7.1 -> 1.3.2-1ubuntu7.3
[UPGRADE] cupsys-client 1.3.2-1ubuntu7.1 -> 1.3.2-1ubuntu7.3
[UPGRADE] cupsys-common 1.3.2-1ubuntu7.1 -> 1.3.2-1ubuntu7.3
[UPGRADE] deskbar-applet 2.20.0-0ubuntu2 -> 2.20.1-0ubuntu1
[UPGRADE] libcupsimage2 1.3.2-1ubuntu7.1 -> 1.3.2-1ubuntu7.3
[UPGRADE] libcupsys2 1.3.2-1ubuntu7.1 -> 1.3.2-1ubuntu7.3
[UPGRADE] libpt-1.10.0 1.10.10-0ubuntu2 -> 1.10.10-0ubuntu2.1
[UPGRADE] libpt-plugins-alsa 1.10.10-0ubuntu2 -> 1.10.10-0ubuntu2.1
[UPGRADE] libpt-plugins-v4l 1.10.10-0ubuntu2 -> 1.10.10-0ubuntu2.1
[UPGRADE] libpt-plugins-v4l2 1.10.10-0ubuntu2 -> 1.10.10-0ubuntu2.1
[UPGRADE] libsnmp-base 5.3.1-6ubuntu2 -> 5.3.1-6ubuntu2.1
[UPGRADE] libsnmp10 5.3.1-6ubuntu2 -> 5.3.1-6ubuntu2.1
[UPGRADE] openssh-client 1:4.6p1-5build1 -> 1:4.6p1-5ubuntu0.1
[UPGRADE] openssh-server 1:4.6p1-5build1 -> 1:4.6p1-5ubuntu0.1
[UPGRADE] squid 2.6.14-1ubuntu2 -> 2.6.14-1ubuntu2.1
[UPGRADE] squid-common 2.6.14-1ubuntu2 -> 2.6.14-1ubuntu2.1
[UPGRADE] ssh-askpass-gnome 1:4.6p1-5build1 -> 1:4.6p1-5ubuntu0.1
[UPGRADE] tomboy 0.8.0-1 -> 0.8.0-1ubuntu0.1
[UPGRADE] evolution-data-server 1.12.1-0ubuntu1 -> 1.12.1-0ubuntu2
[UPGRADE] evolution-data-server-common 1.12.1-0ubuntu1 -> 1.12.1-0ubuntu2
[UPGRADE] gimp 2.4.0~rc3-1ubuntu7 -> 2.4.2-0ubuntu0.7.10.1
[UPGRADE] gimp-data 2.4.0~rc3-1ubuntu7 -> 2.4.2-0ubuntu0.7.10.1
[UPGRADE] gimp-python 2.4.0~rc3-1ubuntu7 -> 2.4.2-0ubuntu0.7.10.1
[UPGRADE] libcamel1.2-10 1.12.1-0ubuntu1 -> 1.12.1-0ubuntu2
[UPGRADE] libdb4.4 4.4.20-8.1ubuntu3 -> 4.4.20-8.1ubuntu3.1
[UPGRADE] libebook1.2-9 1.12.1-0ubuntu1 -> 1.12.1-0ubuntu2
[UPGRADE] libecal1.2-7 1.12.1-0ubuntu1 -> 1.12.1-0ubuntu2
[UPGRADE] libedata-book1.2-2 1.12.1-0ubuntu1 -> 1.12.1-0ubuntu2
[UPGRADE] libedata-cal1.2-6 1.12.1-0ubuntu1 -> 1.12.1-0ubuntu2
[UPGRADE] libedataserver1.2-9 1.12.1-0ubuntu1 -> 1.12.1-0ubuntu2
[UPGRADE] libedataserverui1.2-8 1.12.1-0ubuntu1 -> 1.12.1-0ubuntu2
[UPGRADE] libegroupwise1.2-13 1.12.1-0ubuntu1 -> 1.12.1-0ubuntu2
[UPGRADE] libexchange-storage1.2-3 1.12.1-0ubuntu1 -> 1.12.1-0ubuntu2
[UPGRADE] libgimp2.0 2.4.0~rc3-1ubuntu7 -> 2.4.2-0ubuntu0.7.10.1
[UPGRADE] avahi-autoipd 0.6.20-2ubuntu3 -> 0.6.20-2ubuntu3.1
[UPGRADE] avahi-daemon 0.6.20-2ubuntu3 -> 0.6.20-2ubuntu3.1
[UPGRADE] cupsys 1.3.2-1ubuntu7.3 -> 1.3.2-1ubuntu7.5
[UPGRADE] cupsys-bsd 1.3.2-1ubuntu7.3 -> 1.3.2-1ubuntu7.5
[UPGRADE] cupsys-client 1.3.2-1ubuntu7.3 -> 1.3.2-1ubuntu7.5
[UPGRADE] cupsys-common 1.3.2-1ubuntu7.3 -> 1.3.2-1ubuntu7.5
[UPGRADE] libapache2-mod-php5 5.2.3-1ubuntu6.2 -> 5.2.3-1ubuntu6.3
[UPGRADE] libavahi-client3 0.6.20-2ubuntu3 -> 0.6.20-2ubuntu3.1
[UPGRADE] libavahi-common-data 0.6.20-2ubuntu3 -> 0.6.20-2ubuntu3.1
[UPGRADE] libavahi-common3 0.6.20-2ubuntu3 -> 0.6.20-2ubuntu3.1
[UPGRADE] libavahi-compat-libdnssd1 0.6.20-2ubuntu3 -> 0.6.20-2ubuntu3.1
[UPGRADE] libavahi-core5 0.6.20-2ubuntu3 -> 0.6.20-2ubuntu3.1
[UPGRADE] libavahi-glib1 0.6.20-2ubuntu3 -> 0.6.20-2ubuntu3.1
[UPGRADE] libcupsimage2 1.3.2-1ubuntu7.3 -> 1.3.2-1ubuntu7.5
[UPGRADE] libcupsys2 1.3.2-1ubuntu7.3 -> 1.3.2-1ubuntu7.5
[UPGRADE] libpq5 8.2.5-1.1 -> 8.2.6-0ubuntu0.7.10.1
[UPGRADE] libxml2 2.6.30.dfsg-2ubuntu1 -> 2.6.30.dfsg-2ubuntu1.1
[UPGRADE] libxml2-utils 2.6.30.dfsg-2ubuntu1 -> 2.6.30.dfsg-2ubuntu1.1
[UPGRADE] php5 5.2.3-1ubuntu6.2 -> 5.2.3-1ubuntu6.3
[UPGRADE] php5-common 5.2.3-1ubuntu6.2 -> 5.2.3-1ubuntu6.3
[UPGRADE] php5-curl 5.2.3-1ubuntu6.2 -> 5.2.3-1ubuntu6.3
[UPGRADE] php5-gd 5.2.3-1ubuntu6.2 -> 5.2.3-1ubuntu6.3
[UPGRADE] php5-mysql 5.2.3-1ubuntu6.2 -> 5.2.3-1ubuntu6.3
[UPGRADE] php5-pgsql 5.2.3-1ubuntu6.2 -> 5.2.3-1ubuntu6.3
[UPGRADE] postgresql-8.2 8.2.5-1.1 -> 8.2.6-0ubuntu0.7.10.1
[UPGRADE] postgresql-client-8.2 8.2.5-1.1 -> 8.2.6-0ubuntu0.7.10.1
[UPGRADE] python-libxml2 2.6.30.dfsg-2ubuntu1 -> 2.6.30.dfsg-2ubuntu1.1
[UPGRADE] avahi-autoipd 0.6.20-2ubuntu3.1 -> 0.6.20-2ubuntu3.2
[UPGRADE] avahi-daemon 0.6.20-2ubuntu3.1 -> 0.6.20-2ubuntu3.2
[UPGRADE] libavahi-client3 0.6.20-2ubuntu3.1 -> 0.6.20-2ubuntu3.2
[UPGRADE] libavahi-common-data 0.6.20-2ubuntu3.1 -> 0.6.20-2ubuntu3.2
[UPGRADE] libavahi-common3 0.6.20-2ubuntu3.1 -> 0.6.20-2ubuntu3.2
[UPGRADE] libavahi-compat-libdnssd1 0.6.20-2ubuntu3.1 -> 0.6.20-2ubuntu3.2
[UPGRADE] libavahi-core5 0.6.20-2ubuntu3.1 -> 0.6.20-2ubuntu3.2
[UPGRADE] libavahi-glib1 0.6.20-2ubuntu3.1 -> 0.6.20-2ubuntu3.2
[UPGRADE] libxfont1 1:1.3.0-0ubuntu1 -> 1:1.3.0-0ubuntu1.1
[UPGRADE] xserver-xorg-core 2:1.3.0.0.dfsg-12ubuntu8 -> 2:1.3.0.0.dfsg-12ubuntu8.1
[UPGRADE] bind9-host 1:9.4.1-P1-3 -> 1:9.4.1-P1-3ubuntu1
[UPGRADE] dnsutils 1:9.4.1-P1-3 -> 1:9.4.1-P1-3ubuntu1
[UPGRADE] ghostscript 8.61.dfsg.1~svn8187-0ubuntu3.2 -> 8.61.dfsg.1~svn8187-0ubuntu3.3
[UPGRADE] ghostscript-x 8.61.dfsg.1~svn8187-0ubuntu3.2 -> 8.61.dfsg.1~svn8187-0ubuntu3.3
[UPGRADE] gs-esp-x 8.61.dfsg.1~svn8187-0ubuntu3.2 -> 8.61.dfsg.1~svn8187-0ubuntu3.3
[UPGRADE] libbind9-30 1:9.4.1-P1-3 -> 1:9.4.1-P1-3ubuntu1
[UPGRADE] libdns32 1:9.4.1-P1-3 -> 1:9.4.1-P1-3ubuntu1
[UPGRADE] libgs8 8.61.dfsg.1~svn8187-0ubuntu3.2 -> 8.61.dfsg.1~svn8187-0ubuntu3.3
[UPGRADE] libisc32 1:9.4.1-P1-3 -> 1:9.4.1-P1-3ubuntu1
[UPGRADE] libisccc30 1:9.4.1-P1-3 -> 1:9.4.1-P1-3ubuntu1
[UPGRADE] libisccfg30 1:9.4.1-P1-3 -> 1:9.4.1-P1-3ubuntu1
[UPGRADE] liblwres30 1:9.4.1-P1-3 -> 1:9.4.1-P1-3ubuntu1
[UPGRADE] xserver-xorg-core 2:1.3.0.0.dfsg-12ubuntu8.1 -> 2:1.3.0.0.dfsg-12ubuntu8.3
[UPGRADE] app-install-data-commercial 8.3 -> 8.4
[UPGRADE] apache2 2.2.4-3build1 -> 2.2.4-3ubuntu0.1
[UPGRADE] apache2-mpm-prefork 2.2.4-3build1 -> 2.2.4-3ubuntu0.1
[UPGRADE] apache2-utils 2.2.4-3build1 -> 2.2.4-3ubuntu0.1
[UPGRADE] apache2.2-common 2.2.4-3build1 -> 2.2.4-3ubuntu0.1
[UPGRADE] firefox 2.0.0.11+2nobinonly-0ubuntu0.7.10 -> 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
[UPGRADE] firefox-gnome-support 2.0.0.11+2nobinonly-0ubuntu0.7.10 -> 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
[UPGRADE] linux-headers-2.6.22-14 2.6.22-14.47 -> 2.6.22-14.51
[UPGRADE] linux-headers-2.6.22-14-generic 2.6.22-14.47 -> 2.6.22-14.51
[UPGRADE] linux-image-2.6.22-14-386 2.6.22-14.47 -> 2.6.22-14.51
[UPGRADE] linux-libc-dev 2.6.22-14.47 -> 2.6.22-14.51

```

Does anyone have any idea what the problem might be?  Thanks so much for any help.

---

### Post by The Cog on 2008-02-11
Odd. I don't know if it helps, but I'm up to date on Gutsy, and I don't get any error with that command you posted (except I had to replace the two *s with spaces). I aldo checked that the rule had been entered correctly.
```
root@StevesPC:~# iptables -t nat -A PREROUTING -p tcp -i eth0 -s 118.22.0.0/16 --dport 443 -j REDIRECT --to-ports 22
root@StevesPC:~# iptables -t nat -L -n
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
REDIRECT   tcp  --  118.22.0.0/16        0.0.0.0/0           tcp dpt:443 redir ports 22 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
root@StevesPC:~# iptables -t nat -D PREROUTING -p tcp -i eth0 -s 118.22.0.0/16 --dport 443 -j REDIRECT --to-ports 22
root@StevesPC:~# 

```

---

### Post by Turias on 2008-02-11
Well, you caught it.  Those stars weren't supposed to be there.  I copied and pasted that command from an Adium chat log into a text file, and apparently two UTF8 characters snuck their way in there.  hexdump shows them as c2a0 (non-breaking spaces).  I didn't run into the problem before since I haven't restarted my server in forever.

Luckily this forum software noticed something was weird and replaced those characters with asterisks.  My terminal and text file editor just displays them as spaces.  Thanks for taking a look at this and noticing what I did not.  You saved me from going insane!

---

