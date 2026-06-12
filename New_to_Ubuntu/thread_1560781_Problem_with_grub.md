---
title: "Problem with grub"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Wungle on 2010-08-25
My netbook recently crashed while trying to save an open office doc in an old word format.  After forcing a reboot, I got the Grub rescue prompt. I tried going through the Grub rescue mode commands in the Ubuntu documentation,  but kept getting "Unknown filesystem". After running Boot Info Scripts I can see that there is a problem with the filesystem in sda1, but have no idea how to fix this. Any help much appreciated!
Results of Boot Info Scripts below and attached.

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   306,620,415   306,618,368  83 Linux
/dev/sda2         306,622,462   312,580,095     5,957,634   5 Extended
/dev/sda5         306,622,464   312,580,095     5,957,632  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8118 MB, 8118075392 bytes
250 heads, 62 sectors/track, 1022 cylinders, total 15855616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62    15,840,999    15,840,938   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ddb10d2b-9693-4092-a11d-72d7f09297a1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E392-ADBB                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  03 00 2e 00 0c 00 01 02  2e 00 00 00 8d 12 2c 00  |..............,.|
00000010  0c 00 02 02 2e 2e 00 00  05 00 2e 00 34 00 08 01  |............4...|
00000020  4d 61 6b 65 66 69 6c 65  64 70 6b 67 2d 6e 65 77  |Makefiledpkg-new|
00000030  05 00 2e 00 1c 00 11 01  4d 61 6b 65 66 69 6c 65  |........Makefile|
00000040  2e 64 70 6b 67 2d 6e 65  77 00 00 00 0a 00 2e 00  |.dpkg-new.......|
00000050  18 00 0a 02 66 75 6c 6f  6f 6e 67 2d 32 65 67 2d  |....fuloong-2eg-|
00000060  6e 65 77 00 06 00 2e 00  10 00 06 02 63 6f 6d 6d  |new.........comm|
00000070  6f 6e 00 00 04 00 2e 00  1c 00 07 01 4b 63 6f 6e  |on..........Kcon|
00000080  66 69 67 32 66 2e 64 70  6b 67 2d 6e 65 77 77 00  |fig2f.dpkg-neww.|
00000090  0c 00 2e 00 70 0f 09 02  6c 65 6d 6f 74 65 2d 32  |....p...lemote-2|
000000a0  66 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |f...............|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200
```

---

### Post by john newbuntu on 2010-08-25
Yeah, it appears like you have to repair the filesystem on sda1.  Be aware that at times you may lose a lot of your data during the repair process.  So, it is always advisable to make a copy of either the partition or your whole disk with a tool like say "ddrescue" so that you could try other methods to recover more data later on:
[http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html#Examples](http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html#Examples)

Once this is done (or if you decide to take the risk and skip it), run the following commands from a liveCD or liveUSB
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```If this gives any errors, then run:
```
sudo e2fsck -f -y -v /dev/sda1
```
Finally, reboot.

---

### Post by Wungle on 2010-08-26
Thanks for your help John.
I've now rebooted and have now got a cli screen, which has asked me for my login and password details. Once logged in, I get:
```
Last login: Thu Aug 26 09:48:35 BST 2010 on tty2
Linux Jake-Netbook 2.6.34-020634rc1-generic #020634rc1 SMP Tue Mar 9 10:59:29 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help/ubuntu.com/

jake@Jake-Netbook:~$
```What next?
Thanks again

---

### Post by john newbuntu on 2010-08-26
From here, try to get into GNOME (assuming that is what you were using) using the command:
sudo service gdm start
or
sudo service gdm restart

EDIT: Should you encounter problems, try: 
sudo dpkg-reconfigure gdm
and repeat the first command.

---

### Post by Wungle on 2010-09-01
Thanks again John, and sorry for lack of response - have been away.
I am using GNOME, but after entering the commands that you suggest, all I get is:

```
gdm start/running, process 5796
jake@Jake-Netbook:~$ 
```Any ideas?

---

