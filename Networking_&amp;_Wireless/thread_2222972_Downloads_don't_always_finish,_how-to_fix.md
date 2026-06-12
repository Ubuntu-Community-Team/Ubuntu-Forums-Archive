---
title: "Downloads don't always finish, how-to fix?"
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by willzhigaylo on 2014-05-08
My downloads don't ever finish if the file is too big, I tried downloading on Chrome, Firefox, and even with wget. How can I fix this?

---

### Post by ibjsb4 on 2014-05-09
Please post the output of ..

```
sudo apt-get update
```

with code tags

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

---

### Post by willzhigaylo on 2014-05-09
```
Ign http://us.archive.ubuntu.com trusty InReleaseIgn http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Get:1 http://us.archive.ubuntu.com trusty Release.gpg [933 B]                  
Get:2 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Get:3 http://us.archive.ubuntu.com trusty Release [58.5 kB]                    
Get:4 http://us.archive.ubuntu.com trusty-updates Release [58.5 kB]            
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Ign http://security.ubuntu.com trusty-security InRelease                       
Get:5 http://us.archive.ubuntu.com trusty/main Sources [1,064 kB]              
Get:6 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Get:7 http://security.ubuntu.com trusty-security Release [58.5 kB]             
Get:8 http://us.archive.ubuntu.com trusty/restricted Sources [5,433 B]         
Get:9 http://us.archive.ubuntu.com trusty/universe Sources [6,399 kB]          
Get:10 http://security.ubuntu.com trusty-security/main Sources [12.0 kB]       
Get:11 http://security.ubuntu.com trusty-security/restricted Sources [14 B]    
Get:12 http://security.ubuntu.com trusty-security/universe Sources [2,873 B]   
Get:13 http://security.ubuntu.com trusty-security/multiverse Sources [699 B]   
Get:14 http://security.ubuntu.com trusty-security/main amd64 Packages [37.9 kB]
Ign http://dl.google.com stable InRelease                                      
Get:15 http://dl.google.com stable Release.gpg [198 B]                         
Get:16 http://dl.google.com stable Release [1,351 B]                           
Get:17 http://dl.google.com stable/main amd64 Packages [1,248 B]               
Get:18 http://dl.google.com stable/main i386 Packages [1,244 B]                
Get:19 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:20 http://extras.ubuntu.com trusty Release.gpg [72 B]                      
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:21 http://security.ubuntu.com trusty-security/universe amd64 Packages [13.6 kB]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty Release                                    
Get:22 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1,155 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:23 http://security.ubuntu.com trusty-security/main i386 Packages [37.3 kB] 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:24 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:25 http://security.ubuntu.com trusty-security/universe i386 Packages [13.6 kB]
Get:26 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,389 B]
Get:27 http://security.ubuntu.com trusty-security/main Translation-en [17.0 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Get:28 http://us.archive.ubuntu.com trusty/multiverse Sources [174 kB]         
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Get:29 http://us.archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]      
Get:30 http://security.ubuntu.com trusty-security/universe Translation-en [6,799 B]
Get:31 http://us.archive.ubuntu.com trusty/restricted amd64 Packages [13.0 kB] 
Get:32 http://us.archive.ubuntu.com trusty/universe amd64 Packages [5,859 kB]  
Ign http://security.ubuntu.com trusty-security/main Translation-en_US          
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US      
Get:33 http://us.archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]  
Get:34 http://us.archive.ubuntu.com trusty/main i386 Packages [1,348 kB]       
Get:35 http://us.archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]  
Get:36 http://us.archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]   
Get:37 http://us.archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]   
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Get:38 http://us.archive.ubuntu.com trusty/universe Translation-en [4,089 kB]  
Get:39 http://us.archive.ubuntu.com trusty-updates/main Sources [26.5 kB]      
Get:40 http://us.archive.ubuntu.com trusty-updates/restricted Sources [14 B]   
Get:41 http://us.archive.ubuntu.com trusty-updates/universe Sources [17.2 kB]  
Get:42 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [2,220 B]
Get:43 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [66.2 kB]
Get:44 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]
Get:45 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [43.1 kB]
Get:46 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [7,099 B]
Get:47 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [64.3 kB]
Get:48 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]
Get:49 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [43.1 kB]
Get:50 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [7,277 B]
Get:51 http://us.archive.ubuntu.com trusty-updates/main Translation-en [30.5 kB]
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Get:52 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [21.1 kB]
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en_US   
Fetched 27.1 MB in 48s (564 kB/s)                                              
Reading package lists... Done



```

