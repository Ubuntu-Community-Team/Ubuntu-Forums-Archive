---
title: "How to know who created a file"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by Ev1L on 2009-12-25
Hi,
I am getting 2 weird files:
~/Download/khw
-r-xr--r-- 1 65534 65534       0 2009-12-25 14:57 khw
~/Download/xztonf.exe
-rw-r--r-- 1 65534 65534  836350 2008-04-14 23:53 xztonf.exe
I think it could be some kind of Windows virus, hopely ineffective on linux.
When I try to remove them, they reappear after a while.
How can I know who is recreating them?

---

### Post by x33a on 2009-12-25
maybe it is somehow being downloaded through your browser? (is your download folder set to /home/<username>Download?
try
```
file <filename>
```to see what the file is.

---

### Post by Shazaam on 2009-12-25
Google search for khw...
[http://www.google.com/search?hl=en&as_q=&as_epq=khw&as_oq=malware&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images](http://www.google.com/search?hl=en&as_q=&as_epq=khw&as_oq=malware&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images)
Are you running WINE?

---

### Post by Ev1L on 2009-12-25
evil@hell:~/Download$ file xztonf.exe 
xztonf.exe: PE32 executable for MS Windows (GUI) Intel 80386 32-bit
evil@hell:~/Download$ file khw 
khw: empty

and yes, I have Wine but I have no idea about how it got there and how it can reproduce itself automatically on linux :)

any idea how to remove it in linux (there are plenty of anti-malware on windows, but for linux everyone just tells "don't bother")?

---

### Post by coffeecat on 2009-12-25
> **Ev1L said:**
> I have Wine but I have no idea about how it got there

You don't know how wine got there? :shock:

:wink:

What apps do you run in wine? Some Windows viruses can work in wine but what wine app is using your ~/Downloads folder? I wouldn't have though that likely.

If you want to scan wine for viruses, install clamav from the repos. Search Synaptic. There are a couple of GUI frontends depending what desktop you use.

By the way, if you've acquired a virus called xztonf.exe, you must be the only one. A google search for xztonf.exe throws up only this thread and an Australian site called the goss, with a link back to this thread!

---

### Post by Ev1L on 2009-12-25
Ahah no, I meant I don't know how the virus got there :D
I also searched for that file and found nothing (I did it before opening this thread :p).

I haven't used wine recently (at least not consciously), so I don't know what could be creating this file.

clamav is at work :)

---

### Post by Ev1L on 2009-12-27
it found something, i removed it, but those files appeared again :\
i am not (counsciously) running anything on wine...

---

### Post by Troll_the_Great on 2009-12-27
> **Ev1L said:**
> it found something, i removed it, but those files appeared again :\
i am not (counsciously) running anything on wine...

Open a terminal and type 
```
top
```
Check if wine is running and see with what application.
Cheers!

---

### Post by Ev1L on 2009-12-27
already did but couldn't see nothing.
for example "khw" was created half an hour ago while i was sleeping...
so at most it could be related to some periodical event, not something i open

---

### Post by sandy8925 on 2009-12-27
Even if it's .exe doesn't necessarily mean it's a Windows program. Could be a linux program masquerading as a windows program. Check and see if it's marked as executable? (i.e whether x is marked in rwx permissions)

---

### Post by Ev1L on 2009-12-27
~/Download/khw
-r-xr--r-- 1 65534 65534 0 2009-12-25 14:57 khw
~/Download/xztonf.exe
-rw-r--r-- 1 65534 65534 836350 2008-04-14 23:53 xztonf.exe

---

### Post by JKyleOKC on 2009-12-27
> **Ev1L said:**
> ~/Download/khw
-r-xr--r-- 1 65534 65534 0 2009-12-25 14:57 khw
~/Download/xztonf.exe
-rw-r--r-- 1 65534 65534 836350 2008-04-14 23:53 xztonf.exeThis shows that UserID 65534 is the owner of both files. Looking at /etc/passwd shows that this is user "nobody" which is not capable of logging in, but can be set as the effective user by several server programs. For example, the samba package can be configured to allow guest logins, as "nobody" if the login isn't recognized. And it's not the only one with this feature. You may want to verify all the services you have running; one of them may be opening a hole!

