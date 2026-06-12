---
title: "ddrescue not rescuing (suspect incorrect syntax)"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by bigsuccess on 2009-11-29
Hi,

I'm copying from the failed disk using ddrescue to an image on a raid array with plenty of room. Sadly, it's taking ages but at the end I'm getting a 0k file.

I've searched around and no one seems to be getting the rescued = 0 output I am.

First I tried with 3 re-attempts..

```
tom@heavy:~$ sudo ddrescue -r 3 /dev/sdb /media/array1/backup.img /media/array1/backup.log


Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:         0 B,  errsize:    200 GB,  current rate:        0 B/s
   ipos:   183484 MB,   errors:       1,    average rate:        0 B/s
   opos:   183484 MB,     time from last successful read:     8.7 h
^Ctrying bad sectors... Retry 1
Interrupted by user

```
After the first pass and nothing rescued I cancelled it and re-tried with the same logfile without the retries:


```
tom@heavy:~$ sudo ddrescue /dev/sdb /media/array1/backup.img /media/array1/backup.log

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:    200 GB,  errors:       1
Current status
rescued:         0 B,  errsize:    200 GB,  current rate:        0 B/s
   ipos:         0 B,   errors:       1,    average rate:        0 B/s
   opos:         0 B,     time from last successful read:       0 s
Finished

```
This finished right away (as it had already gone through once) and still didn't write me any rescued data..


So now I'm trying the specific partition with verbose on to see if it comes up with anything..

```
tom@heavy:~$ sudo ddrescue -v /dev/sdb3 /media/array1/backup-sdb3.img /media/array1/backup-sdb3.log

About to copy 178258 MBytes from /dev/sdb3 to /media/array1/backup-sdb3.img
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 hard blocks
Hard block size: 512  bytes
Max_retries: 0    
Direct: no    Sparse: no    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:         0 B,  errsize:    178 GB,  current rate:        0 B/s
   ipos:   137371 MB,   errors:       1,    average rate:        0 B/s
   opos:   137371 MB,     time from last successful read:       1 m
Splitting failed blocks... 

```


Does anyone know what might be wrong? Do I have to mount the drive??

---

### Post by bigsuccess on 2009-11-30
The last attempt still only produces 0k image files..

I tried no split..
```
tom@heavy:~$ sudo ddrescue -v --no-split /dev/sdb3 /media/array1/backup-sdb3.img /media/array1/backup-sdb3.log

About to copy 178258 MBytes from /dev/sdb3 to /media/array1/backup-sdb3.img
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 hard blocks
Hard block size: 512  bytes
Max_retries: 0    
Direct: no    Sparse: no    Split: no    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:    178 GB,  errors:       1
Current status
rescued:         0 B,  errsize:    178 GB,  current rate:        0 B/s
   ipos:         0 B,   errors:       1,    average rate:        0 B/s
   opos:         0 B,     time from last successful read:       0 s
Finished
```

Still error = 1 and rescued - 0B


I saw people were rescuing directories so I thought ok I guess they must mount it. So I tried mounting it in read only mode:
```

root@heavy:~# mount -t ext3 -oro /dev/sdb2  ~/bakmnt
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Ok, so I can't mount it and I don't want to try to rebuild the fs on a dodgy disk..

Then I tried direct access. Thought it might be the difference.. 
```

tom@heavy:~$ sudo ddrescue -v -d /dev/sdb3 /media/array1/backup-sdb3.img /media/array1/backup-sdb3.log


About to copy 178258 MBytes from /dev/sdb3 to /media/array1/backup-sdb3.img
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 hard blocks
Hard block size: 512  bytes
Max_retries: 0    
Direct: yes    Sparse: no    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:    178 GB,  errors:       1
Current status
rescued:         0 B,  errsize:    178 GB,  current rate:        0 B/s
   ipos:    11615 MB,   errors:       1,    average rate:        0 B/s
   opos:    11615 MB,     time from last successful read:     8.7 m
Splitting failed blocks...

```

Still not finding anything... and I don't want to keep running this disk if it's failing and not producing anything, if I'm doing something wrong it's probably making it worse spinning it and not getting the data...!

When I'm using ddrescue on this drive I'm seeing the following (with different blocks) from dmesg
```

[92118.029718] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[92118.029724] end_request: I/O error, dev sdb, sector 155683668
[92118.029749] sd 1:0:0:0: [sdb] Unhandled error code
[92118.029752] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[92118.029756] end_request: I/O error, dev sdb, sector 155683925
[92118.032329] sd 1:0:0:0: [sdb] Unhandled error code
[92118.032332] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[92118.032336] end_request: I/O error, dev sdb, sector 155683926

```

Not sure where to go from here..

---

### Post by bumanie on 2009-11-30
As far as I know the syntax is as simple as > sudo ddrescue /dev/sda /dev/sdb with dev/sda being the damaged hard drive and /dev/sdb being the known undamaged hard drive. I have used standard dd, but have never tried ddrescue - however it looks as though you don't need [COLOR="Red"]/backup-sdb3.img /media/array1/backup-sdb3.log[/COLOR] as part of the syntax. From what the [man page]("http://ss64.com/bash/ddrescue.html") says. Try [COLOR="RoyalBlue"]sudo ddrescue -v /dev/sdb3 /media/array1[/COLOR][COLOR="Black"] would be my guess.[/COLOR] I tend to think you should be copying to an empty external drive if possible, rather than using a raid array to copy to.

---

### Post by bigsuccess on 2009-11-30
Thanks for your response.

In your example as I understand it I'd be overwriting the contents of my array.. and without the logfile you lose the ability to resume as it has to start over.

This is why I'm pointing it to an image and using the logfile but I will try to put another hard disk in there so I'm copying the image straight to a partition as it may be the common factor that is making it not work.

Will have to grab another hdd, I will report back when I do :)

---

### Post by bigsuccess on 2009-12-26
If anyone happens to find this or follows it I ended up mounting the drive in read only mode. I thought it didn't need to be mounted but this worked.

I used still used the log file and image file.

In regards to mounting I originally tried an incorrect syntax:
mount -t ext3 -oro /dev/sdb2  ~/bakmnt

The correct syntax was:
mount -t ext3 -o ro /dev/sdb2  ~/bakmnt

---