---

### Post by bapoumba on 2014-05-09
What kind of downloads ?

---

### Post by willzhigaylo on 2014-05-09
Any large files (.zips in particular) over 50MB.

---

### Post by bapoumba on 2014-05-09
Could you please give more info ?
Any error with wget ?

---

### Post by Hadaka on 2014-05-09
hi, please post the output of..

```
uname -a
df -h
ulimit -a
```
thanks

---

### Post by willzhigaylo on 2014-05-09
> **bapoumba said:**
> Could you please give more info ?
Any error with wget ?
Yes, I still get errors with wget.

---

### Post by willzhigaylo on 2014-05-09
> **Hadaka said:**
> hi, please post the output of..

```
uname -a
df -h
ulimit -a
```
thanks
```
wzhigaylo@ASUSX401A1:~$ uname -aLinux ASUSX401A1 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
wzhigaylo@ASUSX401A1:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  289G  7.2G  267G   3% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  4.0K  1.9G   1% /dev
tmpfs                        384M  1.1M  383M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G  336K  1.9G   1% /run/shm
none                         100M   44K  100M   1% /run/user
/dev/sda2                    237M   46M  180M  21% /boot
/dev/sda1                    511M  3.4M  508M   1% /boot/efi
/dev/sdb1                    7.5G   40K  7.5G   1% /media/wzhigaylo/WZHIGAYLO
wzhigaylo@ASUSX401A1:~$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 30354
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 30354
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited



```

---

### Post by bapoumba on 2014-05-09
> **willzhigaylo said:**
> Yes, I still get errors with wget.

Well, crystal balls have limitations.. Would be useful you post them here, in addition to Hadaka's suggestions.

---

### Post by willzhigaylo on 2014-05-09
> **bapoumba said:**
> Well, crystal balls have limitations.. Would be useful you post them here, in addition to Hadaka's suggestions.

