---
title: "Cannot &quot;See&quot; all my files in my Mobile HDD"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by bochenghu on 2009-06-20
I just recently gave up on my Win OS and moved on to greener pastures in he for of Ubuntu 9.04 (Jaunty)

The migration of data went well and all is fine until I tried to access all the files I have backed up into a mobile Hardisk.... I cannot see all my files in Nautilus. Running fdisk -lu, I can see the occupied disk space which should mean all my files are still there... I used sudo bash and CD to the drive an run an ls, again all my files are there.

Why can't I access my files in nautilus.... I can't even see them.... Really need help on this because I've tried everything my noobie brain knows...

Thanks.

---

### Post by thegreenblob on 2009-06-20
Are they hidden files? If so you should be able to see them by pressing Ctrl+H in nautilus.

---

### Post by bochenghu on 2009-06-20
Thanks for the speedy reply man~

Tried your Ctrl+H in nautilus, screen flicker for a while then back to nothing.

---

### Post by thegreenblob on 2009-06-20
So you can see the files in the terminal when you use "ls" using sudo?

If so probably a permissions problem.

Might be able to fix that with:

```
sudo chown yourusername /location/to/drive/*
```

That should make it so all the files are "yours".

If that doesn't work I suppose you could run nautilus as root.

```
gksudo nautilus
```

To get the files off.

---

### Post by bochenghu on 2009-06-20
Wow~ A heartfelt thanks for the solutions.

sadly it didn't work again.

I entered the commands as listed with no errors
I used the chown command but there was no output on screen, when I ran the normal Nautilus and the gksudo nautilus, it still shows nothing.

I then ran sudo bash, went into the drive and did another ls, the output is:

xxx@xxx-desktop:~$ sudo chown xxx /media/Mobile
xxx@xxx-desktop:~$ cd /media/Mobile
xxx@xxx-desktop:/media/Mobile$ ls
ls: cannot access From D Drive: Input/output error
autorun.inf     From D Drive  $RECYCLE.BIN  Backup    System Volume Information
ccsetup212.exe  PhotoZ        RECYCLER      Backup02  untitled folder
xxx@xxx-desktop:/media/Mobile$ 

All the files listed, neither the regular nor the elevated rights nautilus can see the files....

---

### Post by ddrichardson on 2009-06-20
When you say you can't see your files, is the drive listed in Nautilus?

---

### Post by bochenghu on 2009-06-20
Yes, it's listed. I can write to it and read the newly written data. Just that files from my old computer cannot be seen. All the files and folders listed by ls cannot be seen by nautilus.

The drive is in NTFS format by the way, but I did check to see if ntfs-3g was installed.

---

### Post by bochenghu on 2009-06-20
This here's the screen shot of the results of the LS command

*removed*

And here's a screen shot of my woes....
*removed*

---

### Post by ddrichardson on 2009-06-20
Check the drive for problems```
sudo apt-get install testdisk
sudo testdisk
```
Follow the prompts, its fairly self explanatory if you've any problems post back.

---

### Post by ddrichardson on 2009-06-20
What's the output of```
ls -l /media/Mobile
```

---

### Post by bochenghu on 2009-06-20
```

ls: cannot access /media/Mobile/From D Drive: Input/output error
total 2888
drwxrwxrwx 1 root root       0 2009-05-04 15:22 autorun.inf
-rwxrwxrwx 2 root root 2934168 2008-10-21 15:54 ccsetup212.exe
d????????? ? ?    ?          ?                ? From D Drive
drwxrwxrwx 1 root root    4096 2009-06-19 06:10 PhotoZ
drwxrwxrwx 1 root root       0 2009-05-26 10:34 $RECYCLE.BIN
drwxrwxrwx 1 root root       0 2009-06-13 21:17 RECYCLER
drwxrwxrwx 1 root root    8192 2009-06-19 22:20 Sharon
drwxrwxrwx 1 root root    4096 2009-06-19 22:31 Sharon02
drwxrwxrwx 1 root root    4096 2009-05-21 10:11 System Volume Information
drwxrwxrwx 1 root root       0 2009-06-20 17:01 untitled folder

```

That was the results of ls -l, and the testdisk program found no errors.

A very heartfelt thank you for all your help.

---

### Post by ddrichardson on 2009-06-20
Yes they're all owned by root.```
sudo chown -R username:username /media/Mobile
```where username is your login username.

---

### Post by bochenghu on 2009-06-20
I tried the chown command, it runs for a while, i then did the ls -l /device/Mobile and it is still owned by root..... 

I'm dumbfounded......

I even tried unplugging it, and mounting it again... no luck.

Anyway i can mount the drive as root? Like in windows, I can map a drive or run a program as another user.... can it be done in Ubuntu?

---

### Post by bochenghu on 2009-06-20
```