It also shows that the exe file was last modified on April 14, 2008, so it's been around for many months...

---

### Post by Ev1L on 2009-12-27
ok, thanks, i'll take a look to the services, hoping to find a suspect one, even though i am not an expert about it.

that date is not so important i suppose, everytime the file reappears there, it has the same date, and i am 100% sure it never happened before a couple of weeks ago, at most.

---

### Post by Ev1L on 2009-12-28
honestly, no idea if there is something not supposed to be here :)

> evil@hell:~/Download$ ps -Al
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0     1     0  0  80   0 -   665 poll_s ?        00:00:00 init
1 S     0     2     0  0  75  -5 -     0 kthrea ?        00:00:00 kthreadd
1 S     0     3     2  0 -40   - -     0 migrat ?        00:00:00 migration/0
1 S     0     4     2  0  75  -5 -     0 ksofti ?        00:00:00 ksoftirqd/0
5 S     0     5     2  0 -40   - -     0 watchd ?        00:00:00 watchdog/0
1 S     0     6     2  0 -40   - -     0 migrat ?        00:00:00 migration/1
1 S     0     7     2  0  75  -5 -     0 ksofti ?        00:00:00 ksoftirqd/1
5 S     0     8     2  0 -40   - -     0 watchd ?        00:00:00 watchdog/1
1 R     0     9     2  0  75  -5 -     0 ?      ?        00:00:00 events/0
1 S     0    10     2  0  75  -5 -     0 worker ?        00:00:00 events/1
1 S     0    11     2  0  75  -5 -     0 worker ?        00:00:00 cpuset
1 S     0    12     2  0  75  -5 -     0 worker ?        00:00:00 khelper
1 S     0    13     2  0  75  -5 -     0 worker ?        00:00:00 netns
1 S     0    14     2  0  75  -5 -     0 async_ ?        00:00:00 async/mgr
1 S     0    15     2  0  75  -5 -     0 worker ?        00:00:00 kintegrityd/0
1 S     0    16     2  0  75  -5 -     0 worker ?        00:00:00 kintegrityd/1
1 S     0    17     2  0  75  -5 -     0 worker ?        00:00:00 kblockd/0
1 S     0    18     2  0  75  -5 -     0 worker ?        00:00:00 kblockd/1
1 S     0    19     2  0  75  -5 -     0 worker ?        00:00:00 kacpid
1 S     0    20     2  0  75  -5 -     0 worker ?        00:00:00 kacpi_notify
1 S     0    21     2  0  75  -5 -     0 worker ?        00:00:00 kacpi_hotplug
1 S     0    22     2  0  75  -5 -     0 worker ?        00:00:00 ata/0
1 S     0    23     2  0  75  -5 -     0 worker ?        00:00:00 ata/1
1 S     0    24     2  0  75  -5 -     0 worker ?        00:00:00 ata_aux
1 S     0    25     2  0  75  -5 -     0 worker ?        00:00:00 ksuspend_usbd
1 S     0    26     2  0  75  -5 -     0 hub_th ?        00:00:00 khubd
1 S     0    27     2  0  75  -5 -     0 serio_ ?        00:00:00 kseriod
1 S     0    28     2  0  75  -5 -     0 worker ?        00:00:00 kmmcd
1 S     0    29     2  0  75  -5 -     0 worker ?        00:00:00 bluetooth
1 S     0    30     2  0  80   0 -     0 watchd ?        00:00:00 khungtaskd
1 S     0    31     2  0  80   0 -     0 pdflus ?        00:00:00 pdflush
1 S     0    32     2  0  80   0 -     0 pdflus ?        00:00:00 pdflush
1 S     0    33     2  0  75  -5 -     0 kswapd ?        00:00:00 kswapd0
1 S     0    34     2  0  75  -5 -     0 worker ?        00:00:00 aio/0
1 S     0    35     2  0  75  -5 -     0 worker ?        00:00:00 aio/1
1 S     0    36     2  0  75  -5 -     0 ecrypt ?        00:00:00 ecryptfs-kthrea
1 S     0    37     2  0  75  -5 -     0 worker ?        00:00:00 crypto/0
1 S     0    38     2  0  75  -5 -     0 worker ?        00:00:00 crypto/1
1 S     0    41     2  0  75  -5 -     0 worker ?        00:00:00 pciehpd
1 S     0    47     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_0
1 S     0    48     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_1
1 S     0    49     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_2
1 S     0    50     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_3
1 S     0    51     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_4
1 S     0    52     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_5
1 S     0    58     2  0  75  -5 -     0 worker ?        00:00:00 kstriped
1 S     0    59     2  0  75  -5 -     0 worker ?        00:00:00 kmpathd/0
1 S     0    60     2  0  75  -5 -     0 worker ?        00:00:00 kmpathd/1
1 S     0    61     2  0  75  -5 -     0 worker ?        00:00:00 kmpath_handlerd
1 S     0    62     2  0  75  -5 -     0 worker ?        00:00:00 ksnapd
1 S     0    63     2  0  75  -5 -     0 worker ?        00:00:00 kondemand/0
1 S     0    64     2  0  75  -5 -     0 worker ?        00:00:00 kondemand/1
1 S     0    65     2  0  75  -5 -     0 worker ?        00:00:00 kconservative/0
1 S     0    66     2  0  75  -5 -     0 worker ?        00:00:00 kconservative/1
5 S     0    67     2  0  70 -10 -     0 rfcomm ?        00:00:00 krfcommd
1 S     0   328     2  0  75  -5 -     0 hpsbpk ?        00:00:00 khpsbpkt
1 S     0   387     2  0  75  -5 -     0 nodemg ?        00:00:00 knodemgrd_0
1 S     0   390     2  0  75  -5 -     0 worker ?        00:00:00 usbhid_resumer
1 S     0   434     2  0  75  -5 -     0 kjourn ?        00:00:00 kjournald
1 S     0   490     1  0  80   0 -   568 poll_s ?        00:00:00 upstart-udev-br
5 S     0   492     1  0  76  -4 -   682 poll_s ?        00:00:00 udevd
1 S     0   742     2  0  75  -5 -     0 worker ?        00:00:00 led_workqueue
5 S   108   835     1  0  80   0 -   810 poll_s ?        00:00:00 dbus-daemon
4 S     0   843     1  0  80   0 -   462 syslog ?        00:00:00 dd
5 S   101   845     1  0  80   0 -  8698 poll_s ?        00:00:00 rsyslogd
5 S   111   854     1  0  80   0 -  1566 poll_s ?        00:00:00 hald
5 S     0   855     1  0  80   0 -  4667 poll_s ?        00:00:00 NetworkManager
5 S   110   856     1  0  80   0 -   736 poll_s ?        00:00:00 avahi-daemon
1 S   110   859   856  0  80   0 -   705 unix_s ?        00:00:00 avahi-daemon
5 S     0   871     1  0  80   0 -  5125 poll_s ?        00:00:00 console-kit-dae
0 S     0   934   854  0  80   0 -   835 poll_s ?        00:00:00 hald-runner
1 S     0   939     2  0  75  -5 -     0 worker ?        00:00:00 kpsmoused
4 S     0  1004     1  0  80   0 -  1233 poll_s ?        00:00:00 wpa_supplicant
5 S     0  1009     1  0  78  -2 -   879 poll_s ?        00:00:00 bluetoothd
0 S     0  1010   934  0  80   0 -   853 poll_s ?        00:00:00 hald-addon-rfki
1 S     0  1026     2  0  75  -5 -     0 worker ?        00:00:00 iwlagn
1 S     0  1027     2  0  75  -5 -     0 worker ?        00:00:00 phy0
1 S     0  1051     2  0  75  -5 -     0 worker ?        00:00:00 hd-audio0
5 S     0  1089   492  0  78  -2 -   686 poll_s ?        00:00:00 udevd
5 S     0  1132   492  0  78  -2 -   686 poll_s ?        00:00:00 udevd
0 S     0  1160     1  0  80   0 -   425 n_tty_ tty4     00:00:00 getty
0 S     0  1163     1  0  80   0 -   425 n_tty_ tty5     00:00:00 getty
0 S     0  1171     1  0  80   0 -   425 n_tty_ tty2     00:00:00 getty
0 S     0  1173     1  0  80   0 -   425 n_tty_ tty3     00:00:00 getty
0 S     0  1175     1  0  80   0 -   425 n_tty_ tty6     00:00:00 getty
1 S     0  1183     1  0  80   0 -   493 poll_s ?        00:00:00 acpid
1 S     1  1243     1  0  80   0 -   490 hrtime ?        00:00:00 atd
1 S     0  1244     1  0  80   0 -   522 hrtime ?        00:00:00 cron
0 S     0  1348   934  0  80   0 -   852 poll_s ?        00:00:00 hald-addon-gene
0 S     0  1358   934  0  80   0 -   853 poll_s ?        00:00:00 hald-addon-leds
0 S     0  1384   934  0  80   0 -   854 poll_s ?        00:00:00 hald-addon-stor
0 S     0  1403   934  0  80   0 -   854 poll_s ?        00:00:00 hald-addon-inpu
0 S     0  1409   934  0  80   0 -   856 poll_s ?        00:00:00 hald-addon-cpuf
4 S   111  1413   934  0  80   0 -   815 unix_s ?        00:00:00 hald-addon-acpi
1 S   116  1437     1  0  80   0 -   778 pause  ?        00:00:00 freshclam
1 S     0  1616     1  0  80   0 -   965 reques ?        00:00:00 mount.ntfs-3g
5 S     0  1795     1  0  80   0 -  2174 poll_s ?        00:00:00 nmbd
5 S     0  1799     1  0  80   0 -  3839 poll_s ?        00:00:00 smbd
1 S     0  1800  1799  0  80   0 -  3839 poll_s ?        00:00:00 smbd
1 S     0  1839     1  0  80   0 -   965 reques ?        00:00:00 mount.ntfs-3g
4 S     0  1867     1  0  80   0 -  2149 poll_s ?        00:00:00 gdm-binary
1 S     0  1874     1  0  80   0 -  2937 poll_s ?        00:00:00 winbindd
1 S     0  1882  1874  0  80   0 -  2937 poll_s ?        00:00:00 winbindd
4 S     0  1893  1867  0  80   0 -  2132 poll_s ?        00:00:00 gdm-simple-slav
4 S     0  1897     1  0  80   0 -  1718 ep_pol ?        00:00:00 cupsd
4 S     0  1898  1893  4  80   0 - 209449 poll_s tty7    00:01:26 Xorg
0 S     0  2070     1  0  80   0 -   425 n_tty_ tty1     00:00:00 getty
1 S   105  2110     1  0  80   0 -   845 poll_s ?        00:00:00 dbus-launch
4 S     0  2115     1  0  80   0 -  1591 poll_s ?        00:00:00 devkit-power-da
4 S     0  2165  1893  0  80   0 -  2191 poll_s ?        00:00:00 gdm-session-wor
1 S  1000  2197     1  0  80   0 - 10176 poll_s ?        00:00:00 gnome-keyring-d
4 S  1000  2212  2165  0  80   0 -  6430 poll_s ?        00:00:00 gnome-session
1 S  1000  2253  2212  0  80   0 -  1229 poll_s ?        00:00:00 ssh-agent
1 S  1000  2256     1  0  80   0 -   808 poll_s ?        00:00:00 dbus-daemon
1 S  1000  2257     1  0  80   0 -   845 poll_s ?        00:00:00 dbus-launch
1 S  1000  2261     1  0  80   0 - 21458 poll_s ?        00:00:00 pulseaudio
0 S  1000  2263  2261  0  80   0 -  2658 poll_s ?        00:00:00 gconf-helper
0 S  1000  2265     1  0  80   0 -  1885 poll_s ?        00:00:00 gconfd-2
1 S  1000  2275  2212  0  80   0 -  4982 poll_s ?        00:00:00 seahorse-agent
0 S  1000  2277     1  0  80   0 -  1436 poll_s ?        00:00:00 gvfsd
1 S  1000  2283     1  0  80   0 -  7448 futex_ ?        00:00:00 gvfs-fuse-daemo
1 S  1000  2291     1  0  80   0 -  5654 poll_s ?        00:00:00 seahorse-daemon
1 S  1000  2292     1  0  80   0 - 24256 poll_s ?        00:00:00 gnome-settings-
0 S  1000  2307     1  0  80   0 -  7481 poll_s ?        00:00:00 notify-osd
0 S  1000  2312  2212  0  80   0 - 18008 poll_s ?        00:00:16 compiz.real
0 S  1000  2313  2212  0  80   0 - 11102 poll_s ?        00:00:03 gnome-panel
0 S  1000  2316     1  0  80   0 -   791 hrtime ?        00:00:00 syndaemon
0 S  1000  2317  2212  0  80   0 - 26164 poll_s ?        00:00:03 nautilus
0 S  1000  2319     1  0  80   0 - 10398 poll_s ?        00:00:00 bonobo-activati
0 S  1000  2321  2212  0  80   0 -  7245 poll_s ?        00:00:00 update-notifier
0 S  1000  2327  2212  0  80   0 -  4469 poll_s ?        00:00:00 gnome-power-man
0 S  1000  2328     1  0  80   0 -  7869 poll_s ?        00:00:00 trashapplet
0 S  1000  2329  2212  0  80   0 -   437 wait   ?        00:00:00 thunderbird
0 S  1000  2338  2212  0  80   0 -  9261 poll_s ?        00:00:00 nm-applet
0 S  1000  2343  2212  9  80   0 - 104703 poll_s ?       00:03:13 firefox
0 S  1000  2346  2329  0  80   0 -   437 wait   ?        00:00:00 run-mozilla.sh
0 S  1000  2350     1  0  80   0 -  1631 poll_s ?        00:00:00 gvfs-gdu-volume
0 S  1000  2355  2346  1  80   0 - 44018 poll_s ?        00:00:32 thunderbird-bin
0 S  1000  2356  2212  0  80   0 -  7472 poll_s ?        00:00:00 python
0 S  1000  2359  2212  0  80   0 - 34833 poll_s ?        00:00:04 skype.real
0 R  1000  2360  2212  0  80   0 -  9952 -      ?        00:00:00 gnome-terminal
4 S     0  2362     1  0  80   0 -  1263 poll_s ?        00:00:00 devkit-disks-da
1 S     0  2363  2362  0  80   0 -  1206 poll_s ?        00:00:00 devkit-disks-da
0 S  1000  2364  2212  0  80   0 - 18114 poll_s ?        00:00:02 pidgin
0 S  1000  2367  2212  0  80   0 - 14504 poll_s ?        00:00:00 tomboy
0 S  1000  2368  2212  0  80   0 -  4188 poll_s ?        00:00:00 polkit-gnome-au
0 S  1000  2373  2212  0  80   0 - 23968 poll_s ?        00:00:00 gnome-volume-co
0 S  1000  2376     1  0  80   0 -  1546 poll_s ?        00:00:00 gvfsd-trash
0 S  1000  2378     1  0  80   0 -  1649 poll_s ?        00:00:00 gvfs-gphoto2-vo
0 S  1000  2379  2212  0  80   0 -  4427 poll_s ?        00:00:00 gdu-notificatio
4 S     0  2383     1  0  80   0 -  1467 poll_s ?        00:00:00 polkitd
1 S  1000  2403     1  0  80   0 -  4376 poll_s ?        00:00:00 gnome-screensav
0 S  1000  2405  2360  0  80   0 -   475 unix_s ?        00:00:00 gnome-pty-helpe
0 S  1000  2406  2360  0  80   0 -  1576 n_tty_ pts/0    00:00:00 bash
0 S  1000  2423  2360  0  80   0 -  1576 wait   pts/1    00:00:00 bash
0 S  1000  2490     1  0  80   0 -  6096 poll_s ?        00:00:00 cpufreq-applet
0 S  1000  2492     1  0  80   0 -  8370 poll_s ?        00:00:00 indicator-apple
0 S  1000  2495     1  0  80   0 -  8127 poll_s ?        00:00:00 indicator-apple
0 S  1000  2509  2312  0  80   0 -   437 wait   ?        00:00:00 sh
0 S  1000  2510  2509  0  80   0 -  5203 poll_s ?        00:00:00 gtk-window-deco
0 S  1000  2547     1  0  80   0 -  1436 poll_s ?        00:00:00 gvfsd-burn
0 S  1000  2585     1  0  80   0 -  2072 poll_s ?        00:00:00 indicator-messa
0 S  1000  2587     1  0  80   0 -  3016 poll_s ?        00:00:00 indicator-statu
0 S  1000  2589     1  0  80   0 -  1581 poll_s ?        00:00:00 indicator-users
0 S  1000  2591     1  0  80   0 -  1723 poll_s ?        00:00:00 indicator-sessi
4 S     0  2613   855  0  80   0 -   535 poll_s ?        00:00:00 dhclient
0 S  1000  2621     1  0  80   0 -  1410 poll_s ?        00:00:00 gvfsd-metadata
0 R  1000  3102  2423  0  80   0 -   606 -      pts/1    00:00:00 ps

