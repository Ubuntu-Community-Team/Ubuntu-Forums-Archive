---
title: "Trying to stop FTP service... need help"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by shogan85 on 2009-01-05
Hi guys,

New around here. I have setup ubuntu 8.04 workstation on a virual machine (VMWare server) and am hosting two of my websites from it using XAMPP.

Now, I would like to use Proftpd which comes with xampp for FTP, however it won't start, complaining that there is another FTP daemon already running.

I have managed to figure out the process ID and can kill the process - this only disconnects my FTP session to the existing FTP server (I don't even know what the FTP server is!)

[IMG]http://i71.photobucket.com/albums/i127/shogan85/ftp.jpg[/IMG]

Anyway, this only disconnects my session. I want to locate this FTP server, disable it, and disable it from startup too. That way I will be able to allow Proftpd to run...

Apologies if this is in the wrong section... I'm new to the forums!

Cheers :)

---

### Post by pytheas22 on 2009-01-05
Did you install Ubuntu Server Edition?  If it has no graphical interface, that's what it is.  In that case, it should be sufficient to type:
```

sudo apt-get remove ftp
```

to uninstall the ftp server.  If that doesn't work, type 'sudo apt-get remove ftp' and press tab, and see if it auto-completes any package names relating to ftp.

If you're not using Ubuntu Server Edition, then any ftp programs running on your machine must have been installed by you, as far as I know.

---

### Post by dmizer on 2009-01-05
> **pytheas22 said:**
> If you're not using Ubuntu Server Edition, then any ftp programs running on your machine must have been installed by you, as far as I know.

This is also true of the server edition.

This error does not necessarily mean that you ACTUALLY have another ftp server running, but that a port that proftp needs is being used/blocked.

For more information on configuring proftp, please see the 3rd link in my sig.

---

### Post by shogan85 on 2009-01-06
Thanks guys, I am running the normal workstation version of 8.04. Not the server edition. I have installed a couple of FTP clients, but no server stuff as far as I know... Thanks for the replies - FTP is forwarded to the ubuntu virtual machine on my router, so I don't think port 21 is being blocked by the router. I am currently able to FTP to my ubuntu machine using filezilla from another PC on the network, so I know that there is another FTP server of some type running on the machine other than proftpd.

pytheas I will try that, thanks! If that doesn't help then i'll be looking into that link in your sig thanks dmizer :)

Ok I have tried removing "ftp" Got this problem though :

sean@linuxweb:/etc$ sudo apt-get remove ftp
[sudo] password for sean: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
sean@linuxweb:/etc$

---

### Post by dmizer on 2009-01-06
> **shogan85 said:**
> Ok I have tried removing "ftp" Got this problem though :

sean@linuxweb:/etc$ sudo apt-get remove ftp
[sudo] password for sean: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
sean@linuxweb:/etc$

You cannot both perform "apt-get" on the command line, and have synaptic open. This is done so to prevent you from making simultaneous changes with apt-get and Synaptic.

---

### Post by shogan85 on 2009-01-06
Haha, that was quite noob of me, sorry about that. Ok ftp is busy being removed...

ftp ubuntu-standard is what it found. 209kB disk space to be freed.

*edit : Alright, so after removing ftp, I tried connecting again, and am able to ftp into the home directory still. Tried "sudo kill process#" after doing

ps aux | grep ftp

to find the process ID. This disconnected my FTP session, but I could still start the ftp session again... Seems that "ftp" wasn't the ftp server it is running. Any more ideas?

---

### Post by dmizer on 2009-01-06
Try doing a search in Synaptic for the terms: ftp server

See if that returns any positive results. If not, please post the entire output of
```
ps aux
```

---

### Post by dmizer on 2009-01-06
Try doing a search in Synaptic for the terms: ftp server

See if that returns any positive results.

---

### Post by shogan85 on 2009-01-06
> **dmizer said:**
> Try doing a search in Synaptic for the terms: ftp server

See if that returns any positive results. If not, please post the entire output of
```
ps aux
```

Hi dmizer,

Ok I searched for ftp server, and found a package called ftpd. Removed that, and now I can't connect to the machine via FTP anymore. I tried to manually start proftpd in xampp but it still complained another FTP Daemon running already. Here is the full output as requested :

