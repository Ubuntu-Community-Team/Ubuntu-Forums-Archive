---
title: "Wired Internet Problem"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by cj_g0bl1n on 2008-09-13
I just installed Kubuntu on a new server machine I just built.  It has one wired ethernet port.  I'm plugged into a router, I have DHCP enabled and have an IP address from the router.  I can get to the router, but I cannot get on internet.  I have several other computers hooked into the same router, they all have internet, although they are all wireless connections.  I do not think that matters, if the computer can get to the router, then it should be alright from there...I think...  But what is even more wierd, the Kubuntu computer cannot ping any other computer on the network, but they can all ping the Kubuntu computer...

Any help would be much appreciated!!!

---

### Post by fwre01 on 2008-09-13
that has some really strange symptoms.lol

could you post the output from "route" and "ps -ef" and "ifconfig"

thanks

---

### Post by cj_g0bl1n on 2008-09-13
I know its not the cord, the port on the router, or the NIC.  I restarted the computer and booted up Windows, and I have internet.  So its gotta be the setup in linux somewhere.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 01:20 ?        00:00:01 init [2]
root         2     1  0 01:20 ?        00:00:00 [ksoftirqd/0]
root         3     1  0 01:20 ?        00:00:00 [watchdog/0]
root         4     1  0 01:20 ?        00:00:00 [events/0]
root         5     1  0 01:20 ?        00:00:00 [khelper]
root         6     1  0 01:20 ?        00:00:00 [kthread]
root         8     6  0 01:20 ?        00:00:00 [kblockd/0]
root         9     6  0 01:20 ?        00:00:00 [kacpid]
root       180     6  0 01:20 ?        00:00:00 [pdflush]
root       181     6  0 01:20 ?        00:00:00 [pdflush]
root       183     6  0 01:20 ?        00:00:00 [aio/0]
root       182     1  0 01:20 ?        00:00:00 [kswapd0]
root       776     6  0 01:20 ?        00:00:00 [kseriod]
root      1792     6  0 01:20 ?        00:00:00 [ata/0]
root      1793     6  0 01:20 ?        00:00:00 [ata_hotplug/0]
root      1796     6  0 01:20 ?        00:00:00 [scsi_eh_0]
root      1797     6  0 01:20 ?        00:00:00 [scsi_eh_1]
root      1800     6  0 01:20 ?        00:00:00 [scsi_eh_2]
root      1801     6  0 01:20 ?        00:00:00 [scsi_eh_3]
root      1909     1  0 01:20 ?        00:00:00 [khpsbpkt]
root      1915     6  0 01:20 ?        00:00:00 [khubd]
root      1922     1  0 01:20 ?        00:00:00 [knodemgrd_0]
root      1999     1  0 01:20 ?        00:00:00 [kjournald]
root      2233     1  0 01:20 ?        00:00:00 /sbin/udevd --daemon
root      3040     1  0 01:20 ?        00:00:00 [shpchpd_event]
root      3170     6  0 01:20 ?        00:00:00 [hda_codec/0]
root      3969     1  0 01:20 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/eve
root      4085     1  0 01:20 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /v
klog      4087     1  0 01:20 ?        00:00:00 /sbin/klogd -P /var/run/klogd/km
hplip     4112     1  0 01:20 ?        00:00:00 /usr/sbin/hpiod
hplip     4115     1  0 01:20 ?        00:00:00 python /usr/sbin/hpssd
104       4187     1  0 01:20 ?        00:00:00 /usr/bin/dbus-daemon --system
108       4202     1  0 01:20 ?        00:00:00 /usr/sbin/hald
root      4203  4202  0 01:20 ?        00:00:00 hald-runner
108       4208  4203  0 01:20 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
108       4215  4203  0 01:20 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
108       4219  4203  0 01:20 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
108       4268  4203  0 01:20 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
108       4275  4203  0 01:20 ?        00:00:00 /usr/lib/hal/hald-addon-storage
108       4276  4203  0 01:20 ?        00:00:00 /usr/lib/hal/hald-addon-storage
root      4349     1  0 01:20 ?        00:00:00 hcid: processing events
root      4353     1  0 01:20 ?        00:00:00 /usr/sbin/sdpd
root      4368     1  0 01:20 ?        00:00:00 [krfcommd]
root      4381     1  0 01:20 ?        00:00:00 /sbin/mdadm -F -i /var/run/mdadm
daemon    4415     1  0 01:20 ?        00:00:00 /usr/sbin/atd
root      4428     1  0 01:20 ?        00:00:00 /usr/sbin/cron
root      4771     1  0 01:20 ?        00:00:00 /usr/bin/kdm
root      4805  4771  1 01:20 tty7     00:00:32 /usr/bin/X -br -nolisten tcp :0
root      4822     1  0 01:20 tty1     00:00:00 /sbin/getty 38400 tty1
root      4823     1  0 01:20 tty2     00:00:00 /sbin/getty 38400 tty2
root      4824     1  0 01:20 tty3     00:00:00 /sbin/getty 38400 tty3
root      4825     1  0 01:20 tty4     00:00:00 /sbin/getty 38400 tty4
root      4826     1  0 01:20 tty5     00:00:00 /sbin/getty 38400 tty5
root      4827     1  0 01:20 tty6     00:00:00 /sbin/getty 38400 tty6
root      4844  4771  0 01:20 ?        00:00:00 -:0
admin     4853  4844  0 01:21 ?        00:00:00 /bin/sh /usr/bin/x-session-manag
admin     4889  4853  0 01:21 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus
admin     4892     1  0 01:21 ?        00:00:00 /usr/bin/dbus-launch --exit-with
admin     4893     1  0 01:21 ?        00:00:00 dbus-daemon --fork --print-pid 8
admin     4922     1  0 01:21 ?        00:00:00 kdeinit Running...
admin     4925     1  0 01:21 ?        00:00:00 dcopserver [kdeinit] --nosid
admin     4927  4922  0 01:21 ?        00:00:00 klauncher [kdeinit]
admin     4929     1  0 01:21 ?        00:00:00 kded [kdeinit]
admin     4931     1  0 01:21 ?        00:00:00 /usr/lib/gamin/gam_server
admin     4938  4922  0 01:21 ?        00:00:03 /usr/bin/artsd -F 10 -S 4096 -s
admin     4940     1  0 01:21 ?        00:00:00 kaccess [kdeinit]
admin     4943  4853  0 01:21 ?        00:00:00 kwrapper ksmserver
admin     4945     1  0 01:21 ?        00:00:00 ksmserver [kdeinit]
admin     4954  4922  0 01:21 ?        00:00:01 kwin [kdeinit] -session 107d7b5d
admin     4957     1  0 01:21 ?        00:00:01 kdesktop [kdeinit]
admin     4959     1  0 01:21 ?        00:00:02 kicker [kdeinit]
admin     4960  4922  0 01:21 ?        00:00:00 kio_file [kdeinit] file /tmp/kso
admin     4965     1  0 01:21 ?        00:00:00 kbluetoothd --dontforceshow
admin     4967     1  0 01:21 ?        00:00:00 adept_notifier
admin     4968     1  0 01:21 ?        00:00:00 klipper [kdeinit]
admin     4971     1  0 01:21 ?        00:00:00 kio_uiserver [kdeinit]
admin     4982     1  0 01:21 ?        00:00:00 kmix [kdeinit] -session 10d8cecf
admin     4983  4922  0 01:21 ?        00:00:00 katapult -session 10d9d396680001
admin     4985     1  0 01:21 ?        00:00:00 knotify [kdeinit]
admin     5008     1  0 01:22 ?        00:00:00 /usr/bin/kdesud
cupsys    5411     1  0 01:25 ?        00:00:00 /usr/sbin/cupsd
dhcp      5629     1  0 01:26 ?        00:00:00 dhclient3 -pf /var/run/dhclient.
syslog    5682     1  0 01:26 ?        00:00:00 /sbin/syslogd -u syslog
admin     6070     1  0 01:29 ?        00:00:01 konqueror [kdeinit] -mimetype in
admin     6135  4922  0 01:54 ?        00:00:00 konsole [kdeinit]
admin     6136  6135  0 01:54 pts/1    00:00:00 /bin/bash
admin     6173  4922  0 01:55 ?        00:00:00 /bin/sh /usr/lib/openoffice/prog
admin     6184  6173 21 01:55 ?        00:00:02 /usr/lib/openoffice/program/soff
admin     6192  6136  0 01:55 pts/1    00:00:00 ps -ef


eth0      Link encap:Ethernet  HWaddr 00:0F:EA:5D:68:0B
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fe5d:680b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:197456 (192.8 KiB)  TX bytes:72179 (70.4 KiB)
          Interrupt:225 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14356 (14.0 KiB)  TX bytes:14356 (14.0 KiB)

---

### Post by fwre01 on 2008-09-13
hmmmmm, it all looks ok. can you paste the output from "arp" (it takes a few seconds it display results) AFTER you have tried to ping a host on the network and the router?

If you are getting arp entries we can hopefully eliminate there being a physical problem in kubuntu (...which i know you kindof already have, but i think its still worth getting another set of confirming results)

---

### Post by cj_g0bl1n on 2008-09-13
Oh wow...its working.  I dunno whats up with that, but hey...works for me.  Thanks for the help!!!

---