haron@sharon-desktop:/$ sudo chown -R sharon:sharon /media/Mobile
chown: cannot access `/media/Mobile/From D Drive': Input/output error
sharon@sharon-desktop:/$ ls -l /media/Mobile
ls: cannot access /media/Mobile/From D Drive: Input/output error
total 2888
drwxrwxrwx 1 root root       0 2009-05-04 15:22 autorun.inf
-rwxrwxrwx 2 root root 2934168 2008-10-21 15:54 ccsetup212.exe
d????????? ? ?    ?          ?                ? From D Drive
drwxrwxrwx 1 root root    4096 2009-06-19 06:10 PhotoZ
drwxrwxrwx 1 root root       0 2009-05-26 10:34 $RECYCLE.BIN
drwxrwxrwx 1 root root       0 2009-06-13 21:17 RECYCLER
drwxrwxrwx 1 root root    8192 2009-06-19 22:20 Sharon
drwxrwxrwx 1 root root    4096 2009-06-19 22:31 Sharon02
drwxrwxrwx 1 root root    4096 2009-05-21 10:11 System Volume Information
drwxrwxrwx 1 root root       0 2009-06-20 17:01 untitled folder
sharon@sharon-desktop:/$ sudo chown -R sharon:sharon /media/Mobile
chown: cannot access `/media/Mobile/From D Drive': Input/output error

```

As you can see from the screen dump... it's still the same :confused:

---

### Post by ddrichardson on 2009-06-20
Can you unplug then replug in and tell me the last few lines from the dmesg command?

---

### Post by bochenghu on 2009-06-20
```

[   16.517914] r8169: eth0: link up
[   26.525020] eth0: no IPv6 routers present
[  516.973031] usb 1-5: USB disconnect, address 2
[  527.372043] usb 1-5: new high speed USB device using ehci_hcd and address 3
[  527.509857] usb 1-5: configuration #1 chosen from 1 choice
[  527.512186] scsi3 : SCSI emulation for USB Mass Storage devices
[  527.512669] usb-storage: device found at 3
[  527.512672] usb-storage: waiting for device to settle before scanning
[  532.512190] usb-storage: device scan complete
[  532.512808] scsi 3:0:0:0: Direct-Access     TOSHIBA  MK6021GAS        0014 PQ: 0 ANSI: 0
[  532.516346] sd 3:0:0:0: [sdb] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[  532.519050] sd 3:0:0:0: [sdb] Write Protect is off
[  532.519054] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  532.519057] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  532.521042] sd 3:0:0:0: [sdb] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[  532.523296] sd 3:0:0:0: [sdb] Write Protect is off
[  532.523300] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  532.523303] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  532.523308]  sdb: sdb1
[  532.590732] sd 3:0:0:0: [sdb] Attached SCSI disk
[  532.590810] sd 3:0:0:0: Attached scsi generic sg2 type 0

```

I think these are the ones you were talking about?

Thanks for you patience in the matter....

---

### Post by ddrichardson on 2009-06-20
There's something not right with the "From D Drive" folder.  Have you got access to a Windows machine that you can chkdsk from?

---

### Post by bochenghu on 2009-06-20
Gulp.... I gotta drive up to my office to do that. 

Ok, will give it a go. Be back in two hours. Thanks for all the advice. you're a gem.

---

### Post by bochenghu on 2009-06-23
Finally retrieved my files. Seems you're right. I plugged the external HDD to my office Windows machine and found some errors after running scandisk.

Thanks for all the help ya'all.

---

### Post by ddrichardson on 2009-06-24
> **bochenghu said:**
> Finally retrieved my files. Seems you're right. I plugged the external HDD to my office Windows machine and found some errors after running scandisk.

Thanks for all the help ya'all.
Its quite common and there are ways around it but not having access to your data its always best to suggest the MS route.

Manually mounting, using ntfs-3g will tell you more:```
ntfs-3g /dev/sdb1 /media/Mobile
```Often supplying the --force option is enough but YMMV.

Removable media is becoming more of a pain for me, FAT32 doesn't like files over 4Gb (which I have) and NTFS is terrible at recovering from an unsafe mount.  If Windows had decent support for other filesystems, I'd switch in a heartbeat.

---