### Post by john newbuntu on 2010-09-01
Not sure if some files are missing or were corrupted.  Try:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by Wungle on 2010-09-02
The update works fine, but when I enter the install command line, I get 
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
jake@Jake-Netbook:~$
```

Tried running the sudo service gdm start command again, but no joy, though I do get what appears to be some sort of a starting up screen, the bottom line of which is Checking battery state, which I recognise, this flickers momentarily 3 or 4 times, before returning to the CLI.
Any further help would be much appreciated.

---

### Post by john newbuntu on 2010-09-03
From the prompt, try:
sudo service gdm stop
and type:
startx

If this does not work, check if you have enough space in your filesystem by issuing the command:
df -Th

Also take a look at the logs using the commands and see if you can spot anything:
tail /var/log/syslog
tail /var/log/Xorg.0.log
tail /var/log/auth.log
dmesg

---

### Post by Wungle on 2010-09-03
sudo service gdm stop
leads to 
stop: Unknown instance:
df-Th command is not found

Not really sure what I'm looking for in the logs, so can't tell whether there's anything out of order...

---

### Post by QLee on 2010-09-03
[QUOTE=Wungle]sudo service gdm stop
leads to 
stop: Unknown instance:
df-Th command is not found

...[/QUOTE]

Are you doing that desktop manager service stop/restart from a tty terminal (for example tty2) or from within a gnome X session?

You left out the space in the df command, should be df -Th, not df-Th.

Edit: Another thought before I leave for the day. Is this a netbook edition install, if so, John may want to amend what was suggested for reinstall in post 6.

---

### Post by john newbuntu on 2010-09-03
You're right Qlee.  Thanks for the correction. Wungle got a lot more than what he asked for.  For netbook remix only, 
```
sudo apt-get install ubuntu-netbook-remix
```[COLOR=#000099]
[/COLOR]should have been sufficient to install it.  Instead he got the whole desktop.

@Wungle, you may want to uninstall the ubuntu-desktop using:
```
sudo apt-get remove ubuntu-desktop
```and then run the first command above.

But basically, the error looks elsewhere possibly with disk space, display driver or areas that I am unfamiliar with that others could help, which is why I wanted to take a look at the files such as /var/log/Xorg.0.log.  Usually, startx should bring up the X session.  If you can post the contents of your Xorg.0.log file in code tags, it might help.

---

### Post by Wungle on 2010-09-06
@QLee - thanks for the correction, maybe should have spotted that myself...!
Also, the missing space was due to my typo, as I'm manually typing in what I see on my netbook in the tty2 terminal onto this post on my desktop.
@John - And this is where it gets difficult to post the logs, as I'm using my desktop to work on/update this post, while I enter the commands that you are suggesting onto my netbook - can I cut and paste from the tty terminal into here on a different machine?

---

### Post by Wungle on 2010-09-06
> **Wungle said:**
> the missing space was due to my typo
Actually, reading back through the post, I've realised that I was entering df-Th into the command line.
Have just entered df -Th and got the following:
```
Filesystem Type Size Used Avail Use% Mounted on
/dev/sda1 ext4 144G 6.0G 131G 5% /
none tmfps 497M 280K 497M 1% /dev
none tmfps 497M 0 497M 0% /dev/shm
none tmfps 497M 68K 497M 1% /var/run
none tmfps 497M 0 497M 0% /var/lock
none tmfps 497M 0 497M 0% /lib/init/rw
```

Doesn't look like a problem with disk space.

---

### Post by Wungle on 2010-09-06
```
Filesystem Type  Size Used Avail  Use% Mounted on
/dev/sda1  ext4  144G 6.0G  131G    5% /
none      tmfps  497M 280K  497M    1% /dev
none      tmfps  497M    0  497M    0% /dev/shm
none      tmfps  497M  68K  497M    1% /var/run
none      tmfps  497M    0  497M    0% /var/lock
none      tmfps  497M    0  497M    0% /lib/init/rw
```This should be a bit clearer.

---

### Post by john newbuntu on 2010-09-06
Right.  You are ok as far as disk space goes.  Perhaps something wrong with the driver that is used to bring up X.  I am not sure on whether you tried the command:
startx
See if that helps.  I suspect it to be a graphics problem. See if you can identify anything out of the ordinary in Xorg.0.log.  You could copy the file to a mounted USB drive on the netbook (I hope it has one at least) and then try posting that way.

---

### Post by Wungle on 2010-09-08
startx command gives me
```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux Jake-Netbook 2.6.34-020634rc1-generic #020634rc1 SMP Tue Mar 9 10:59:29 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.34-020634rc1-generic root=UUID=c8aa5a8b-b7d8-472e-a3e5-a5b2a5b4c808 ro quiet splash hpet=force nolapic
Build Date: 21 July 2010 12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational),
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep  8 10:20:40 2010
(==) Using config directory: "/usr/lib/X11/xorg.config.d"

