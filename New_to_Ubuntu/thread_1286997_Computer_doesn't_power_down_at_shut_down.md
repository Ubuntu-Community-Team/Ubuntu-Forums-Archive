---
title: "Computer doesn't power down at shut down"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by croc1 on 2009-10-09
If I shutdown my computer from the login window it shuts down and will power down, 
but when shut down after login it hangs at power down.
Has anyone an idea how to solve this.
Its a dual boot with windows xp

---

### Post by anewguy on 2009-10-09
:)Edit your grub menu.lst file and add the following to the kernel line for your normal boot:

acpi=force


If you need help editing the file, just let us know.

Dave

---

### Post by croc1 on 2009-10-09
Added it to grub still not powering down

---

### Post by LewRockwell on 2009-10-09
[http://ubuntuforums.org/showthread.php?t=307643](http://ubuntuforums.org/showthread.php?t=307643)

.

---

### Post by croc1 on 2009-10-09
Thanks LewRockwell but that did not work ether

---

### Post by LewRockwell on 2009-10-09
> **croc1 said:**
> Added it to grub still not powering down

you might check your BIOS settings

also, we are assuming you added acpi=force to the proper place in your /boot/grub/menu.lst file

.

---

### Post by croc1 on 2009-10-09
BIOS Settings  acpi - enabled

/boot/grub/menu.lst file

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=e2ebda64-c01c-43fb-b7cb-c311193cbf70 ro quiet  acpi=force

initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=e2ebda64-c01c-43fb-b7cb-c311193cbf70 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2ebda64-c01c-43fb-b7cb-c311193cbf70 ro quiet #splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=e2ebda64-c01c-43fb-b7cb-c311193cbf70 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by anewguy on 2009-10-10
While I don't really think it will make any difference, try adding:

apic=off to the boot line right before the acpi=force option


Of course you have to reboot for any of these options to take effect.  After rebooting and trying shutdown again, if this doesn't work just remove it from the boot line.

Dave :)

---

### Post by croc1 on 2009-10-11
Thanks Dave,
I tried it and it and you were right it didn't work.

---

### Post by anewguy on 2009-10-12
Okay, I know this is a dumb question, but bear with me:

When you select the option from grub to boot Ubuntu, which of the kernels are you booting (i.e., are you sure it's the one you added the acpi=force option to)?

I'll have to do some more thinking/digging and let you know if I come up with something.

BTW - what brand/model is the computer, and do you know the motherboard type?

Thanks
Dave :)

EDIT:  Also, before shutting down, go into a terminal window and type sudo ps -Al and press enter, then copy/paste the output back in a reply here.  Maybe you have some process that just won't die.

---

### Post by croc1 on 2009-10-12
Booting the same kernel with the acpi=force option

Motherboard

AZUS P5GD1 PRO
- Intel LGA775 Pentium 4 CPU
- Intel 915P chipset
- PCI Express Architecture
- AI NOS
- AI NET2
- Dual-Channel DDR400
- High Definition Audio
Serial ATA RAID

Output sudo ps -Al