wget log: 
```
--2014-05-08 18:27:30--  http://goo.im/gapps/gapps-kk-20140105-signed.zipResolving goo.im (goo.im)... 108.166.173.92
Connecting to goo.im (goo.im)|108.166.173.92|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://108.166.171.38/goodata/gapps/gapps-kk-20140105-signed.zip?st=UbwFGR3MDhUuPvmmxCSnJg&e=1399588351 [following]
--2014-05-08 18:27:31--  http://108.166.171.38/goodata/gapps/gapps-kk-20140105-signed.zip?st=UbwFGR3MDhUuPvmmxCSnJg&e=1399588351
Connecting to 108.166.171.38:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 87179530 (83M) [application/zip]
Saving to: ‘gapps-kk-20140105-signed.zip.3’




 1% [                                       ] 1,163,700    133KB/s  eta 8m 5s  
 1% [                                       ] 1,192,020    133KB/s  eta 8m 5s  
 1% [                                       ] 1,226,004    130KB/s  eta 8m 5s  
 1% [                                       ] 1,250,076    125KB/s  eta 8m 5s  
 1% [                                       ] 1,283,756    116KB/s  eta 8m 31s 
 1% [                                       ] 1,316,628    118KB/s  eta 8m 31s 
 1% [                                       ] 1,337,868    116KB/s  eta 8m 31s 
 1% [                                       ] 1,364,772    117KB/s  eta 8m 31s 
 1% [                                       ] 1,397,036    111KB/s  eta 8m 52s 
 1% [                                       ] 1,432,436    108KB/s  eta 8m 52s 
 1% [                                       ] 1,456,812    109KB/s  eta 8m 52s 
 1% [                                       ] 1,469,252    104KB/s  eta 8m 52s 
 1% [                                       ] 1,486,548    105KB/s  eta 9m 19s 
 1% [                                       ] 1,500,708    103KB/s  eta 9m 19s 
 1% [                                       ] 1,523,060   98.6KB/s  eta 9m 19s 
 1% [                                       ] 1,543,188   94.7KB/s  eta 9m 19s 
 1% [                                       ] 1,558,764   89.8KB/s  eta 9m 48s 
 1% [                                       ] 1,571,508   87.0KB/s  eta 9m 48s 
 1% [                                       ] 1,584,252   83.7KB/s  eta 9m 48s 
 1% [                                       ] 1,601,244   81.4KB/s  eta 9m 48s 
 1% [                                       ] 1,620,764   77.8KB/s  eta 10m 18s
 1% [                                       ] 1,629,564   74.6KB/s  eta 10m 18s
 1% [                                       ] 1,645,140   71.9KB/s  eta 10m 18s
 1% [                                       ] 1,662,132   70.0KB/s  eta 10m 18s
 1% [                                       ] 1,679,124   68.7KB/s  eta 10m 18s
 1% [                                       ] 1,694,700   69.6KB/s  eta 10m 48s
 1% [                                       ] 1,714,524   66.6KB/s  eta 10m 48s
 1% [                                       ] 1,734,348   65.9KB/s  eta 10m 48s
 2% [                                       ] 1,756,700   65.2KB/s  eta 10m 48s
 2% [                                       ] 1,779,660   66.8KB/s  eta 11m 12s
 2% [                                       ] 1,796,652   67.3KB/s  eta 11m 12s
 2% [                                       ] 1,823,252   65.5KB/s  eta 11m 12s
 2% [                                       ] 1,834,884   65.0KB/s  eta 11m 12s
 2% [                                       ] 1,854,708   66.1KB/s  eta 11m 35s
 2% [                                       ] 1,878,780   68.3KB/s  eta 11m 35s
 2% [                                       ] 1,900,020   69.1KB/s  eta 11m 35s
 2% [                                       ] 1,921,260   70.6KB/s  eta 11m 35s
 2% [                                       ] 1,942,500   71.5KB/s  eta 11m 47s
 2% [                                       ] 1,958,076   73.6KB/s  eta 11m 47s
 2% [                                       ] 1,980,732   75.3KB/s  eta 11m 47s
 2% [                                       ] 2,010,164   75.0KB/s  eta 11m 47s
 2% [                                       ] 2,033,124   75.7KB/s  eta 12m 1s 
 2% [                                       ] 2,058,612   77.9KB/s  eta 12m 1s 
 2% [                                       ] 2,079,852   78.4KB/s  eta 12m 1s 
 2% [                                       ] 2,101,092   79.3KB/s  eta 12m 1s 
 2% [                                       ] 2,105,340   77.5KB/s  eta 12m 1s 
 2% [                                       ] 2,111,004   67.2KB/s  eta 12m 36s
 2% [                                       ] 2,120,916   65.7KB/s  eta 12m 36s
 2% [                                       ] 2,144,988   66.3KB/s  eta 12m 36s
 2% [                                       ] 2,167,644   69.0KB/s  eta 12m 36s
 2% [                                       ] 2,193,132   71.5KB/s  eta 12m 46s
 2% [                                       ] 2,215,788   72.1KB/s  eta 12m 46s
 2% [>                                      ] 2,239,860   71.8KB/s  eta 12m 46s
 2% [>                                      ] 2,256,852   71.1KB/s  eta 12m 46s
 2% [>                                      ] 2,273,844   70.2KB/s  eta 12m 46s
 2% [>                                      ] 2,288,004   69.4KB/s  eta 12m 59s
 2% [>                                      ] 2,299,332   67.4KB/s  eta 12m 59s
 2% [>                                      ] 2,312,076   66.2KB/s  eta 12m 59s
 2% [>                                      ] 2,331,900   66.6KB/s  eta 12m 59s
 2% [>                                      ] 2,352,836   63.7KB/s  eta 13m 14s
 2% [>                                      ] 2,370,132   64.0KB/s  eta 13m 14s
 2% [>                                      ] 2,381,156   60.9KB/s  eta 13m 14s
 2% [>                                      ] 2,398,148   54.9KB/s  eta 13m 42s
 2% [>                                      ] 2,404,116   53.0KB/s  eta 13m 42s
 2% [>                                      ] 2,415,444   53.4KB/s  eta 13m 42s
 2% [>                                      ] 2,426,772   58.7KB/s  eta 13m 42s
 2% [>                                      ] 2,439,516   59.7KB/s  eta 13m 42s
 2% [>                                      ] 2,446,596   54.5KB/s  eta 14m 20s
 2% [>                                      ] 2,460,756   51.9KB/s  eta 14m 20s
 2% [>                                      ] 2,476,332   50.3KB/s  eta 14m 20s
 2% [>                                      ] 2,493,324   49.8KB/s  eta 14m 20s
 2% [>                                      ] 2,510,316   48.7KB/s  eta 14m 31s
 2% [>                                      ] 2,525,892   47.6KB/s  eta 14m 31s
 2% [>                                      ] 2,545,716   48.7KB/s  eta 14m 31s
 2% [>                                      ] 2,566,956   48.3KB/s  eta 14m 31s
 2% [>                                      ] 2,589,612   49.8KB/s  eta 14m 38s
 2% [>                                      ] 2,610,852   48.7KB/s  eta 14m 38s
 3% [>                                      ] 2,632,092   48.7KB/s  eta 14m 38s
 3% [>                                      ] 2,654,748   51.7KB/s  eta 14m 38s
 3% [>                                      ] 2,677,404   57.8KB/s  eta 14m 43s
 3% [>                                      ] 2,699,756   62.4KB/s  eta 14m 43s
 3% [>                                      ] 2,728,380   66.3KB/s  eta 14m 43s
 3% [>                                      ] 2,748,204   67.5KB/s  eta 14m 43s
 3% [>                                      ] 2,773,692   77.3KB/s  eta 14m 43s
 3% [>                                      ] 2,783,604   78.1KB/s  eta 14m 45s
 3% [>                                      ] 2,813,340   81.6KB/s  eta 14m 45s
 3% [>                                      ] 2,831,748   81.0KB/s  eta 14m 45s
 3% [>                                      ] 2,855,820   83.1KB/s  eta 14m 45s
 3% [>                                      ] 2,874,228   83.2KB/s  eta 14m 45s
 3% [>                                      ] 2,903,964   86.9KB/s  eta 14m 40s
 3% [>                                      ] 2,932,284   89.5KB/s  eta 14m 40s
 3% [>                                      ] 2,957,772   91.8KB/s  eta 14m 40s
 3% [>                                      ] 2,984,676   95.5KB/s  eta 14m 40s
 3% [>                                      ] 3,015,828   97.0KB/s  eta 14m 40s
 3% [>                                      ] 3,044,148    101KB/s  eta 14m 30s
 3% [>                                      ] 3,072,468    101KB/s  eta 14m 30s
 3% [>                                      ] 3,105,036    107KB/s  eta 14m 30s
 3% [>                                      ] 3,126,276    105KB/s  eta 14m 30s
 3% [>                                      ] 3,158,844    107KB/s  eta 14m 30s
 3% [>                                      ] 3,192,828    111KB/s  eta 14m 18s
 3% [>                                      ] 3,216,900    114KB/s  eta 14m 18s
 3% [>                                      ] 3,239,556    114KB/s  eta 14m 18s
 3% [>                                      ] 3,263,628    115KB/s  eta 14m 18s
 3% [>                                      ] 3,284,564    115KB/s  eta 14m 18s
 3% [>                                      ] 3,323,100    119KB/s  eta 14m 12s
 3% [>                                      ] 3,352,836    117KB/s  eta 14m 12s
 3% [>                                      ] 3,369,524    106KB/s  eta 14m 12s
 3% [>                                      ] 3,385,404   96.9KB/s  eta 14m 27s
 3% [>                                      ] 3,386,820   77.2KB/s  eta 14m 52s
 3% [>                                      ] 3,386,820   65.0KB/s  eta 14m 52s
 3% [>                                      ] 3,386,820   56.2KB/s  eta 15m 39s
 3% [>                                      ] 3,386,820   49.5KB/s  eta 15m 39s
 3% [>                                      ] 3,386,820   44.2KB/s  eta 16m 26s
 3% [>                                      ] 3,388,236   39.8KB/s  eta 16m 26s
 3% [>                                      ] 3,389,652   36.2KB/s  eta 17m 10s
 3% [>                                      ] 3,389,652   33.2KB/s  eta 17m 10s
 3% [>                                      ] 3,391,068   30.7KB/s  eta 17m 44s
 3% [>                                      ] 3,392,484   28.3KB/s  eta 18m 10s
 3% [>                                      ] 3,392,484   26.3KB/s  eta 18m 10s
 3% [>                                      ] 3,392,484   24.6KB/s  eta 18m 57s
 3% [>                                      ] 3,392,484   23.1KB/s  eta 18m 57s
 3% [>                                      ] 3,392,484   21.8KB/s  eta 19m 44s
 3% [>                                      ] 3,392,484   --.-K/s  eta 19m 44s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 20m 30s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 20m 30s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 21m 17s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 21m 17s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 22m 4s  
 3% [>                                      ] 3,392,484   --.-K/s  eta 22m 4s  
 3% [>                                      ] 3,392,484   --.-K/s  eta 22m 51s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 22m 51s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 23m 38s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 23m 38s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 24m 25s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 24m 25s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 25m 12s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 25m 12s 
 3% [>                                      ] 3,392,484   --.-K/s  eta 25m 59s 
 3% [>                                      ] 3,398,148   5.53KB/s  eta 25m 59s
 3% [>                                      ] 3,398,148   2.83KB/s  eta 26m 38s
 3% [>                                      ] 3,398,148   1.91KB/s  eta 26m 38s
 3% [>                                      ] 3,398,148   1.44KB/s  eta 27m 25s
 3% [>                                      ] 3,398,148   1.15KB/s  eta 27m 25s
 3% [>                                      ] 3,398,148    984B/s  eta 28m 12s 
 3% [>                                      ] 3,398,148   --.-K/s  eta 28m 12s 
 3% [>                                      ] 3,398,148   --.-K/s  eta 28m 59s 
 3% [>                                      ] 3,398,148   --.-K/s  eta 28m 59s 
 3% [>                                      ] 3,398,148   --.-K/s  eta 29m 45s 
 3% [>                                      ] 3,398,148   --.-K/s  eta 29m 45s 
 3% [>                                      ] 3,398,148   --.-K/s  eta 30m 32s 
 3% [>                                      ] 3,398,148   --.-K/s  eta 30m 32s 
 3% [>                                      ] 3,398,148   --.-K/s  eta 31m 19s 
 3% [>                                      ] 3,398,148   --.-K/s  eta 31m 19s 
 3% [>                                      ] 3,398,148   --.-K/s  eta 32m 6s  
 3% [>                                      ] 3,398,148   --.-K/s  eta 32m 6s  
 3% [>                                      ] 3,398,148   --.-K/s  eta 32m 53s 
 3% [>                                      ] 3,398,148   --.-K/s  eta 32m 53s 
 3% [>                                      ] 3,400,980   2.77KB/s  eta 33m 24s
 3% [>                                      ] 3,400,980   1.42KB/s  eta 33m 24s
 3% [>                                      ] 3,400,980    976B/s  eta 34m 11s 
 3% [>                                      ] 3,400,980    735B/s  eta 34m 11s 
 3% [>                                      ] 3,400,980    589B/s  eta 34m 57s 
 3% [>                                      ] 3,400,980    492B/s  eta 34m 57s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 35m 44s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 35m 44s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 36m 31s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 36m 31s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 37m 18s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 37m 18s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 38m 5s  
 3% [>                                      ] 3,400,980   --.-K/s  eta 38m 5s  
 3% [>                                      ] 3,400,980   --.-K/s  eta 38m 52s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 38m 52s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 39m 39s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 39m 39s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 40m 25s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 40m 25s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 41m 12s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 41m 12s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 41m 59s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 41m 59s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 42m 46s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 42m 46s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 43m 33s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 43m 33s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 44m 20s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 44m 20s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 45m 7s  
 3% [>                                      ] 3,400,980   --.-K/s  eta 45m 7s  
 3% [>                                      ] 3,400,980   --.-K/s  eta 45m 53s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 45m 53s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 46m 40s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 46m 40s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 47m 27s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 47m 27s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 48m 14s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 48m 14s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 49m 1s  
 3% [>                                      ] 3,400,980   --.-K/s  eta 49m 1s  
 3% [>                                      ] 3,400,980   --.-K/s  eta 49m 48s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 49m 48s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 50m 35s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 50m 35s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 51m 21s 
 3% [>                                      ] 3,400,980   --.-K/s  eta 51m 21s 
 3% [>                                      ] 3,402,396   1.38KB/s  eta 51m 49s
 3% [>                                      ] 3,403,812   1.42KB/s  eta 51m 49s
 3% [>                                      ] 3,403,812    976B/s  eta 52m 35s 
 3% [>                                      ] 3,403,812    735B/s  eta 52m 35s 
 3% [>                                      ] 3,403,812    589B/s  eta 53m 22s 
 3% [>                                      ] 3,403,812    492B/s  eta 53m 22s 
 3% [>                                      ] 3,405,228    672B/s  eta 53m 57s 
 3% [>                                      ] 3,406,644    779B/s  eta 53m 57s 
 3% [>                                      ] 3,406,644    689B/s  eta 54m 43s 
 3% [>                                      ] 3,406,644    618B/s  eta 54m 43s 
 3% [>                                      ] 3,406,644    560B/s  eta 55m 30s 
 3% [>                                      ] 3,406,644    511B/s  eta 55m 30s 
 3% [>                                      ] 3,408,060    623B/s  eta 55m 59s 
 3% [>                                      ] 3,408,060    574B/s  eta 55m 59s 
 3% [>                                      ] 3,408,060    533B/s  eta 56m 46s 
 3% [>                                      ] 3,408,060    498B/s  eta 56m 46s 
 3% [>                                      ] 3,408,060    466B/s  eta 57m 32s 
 3% [>                                      ] 3,408,060    439B/s  eta 57m 32s 
 3% [>                                      ] 3,408,060   --.-K/s  eta 58m 19s 
 3% [>                                      ] 3,416,252   8.00KB/s  eta 58m 19s
 3% [>                                      ] 3,417,972   7.12KB/s  eta 58m 19s
 3% [>                                      ] 3,420,804   6.51KB/s  eta 58m 35s
 3% [>                                      ] 3,425,052   7.34KB/s  eta 58m 35s
 3% [>                                      ] 3,430,716   8.83KB/s  eta 58m 35s
 3% [>                                      ] 3,432,132   7.39KB/s  eta 58m 53s
 3% [>                                      ] 3,439,212   8.55KB/s  eta 58m 53s
 3% [>                                      ] 3,444,876   8.96KB/s  eta 58m 53s
 3% [>                                      ] 3,447,708   9.12KB/s  eta 59m 3s 
 3% [>                                      ] 3,450,540   8.89KB/s  eta 59m 3s 
 3% [>                                      ] 3,457,620   9.79KB/s  eta 59m 3s 
 3% [>                                      ] 3,466,116   10.8KB/s  eta 59m 8s 
 4% [>                                      ] 3,494,436   15.4KB/s  eta 59m 8s 
 4% [>                                      ] 3,529,836   20.8KB/s  eta 59m 8s 
 4% [>                                      ] 3,542,580   22.8KB/s   in 2m 27s 


2014-05-08 18:29:58 (23.5 KB/s) - Connection closed at byte 3542580. Retrying.


--2014-05-08 18:29:59--  (try: 2)  http://108.166.171.38/goodata/gapps/gapps-kk-20140105-signed.zip?st=UbwFGR3MDhUuPvmmxCSnJg&e=1399588351
Connecting to 108.166.171.38:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 87179530 (83M), 83636950 (80M) remaining [application/zip]
Saving to: ‘gapps-kk-20140105-signed.zip.3’


        [ skipping 3450K ]
  3450K ,,,,,,,,,. .......... .......... .......... ..........  4% 74.8K 22m29s
  3500K .......... .......... .......... .......... ..........  4% 64.3K 21m45s
  3550K .......... .......... .......... .......... ..........  4%  100K 18m50s
  3600K .......... .......... .......... .......... ..........  4% 51.8K 20m46s
  3650K .......... .......... .......... .......... ..........  4% 79.9K 19m58s
  3700K .......... .......... .......... .......... ..........  4%  127K 18m21s
  3750K .......... .......... .......... .......... ..........  4%  113K 17m24s
  3800K .......... .......... .......... .......... ..........  4% 98.2K 16m56s
  3850K .......... .......... .......... .......... ..........  4%  134K 16m9s
  3900K .......... .......... .......... .......... ..........  4%  131K 15m33s
  3950K .......... .......... .......... .......... ..........  4%  104K 15m18s
  4000K .......... .......... .......... .......... ..........  4%  130K 14m52s
  4050K .......... .......... .......... .......... ..........  4%  131K 14m30s
  4100K .......... .......... .......... .......... ..........  4%  149K 14m6s
  4150K .......... .......... .......... .......... ..........  4%  143K 13m47s
  4200K .......... .......... .......... .......... ..........  4% 93.5K 13m49s
  4250K .......... .......... .......... .......... ..........  5% 22.7K 16m30s
  4300K .......... .......... .......... .......... ..........  5% 36.9K 17m37s
  4350K .......... .......... .......... .......... ..........  5% 45.4K 18m15s
  4400K .......... .......... .......... .......... ..........  5% 61.7K 18m25s
  4450K .......... .......... .......... .......... ..........  5% 57.7K 18m38s
  4500K .......... .......... .......... .......... ..........  5% 84.6K 18m30s
  4550K .......... .......... .......... .......... ..........  5% 50.1K 18m51s
  4600K .......... .......... .......... .......... ..........  5% 50.6K 19m10s
  4650K .......... .......... .......... .......... ..........  5% 63.1K 19m14s
  4700K .......... .......... .......... .......... ..........  5% 87.7K 19m4s
  4750K .......... .......... .......... .......... ..........  5%  105K 18m49s
  4800K .......... .......... .......... .......... ..........  5%  102K 18m36s
  4850K .......... .......... .......... .......... ..........  5% 79.0K 18m32s
  4900K .......... .......... .......... .......... ..........  5% 49.7K 18m48s
  4950K .......... .......... .......... .......... ..........  5% 52.9K 19m0s
  5000K .......... .......... .......... .......... ..........  5% 75.0K 18m57s
  5050K .......... .......... .......... .......... ..........  5% 80.5K 18m52s
  5100K .......... .......... .......... .......... ..........  6% 92.0K 18m44s
  5150K .......... .......... .......... .......... ..........  6% 88.7K 18m37s
  5200K .......... .......... .......... .......... ..........  6% 69.7K 18m37s
  5250K .......... .......... .......... .......... ..........  6% 76.9K 18m34s
  5300K .......... .......... .......... .......... ..........  6% 98.6K 18m25s
  5350K .......... .......... .......... .......... ..........  6% 68.0K 18m26s
  5400K .......... .......... .......... .......... ..........  6% 72.4K 18m26s
  5450K .......... .......... .......... .......... ..........  6% 86.5K 18m20s
  5500K .......... .......... .......... .......... ..........  6% 73.4K 18m19s
  5550K .......... .......... .......... .......... ..........  6% 57.6K 18m25s
  5600K .......... .......... .......... .......... ..........  6% 10.9K 20m46s
  5650K .......... .......... .......... .......... ..........  6% 37.3K 21m5s
  5700K .......... .......... ........                          6%  375 =1m53s


2014-05-08 18:46:54 (20.0 KB/s) - Read error at byte 5865945/87179530 (Connection timed out). Retrying.


--2014-05-08 18:46:56--  (try: 3)  http://108.166.171.38/goodata/gapps/gapps-kk-20140105-signed.zip?st=UbwFGR3MDhUuPvmmxCSnJg&e=1399588351
Connecting to 108.166.171.38:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2014-05-08 18:47:17 ERROR 403: Forbidden.
```