> evil@hell:~/Download$ service --status-all
 [ - ]  NetworkManager.dpkg-backup
 [ ? ]  acpi-support
 [ ? ]  acpid
 [ ? ]  alsa-utils
 [ ? ]  anacron
 [ ? ]  apmd
 [ - ]  apparmor
 [ ? ]  apport
 [ ? ]  atd
 [ ? ]  avahi-daemon
 [ ? ]  binfmt-support
 [ + ]  bluetooth
 [ - ]  bootlogd
 [ - ]  brltty
 [ + ]  clamav-freshclam
 [ ? ]  console-setup
 [ ? ]  cpufrequtils
 [ ? ]  cron
 [ + ]  cups
 [ ? ]  dbus
 [ - ]  dkms_autoinstaller
 [ ? ]  dmesg
 [ ? ]  dns-clean
 [ ? ]  emifreq-applet
 [ ? ]  failsafe-x
 [ ? ]  fancontrol
 [ ? ]  gdm
 [ - ]  grub-common
 [ ? ]  hal
 [ ? ]  hddtemp
 [ ? ]  hotkey-setup
 [ ? ]  hwclock
 [ ? ]  hwclock-save
 [ ? ]  hwclock.sh.dpkg-obsolete
 [ - ]  kerneloops
 [ ? ]  keyboard-setup
 [ ? ]  killprocs
 [ - ]  klogd
 [ - ]  laptop-mode
 [ ? ]  linux-restricted-modules-common
 [ ? ]  lm-sensors
 [ ? ]  loadcpufreq
 [ ? ]  module-init-tools
 [ ? ]  network-manager
 [ ? ]  networking
 [ ? ]  ondemand
 [ ? ]  pcmciautils
 [ ? ]  policykit
 [ - ]  postfix
 [ ? ]  pppd-dns
 [ ? ]  procps
 [ + ]  pulseaudio
 [ ? ]  rc.local
 [ ? ]  readahead
 [ ? ]  readahead-desktop
 [ - ]  rsync
 [ ? ]  rsyslog
 [ ? ]  rsyslog-kmsg
 [ + ]  samba
 [ - ]  saned
 [ ? ]  screen-cleanup
 [ ? ]  sendsigs
 [ ? ]  speech-dispatcher
 [ ? ]  stop-bootlogd
 [ ? ]  stop-bootlogd-single
 [ ? ]  stop-readahead
 [ - ]  sysklogd
 [ ? ]  udev
 [ ? ]  udev-finish
 [ ? ]  udevmonitor
 [ ? ]  udevtrigger
 [ ? ]  ufw
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ ? ]  unattended-upgrades
 [ - ]  urandom
 [ ? ]  ushare
 [ ? ]  vboxdrv
 [ - ]  wicd
 [ + ]  winbind
 [ ? ]  wpa-ifupdown
 [ - ]  x11-common