bob@cally:~$ sudo ps -Al
[sudo] password for bob: 
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0     1     0  0  80   0 -  1005 -      ?        00:00:00 init
1 S     0     2     0  0  75  -5 -     0 kthrea ?        00:00:00 kthreadd
1 S     0     3     2  0 -40   - -     0 migrat ?        00:00:00 migration/0
1 S     0     4     2  0  75  -5 -     0 ksofti ?        00:00:00 ksoftirqd/0
5 S     0     5     2  0 -40   - -     0 watchd ?        00:00:00 watchdog/0
1 S     0     6     2  0 -40   - -     0 migrat ?        00:00:00 migration/1
1 S     0     7     2  0  75  -5 -     0 ksofti ?        00:00:00 ksoftirqd/1
5 S     0     8     2  0 -40   - -     0 watchd ?        00:00:00 watchdog/1
1 S     0     9     2  0  75  -5 -     0 worker ?        00:00:00 events/0
1 S     0    10     2  0  75  -5 -     0 worker ?        00:00:00 events/1
1 S     0    11     2  0  75  -5 -     0 worker ?        00:00:00 khelper
1 S     0    44     2  0  75  -5 -     0 worker ?        00:00:00 kblockd/0
1 S     0    45     2  0  75  -5 -     0 worker ?        00:00:00 kblockd/1
1 S     0    48     2  0  75  -5 -     0 worker ?        00:00:00 kacpid
1 S     0    49     2  0  75  -5 -     0 worker ?        00:00:00 kacpi_notify
1 S     0   134     2  0  75  -5 -     0 serio_ ?        00:00:00 kseriod
1 S     0   179     2  0  80   0 -     0 pdflus ?        00:00:00 pdflush
1 S     0   180     2  0  80   0 -     0 pdflus ?        00:00:00 pdflush
1 S     0   181     2  0  75  -5 -     0 kswapd ?        00:00:00 kswapd0
1 S     0   224     2  0  75  -5 -     0 worker ?        00:00:00 aio/0
1 S     0   225     2  0  75  -5 -     0 worker ?        00:00:00 aio/1
1 S     0  1463     2  0  75  -5 -     0 worker ?        00:00:00 ksuspend_usbd
1 S     0  1464     2  0  75  -5 -     0 hub_th ?        00:00:00 khubd
1 S     0  1555     2  0  75  -5 -     0 worker ?        00:00:00 ata/0
1 S     0  1559     2  0  75  -5 -     0 worker ?        00:00:00 ata/1
1 S     0  1563     2  0  75  -5 -     0 worker ?        00:00:00 ata_aux
1 S     0  2289     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_0
1 S     0  2290     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_1
1 S     0  2291     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_2
1 S     0  2292     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_3
1 S     0  2343     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_4
1 S     0  2344     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_5
1 S     0  2566     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_6
1 S     0  2567     2  0  75  -5 -     0 -      ?        00:00:00 usb-storage
1 S     0  2898     2  0  75  -5 -     0 kjourn ?        00:00:00 kjournald
5 S     0  3118     1  0  76  -4 -  4296 -      ?        00:00:00 udevd
1 S     0  3551     2  0  75  -5 -     0 worker ?        00:00:00 kpsmoused
1 S     0  4819     2  0  75  -5 -     0 kjourn ?        00:00:00 kjournald
0 S     0  5204     1  0  80   0 -   966 -      tty4     00:00:00 getty
0 S     0  5205     1  0  80   0 -   966 -      tty5     00:00:00 getty
0 S     0  5209     1  0  80   0 -   966 -      tty2     00:00:00 getty
0 S     0  5210     1  0  80   0 -   966 -      tty3     00:00:00 getty
0 S     0  5211     1  0  80   0 -   966 -      tty6     00:00:00 getty
1 S     0  5391     1  0  80   0 -  3269 -      ?        00:00:00 acpid
1 S     0  5419     2  0  75  -5 -     0 worker ?        00:00:00 kondemand/0
1 S     0  5420     2  0  75  -5 -     0 worker ?        00:00:00 kondemand/1
5 S   102  5506     1  0  80   0 -  3074 -      ?        00:00:00 syslogd
4 S     0  5566     1  0  80   0 -  2033 syslog ?        00:00:00 dd
1 S   103  5568     1  0  80   0 -  1734 pipe_w ?        00:00:00 klogd
5 S   108  5590     1  0  80   0 -  5446 -      ?        00:00:00 dbus-daemon
5 S     0  5606     1  0  80   0 - 10028 436454 ?        00:00:00 NetworkManager
1 S     0  5620     1  0  80   0 -  6032 -      ?        00:00:00 NetworkManager
5 S     0  5633     1  0  80   0 -  8798 -      ?        00:00:00 system-tools-b
5 S   109  5653     1  0  80   0 -  7428 -      ?        00:00:00 avahi-daemon
1 S   109  5654  5653  0  80   0 -  7395 -      ?        00:00:00 avahi-daemon
5 S     0  5685     1  0  80   0 - 20160 -      ?        00:00:00 cupsd
5 S     0  5733     1  0  80   0 - 13511 -      ?        00:00:00 nmbd
5 S     0  5735     1  0  80   0 - 18634 -      ?        00:00:00 smbd
1 S     0  5752     1  0  80   0 - 13898 -      ?        00:00:00 winbindd
1 S     0  5790     1  0  80   0 -  1568 -      ?        00:00:00 dhcdbd
1 S     0  5791  5752  0  80   0 - 13898 -      ?        00:00:00 winbindd
1 S     0  5793  5752  0  80   0 - 13900 -      ?        00:00:00 winbindd
1 S     0  5808  5752  0  80   0 - 13898 -      ?        00:00:00 winbindd
1 S     0  5809  5735  0  80   0 - 18634 pause  ?        00:00:00 smbd
5 S   111  5813     1  0  80   0 -  9012 429493 ?        00:00:00 hald
5 S     0  5816     1  0  80   0 -  9215 439005 ?        00:00:00 console-kit-da
0 S     0  5878  5813  0  80   0 -  4455 283038 ?        00:00:00 hald-runner
0 S     0  5902  5878  0  80   0 -  4985 395422 ?        00:00:00 hald-addon-cpu
4 S   111  5903  5878  0  80   0 -  4168 -      ?        00:00:00 hald-addon-acp
0 S     0  5904  5878  0  80   0 -  4982 283038 ?        00:00:00 hald-addon-inp
0 S     0  5916  5878  0  80   0 -  4982 -      ?        00:00:00 hald-addon-sto
4 S     0  5923  5878  0  80   0 -  4982 440705 ?        00:00:00 hald-addon-sto
4 S     0  5925  5878  0  80   0 -  4982 440705 ?        00:00:00 hald-addon-sto
4 S     0  5927  5878  0  80   0 -  4982 440705 ?        00:00:00 hald-addon-sto
4 S     0  5929  5878  0  80   0 -  4982 440705 ?        00:00:00 hald-addon-sto
4 S     0  5931  5878  0  80   0 -  4982 440705 ?        00:00:00 hald-addon-sto
0 S     0  5934  5878  0  80   0 -  4982 429493 ?        00:00:00 hald-addon-sto
0 S     0  5937  5878  0  80   0 -  4982 429493 ?        00:00:00 hald-addon-sto
5 S     0  5957     1  0  80   0 -  3383 448962 ?        00:00:00 hcid
1 S     0  5964     2  0  75  -5 -     0 worker ?        00:00:00 btaddconn
1 S     0  5965     2  0  75  -5 -     0 worker ?        00:00:00 btdelconn
4 S     0  5975  5957  0  80   0 -  3338 440035 ?        00:00:00 bluetoothd-ser
4 S     0  5979  5957  0  80   0 -  3357 283038 ?        00:00:00 bluetoothd-ser
5 S     0  5985     2  0  70 -10 -     0 rfcomm ?        00:00:00 krfcommd
1 S     0  6034     1  0  80   0 - 29050 858990 ?        00:00:00 gdm
5 S     0  6054  6034  0  80   0 - 42015 -      ?        00:00:00 gdm
4 S     0  6058  6054  2  80   0 - 29457 -      tty7     00:00:25 Xorg
5 S   112  6060     1  0  78  -2 -  6355 -      ?        00:00:00 ntpd
1 S     1  6094     1  0  80   0 -  4107 -      ?        00:00:00 atd
1 S     0  6108     1  0  80   0 -  4655 -      ?        00:00:00 cron
0 S     0  6229     1  0  80   0 -   966 -      tty1     00:00:00 getty
0 S  1000  6263     1  0  80   0 - 10558 -      ?        00:00:00 gconfd-2
1 S  1000  6265     1  0  80   0 - 17023 -      ?        00:00:00 gnome-keyring-
4 S  1000  6266  6054  0  80   0 - 48399 172532 ?        00:00:00 x-session-mana
1 S  1000  6323  6266  0  80   0 - 53736 107374 ?        00:00:00 seahorse-agent
1 S  1000  6327     1  0  80   0 -  5363 880038 ?        00:00:00 dbus-daemon
0 S  1000  6328  6266  0  80   0 - 66275 923553 ?        00:00:00 gnome-settings
0 S  1000  6336  6328  0  80   0 - 37052 -      ?        00:00:01 pulseaudio
0 S  1000  6339  6336  0  80   0 - 13920 347779 ?        00:00:00 gconf-helper
1 S  1000  6349     1  0  80   0 - 33491 -      ?        00:00:01 gnome-screensa
0 S  1000  6354  6266  0  80   0 -   986 wait   ?        00:00:00 compiz
0 S  1000  6356  6266  0  80   0 - 77424 -      ?        00:00:04 gnome-panel
0 S  1000  6357  6266  0  80   0 - 106861 844437 ?       00:00:00 nautilus
0 S  1000  6377     1  0  80   0 - 36932 267652 ?        00:00:00 bonobo-activat
0 S  1000  6388     1  0  80   0 - 11195 447002 ?        00:00:00 gvfsd
1 S  1000  6417     1  0  80   0 - 15580 futex_ ?        00:00:00 gvfs-fuse-daem
0 S  1000  6423  6354  2  80   0 - 67187 349322 ?        00:00:25 compiz.real
0 S  1000  6427  6266  0  80   0 - 33424 429493 ?        00:00:01 emerald
0 S  1000  6430  6266  0  80   0 - 51893 923385 ?        00:00:00 update-notifie
0 S  1000  6434  6266  0  80   0 - 30008 -      ?        00:00:00 tracker-applet
0 S  1000  6437  6266  0  99  19 - 34339 923582 ?        00:00:01 trackerd
0 S  1000  6440  6266  0  80   0 - 49374 429493 ?        00:00:00 nm-applet
1 S  1000  6441     1  0  80   0 - 46821 287353 ?        00:00:00 gnome-volume-m
0 S  1000  6442  6266  0  80   0 - 47948 923385 ?        00:00:00 python
1 S  1000  6445     1  0  80   0 - 53322 287343 ?        00:00:00 gnome-power-ma
0 S  1000  6455     1  0  80   0 - 11195 459561 ?        00:00:00 gvfsd-burn
0 S  1000  6460     1  0  80   0 - 15847 923553 ?        00:00:00 gvfsd-trash
0 S  1000  6476     1  0  80   0 - 77824 267653 ?        00:00:00 evolution-data
0 S  1000  6482     1  0  80   0 - 60293 171798 ?        00:00:00 mixer_applet2
0 S  1000  6484     1  0  80   0 - 51258 -      ?        00:00:00 trashapplet
0 S  1000  6514     1  0  80   0 - 47484 -      ?        00:00:02 geyes_applet2
0 S  1000  6518     1  0  80   0 - 70726 923540 ?        00:00:00 gweather-apple
0 S  1000  6643     1  4  80   0 - 136005 260096 ?       00:00:33 firefox
0 S  1000  6788     1  0  80   0 - 74451 206771 ?        00:00:00 evolution-alar
0 R  1000  6863     1  1  80   0 - 64506 -      ?        00:00:00 gnome-terminal
0 S  1000  6865  6863  0  80   0 -  4837 -      ?        00:00:00 gnome-pty-help
0 S  1000  6866  6863  0  80   0 -  5170 wait   pts/0    00:00:00 bash
4 R     0  6883  6866  0  80   0 -  1661 -      pts/0    00:00:00 ps
bob@cally:~$ 