```

sean@linuxweb:/etc$ sudo /opt/lampp/lampp startftp
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Another FTP daemon is already running.
sean@linuxweb:/etc$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   2844  1692 ?        Ss   Jan04   0:04 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   Jan04   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Jan04   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   Jan04   0:20 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Jan04   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   Jan04   0:11 [events/0]
root         7  0.0  0.0      0     0 ?        S<   Jan04   0:00 [khelper]
root        41  0.0  0.0      0     0 ?        S<   Jan04   0:02 [kblockd/0]
root        44  0.0  0.0      0     0 ?        S<   Jan04   0:00 [kacpid]
root        45  0.0  0.0      0     0 ?        S<   Jan04   0:00 [kacpi_notify]
root       105  0.0  0.0      0     0 ?        S<   Jan04   0:00 [kseriod]
root       139  0.0  0.0      0     0 ?        S    Jan04   0:00 [pdflush]
root       140  0.0  0.0      0     0 ?        S    Jan04   0:05 [pdflush]
root       141  0.0  0.0      0     0 ?        S<   Jan04   0:00 [kswapd0]
root       182  0.0  0.0      0     0 ?        S<   Jan04   0:00 [aio/0]
root      1430  0.0  0.0      0     0 ?        S<   Jan04   0:58 [ata/0]
root      1434  0.0  0.0      0     0 ?        S<   Jan04   0:00 [ata_aux]
root      1447  0.0  0.0      0     0 ?        S<   Jan04   0:00 [scsi_eh_0]
root      1460  0.0  0.0      0     0 ?        S<   Jan04   0:00 [scsi_eh_1]
root      1462  0.0  0.0      0     0 ?        S<   Jan04   0:25 [scsi_eh_2]
root      2506  0.0  0.0      0     0 ?        S<   Jan04   0:04 [kjournald]
root      2731  0.0  0.1   2408   952 ?        S<s  Jan04   0:02 /sbin/udevd --daemon
root      2962  0.0  0.0      0     0 ?        S<   Jan04   0:00 [kpsmoused]
root      4216  0.0  0.0   1716   512 tty4     Ss+  Jan04   0:00 /sbin/getty 38400 tty4
root      4217  0.0  0.0   1716   512 tty5     Ss+  Jan04   0:00 /sbin/getty 38400 tty5
root      4221  0.0  0.0   1716   512 tty2     Ss+  Jan04   0:00 /sbin/getty 38400 tty2
root      4223  0.0  0.0   1716   512 tty3     Ss+  Jan04   0:00 /sbin/getty 38400 tty3
root      4224  0.0  0.0   1716   504 tty6     Ss+  Jan04   0:00 /sbin/getty 38400 tty6
root      4388  0.0  0.1   2456  1360 ?        Ss   Jan04   0:00 /usr/sbin/acpid -c /etc
root      4423  0.0  0.0      0     0 ?        S<   Jan04   0:00 [kondemand/0]
syslog    4495  0.0  0.0   1936   684 ?        Ss   Jan04   0:02 /sbin/syslogd -u syslog
root      4550  0.0  0.0   1872   536 ?        S    Jan04   0:00 /bin/dd bs 1 if /proc/k
klog      4552  0.0  0.2   3036  1872 ?        Ss   Jan04   0:00 /sbin/klogd -P /var/run
108       4574  0.0  0.1   2920  1396 ?        Ss   Jan04   0:01 /usr/bin/dbus-daemon --
root      4590  0.0  0.2  12892  2092 ?        Ssl  Jan04   0:00 /usr/sbin/NetworkManage
root      4604  0.0  0.1   3536  1312 ?        Ss   Jan04   0:00 /usr/sbin/NetworkManage
root      4617  0.0  0.1   4140  1336 ?        Ss   Jan04   0:00 /usr/bin/system-tools-b
avahi     4637  0.0  0.1   2860  1488 ?        Ss   Jan04   0:01 avahi-daemon: running [
avahi     4638  0.0  0.0   2760   468 ?        Ss   Jan04   0:00 avahi-daemon: chroot he
root      4747  0.0  0.3   6048  2512 ?        Ss   Jan04   0:00 /usr/sbin/cupsd
root      4781  0.0  0.0   1896   588 ?        Ss   Jan04   0:00 /usr/sbin/inetd
root      4819  0.0  0.1   6532  1376 ?        Ss   Jan04   0:08 /usr/sbin/nmbd -D
root      4821  0.0  0.3  10124  2752 ?        Ss   Jan04   0:01 /usr/sbin/smbd -D
root      4862  0.0  0.1   2020   904 ?        Ss   Jan04   0:55 /usr/sbin/dhcdbd --syst
111       4881  0.0  0.4   6140  3112 ?        Ss   Jan04   0:06 /usr/sbin/hald
root      4882  0.0  0.1  10124  1064 ?        S    Jan04   0:00 /usr/sbin/smbd -D
root      4885  0.0  0.3   7884  2376 ?        Ssl  Jan04   0:00 /usr/sbin/console-kit-d
root      4886  0.0  0.1   3352  1144 ?        S    Jan04   0:00 hald-runner
root      4959  0.0  0.1   3416  1148 ?        S    Jan04   0:00 hald-addon-input: Liste
111       4968  0.0  0.1   2204   904 ?        S    Jan04   0:00 hald-addon-acpi: listen
root      4969  0.0  0.1   3420  1120 ?        S    Jan04   0:04 hald-addon-storage: no 
root      4976  0.0  0.1   3420  1136 ?        S    Jan04   0:32 hald-addon-storage: pol
root      5019  0.0  0.1   3172  1256 ?        Ss   Jan04   0:00 /usr/sbin/hcid -x -s
dhcp      5027  0.0  0.1   2440  1180 ?        S    Jan04   0:00 /sbin/dhclient -1 -lf /
root      5033  0.0  0.0      0     0 ?        S<   Jan04   0:00 [btaddconn]
root      5034  0.0  0.0      0     0 ?        S<   Jan04   0:00 [btdelconn]
root      5048  0.0  0.1   3084  1284 ?        S    Jan04   0:00 /usr/lib/bluetooth/blue
root      5049  0.0  0.1   3020  1092 ?        S    Jan04   0:00 /usr/lib/bluetooth/blue
root      5053  0.0  0.0      0     0 ?        S<   Jan04   0:00 [krfcommd]
root      5082  0.0  0.2  14080  1604 ?        Ss   Jan04   0:00 /usr/sbin/gdm
root      5083  0.0  0.5  18484  4300 ?        S    Jan04   0:00 /usr/sbin/gdm
root      5089  0.6  1.9  22336 15136 tty7     Rs+  Jan04  20:46 /usr/bin/X :0 -br -audi
daemon    5122  0.0  0.0   1984   424 ?        Ss   Jan04   0:00 /usr/sbin/atd
root      5138  0.0  0.1   2104   888 ?        Ss   Jan04   0:01 /usr/sbin/cron
sean      5324  0.0  0.2  14352  2072 ?        S    Jan04   0:00 /usr/bin/gnome-keyring-
root      5325  0.0  1.9  25892 15308 ?        Ss   Jan04   0:25 /opt/lampp/bin/httpd -k
sean      5328  0.0  1.7  34932 13832 ?        Ssl  Jan04   0:04 x-session-manager
root      5384  0.0  0.0   1772   520 ?        S    Jan04   0:00 /bin/sh /opt/lampp/bin/
root      5456  0.0  0.0   1716   508 tty1     Ss+  Jan04   0:00 /sbin/getty 38400 tty1
nobody    5459  0.0  1.4  23132 10964 ?        S    Jan04   0:00 /opt/lampp/bin/httpd -k
nobody    5469  0.0  1.0  30284  8408 ?        Sl   Jan04   0:15 /opt/lampp/sbin/mysqld
sean      5511  0.0  0.6   7588  4676 ?        S    Jan04   0:18 /usr/lib/libgconf2-4/gc
sean      5517  0.0  0.8  23092  6832 ?        Ss   Jan04   0:02 /usr/bin/seahorse-agent
sean      5521  0.0  0.1   2700  1140 ?        Ss   Jan04   0:00 dbus-daemon --fork --pr
sean      5522  0.0  1.3  40476 10592 ?        Sl   Jan04   0:21 gnome-settings-daemon
sean      5526  0.0  0.6  11088  4852 ?        S    Jan04   0:34 /usr/bin/pulseaudio --l
sean      5527  0.0  0.2   5776  2260 ?        S    Jan04   0:00 /usr/lib/pulseaudio/pul
sean      5541  0.0  0.2   5380  2124 ?        S    Jan04   0:00 /usr/lib/gvfs/gvfsd
sean      5542  0.0  0.6  15368  4752 ?        Ss   Jan04   0:42 gnome-screensaver
sean      5544  0.0  0.4  31944  3232 ?        Ssl  Jan04   0:00 /usr/lib/bonobo-activat
sean      5554  0.0  0.2  29048  1896 ?        Ssl  Jan04   0:00 /usr/lib/gvfs//gvfs-fus
sean      5559  0.0  1.5  20524 12080 ?        S    Jan04   0:29 /usr/bin/metacity --rep
sean      5561  0.2  1.5  23368 12036 ?        S    Jan04   7:24 /usr/lib/vino/vino-serv
sean      5563  0.0  2.6  36540 20588 ?        S    Jan04   1:40 gnome-panel --sm-client
sean      5564  0.0  3.5  70596 27740 ?        S    Jan04   2:50 nautilus --no-default-w
sean      5573  0.3  0.3   6728  2624 ?        S    Jan04  11:30 /usr/lib/vmware-tools/b
sean      5603  0.0  0.7  14636  5776 ?        S    Jan04   0:00 bluetooth-applet --sing
sean      5605  0.0  1.8  26376 14036 ?        S    Jan04   0:19 update-notifier
sean      5610  0.0  0.7  15256  5564 ?        S    Jan04   0:00 tracker-applet
sean      5611  0.0  1.2  37660  9804 ?        Sl   Jan04   0:03 /usr/lib/evolution/2.22
sean      5614  0.0  1.3  30740 10388 ?        SNl  Jan04   0:00 trackerd
sean      5620  0.0  1.5  24292 12192 ?        S    Jan04   0:01 python /usr/share/syste
sean      5621  0.2  1.5  25240 11844 ?        S    Jan04   6:09 nm-applet --sm-disable
sean      5634  0.0  0.2   5380  2148 ?        S    Jan04   0:00 /usr/lib/gvfs/gvfsd-bur
sean      5675  0.0  1.3  23372 10236 ?        S    Jan04   0:02 /usr/lib/gnome-applets/
sean      5682  0.0  0.6  20704  4704 ?        Ss   Jan04   0:07 /usr/lib/gnome-volume-m
sean      5687  0.0  0.9  23376  7680 ?        Ss   Jan04   0:11 gnome-power-manager
sean      5693  0.0  0.3  22048  2700 ?        S    Jan04   1:17 /usr/lib/gvfs/gvfsd-tra
sean      5755  0.0  1.9  36484 14944 ?        S    Jan04   0:03 /usr/lib/gnome-applets/
sean      5759  0.0  1.7  26136 13308 ?        S    Jan04   0:02 /usr/lib/fast-user-swit
sean      5806  0.0  1.7  24692 13740 ?        S    Jan04   0:06 /usr/lib/notification-d
nobody   12665  0.0  1.9  26488 15352 ?        S    Jan05   0:01 /opt/lampp/bin/httpd -k
root     12851  0.0  0.1   2912   844 ?        S    17:56   0:00 gnome-pty-helper
nobody   14030  0.0  2.2  28560 17524 ?        S    Jan05   0:03 /opt/lampp/bin/httpd -k
nobody   22015  0.0  2.4  30112 18956 ?        S    Jan05   0:02 /opt/lampp/bin/httpd -k
nobody   22017  0.0  2.2  28792 17696 ?        S    Jan05   0:01 /opt/lampp/bin/httpd -k
nobody   23248  0.0  2.2  28512 17444 ?        S    Jan05   0:01 /opt/lampp/bin/httpd -k
sean     26292  0.1  1.7  24432 13536 ?        S    17:47   0:01 gksu /usr/sbin/synaptic
root     26309  2.8  5.6  87636 44160 ?        Ss   17:47   0:26 /usr/sbin/synaptic
nobody   27677  0.0  1.9  26768 14924 ?        S    Jan05   0:00 /opt/lampp/bin/httpd -k
nobody   27680  0.0  2.3  29548 18148 ?        S    Jan05   0:00 /opt/lampp/bin/httpd -k
nobody   27761  0.0  2.2  28580 17484 ?        S    Jan05   0:01 /opt/lampp/bin/httpd -k
sean     28685  0.0  0.1   2644  1004 pts/0    R+   18:03   0:00 ps aux
sean     29549  0.0  0.3  14220  2900 ?        S    00:10   0:00 /usr/lib/gvfs/gvfsd-com
sean     29804  0.0  2.7  75740 21596 ?        Rl   00:26   0:58 gnome-terminal
sean     29807  0.0  0.1   2912   856 ?        S    00:27   0:00 gnome-pty-helper
sean     29808  0.0  0.3   5640  3064 pts/0    Ss   00:27   0:02 bash
root     30153  0.0  1.4  13136 11200 ?        S    00:49   0:01 /usr/bin/perl /usr/shar
nobody   30200  0.0  2.0  26804 15564 ?        S    00:50   0:00 /opt/lampp/bin/httpd -k
nobody   30202  0.0  2.2  28516 17208 ?        S    00:50   0:00 /opt/lampp/bin/httpd -k
root     30782  0.0  0.0   3008   616 pts/0    S    01:25   0:00 dbus-launch --autolaunc
root     30783  0.0  0.1   2568   928 ?        Ss   01:25   0:00 /usr/bin/dbus-daemon --
sean     30818  0.0  1.7  24436 13544 ?        S    01:26   0:01 gksudo python /opt/lamp
root     30820  3.5  2.4  39444 18700 ?        Ssl  01:26  35:36 python /opt/lampp/share
sean@linuxweb:/etc$

```

---

