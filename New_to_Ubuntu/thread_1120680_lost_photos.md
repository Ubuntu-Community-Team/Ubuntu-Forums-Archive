---
title: "lost photos"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by sekani on 2009-04-09
i have tried to add some photos to a cd-rw that already had photos on it.  the cd/dvd creator opened up automatically and i tried to write to disc but for some reason lost all the photos on the cd-rw! this is the first time i have used cd/dvd creator... i use ubuntu 8.10 and a dell inspiron 530s...have i lost the photos for good or can i retrieve them...i am guessing the problem is operator error,can anyone help?

---

### Post by tjwoosta on 2009-04-09
> **sekani said:**
> i have tried to add some photos to a cd-rw that already had photos on it.  the cd/dvd creator opened up automatically and i tried to write to disc but for some reason lost all the photos on the cd-rw! this is the first time i have used cd/dvd creator... i use ubuntu 8.10 and a dell inspiron 530s...have i lost the photos for good or can i retrieve them...i am guessing the problem is operator error,can anyone help?

hmm.. it sounds to me like they might be gone

did you see it try to reformat the disk or something?

here is some usefull info i just found that might help

>   Recovery of fast blanked CD-RW

It's possible to recover data from a quick-erased CD-RW disc without modifying it!

When a CD-RW is fast erased, the PMA, TOC, pregap and the first sectors of your CD-RW are erased. Because the TOC has been erased, CD-RW appears as blank/empty. Because the first sectors has been erased including the headers, sectors 0, 1, 2... can't be located anymore but subsequent sectors can still be found. Unfortunatly, not each OS allows you to easilly access such sector but it works using Linux.

To recover your lost data, run Linux version of Photorec. If CD-RW listed size is 0 or 2048 bytes, the CDROM reader firmware will block further read request, so you have to use another CDROM reader/writer. Start of the recovery is really slow because the first sectors are unreadable but usually after sector 300, data can be recovered, so be patient.
Read of previous cdrom session

With multi-session cdrom, it is possible to delete files of previous session. Because the files are not really deleted, it is possible to recover them. To read files from the first session, run under Linux
```

mount /dev/cdrom /mnt/cdrom -t iso9660  -o session=0
```



source  [http://www.cgsecurity.org/wiki/CDRW]("http://www.cgsecurity.org/wiki/CDRW")

---

### Post by sekani on 2009-04-10
i have tried to run the command but get this message...dean@dean-desktop:~$ mount /dev/cdrom /mnt/cdrom -t iso9660  -o session=0
mount: only root can do that
dean@dean-desktop:~$ ...where do i go from here?  thanks

---

### Post by Penguin Guy on 2009-04-10
> **sekani said:**
> i have tried to run the command but get this message...dean@dean-desktop:~$ mount /dev/cdrom /mnt/cdrom -t iso9660  -o session=0
mount: only root can do that
dean@dean-desktop:~$ ...where do i go from here?  thanks
Try: [COLOR="DimGray"]sudo mount /dev/cdrom /mnt/cdrom -t iso9660  -o session=0[/COLOR], then enter password.

---

### Post by sekani on 2009-04-10
dean@dean-desktop:~$ sudo mount /dev/cdrom /mnt/cdrom -t iso9660 -o session=0
mount: mount point /mnt/cdrom does not exist
this is the message i got after entering my password...the cd/rw is in the drive....thanks

---

### Post by tjwoosta on 2009-04-11
for a mountpoint you can really use any directory you want

(/mnt/cdrom is really just a suggested mountpoint)

you could just make a new directory called /mnt/cdrom if you really want, but its likely that ubuntu already has one created named /media/cdrom

so try 

```

sudo mount /dev/cdrom /media/cdrom -t iso9660  -o session=0

```


if it says /media/cdrom doesn't exist either, then just make one  

(the mountpoint is simply the directory that you will be navigating to in order to view the files that are on the cdrom device , it can be anywhere you choose)



also just to clarify on your last post about what root is 


root basically means "administrator privelages"  

when it says only root can do that, it means you must have administrator privelages to do it


anytime you want administrator privelages in ubuntu you will need to use the sudo command before the other commands that you are trying to execute

sudo stands for (Super User DO)

so if it says you need root privelages to do the mount command, you will simply put sudo before it and it will ask four your administrator password after you press enter

---

### Post by sekani on 2009-04-11
this is the message i now get...dean@dean-desktop:~$ sudo mount /dev/cdrom /media/cdrom -t iso9660  -o session=0mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

can anyone tell me what this means and what i need to do next? thanks for the 'sudo' explanation

---

### Post by sekani on 2009-04-13
when i enter 'dmesg | tail' this message also appears....dean@dean-desktop:~$ dmesg | tail
[  183.332014] eth0: no IPv6 routers present
[  514.625149] cdrom: This disc doesn't have any tracks I recognize!
[  514.664971] end_request: I/O error, dev sr0, sector 0
[  514.664984] Buffer I/O error on device sr0, logical block 0
[  514.667320] end_request: I/O error, dev sr0, sector 0
[  514.667329] Buffer I/O error on device sr0, logical block 0
[  629.218417] ISOFS: Invalid session number or type of track
[  629.218430] ISOFS: Invalid session number
[  629.219826] end_request: I/O error, dev sr0, sector 64
[  629.219926] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=
does this help anyone? not me i am confused...thanks

---