Thanks 
Bob

---

### Post by anewguy on 2009-10-12
it's a shot in the dark, but....

kill your weather applet, and firefox (if showing like what you posted) if they are running when you are ready to shutdown.

don't know if it will make any difference or not.  Right now I don't really know why you can't shut down.

Dave :)

---

### Post by croc1 on 2009-10-12
killed the weather applet, and firefox still no joy.

Bob:confused:

---

### Post by OffAxis on 2009-10-12
try shutting down from the command prompt

```
sudo shutdown now
```

and try a reboot

```
sudo reboot
```

any love?

also, do any of the earlier kernels shut down properly?

---

### Post by croc1 on 2009-10-12
Thanks OffAxis
sudo shutdown now - ubuntu logged out and went to recovery menu
sudo reboot       - haven't tried, reboot is not a problem
none of the earlier kernels have powered down properly either. 

Bob

---

### Post by anewguy on 2009-10-12
Well, as long as we're willing to try the command line to see if we can track this down, try this:

sudo shutdown -P now

The -P requests a power down after the system is halted.  I don't remember if this is a default, or if the default is to just halt but not power down.

Also, I know this is going to sound like a no-no, but for testing try setting your bios acpi setting to off and then try to shutdown with the acpi=force option still in place.  After testing, just set the bios acpi setting back to where it was.