After trying more than 10 times I was able to finally able to successfully download this file. but the fact that it took me so many times is annoying. Also, if you look at my pprevious post you will see that I answered Hadaka's question.

---

### Post by bapoumba on 2014-05-09
> **willzhigaylo said:**
> wget log: 
```
..
HTTP request sent, awaiting response... 302 Found
..
Connecting to 108.166.171.38:80... connected.
HTTP request sent, awaiting response... 200 OK
..
2014-05-08 18:29:58 (23.5 KB/s) - Connection closed at byte 3542580. Retrying.
..
..
Connecting to 108.166.171.38:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2014-05-08 18:47:17 ERROR 403: Forbidden.
```

After trying more than 10 times I was able to finally able to successfully download this file. but the fact that it took me so many times is annoying. Also, if you look at my pprevious post you will see that I answered Hadaka's question.

Downloaded. No obvious issues. Must be something on your end.
What kind of Android app is that ?

---

### Post by willzhigaylo on 2014-05-09
> **bapoumba said:**
> Downloaded. No obvious issues. Must be something on your end.
What kind of Android app is that ?

That was the gapps/Google Apps in order to be used with Genymotion (though it didn't work correctly). I guess the problem may be my internet.

---

### Post by bapoumba on 2014-05-09
> **willzhigaylo said:**
> That was the gapps/Google Apps in order to be used with Genymotion (though it didn't work correctly). I guess the problem may be my internet.

Thanks, did not look that deep into it. May be someone else can help you troubleshoot that part. dl was not quick here, so I'd say there is some of it on their end, but no error or anything like that.

---

### Post by willzhigaylo on 2014-05-09
There dosen't really seem to be a solution, but I am marking this as solved ;(

---

### Post by bapoumba on 2014-05-09
> **willzhigaylo said:**
> There dosen't really seem to be a solution, but I am marking this as solved ;(
Okay :)
Please do not hesitate if at some point you feel there is more into it.

---

