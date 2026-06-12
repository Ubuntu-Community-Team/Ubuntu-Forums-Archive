---
title: "media/cdrom nothing there?"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by revlimit7000 on 2010-03-27
I am really new to Linux, and really and bad at posting on forums so's.... help lol. I am trying to see files cd/dvd drive using dolphin, I cant though. I can see it using (lshw -c disk). 
> [SIZE="1"]********@********-desktop:~$ sudo lshw -c disk
[sudo] password for duplicity:                  
  *-disk                                        
       description: ATA Disk                    
       product: WDC WD3200AAKS-7                
       vendor: Western Digital                  
       physical id: 0                           
       bus info: scsi@2:0.1.0                   
       logical name: /dev/sda                   
       version: 01.0                            
       serial: WD-WMAT12725004                  
       size: 298GiB (320GB)                     
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=f2e89e78
  *-cdrom                                             
       description: DVD-RAM writer                    
       product: iHAS422   8                           
       vendor: ATAPI                                  
       physical id: 1                                 
       bus info: scsi@3:0.1.0                         
       logical name: /dev/cdrom                       
       logical name: /dev/cdrw                        
       logical name: /dev/dvd                         
       logical name: /dev/dvdrw                       
       logical name: /dev/scd0                        
       logical name: /dev/sr0                         
       version: 4L16                                  
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc                
************@**********-desktop:~$ sudo hdparam -i /dev/dvd
sudo: hdparam: command not found                       
********@*******-desktop:~$ sudo hdparm -i /dev/dvd[/SIZE][/SIZE]
 I really don't know what to do I cant see it in dolphin I can see the folder *cdrom* but its blank inside and I can still play movies using dragon player.

---

### Post by revlimit7000 on 2010-03-27
Bump

---

### Post by CharlesA on 2010-03-27
You should only bump threads once every 24-hours.

You said that you can play movies, but is the media mounted?

Post the outpost of: ```
mount -l
```

---

### Post by revlimit7000 on 2010-03-27
Sorry about the bump I was just in a rush.
this is the print out. 
> duplicity@duplicity-desktop:~$ mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)                   
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)       
none on /sys/kernel/security type securityfs (rw) 
udev on /dev type tmpfs (rw,mode=0755)            
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)                  
none on /var/run type tmpfs (rw,nosuid,mode=0755)              
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)          
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)          
none on /var/lib/ureadahead/debugfs type debugfs (rw)          
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

### Post by CharlesA on 2010-03-27
Looks like the cdrom isn't mounted, is there a disc in the drive?

---

### Post by revlimit7000 on 2010-03-27
I that print out there nothing but in this one there is one. 


> duplicity@duplicity-desktop:~$ mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=duplicity) [One-20091-KDE4]

I can pull the disk up in dolphin and theres nothing inside of it....

---

### Post by CharlesA on 2010-03-27
Try it in a different machine. It looks like it is mounted correctly, there is no reason it should be blank unless it had a bad burn.

---

### Post by revlimit7000 on 2010-03-27
Ok... looked on other PC and it worked. I used it on this computer nothing and then used konsole and browsed to the disk drive it wants to show up now, all I did was use cd to go 2 that dir? Anyhow I think this one is solved it might just be a user error on my part. I think this problem is solved it was just a ID-10t  error. sorry about wasting you time but thanks for the help.

---