Dave

EDIT:  Also, when you say it logged out and went to the recovery menu, do you mean that X windows shutdown and you were presented with the terminal login prompt?

---

### Post by croc1 on 2009-10-12
sudo shutdown -P now -  shutdown normally and stopped at 
(5232.688393) power down

bios acpi setting to off - also shutdown normally and stopped at
(125.146434) power down

yes x windows shutdown went to the terminal login prompt and then the recovery menu,

---

### Post by anewguy on 2009-10-12
Well, I guess I'm out of things for you to try - sorry I couldn't be of help.  Normally that would have done it.  Don't know why Ubuntu shuts down but the system itself hangs at power down.

Sorry I couldn't have been of help!!

Dave :)

---

### Post by croc1 on 2009-10-12
Thanks anyway for trying Dave, If it is ever solved it will probable be something simple. 

Thanks again 
Bob

---

### Post by anewguy on 2009-10-12
I did a web search (google) with the following search string:

linux doesn't power down on shutdown

and got many hits.  One of the things I noticed was apparent bugs in the kernel depending on your hardware and bios.  It may be worth a shot to either upgrade to 9.04 or at least try the LiveCD for 9.04 and see if it shutsdown, the try the LiveCD for 8.04 (which it appears you are running) and see if it shutsdown.  It might be worth it to upgrade to 9.04

