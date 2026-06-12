---
title: "cd mounting problem"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by minsf on 2008-12-17
hi there,

just installed intrepid and i have a problem mounting my cd drive.

when i try
```

sudo mount -t iso9660 /dev/cdrom /media/cdrom0 

```
i get
```

mount: No medium found

```

when i try 
```

sudo mount -t iso9660 /dev/scd0 /media/cdrom0

```
i get 
```

mount: special device /dev/scd does not exist

```

i know the cd drive works (even though it got a little hit a couple of days ago), because i can boot with the live cd from it.

the cd itself is not empty (i can access it on other computers)

i tried to change the booting order in the bios. i think this helped last time i installed ubuntu, but not this time...

here's what lshw gives:
```

           *-cdrom
                description: DVD reader
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd
                configuration: status=open

```
(let me know if you need other pieces of info from the long lshw output)

the relevant line from /etc/fstab is probably
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
my /etc/mtab file does not seem to have anything about the cd drive.
(i can post its output if you want)

any advice?
thanks for your help!

---

### Post by Michael.Godawski on 2008-12-17
Just to compare:here is my cd-rom fstab entry

```
cdrom
                description: DVD writer
                product: DVD+-RW TS-L632D
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DE04
                capabilities: removable audio cd-r cd-rw dvd dvd-r
              **  configuration: ansiversion=5 status=nodisc**
```
This line is different...maybe it has something to do with the issue... I have to search further.

---

### Post by lovelyvik293 on 2008-12-17
I think the last line in Michael.Godawski's output means there is no disc in the drive and according to minsf's output the cd rom in not closed(It's not closed properly.)

---

### Post by minsf on 2008-12-17
lovelyvik, i agree, but my cd tray is in fact closed when i get this lshw output...
michael, i think you posted your lshw output, right? my fstab is completely different.
to add to the mystery, my cd does mount automatically once in a while (twice in the last 11 boots today)... when it does mount, i get the following output from lshw:
```
        *-cdrom
               description: DVD reader
               product: CDRW/DVD SN-324B
               vendor: SAMSUNG
               physical id: 0.1.0
               bus info: scsi@0:0.1.0
               logical name: /dev/cdrom
               logical name: /dev/cdrw
               logical name: /dev/dvd
               logical name: /dev/scd0
               logical name: /dev/sr0
               logical name: /media/cdrom0
               version: U101
               capabilities: removable audio cd-r cd-rw dvd
               configuration: ansiversion=5 mount.fstype=iso9660
mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
             *-medium
                  physical id: 0
                  logical name: /dev/cdrom
                  logical name: /media/cdrom0
                  configuration: mount.fstype=iso9660
mount.options=ro,nosuid,nodev,utf8 state=mounted

```
seems like ubuntu was able to detect the hardware better (includes vendor name, etc...). 

is there a way to ask ubuntu to refresh the hardware detection without reboot? 
any idea why the cd mounts only 2 in 11 boots?

---

