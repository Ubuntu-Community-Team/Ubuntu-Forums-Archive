---
title: "Port question"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by fynlam on 2007-08-23
i ran this command
```
netstat -natp|grep 0.0.0.0
```

among the output there were 2 lines that looked like this

```

tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:46545           0.0.0.0:*               LISTEN     -                   

```

so these ports 2049 and 46545 are open but no processes are associated with them, i can also telnet to them
```

telnet localhost 2049
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
alskf
Connection closed by foreign host.

```
and thats what happens
whats the deal with these ports and how can i close them?

---

### Post by netztier on 2007-08-24
> **fynlam said:**
>  what happens
whats the deal with these ports and how can i close them?

tcp/2049 is NFS-over-TCP. Nothing bad or worrysome - if you run an NFS server on that machine.
Disabling the NFS server should also disable the port.

As for tcp/46545 .. never heard of. You wouldn't happen to be running a Bittorrent client, Skype or some other Peer-to-Peer networking app?

best regards

Marc

---

### Post by fynlam on 2007-08-24
i was running gaim and evolution shut them both down but still get 
```

 sudo netstat -natp|grep 0.0.0.0
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:53436           0.0.0.0:*               LISTEN     -    

```

2049 is prob ok since i got exportfs installed
but the other port keeps changing every time i reboot now its tcp/53436?
what could it be?

maybe a list of processes will help
```

 ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 migration/1
    6 ?        00:00:00 ksoftirqd/1
    7 ?        00:00:00 watchdog/1
    8 ?        00:00:00 events/0
    9 ?        00:00:00 events/1
   10 ?        00:00:00 khelper
   11 ?        00:00:00 kthread
   35 ?        00:00:00 kblockd/0
   36 ?        00:00:00 kblockd/1
   37 ?        00:00:00 kacpid
   38 ?        00:00:00 kacpi_notify
  125 ?        00:00:00 kseriod
  152 ?        00:00:00 pdflush
  153 ?        00:00:00 pdflush
  154 ?        00:00:00 kswapd0
  155 ?        00:00:00 aio/0
  156 ?        00:00:00 aio/1
  785 ?        00:00:00 kirqd
 2029 ?        00:00:00 ksuspend_usbd
 2030 ?        00:00:00 khubd
 2083 ?        00:00:00 ata/0
 2088 ?        00:00:00 ata/1
 2089 ?        00:00:00 ata_aux
 2134 ?        00:00:00 scsi_eh_0
 2135 ?        00:00:00 scsi_eh_1
 2180 ?        00:00:00 scsi_eh_2
 2181 ?        00:00:00 scsi_eh_3
 2390 ?        00:00:00 kjournald
 2592 ?        00:00:00 udevd
 3494 ?        00:00:00 kpsmoused
 4387 tty4     00:00:00 getty
 4388 tty5     00:00:00 getty
 4390 tty2     00:00:00 getty
 4392 tty3     00:00:00 getty
 4394 tty1     00:00:00 getty
 4395 tty6     00:00:00 getty
 4653 ?        00:00:00 acpid
 4770 ?        00:00:00 syslogd
 4826 ?        00:00:00 dd
 4828 ?        00:00:00 klogd
 4849 ?        00:00:00 dbus-daemon
 4865 ?        00:00:02 hald
 4866 ?        00:00:00 hald-runner
 4872 ?        00:00:00 hald-addon-acpi
 4880 ?        00:00:00 hald-addon-keyb
 4889 ?        00:00:00 hald-addon-keyb
 4892 ?        00:00:00 hald-addon-keyb
 4907 ?        00:00:00 hald-addon-stor
 4920 ?        00:00:00 dhcdbd
 4935 ?        00:00:00 NetworkManager
 4953 ?        00:00:00 avahi-daemon
 4954 ?        00:00:00 avahi-daemon
 4970 ?        00:00:00 NetworkManagerD
 4983 ?        00:00:00 system-tools-ba
 4984 ?        00:00:00 dbus-daemon
 5035 ?        00:00:00 gdm
 5036 ?        00:00:00 gdm
 5039 tty7     00:00:09 Xorg
 5042 ?        00:00:00 dhclient
 5457 ?        00:00:00 lockd
 5458 ?        00:00:00 rpciod/0
 5459 ?        00:00:00 rpciod/1
 5460 ?        00:00:00 nfsd4
 5461 ?        00:00:00 nfsd
 5462 ?        00:00:00 nfsd
 5463 ?        00:00:00 nfsd
 5464 ?        00:00:00 nfsd
 5465 ?        00:00:00 nfsd
 5466 ?        00:00:00 nfsd
 5467 ?        00:00:00 nfsd
 5468 ?        00:00:00 nfsd
 5505 ?        00:00:00 nmbd
 5520 ?        00:00:00 uml_switch
 5609 ?        00:00:00 rpc.idmapd
 5626 ?        00:00:00 hcid
 5646 ?        00:00:00 krfcommd
 5664 ?        00:00:00 x-session-manag
 5693 ?        00:00:00 atd
 5707 ?        00:00:00 cron
 5854 ?        00:00:00 ssh-agent
 5857 ?        00:00:00 dbus-launch
 5858 ?        00:00:00 dbus-daemon
 5860 ?        00:00:00 gconfd-2
 5863 ?        00:00:00 gnome-keyring-d
 5865 ?        00:00:00 gnome-settings-
 5872 ?        00:00:00 sh
 5873 ?        00:00:00 esd
 5877 ?        00:00:01 metacity
 5880 ?        00:00:01 gnome-panel
 5881 ?        00:00:01 nautilus
 5889 ?        00:00:00 bonobo-activati
 5890 ?        00:00:00 gnome-volume-ma
 5898 ?        00:00:00 gnome-vfs-daemo
 5902 ?        00:00:00 update-notifier
 5909 ?        00:00:00 nm-applet
 5910 ?        00:00:00 gnome-cups-icon
 5911 ?        00:00:00 gnome-power-man
 5914 ?        00:00:00 mapping-daemon
 5921 ?        00:00:00 trashapplet
 5956 ?        00:00:00 multiload-apple
 5961 ?        00:00:00 mixer_applet2
 5969 ?        00:00:00 gnome-terminal
 5972 ?        00:00:00 gnome-pty-helpe
 5973 pts/0    00:00:00 bash
 5992 ?        00:00:00 gnome-screensav
 6195 ?        00:00:16 firefox-bin
 6323 pts/1    00:00:00 bash
 6380 pts/1    00:00:00 ps

```

---