waiting for X server to shut down  ddxSigGiveUp: Closing log
```tail /var/log/syslog command:
```
Sep  8 07:44:02 Jake-Netbook anacron[7038]: Normal exit (1 job run)
Sep  8 08:17:01 Jake-Netbook CRON[7158]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  8 09:17:01 Jake-Netbook CRON[7163]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  8 10:16:59 Jake-Netbook acpid: client 6603[0:0] has disconnected
Sep  8 10:16:59 Jake-Netbook acpid: client connected from 7184[0:0]
Sep  8 10:16:59 Jake-Netbook acpid: 1 client rule loaded
Sep  8 10:17:01 Jake-Netbook CRON[7243]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  8 10:20:40 Jake-Netbook acpid: client 7184[0:0] has disconnected
Sep  8 10:20:40 Jake-Netbook acpid: client connected from 7266[0:0]
Sep  8 10:20:40 Jake-Netbook acpid: 1 client rule loaded
```tail /var/log/Xorg.0.log command:
```
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) USB2.0 UVC WebCam: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) PS/2 Mouse: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
 ddxSigGiveUp: Closing log
```tail /var/log/auth.log command:
```
Sep  8 07:17:01 Jake-Netbook CRON[7028]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  8 07:17:01 Jake-Netbook CRON[7028]: pam_unix(cron:session): session closed for user root
Sep  8 07:30:01 Jake-Netbook CRON[7033]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  8 07:30:01 Jake-Netbook CRON[7033]: pam_unix(cron:session): session closed for user root
Sep  8 08:17:01 Jake-Netbook CRON[7156]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  8 08:17:01 Jake-Netbook CRON[7156]: pam_unix(cron:session): session closed for user root
Sep  8 09:17:01 Jake-Netbook CRON[7161]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  8 09:17:01 Jake-Netbook CRON[7161]: pam_unix(cron:session): session closed for user root
Sep  8 10:17:01 Jake-Netbook CRON[7242]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  8 09:17:01 Jake-Netbook CRON[7161]: pam_unix(cron:session): session closed for user root
```The dmesg command output is too long for me to copy out, and I can't figure out how to copy it to the USB drive, or even scroll up through the lines in tty2... sorry noob alert!

---

### Post by john newbuntu on 2010-09-09
Looks like you are having a problem with X.  You could try to make the OS use failsafe vesa driver instead of the current one.  First, try the command
```
sudo xinit gdm
```and see if it helps.  If not, try reconfiguring X using the command:
```
sudo dpkg-reconfigure xserver-xorg
```and choose vesa for the standard video driver

---

### Post by Wungle on 2010-09-09
sudo xinit gdm command does something: goes into the launching screen with Checking Battery State as final line of text, but then reverts back to cli, after flashing a white box in the top left corner of the screen (takes up roughly a quarter of the area of the screen).

[FONT=monospace]When I enter the sudo dpkg-reconfigure xserver-xorg command, nothing happens, I just get another command line, so I'm not sure how to choose vesa as the standard video driver.
[/FONT]

---

### Post by john newbuntu on 2010-09-10
Normally you will find a file called /etc/X11/xorg.conf, where you would make your changes.  Only if you do not find this file, run:
```
sudo service gdm stop
sudo Xorg -configure
```This will generate the xorg.conf but in the home directory.  Move it to the right place using:
```
sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
```Edit this file and you will find a section called "Device" and a line for "driver" .  You will have to change the word following driver to vesa.  For editing, you can use "nano /etc/X11/xorg.conf" or any other CLI editor of your choice.

 I have personally been able to use dpkg-reconfigure successfully.  I am wondering if some X related stuff is missing.  You might want to check this ubuntu geek article on how to re-install X.  I have to warn you that I have not tried this myself, but in theory it should work.  Also take a moment to read the comments by some of the posters. 
[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

---

### Post by Wungle on 2010-09-13
Hi John,
Thanks for all your help on this. I didn't have any luck with your last suggestions, nor did the post in the ubuntugeek forum shed any more light.  So in the end I cut my losses and reinstalled the netbook remix.
Thanks again - I learnt a lot!
Jake

---