---

### Post by JKyleOKC on 2009-12-28
I don't recognize a number of the services listed, but don't see anything that looks suspicious.

I do see that you have samba running, so you may want to run
```
testparm -v|grep guest

```(press ENTER when it prompts you) and look for "guest ok" entries. Here's what I get:
```
jim@mehitabel:~$ testparm -v|grep guest
Load smb config files from /etc/samba/smb.conf
Processing section "[jim]"
Processing section "[all]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

	map to guest = Bad User
	guest account = nobody
	usershare allow guests = No
	guest only = No
	guest ok = No
	guest ok = Yes
	guest ok = Yes
jim@mehitabel:~$ 

```
The first of those is my "global" setting and the other two are for specific shares. I believe that the default global setting is "yes" and that can open you up to invasion. The one time that I got seriously infected was when I first set up samba (on a much older system) and the invader got in through that setting. While it did no damage to my Linux box through which it entered, the virus did wipe out two Win95 boxes on my home LAN. If you're using samba to access Windows systems, it might be one of them that is creating the mystery files. A number of such varmints do try to spread to every machine on the network they inhabit.

---

### Post by Ev1L on 2009-12-28
evil@hell:~/Download$ testparm -v | grep guest
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

	map to guest = Bad User
	guest account = nobody
	usershare allow guests = No
	guest only = No
	guest ok = No

