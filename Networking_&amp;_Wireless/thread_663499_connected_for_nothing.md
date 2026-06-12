---
title: "connected for nothing"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by bartoldo on 2008-01-10
Well, the machine where I have the problem is not properly an Ubuntu (although I am writting this on an Ubuntu :)), but just an Debian Etch. However, I'll be so insolent to ask for a help here, since somebody in this learned community might be able to give me an enllightement...
So , I can connect to the Internet (using an ADSL modem with Eciadsl program) and I am connected indeed, I can ping, telnet (to port 80 too), lookup etc., here is a proof: 

telnet google.com 80 

Trying 209.85.135.104...
Connected to [www.l.google.com.](www.l.google.com.)
Escape character is '^]'. 

If I give the command "GET / HTTP/1.0", I get the following:

HTTP/1.0 302 Found
Location: [http://www.google.it/](http://www.google.it/)
Cache-Control: private
Set-Cookie: PREF=ID=2b473b8a23266481:TM=1199939109:LM=11999391 09:S=VkUR-S-LP3Vjo6dl; expires=Sat, 09-Jan-2010 04:25:09 GMT; path=/; domain=.google.com
Content-Type: text/html
Server: gws
Content-Length: 218
Date: Thu, 10 Jan 2008 04:25:09 GMT
Connection: Close

But, no one my browser (Opera, Firefox, Konqueror, Galeon, Epiphany etc.) seems to see it. They are "connecing to" a web server... forever. In fact, their behavior looks like they are being redirected... to nowhere ("web sever found, waiting for a response", or something alike). But, if there actually is not any connection, they give me an error immediately. Nothing changes if I try IP address instead of URL. I can even send mail and Evolution can login to my POP account (and even see how many messeges there're), but, doesn't seem able to rethrieve them ("checking mail"... forever).
I am posting the outputs of some commands (route, ip route, netstat) in attachment. (Obviously, the first part of my IP is fake, as well as the computer and network names.) 

On the other hand, I can, without any problems, browse my LAN's web (web server on another machine). And vice versa. But, the machine where I have the problem is supposed to be the Internet gateway, so I can't browse the Internet from LAN neither. I feel that the key issue is that I cannot receive any *larger* packages from Internet. I am connecting via an ADSL modem, and after negotiation I have MPU 1492. On ethernet I have 1500 (and that machine, beside an Internet address, have its local static address 192.168.0.1 of the network card).
Everything looks to me like there is some firewall and/or a proxy active, but, I am not able to find it and as long as I am aware of there shouldn't be an active firewall. What could it be!!!? I don't know how to play with iptables configuration (or something else, if it's something else).
Here is the list of running processes:
[list]
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   87 ?        00:00:00 kseriod
  125 ?        00:00:00 pdflush
  126 ?        00:00:00 pdflush
  127 ?        00:00:00 kswapd0
  128 ?        00:00:00 aio/0
  572 ?        00:00:00 khubd
 1592 ?        00:00:00 udevd
 2082 ?        00:00:00 kgameportd
 2103 ?        00:00:00 kpsmoused
 2350 ?        00:00:00 cqueue/0
 2400 ?        00:00:00 jfsIO
 2401 ?        00:00:00 jfsCommit
 2402 ?        00:00:00 jfsSync
 2454 ?        00:00:00 xfslogd/0
 2455 ?        00:00:00 xfsdatad/0
 2575 ?        00:00:00 kcryptd/0
 2593 ?        00:00:00 exec-osm/0
 2608 ?        00:00:00 block-osm/0
 2669 ?        00:00:00 pciehpd_event
 2712 ?        00:00:00 ata/0
 2713 ?        00:00:00 ata_aux
 2831 ?        00:00:00 ocfs2_wq
 3004 ?        00:00:00 kmirrord
 6012 ?        00:00:00 reiserfs/0
 6044 ?        00:00:00 kjournald
 6047 ?        00:00:00 kjournald
 6050 ?        00:00:00 kjournald
 6654 ?        00:00:00 portmap
 6957 ?        00:00:00 syslogd
 6963 ?        00:00:00 klogd
 7019 ?        00:00:00 named
 7033 ?        00:00:00 lwresd
 7158 ?        00:00:00 postmaster
 7299 ?        00:00:00 acpid
 7327 ?        00:00:00 cupsd
 7347 ?        00:00:00 dbus-daemon
 7355 ?        00:00:03 hald
 7356 ?        00:00:00 hald-runner
 7371 ?        00:00:00 hald-addon-acpi
 7408 ?        00:00:00 hald-addon-keyb
 7431 ?        00:00:00 hald-addon-stor
 7433 ?        00:00:00 hald-addon-stor
 7738 ?        00:00:00 dhcdbd
 7745 ?        00:00:00 NetworkManager
 7776 ?        00:00:00 avahi-daemon
 7777 ?        00:00:00 avahi-daemon
 7784 ?        00:00:00 NetworkManagerD
 7863 ?        00:00:00 exim4
 7879 ?        00:00:00 lisa
 7891 ?        00:00:00 netdaemon
 7901 ?        00:00:00 atalkd
 7912 ?        00:00:00 papd
 7914 ?        00:00:00 afpd
 7916 ?        00:00:00 cnid_metad
 7929 ?        00:00:00 nfsd4
 7930 ?        00:00:00 nfsd
 7931 ?        00:00:00 nfsd
 7932 ?        00:00:00 nfsd
 7933 ?        00:00:00 nfsd
 7934 ?        00:00:00 nfsd
 7935 ?        00:00:00 nfsd
 7936 ?        00:00:00 nfsd
 7937 ?        00:00:00 nfsd
 7938 ?        00:00:00 lockd
 7939 ?        00:00:00 rpciod/0
 7943 ?        00:00:00 rpc.mountd
 7959 ?        00:00:00 inetd
 7967 ?        00:00:00 pptpd
 7971 ?        00:00:00 nmbd
 7973 ?        00:00:00 smbd
 7980 ?        00:00:00 slpd
 7982 ?        00:00:00 smbd
 7990 ?        00:00:00 sshd
 7993 ?        00:00:00 swapd
 7997 ?        00:00:00 uml_switch
 8014 ?        00:00:00 winbindd
 8020 ?        00:00:00 winbindd
 8094 ?        00:00:00 xinetd
 8127 ?        00:00:00 gdm
 8133 ?        00:00:00 gdm
 8136 tty7     00:01:47 Xorg
 8139 ?        00:00:00 rpc.statd
 8148 ?        00:00:00 rpc.idmapd
 8171 ?        00:00:00 miniserv.pl
 8190 ?        00:00:00 miniserv.pl
 8216 ?        00:00:00 atd
 8223 ?        00:00:00 cron
 8262 ?        00:00:00 apache
 8279 ?        00:00:00 apache-ssl
 8350 tty1     00:00:00 getty
 8351 tty2     00:00:00 getty
 8352 tty3     00:00:00 getty
 8353 tty4     00:00:00 getty
 8354 tty5     00:00:00 getty
 8355 tty6     00:00:00 getty
 8520 ?        00:00:00 startkde
 8568 ?        00:00:00 ssh-agent
 8571 ?        00:00:00 dbus-launch
 8572 ?        00:00:00 dbus-daemon
 8600 ?        00:00:00 start_kdeinit
 8601 ?        00:00:00 kdeinit
 8604 ?        00:00:00 dcopserver
 8606 ?        00:00:00 klauncher
 8608 ?        00:00:02 kded
 8613 ?        00:00:00 kwrapper
 8615 ?        00:00:00 ksmserver
 8616 ?        00:00:04 kwin
 8618 ?        00:00:02 kdesktop
 8620 ?        00:00:10 kicker
 8625 ?        00:00:04 artsd
 8627 ?        00:00:00 kaccess
 8629 ?        00:00:00 konqueror
 8631 ?        00:00:00 krandrtray
 8632 ?        00:00:00 konqueror
 8633 ?        00:00:02 nautilus
 8636 ?        00:00:00 gconfd-2
 8637 ?        00:00:00 kmix
 8638 ?        00:00:02 netapplet
 8641 ?        00:00:00 smb4k
 8642 ?        00:00:00 konqueror
 8643 ?        00:00:00 konqueror
 8644 ?        00:00:00 kedit
 8645 ?        00:00:00 kedit
 8646 ?        00:00:00 konqueror
 8647 ?        00:00:00 konqueror
 8648 ?        00:00:00 konqueror
 8649 ?        00:00:00 konqueror
 8650 ?        00:00:00 konqueror
 8651 ?        00:00:00 konqueror
 8652 ?        00:00:00 konqueror
 8653 ?        00:00:00 konqueror
 8656 ?        00:00:00 bonobo-activati
 8657 ?        00:00:00 kedit
 8663 ?        00:00:00 gnome-vfs-daemo
 8664 ?        00:00:00 knotify
 8671 ?        00:00:00 winbindd
 8672 ?        00:00:00 kedit
 8688 ?        00:00:00 kedit
 8689 ?        00:00:00 kedit
 8691 ?        00:00:03 konsole
 8695 ?        00:00:00 mapping-daemon
 8697 ?        00:00:00 kgpg
 8701 ?        00:00:00 kedit
 8703 ?        00:00:00 kget
 8704 ?        00:00:00 kedit
 8706 ?        00:00:00 kedit
 8707 ?        00:00:00 evolution-alarm
 8716 pts/0    00:00:00 bash
 8719 ?        00:00:01 evolution-data-
 8734 ?        00:00:00 klipper
 8748 ?        00:00:00 korgac
 8752 ?        00:00:00 kmail
 9192 ?        00:00:00 apache
 9193 ?        00:00:00 apache
 9194 ?        00:00:00 apache
 9195 ?        00:00:00 apache
 9224 ?        00:00:00 gcache
 9225 ?        00:00:00 apache-ssl
 9256 ?        00:00:00 apache
 9257 ?        00:00:00 apache-ssl
 9258 ?        00:00:00 apache-ssl
 9259 ?        00:00:00 apache-ssl
 9260 ?        00:00:00 apache-ssl
 9302 ?        00:00:00 dirmngr
 9660 ?        00:00:00 kdesu
 9661 ?        00:00:49 konqueror
 9765 ?        00:00:20 konqueror
10866 ?        00:00:00 pppd
10911 ?        00:00:21 eciadsl-pppoeci
10974 ?        00:00:00 apache
11709 ?        00:00:00 kio_uiserver
12059 ?        00:00:00 kio_file
12097 ?        00:00:00 smbd
12393 ?        00:00:00 kio_thumbnail
12396 pts/0    00:00:00 ps
[/list] 
I have 5 OS's on the machine that I use to connect to the Ineternat, but I am bound to use Win2K. Please, help me to use Debian!

---

