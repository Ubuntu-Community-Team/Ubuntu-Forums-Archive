---
title: "Mystery program using bandwidth"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by ottothecow on 2008-03-09
My laptop has recently been having horrible battery life but I found that it was fine when I pulled out the wireless card.  I did some poking around and realized that at idle I might be using ~30kb/s of bandwidth in system monitor.  I had no apps open that should be using it so I found a few programs that would give me a breakdown of what is using bandwidth.  Here is the nethogs output:

NetHogs version 0.6.0

  PID USER     PROGRAM                      DEV        SENT      RECEIVED       
0     root     unknown                                 0.000      27.625 KB/sec
6004  otto     skype                        eth1       0.000       0.000 KB/sec
5900  otto     pidgin                       eth1       0.000       0.000 KB/sec
5826  otto     firefox-bin                  eth1       0.000       0.000 KB/sec

  TOTAL                                                0.000      27.625 KB/sec 

It looks like there is some unknown program using my bandwidth as root.  This makes it kind of hard for me to track down.  Hopefully someone has some ideas?

Here is my ps-A
otto@littleblue:~$ sudo ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   26 ?        00:00:00 kblockd/0
   27 ?        00:00:00 kacpid
   28 ?        00:00:00 kacpi_notify
  119 ?        00:00:00 kseriod
  136 ?        00:00:00 pdflush
  137 ?        00:00:00 pdflush
  138 ?        00:00:00 kswapd0
  190 ?        00:00:00 aio/0
 1980 ?        00:00:00 ksuspend_usbd
 1981 ?        00:00:00 khubd
 2049 ?        00:00:00 ata/0
 2050 ?        00:00:00 ata_aux
 2084 ?        00:00:00 scsi_eh_0
 2085 ?        00:00:00 scsi_eh_1
 2342 ?        00:00:00 kjournald
 2548 ?        00:00:00 udevd
 3432 ?        00:00:00 pccardd
 3450 ?        00:00:00 kpsmoused
 3471 ?        00:00:00 pccardd
 3521 ?        00:00:00 irda_sir_wq
 3936 ?        00:00:00 portmap
 3955 ?        00:00:00 rpc.statd
 4082 tty4     00:00:00 getty
 4083 tty5     00:00:00 getty
 4087 tty2     00:00:00 getty
 4088 tty3     00:00:00 getty
 4089 tty1     00:00:00 getty
 4090 tty6     00:00:00 getty
 4159 ?        00:00:00 kondemand/0
 4370 ?        00:00:00 acpid
 4452 ?        00:00:00 syslogd
 4507 ?        00:00:00 dd
 4509 ?        00:00:00 klogd
 4530 ?        00:00:00 dbus-daemon
 4546 ?        00:00:03 NetworkManager
 4560 ?        00:00:00 NetworkManagerD
 4573 ?        00:00:00 system-tools-ba
 4574 ?        00:00:00 dbus-daemon
 4593 ?        00:00:00 hald
 4594 ?        00:00:00 hald-runner
 4637 ?        00:00:00 hald-addon-keyb
 4638 ?        00:00:00 hald-addon-keyb
 4640 ?        00:00:00 hald-addon-cpuf
 4641 ?        00:00:00 hald-addon-acpi
 4642 ?        00:00:00 hald-addon-keyb
 4643 ?        00:00:00 hald-addon-keyb
 4682 ?        00:00:00 hald-addon-stor
 4734 ?        00:00:00 cupsd
 4815 ?        00:00:00 thinkpad-keys
 4822 ?        00:00:00 hald-addon-keyb
 4875 ?        00:00:00 lockd
 4876 ?        00:00:00 rpciod/0
 4880 ?        00:00:00 nfsd4
 4881 ?        00:00:00 nfsd
 4882 ?        00:00:00 nfsd
 4883 ?        00:00:00 nfsd
 4884 ?        00:00:00 nfsd
 4885 ?        00:00:00 nfsd
 4886 ?        00:00:00 nfsd
 4887 ?        00:00:00 nfsd
 4888 ?        00:00:00 nfsd
 4892 ?        00:00:00 rpc.mountd
 4905 ?        00:00:01 ntop
 4948 ?        00:00:00 nmbd
 4950 ?        00:00:00 smbd
 5001 ?        00:00:00 console-kit-dae
 5079 ?        00:00:00 dhcdbd
 5096 ?        00:00:00 hcid
 5106 ?        00:00:00 bluetoothd-serv
 5110 ?        00:00:00 bluetoothd-serv
 5111 ?        00:00:00 smbd
 5114 ?        00:00:00 krfcommd
 5144 ?        00:00:00 gdm
 5147 ?        00:00:00 gdm
 5152 tty7     00:02:41 Xorg
 5176 ?        00:00:00 ntpd
 5233 ?        00:00:00 atd
 5247 ?        00:00:00 cron
 5533 ?        00:00:00 avahi-autoipd
 5534 ?        00:00:00 avahi-autoipd
 5537 ?        00:00:00 gnome-keyring-d
 5540 ?        00:00:00 x-session-manag
 5575 ?        00:00:00 ssh-agent
 5577 ?        00:00:01 gconfd-2
 5582 ?        00:00:07 at-spi-registry
 5585 ?        00:00:00 bonobo-activati
 5591 ?        00:00:00 dbus-daemon
 5593 ?        00:00:00 gnome-settings-
 5599 ?        00:00:09 metacity
 5600 ?        00:00:11 gnome-panel
 5602 ?        00:00:01 nautilus
 5607 ?        00:00:00 gnome-volume-ma
 5611 ?        00:00:00 dhclient3
 5651 ?        00:00:00 sshd
 5655 ?        00:00:00 vino-session
 5658 ?        00:00:00 update-notifier
 5663 ?        00:00:00 gnome-vfs-daemo
 5671 ?        00:00:00 trackerd
 5675 ?        00:00:03 nm-applet
 5676 ?        00:00:00 python
 5683 ?        00:00:00 trashapplet
 5692 ?        00:00:00 dbus-launch
 5693 ?        00:00:00 dbus-daemon
 5695 ?        00:00:00 gnome-vfs-daemo
 5706 ?        00:00:03 gnome-screensav
 5712 ?        00:00:00 gnome-power-man
 5716 ?        00:00:00 mapping-daemon
 5745 ?        00:00:13 wpa_supplicant
 5763 ?        00:00:02 fast-user-switc
 5767 ?        00:00:00 mixer_applet2
 5769 ?        00:00:00 dhclient
 5782 ?        00:00:00 firefox
 5800 ?        00:00:00 evolution-excha
 5809 ?        00:00:00 run-mozilla.sh
 5826 ?        00:03:35 firefox-bin
 5870 ?        00:00:00 evolution-data-
 5900 ?        00:00:06 pidgin
 5911 ?        00:00:00 thunderbird
 5923 ?        00:00:00 run-mozilla.sh
 5927 ?        00:01:28 thunderbird-bin
 5985 ?        00:00:02 deskbar-applet
 6004 ?        00:00:14 skype
 6185 ?        00:00:12 gnome-terminal
 6187 ?        00:00:00 gnome-pty-helpe
 6188 pts/0    00:00:00 bash
 6219 pts/0    00:00:55 nethogs
 6309 ?        00:00:00 notification-da
 6671 pts/1    00:00:00 bash
 6690 pts/1    00:00:00 ps
