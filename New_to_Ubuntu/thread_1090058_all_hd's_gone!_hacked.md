---
title: "all hd's gone?!? hacked?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by rogasgr on 2009-03-07
:( i was a happy noob ubuntu since now. i get back home and start my system   and it didnt start gnome, it would only get me till the tty. i said "ok, there is smthing wrong..". startx loaded ok and i got in gnome. my hd's can't be mounted although i see them as shortcuts on the locations menu, there are 8 usb (usb0 to usb7) devices set on /media and i cant mount the hd's.  all these since last time that i was fighting all day with xampp+joomla+web server  + router config. i forwarded a port on my router 8080 i get back to the router and see that some changes are made! it is set to cnf from remote on port 8081 that's smthing i didnt do b4! ****! i try to start lampp and my DB is down. pretty bad **** it seems.
this is the weblizer report for the 1st day of lampp :(
```
Top 3 of 3 Total Sites By KBytes
# 	Hits 	Files 	KBytes 	Visits 	Hostname
1 	1829 	85.19% 	1368 	82.96% 	7340 	86.00% 	4 	40.00% 	127.0.0.1      <-loopback? why?
2 	300 	13.97% 	276 	16.74% 	1127 	13.20% 	4 	40.00% 	192.168.1.2    <----ME
3 	18 	0.84% 	5 	0.30% 	68 	0.80% 	2 	20.00% 	195.74.247.144  <--   hmmm visitor?   
```

---

### Post by DGortze380 on 2009-03-07
Some insite-

Loopback is used by a number or programs. It shouldn't be a problem. Basic explanation would be that it's a way for your computer to access itself through a network interface.

I'd be willing to bet the third IP is your own.
Can you please go to whatsmyip.com and see what it tells you your external IP is. Don't post it, just compare to the thrid IP you posted above. Here's some information about the IP. It appears to have been assigned to an aDSL provider in Greece.

```

OrgName:    RIPE Network Coordination Centre 
OrgID:      RIPE
Address:    P.O. Box 10096
City:       Amsterdam
StateProv:  
PostalCode: 1001EB
Country:    NL

ReferralServer: whois://whois.ripe.net:43

NetRange:   195.0.0.0 - 195.255.255.255 
CIDR:       195.0.0.0/8 
NetName:    RIPE-CBLK3
NetHandle:  NET-195-0-0-0-1
Parent:     
NetType:    Allocated to RIPE NCC
NameServer: NS-PRI.RIPE.NET
NameServer: NS3.NIC.FR
NameServer: SUNIC.SUNET.SE
NameServer: NS-EXT.ISC.ORG
NameServer: SEC1.APNIC.NET
NameServer: SEC3.APNIC.NET
NameServer: TINNIE.ARIN.NET
Comment:    These addresses have been further assigned to users in
Comment:    the RIPE NCC region. Contact information can be found in
Comment:    the RIPE database at http://www.ripe.net/whois
RegDate:    1996-03-25
Updated:    2005-08-03

RTechHandle: RIPE-NCC-ARIN
RTechName:   RIPE NCC Hostmaster 
RTechPhone:  +31 20 535 4444
RTechEmail:  search-ripe-ncc-not-arin@ripe.net 

# ARIN WHOIS database, last updated 2009-03-06 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.


```

As for the hard drives, I don't quite follow, can you please post the output of 

```

fdisk -l

```

---

### Post by rogasgr on 2009-03-07
```
rogas@rogas-desktop:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc
Cannot open /dev/sdd

``` claps claps?

 my ip is 77.49.53.xxx so the one you saw is not mine.

---

### Post by Hospadar on 2009-03-07
```
sudo fdisk -l
```
fdisk needs root access to get raw data on your drives

---

### Post by rogasgr on 2009-03-07
> **Hospadar said:**
> ```
sudo fdisk -l
```
fdisk needs root access to get raw data on your drives

hoho im noob...

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x622d1191

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      484521   244198552+  42  SFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23ed23ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xadf66efc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161   42  SFS

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b8bff7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9729    78148161    7  HPFS/NTFS

```

---

### Post by taurus on 2009-03-07
Do you have those drives mounted (from /etc/fstab) when you boot Ubuntu?

```
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by rogasgr on 2009-03-07
> **taurus said:**
> Do you have those drives mounted (from /etc/fstab) when you boot Ubuntu?

```
sudo blkid
cat /etc/fstab
df -h
```


they werent mounted b4 either at startup but now i cant mount them at all


```
rogas@rogas-desktop:~$ sudo blkid
/dev/sda1: UUID="3A2C75832C753AC9" LABEL="250 Diakosopenintaris" TYPE="ntfs" 
/dev/sdb1: UUID="a54cbd74-27d4-41f2-a247-9965ad7de8c6" TYPE="ext3" 
/dev/sdc1: UUID="E0F00419F003F516" LABEL="80" TYPE="ntfs" 
/dev/sdd1: UUID="FCF8084DF808091A" LABEL="80 Downloads" TYPE="ntfs" 
/dev/sdb5: TYPE="swap" UUID="f5132f1f-9b1e-44f4-80af-a3fbb4381659" 
rogas@rogas-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a54cbd74-27d4-41f2-a247-9965ad7de8c6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f5132f1f-9b1e-44f4-80af-a3fbb4381659 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
rogas@rogas-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              36G  8,0G   26G  24% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  304K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2,8M  498M   1% /dev
tmpfs                 501M   12K  501M   1% /dev/shm
lrm                   501M  2,4M  499M   1% /lib/modules/2.6.27-13-generic/volatile


```

---

### Post by taurus on 2009-03-07
See if you at least can mount one of them from a prompt.

```
sudo mkdir /media/sdd1
sudo mount -t ntfs-3g /dev/sdd1 /media/sdd1
df -h
```

---

### Post by rogasgr on 2009-03-08
> **taurus said:**
> See if you at least can mount one of them from a prompt.

```
sudo mkdir /media/sdd1
sudo mount -t ntfs-3g /dev/sdd1 /media/sdd1
df -h
```

done all mounting successfuly! 
df -h now shows...
```
@rogas-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              36G  8,0G   26G  24% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  304K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2,8M  498M   1% /dev
tmpfs                 501M   12K  501M   1% /dev/shm
lrm                   501M  2,4M  499M   1% /lib/modules/2.6.27-13-generic/volatile
/dev/sda1             233G  213G   21G  92% /media/250GB
/dev/sdc1              75G   33G   42G  45% /media/80GB
/dev/sdd1              75G   21G   54G  28% /media/80Downloads

```

all my drives are ok. what about the usb0-7  folders that exist in my /media ? i never made those!

---

### Post by skymera on 2009-03-08
When you plug in USB devices they mount automatically in a directory in /media/

---

### Post by rogasgr on 2009-03-08
> **skymera said:**
> When you plug in USB devices they mount automatically in a directory in /media/

this wasnt setup by me
i never had a usb folder.

and now i see that the drop   down menu for restart-standby-shutdown is gone!   how can i restore it? :(  damn assh0le he ruined my sweet ubuntu

---