I removed almost everything, I could temporarily stop samba as well and see if those files will come back.

---

### Post by lavinog on 2009-12-28
When you delete the file, how long does it take to come back?

You could use a script to notify you when it does come back, this way you can see if it is triggered by a particular program.

---

### Post by Ev1L on 2009-12-28
that is what I was thinking, but I wouldn't know how to do it.

now i changed something on samba, removing guest users. it didnt come back so far.
if it does, then i'll keep track of creation dates to see if there's a pattern, last chance is to write such script (don't know how)

---

### Post by lavinog on 2009-12-28
you can try this script:
```

#! /usr/bin/env python

filetowatchfor='/home/evil/Download/khw'

import os
import time

def sendalarm():
  import subprocess
  message = 'The file: %s has returned' % filetowatchfor
  p = subprocess.Popen(['zenity','--info','--text',message])

def main():
  while True:
    if os.path.exists(filetowatchfor):
      sendalarm()
      break
    time.sleep(2)

main()

```
save it in a file called filealarm.py
you can execute it with
```

python filealarm.py

```
it will pop up a message if the file shows up, then exit.

---

### Post by Ev1L on 2009-12-28
thank you very much!

---

### Post by karatedog on 2010-01-09
I like manual methods, as I'm a newbie to system administration. Recently I had this same symptom (a forgotten server of mine has been hacked but sadly not with windows exe files :( ).
So I deleted the files that kept reappearing, and issued:

>$while true; do fuser -u <path/filename>; done > catch_those_nifty_files.txt &

(or you can start this little script first THEN delete the files)

This will poll the file (even if it doesn't exist yet), and if it is created it'll write some info of the running process and username to the "catch_those..." file. As this script constantly polls the file, it will cost a bit more CPU than an event triggered application.

Leave this running for a few hours, check the saved file for the PID appearing, then use 'ps -p PID -F' to get full name of the running process.

---