otto@littleblue:~$ 

See anything in there?  I need to get this figured out as my connection feels very slow now and I get very little battery life (it's old but with only mild internet use I used to be able to go for an hour...now it is like 15 min).

Thanks

---

### Post by vasquez on 2008-03-09
maybe you are hacked and your band is used for spam/ircbots/portscan etc., look for some anti-rootkit programs to give it a scan

---

### Post by ottothecow on 2008-03-09
ran chkrootkit and rkhunter

both found nothing although rkhunter warned on hidden files.  here is the bit from the logfile:
[21:12:58]   Checking for hidden files and directories       [ Warning ]
[21:12:58] Warning: Hidden directory found: /etc/.java
[21:12:58] Warning: Hidden directory found: /dev/.static
[21:12:58] Warning: Hidden directory found: /dev/.udev
[21:12:58] Warning: Hidden directory found: /dev/.initramfs

*edit* This is on Gutsy with updates pretty regularily applied.  The problem started within the past month though I only noticed the cause this week.

---

### Post by ottothecow on 2008-03-10
Is there something else out there that can tell me what program us using the traffic since nethogs cannot?

I find it hard to believe that a process on linux could be completely unknown...there should be some way to find it.  

I wonder if it isn't something with mDNS (the network I'm on probably has a lot of open itunes shares and stuff) but if I kill the avahi stuff the problem still exists.

---

### Post by ottothecow on 2008-03-10
anybody have a good idea about what this might be?

---

### Post by The Cog on 2008-03-10
Try this command:
**sudo netstat -plantu**
which should list all the active TCP and UDP sockets along with their owning processes.

---

### Post by ottothecow on 2008-03-10
[http://pastebin.com/m6a70b404](http://pastebin.com/m6a70b404)

It doen't look like anything is there (it just shows the two tcp connections to flashbin but my nethogs output still looks like this:

NetHogs version 0.6.0

  PID USER     PROGRAM                      DEV        SENT      RECEIVED       
0     root     unknown                                 0.000      14.414 KB/sec
6118  otto     firefox-bin                  eth1       0.000       0.000 KB/sec

  TOTAL                                                0.000      14.414 KB/sec

---

### Post by The Cog on 2008-03-11
IN that case, how about using
**sudo tcpdump**
for a few seconds (Use Ctrl-C to stop it again). Pipe it to a file to save the output like this:
**sudo tcpdump > tcpdump.txt**

---

### Post by Drostie on 2008-03-12
I'm having the same problem, but I've gotten a step further in the analysis.

In my case, I've determined that the traffic does not originate from my computer -- I am on a local network, and it appears that Ubuntu is regarding *all of the broadcast wireless traffic* as incoming data -- even when that data is not directed at my particular IP.

(Start up a torrent on a different computer on the same network, and watch the DL amounts soar.)

I'm interested in the solution, though, too: how does one keep their wireless connection stats from detecting all of the surrounding traffic?

---

### Post by Mithrilhall on 2008-03-14
Try...

Wireshark
iftop
iptraf

---

### Post by ottothecow on 2008-03-17
> **Drostie said:**
> 
In my case, I've determined that the traffic does not originate from my computer -- I am on a local network, and it appears that Ubuntu is regarding *all of the broadcast wireless traffic* as incoming data -- even when that data is not directed at my particular IP.


My problem seems to be similar.  If I run iftop on the connection, my IP is not listed as either the source or the destination of the traffic flow in question.  This doesn't seem to be simply a problem of it reporting it as bandwidth though as my connection is definately slow (the updates I just downloaded went at less than 10kb/s despite being on the university wireless and browsing feels slow).

Why would other peoples traffic be getting processed by me and not just ignored?

---

### Post by akudewan on 2008-05-19
I'm having the same issue. I don't have a wifi connection, but I'm connected on a wired LAN.

Anyone figured out what this mystery process is ?

---

### Post by Maybelline on 2008-06-30
Could this be UPnP traffic?  Maybe some samba/nfs overhead?

---