I'll keep looking and if I find something I'll let you know.

dave :)

BTW - did you ever tell us what hardware you are running (make/model)?

---

### Post by croc1 on 2009-10-14
Doesn't shutdown with LiveCD for 8.04, will download 9,04 and try that.
Motherboard is 
AZUS P5GD1 PRO
- Intel LGA775 Pentium 4 CPU
- Intel 915P chipset
- PCI Express Architecture
- AI NOS
- AI NET2
- Dual-Channel DDR400
- High Definition Audio
Serial ATA RAID

computer has no make/model

---

### Post by LewRockwell on 2009-10-14
> **croc1 said:**
> will download 9.04 and try that

+ 1

.

---

### Post by croc1 on 2009-10-14
Tried the LiveCD for 9.04 and the computer Shutdown and Powered Down, Apparently the problem is a bug in the kernel 
In 15 days will do clean install of 9.10 final.

Thanks to everybody for their help in solving this.

Bob :grin:

---

### Post by anewguy on 2009-10-15
You're welcome!

Dave :)

---

### Post by loweehahn on 2009-11-03
[SIZE=3]Mine is a slightly different story. Mine is also a dual boot with XP and Ubuntu 9.10. Whenever I shut Ubuntu down it'll shut down until the black screen appears with some words at the top left of the screen and then the next thing is the word **logical block** is shown and it just stops there.[/SIZE]

---

