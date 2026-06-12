---
title: "hard drive issues Software raid"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by jasonkk on 2009-08-31
This is a screen shot I have 4 drives 500gb each with  32MB cache each 7200 rpm. 

sda - sdc -sdd are in a raid 0 array (software  raid  ) each have a 2.8 gb partition as one dirve uses it for  boot and another for swap and then a 465 gb partition that is in the array

all disk are sata2 disk 

and sdb disk is for back up of config files for the server .

Why do i get the same speed for disk sdb as i do for the 3 disk array md0 have i done something wrong in my settings the reason the array drives have 2 partitions is i could not boot from (md0) so i made a 2.8 gb partition for boot 

Im using Ubuntu server 8.10 updateed and upgraded to current date.

root@server:/home/jason# hdparm -I /dev/sda | grep SATA
           *    SATA-I signaling speed (1.5Gb/s)
root@server:/home/jason# hdparm -I /dev/sdb | grep SATA
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-II signaling speed (3.0Gb/s)
root@server:/home/jason# hdparm -I /dev/sdc | grep SATA
           *    SATA-I signaling speed (1.5Gb/s)
root@server:/home/jason# hdparm -I /dev/sdd | grep SATA
           *    SATA-I signaling speed (1.5Gb/s)
root@server:/home/jason# hdparm -I /dev/ | grep SATA
/dev/: Is a directory
root@server:/home/jason# hdparm -I /dev/sd* | grep SATA
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-II signaling speed (3.0Gb/s)
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-II signaling speed (3.0Gb/s)
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-I signaling speed (1.5Gb/s)
root@server:/home/jason# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   4698 MB in  2.00 seconds = 2350.03 MB/sec
 Timing buffered disk reads:  318 MB in  3.02 seconds = 105.45 MB/sec
root@server:/home/jason# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   4764 MB in  2.00 seconds = 2382.18 MB/sec
 Timing buffered disk reads:  382 MB in  3.00 seconds = 127.29 MB/sec
root@server:/home/jason# hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   4684 MB in  2.00 seconds = 2343.10 MB/sec
 Timing buffered disk reads:  304 MB in  3.01 seconds = 100.90 MB/sec   
root@server:/home/jason# hdparm -tT /dev/sdd

/dev/sdd:
 Timing cached reads:   4750 MB in  2.00 seconds = 2375.26 MB/sec
 Timing buffered disk reads:  290 MB in  3.02 seconds =  96.11 MB/sec
root@server:/home/jason# hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   4798 MB in  2.00 seconds = 2399.50 MB/sec
 Timing buffered disk reads:  450 MB in  3.00 seconds = 149.86 MB/sec

---

### Post by overdrank on 2009-08-31
Hi and welcome, moved to Absolute Beginner Talk

---

