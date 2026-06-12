---
title: "High CPU Load with no apparent reason"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by shoaibi on 2011-06-11
I am using Ubuntu 11.04 64b on with unity 2d for better performance. After a certain period of time my cpu load average goes above 1, sometimes even above than 10, i am not running any resource hungry application, usually processes include:
Chrome/Chromium[8-10 tabs, no flash, basically gmailx3, linkedin, etc] Gnote, Terminal, Skype, Empathy
and thats all.




Here are my system specs:
```


[Sat Jun 11|20:04:08][shoaibi@abacus:~/tmp]$ free -m
             total       used       free     shared    buffers     cached
Mem:          7983       2256       5727          0        252       1010
-/+ buffers/cache:        993       6990
Swap:        10239          0      10239
[Sat Jun 11|20:06:18][shoaibi@abacus:~/tmp]$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 8
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 3990.78
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 8
core id		: 0
cpu cores	: 4
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 11632.67
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 8
core id		: 1
cpu cores	: 4
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 3990.85
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 8
core id		: 1
cpu cores	: 4
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 3991.01
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 4
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 8
core id		: 2
cpu cores	: 4
apicid		: 4
initial apicid	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 3991.00
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 5
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 8
core id		: 2
cpu cores	: 4
apicid		: 5
initial apicid	: 5
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 3991.00
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 6
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 8
core id		: 3
cpu cores	: 4
apicid		: 6
initial apicid	: 6
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 3991.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 7
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 8
core id		: 3
cpu cores	: 4
apicid		: 7
initial apicid	: 7
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 3991.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


```




and yes, i have tried disabling swap altogether to  observe changes but no use.
I am using a ramdisk for chrome/ium cache, tried disabling that as well, but again, no use.

Also its not chrome/ium causing the issue as i have tested using firefox and same happens.

Following is my fstab (contains some modifications for performance, this cpu load issue started occurring before the optimizations applied here which actually tempted me to do these.)
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# rootfs
/dev/sda3       /               ext4    rw,data=writeback,barrier=0,nobh,noatime,nodiratime,commit=100,nouser_xattr,errors=remount-ro 0       1

# /home was on /dev/sda5 during installation
/dev/sda5 /home           ext4    rw,data=writeback,barrier=0,nobh,noatime,nodiratime,commit=100,nouser_xattr,errors=remount-ro        0       2




# NTFS drives
/dev/sda1	/drives/system	auto	defaults	0	0
/dev/sda2	/drives/windows	auto	defaults	0	0
/dev/sda6	/drives/share	auto	defaults	0	0

# RAM disk
tmpfs /media/ramdisk tmpfs defaults,noatime,mode=1777 0 0

# Extra Swap
/home/swapfile	swap	swap	defaults	0	0


```



Following contains outputs of:
top
iostat -x
and iotop at random intervals during high load.

```


Top:

top - 19:58:24 up  7:10,  3 users,  load average: 1.47, 1.27, 1.04
Tasks: 250 total,   1 running, 247 sleeping,   0 stopped,   2 zombie
Cpu(s):  3.7%us,  1.2%sy,  0.8%ni, 94.2%id,  0.1%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   8175328k total,  3599328k used,  4576000k free,   256740k buffers
Swap: 10485756k total,        0k used, 10485756k free,   963308k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                    
10509 root      20   0 19480 1412  952 R   33  0.0   0:00.64 top                                                        
 2143 shoaibi   20   0  465m  41m  18m S   21  0.5   1:28.92 /usr/bin/termin                                            
 2622 shoaibi   20   0  648m  55m  23m S   17  0.7  42:51.31 chrome                                                     
 1178 root      20   0  401m 110m  82m S   15  1.4  22:15.21 Xorg                                                       
 2427 shoaibi   20   0  996m 183m  21m S   11  2.3   9:41.18 chrome                                                     
 2232 shoaibi   20   0  756m 133m  38m S    8  1.7  23:13.86 chrome                                                     
 2435 shoaibi   20   0  978m 162m  19m S    8  2.0   8:21.92 chrome                                                     
 2610 shoaibi   20   0  895m  76m  18m S    8  1.0   4:27.85 chrome                                                     
 2421 shoaibi   25   5  910m  91m  17m S    5  1.1   3:56.46 chrome                                                     
 2600 shoaibi   25   5  943m  96m  17m S    5  1.2   3:44.16 chrome                                                     
 2462 shoaibi   25   5  902m  72m  17m S    4  0.9   2:36.76 chrome                                                     
 8241 shoaibi   20   0  288m  92m  21m S    3  1.2   3:55.71 skype                                                      
 9047 shoaibi   20   0  395m  37m  17m S    3  0.5   1:24.76 xchat                                                      
10432 root      20   0     0    0    0 S    3  0.0   0:00.63 kworker/0:3                                                
  218 root      20   0     0    0    0 S    1  0.0   0:14.71 usb-storage                                                
 1645 shoaibi   20   0  316m  12m 8636 S    1  0.2   1:37.58 diodon                                                     
 1696 shoaibi   20   0  612m  56m  19m S    1  0.7   0:22.21 dropbox                                                    
 7899 root      20   0     0    0    0 S    1  0.0   0:06.30 kworker/3:1                                                
10352 root      20   0     0    0    0 S    1  0.0   0:07.00 kworker/1:3                                                
10431 root      20   0     0    0    0 S    1  0.0   0:00.37 kworker/1:0                                                
    1 root      20   0 24128 2280 1368 S    0  0.0   0:02.88 init                                                       
    2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd                                                   
    3 root      20   0     0    0    0 S    0  0.0   0:01.55 ksoftirqd/0                                                
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                     
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                    
   31 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                      
   33 root      20   0     0    0    0 S    0  0.0   0:00.12 sync_supers                                                
   34 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                
   35 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                
   36 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                    
   37 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpid                                                     
   38 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                               
   39 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                              
   40 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                    
   41 root      20   0     0    0    0 S    0  0.0   0:00.01 khubd                                                      
   42 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                         
   44 root      20   0     0    0    0 S    0  0.0   0:00.02 khungtaskd                                                 
   45 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                    
   46 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                       
   47 root      20   0     0    0    0 S    0  0.0   0:00.00 fsnotify_mark                                              
   48 root       0 -20     0    0    0 S    0  0.0   0:00.00 aio                                                        
   49 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                            
   50 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                     
   54 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                   
   56 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpathd                                                    
   57 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd                                            
   58 root       0 -20     0    0    0 S    0  0.0   0:00.00 kondemand                                                  
   59 root       0 -20     0    0    0 S    0  0.0   0:00.00 kconservative                                              
  182 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                  
  183 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                  
  184 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                  
  185 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                  
  186 root      20   0     0    0    0 S    0  0.0   0:02.29 scsi_eh_4                                                  
  187 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                  
  217 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_6                                                  
  235 root      20   0  7200  252  144 S    0  0.0   0:01.02 v86d                                                       
  296 root      20   0     0    0    0 S    0  0.0   0:00.62 jbd2/sda3-8                                                
  297 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
  349 root      20   0 17052  640  456 S    0  0.0   0:00.26 upstart-udev-br                                            
  525 root      20   0 22240 1084  592 S    0  0.0   0:00.09 mount.ntfs                                                 
  529 root      16  -4 21740 1192  352 S    0  0.0   0:00.18 udevd                                                      
  867 root      20   0 15004  388  196 S    0  0.0   0:00.02 upstart-socket-                                            
  870 root       0 -20     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                  
  894 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio0                                                  
  917 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio1                                                  
  948 root      20   0 22240 1128  592 S    0  0.0   0:00.08 mount.ntfs                                                 
  990 root      20   0 22452 1604  748 S    0  0.0   0:00.50 mount.ntfs                                                 
  993 root      20   0     0    0    0 S    0  0.0   0:04.20 jbd2/sda5-8                                                
  994 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
 1013 root      20   0 91592 4916 3748 S    0  0.1   0:00.01 smbd                                                       
 1019 root      20   0 49464 2752 2172 S    0  0.0   0:00.00 sshd                                                       
 1026 syslog    20   0  117m 1648 1112 S    0  0.0   0:01.87 rsyslogd                                                   
 1037 root      20   0 91592 1552  384 S    0  0.0   0:00.00 smbd                                                       
 1039 messageb  20   0 24764 2196  856 S    0  0.0   0:05.74 dbus-daemon                                                
 1049 root      20   0 83168 4016 3084 S    0  0.0   0:00.37 gdm-binary                                                 
 1053 avahi     20   0 32132 1704 1400 S    0  0.0   0:00.19 avahi-daemon                                               
 1054 avahi     20   0 32008  468  212 S    0  0.0   0:00.00 avahi-daemon                                               
 1055 root      20   0  154m 5104 3884 S    0  0.1   0:03.49 NetworkManager                                             
 1057 root      20   0  250m 4096 2756 S    0  0.1   0:00.62 console-kit-dae                                            
 1059 root      20   0 64656 2780 2152 S    0  0.0   0:00.05 modem-manager                                              
 1081 root      20   0  126m 4448 2852 S    0  0.1   0:01.49 polkitd                                                    
 1145 root      20   0 75512 3132 2324 S    0  0.0   0:00.03 cupsd                                                      
 1152 root      20   0 97752 4388 3312 S    0  0.1   0:00.01 gdm-simple-slav                                            
 1172 root      20   0 28812 2960 2448 S    0  0.0   0:02.09 wpa_supplicant                                             
 1229 root      20   0  6196  656  548 S    0  0.0   0:00.00 getty                                                      
 1233 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1240 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1241 root      20   0  6196  656  548 S    0  0.0   0:00.00 getty                                                      
 1244 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1252 root      20   0  4416  896  572 S    0  0.0   0:00.02 acpid                                                      
 1265 mysql     20   0  166m  23m 6692 S    0  0.3   0:11.74 mysqld                                                     
 1266 root      20   0 15780  672  500 S    0  0.0   0:11.22 irqbalance                                                 
 1272 root      20   0 18928 1056  816 S    0  0.0   0:00.10 cron                                                       
 1273 daemon    20   0 16728  376  220 S    0  0.0   0:00.00 atd                                                        
 1301 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1302 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1303 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1327 root      20   0     0    0    0 S    0  0.0   0:03.23 flush-8:0                                                  
 1504 root      20   0  6196  660  552 S    0  0.0   0:00.00 getty                                                      
 1557 root      20   0 99.4m 3808 2884 S    0  0.0   0:00.00 gdm-session-wor                                            
 1566 shoaibi   20   0  237m 8516 6328 S    0  0.1   0:00.54 gnome-session                                              
 1601 shoaibi   20   0 12092  288    0 S    0  0.0   0:00.14 ssh-agent                                                  
 1604 shoaibi   20   0 26400  620  352 S    0  0.0   0:00.00 dbus-launch                                                
 1605 shoaibi   20   0 28284 4440  664 S    0  0.1   0:50.63 dbus-daemon                                                
 1610 shoaibi   20   0 60956 5496 2576 S    0  0.1   0:03.00 gconfd-2                                                   
 1617 shoaibi   20   0  168m  10m 3120 S    0  0.1   0:00.38 gnome-keyring-d                                            
 1622 shoaibi   20   0  466m  19m  10m S    0  0.2   0:17.07 gnome-settings-                                            
 1625 shoaibi   20   0 55956 2468 2056 S    0  0.0   0:00.15 gvfsd                                                      
 1630 shoaibi   20   0 81008 2684 1816 S    0  0.0   0:00.00 gvfs-fuse-daemo                                            
 1636 shoaibi   20   0  294m 6704 3836 S    0  0.1   5:23.41 pulseaudio                                                 
 1638 rtkit     21   1  100m 1324 1080 S    0  0.0   0:00.50 rtkit-daemon                                               
 1641 shoaibi   20   0  401m  17m  12m S    0  0.2   0:28.72 metacity                                                   
 1643 shoaibi   20   0  650m  48m  31m S    0  0.6   0:40.52 nautilus                                                   
 1646 shoaibi   20   0  327m  11m 8288 S    0  0.1   0:00.16 bluetooth-apple                                            
 1648 shoaibi   20   0  217m 5856 4348 S    0  0.1   0:00.34 zeitgeist-datah                                            
 1649 shoaibi   20   0  676m  46m  27m S    0  0.6   1:03.35 unity-2d-launch                                            
 1650 shoaibi   20   0  633m  47m  25m S    0  0.6   1:28.61 unity-2d-panel                                             
 1651 shoaibi   20   0  389m  18m  13m S    0  0.2   0:04.17 nm-applet                                                  
 1655 shoaibi   20   0  226m 7272 5632 S    0  0.1   0:00.14 polkit-gnome-au                                            
 1657 shoaibi   20   0  470m  32m  19m S    0  0.4   0:03.50 synapse                                                    
 1658 shoaibi   20   0  370m  26m  12m S    0  0.3   0:00.27 touchpad-indica                                            
 1659 shoaibi   20   0  443m  35m  15m S    0  0.4   0:06.92 python                                                     
 1661 shoaibi   20   0  358m  10m 7752 S    0  0.1   0:03.43 gnome-power-man                                            
 1664 shoaibi   20   0  182m  20m 7364 S    0  0.3   0:01.44 zeitgeist-daemo                                            
 1692 shoaibi   20   0  310m  16m  11m S    0  0.2   0:34.67 notify-osd                                                 
 1693 shoaibi   20   0  177m 3944 3056 S    0  0.0   0:00.00 gconf-helper                                               
 1756 shoaibi   20   0 10848  588  492 S    0  0.0   0:00.00 cat                                                        
 1758 shoaibi   20   0 71904 3748 2908 S    0  0.0   0:00.11 gvfs-gdu-volume                                            
 1760 root      20   0  124m 4004 2960 S    0  0.0   0:00.59 udisks-daemon                                              
 1761 root      20   0 45168 1128  756 S    0  0.0   0:05.98 udisks-daemon                                              
 1764 root      20   0  139m 4424 3304 S    0  0.1   0:02.60 upowerd                                                    
 1826 shoaibi   20   0 77352 2628 2112 S    0  0.0   0:01.25 gvfs-afc-volume                                            
 1832 shoaibi   20   0 63556 2660 1920 S    0  0.0   0:00.00 gvfs-gphoto2-vo                                            
 1846 shoaibi   20   0  220m  10m 6696 S    0  0.1   0:19.12 bamfdaemon                                                 
 1847 shoaibi   20   0     0    0    0 Z    0  0.0   0:00.26 python <defunct>                                           
 1848 shoaibi   20   0     0    0    0 Z    0  0.0   0:00.01 zeitgeist-datah <defunct>                                  
 1850 shoaibi   20   0 22740 1212  904 S    0  0.0   0:19.50 syndaemon                                                  
 1902 shoaibi   20   0  183m 2696 2180 S    0  0.0   0:00.02 dconf-service                                              
 1925 shoaibi   20   0 56220 2784 2168 S    0  0.0   0:00.00 gvfsd-burn                                                 
 1952 shoaibi   20   0  234m 6044 4716 S    0  0.1   0:00.26 indicator-sessi                                            
 1954 shoaibi   20   0  202m 5236 3784 S    0  0.1   0:03.31 indicator-appli                                            
 1956 shoaibi   20   0  237m 5104 4024 S    0  0.1   0:00.03 indicator-messa                                            
 1965 shoaibi   20   0  307m 7828 6072 S    0  0.1   0:00.11 indicator-datet                                            
 1969 shoaibi   20   0  331m 6780 5152 S    0  0.1   0:01.17 indicator-sound                                            
 1988 shoaibi   20   0  155m 4796 3716 S    0  0.1   0:00.26 geoclue-master                                             
 2022 shoaibi   20   0  248m 9688 7404 S    0  0.1   0:09.74 gnome-screensav                                            
 2057 root      20   0 61652 1628  752 S    0  0.0   0:02.77 nmbd                                                       
 2072 shoaibi   20   0  175m 7480 5620 S    0  0.1   0:00.08 gdu-notificatio                                            
 2074 shoaibi   20   0  262m 7840 5236 S    0  0.1   0:01.70 unity-applicati                                            
 2076 shoaibi   20   0  176m 4592 3612 S    0  0.1   0:00.76 unity-files-dae                                            
 2124 shoaibi   20   0  232m  23m  10m S    0  0.3   0:12.43 applet.py                                                  
 2131 shoaibi   20   0 60720 3468 2652 S    0  0.0   0:00.03 gvfsd-trash                                                
 2148 shoaibi   20   0 14612  856  692 S    0  0.0   0:00.01 gnome-pty-helpe                                            
 2206 shoaibi   20   0  317m  15m  11m S    0  0.2   0:01.75 update-notifier                                            
 2227 shoaibi   20   0  486m  37m  22m S    0  0.5   0:08.25 gnote                                                      
 2237 shoaibi   20   0  234m  10m 3432 S    0  0.1   0:13.44 chrome                                                     
 2239 shoaibi   20   0  276m  15m 8124 S    0  0.2   0:00.29 chrome                                                     
 2260 shoaibi   20   0  852m  21m 9.9m S    0  0.3   0:03.29 chrome                                                     
 2264 shoaibi   20   0  855m  27m  14m S    0  0.4   0:14.82 chrome                                                     
 2266 shoaibi   20   0  852m  22m 9.9m S    0  0.3   0:11.92 chrome                                                     
 2268 shoaibi   20   0  854m  25m  12m S    0  0.3   0:14.10 chrome                                                     
 2271 shoaibi   20   0  855m  28m  12m S    0  0.4   0:25.28 chrome                                                     
 2274 shoaibi   20   0  869m  42m  15m S    0  0.5   4:10.71 chrome                                                     
 2277 shoaibi   20   0  872m  28m  12m S    0  0.4   0:28.99 chrome                                                     
 2280 shoaibi   20   0  880m  55m  17m S    0  0.7   1:52.00 chrome                                                     
 2284 shoaibi   20   0  859m  34m  16m S    0  0.4   1:20.07 chrome                                                     
 2286 shoaibi   20   0  870m  40m  13m S    0  0.5   1:12.61 chrome                                                     
 2289 shoaibi   20   0  854m  24m  11m S    0  0.3   0:14.14 chrome                                                     
 2292 shoaibi   20   0  854m  24m  10m S    0  0.3   0:13.45 chrome                                                     
 2295 shoaibi   20   0  852m  21m 9976 S    0  0.3   0:03.46 chrome                                                     
 2299 shoaibi   20   0  852m  21m 9.9m S    0  0.3   0:03.45 chrome                                                     
 2301 shoaibi   20   0  852m  22m 9.8m S    0  0.3   0:22.24 chrome                                                     
 2304 shoaibi   20   0  854m  24m  11m S    0  0.3   0:12.99 chrome                                                     
 2307 shoaibi   20   0  854m  25m  11m S    0  0.3   0:18.50 chrome                                                     
 2311 shoaibi   20   0  853m  22m  10m S    0  0.3   0:03.40 chrome                                                     
 2313 shoaibi   20   0  880m  28m  12m S    0  0.4   0:19.90 chrome                                                     
 2316 shoaibi   20   0  853m  22m  10m S    0  0.3   0:03.49 chrome                                                     
 2319 shoaibi   20   0  853m  24m  11m S    0  0.3   0:14.38 chrome                                                     
 2323 shoaibi   20   0  856m  30m  13m S    0  0.4   0:26.70 chrome                                                     
 2326 shoaibi   20   0  856m  28m  12m S    0  0.4   0:24.58 chrome                                                     
 2329 shoaibi   20   0  856m  27m  13m S    0  0.4   0:05.76 chrome                                                     
 2417 shoaibi   25   5  904m  75m  17m S    0  0.9   1:12.33 chrome                                                     
 2424 shoaibi   25   5  890m  78m  17m S    0  1.0   0:51.08 chrome                                                     
 2454 shoaibi   20   0  274m  16m 9248 S    0  0.2   0:00.04 chrome                                                     
 2597 shoaibi   25   5  901m  75m  18m S    0  1.0   1:58.17 chrome                                                     
 2604 shoaibi   25   5  931m 116m  17m S    0  1.5   2:42.65 chrome                                                     
 2613 shoaibi   25   5  882m  67m  16m S    0  0.8   0:30.97 chrome                                                     
 2656 shoaibi   20   0  672m  44m  23m S    0  0.6   1:19.57 empathy                                                    
 2658 shoaibi   20   0 59508 5772 3616 S    0  0.1   0:03.55 mission-control                                            
 2665 shoaibi   20   0  159m 5064 4012 S    0  0.1   0:00.16 telepathy-logge                                            
 3188 shoaibi   20   0  549m  93m  29m S    0  1.2   0:24.64 unity-2d-spread                                            
 3193 shoaibi   20   0  542m  54m  25m S    0  0.7   0:10.72 unity-2d-places                                            
 3338 shoaibi   20   0 49728 2232 1812 S    0  0.0   0:00.02 gvfsd-metadata                                             
 5559 shoaibi   20   0 27908 5396 1704 S    0  0.1   0:00.40 bash                                                       
 7190 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                
 7192 root      20   0     0    0    0 S    0  0.0   0:00.25 ksoftirqd/1                                                
 7193 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                                                
 7194 root      20   0     0    0    0 S    0  0.0   0:10.77 kworker/2:3                                                
 7195 root      20   0     0    0    0 S    0  0.0   0:00.15 ksoftirqd/2                                                
 7196 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                                                
 7198 root      20   0     0    0    0 S    0  0.0   0:00.13 ksoftirqd/3                                                
 7199 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/4                                                
 7201 root      20   0     0    0    0 S    0  0.0   0:00.15 ksoftirqd/4                                                
 7202 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/5                                                
 7204 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/5                                                
 7205 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/6                                                
 7206 root      20   0     0    0    0 S    0  0.0   0:01.99 kworker/6:3                                                
 7207 root      20   0     0    0    0 S    0  0.0   0:00.11 ksoftirqd/6                                                
 7210 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/7                                                
 7211 root      20   0     0    0    0 S    0  0.0   0:08.95 kworker/7:3                                                
 7212 root      20   0     0    0    0 S    0  0.0   0:00.29 ksoftirqd/7                                                
 7230 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:28                                               
 7231 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:29                                               
 7276 root       0 -20     0    0    0 S    0  0.0   0:00.00 hci0                                                       
 7295 root      18  -2 21736 1188  344 S    0  0.0   0:00.00 udevd                                                      
 7296 root      18  -2 21736 1116  276 S    0  0.0   0:00.00 udevd                                                      
 7305 root      20   0 23072 1988 1524 S    0  0.0   0:00.01 bluetoothd                                                 
 7317 root       0 -20     0    0    0 S    0  0.0   0:00.00 l2cap                                                      
 7342 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd                                                   
 7408 root      20   0     0    0    0 S    0  0.0   0:00.00 RtmpCmdQTask                                               
 8032 root      20   0  7084 1548 1060 S    0  0.0   0:00.03 dhclient                                                   
 8043 shoaibi   20   0  376m  28m  13m S    0  0.4   0:14.94 telepathy-gabbl                                            
 8047 shoaibi   20   0  214m  13m 8708 S    0  0.2   0:00.46 telepathy-haze                                             
 8185 shoaibi   20   0  133m  27m 5868 S    0  0.3   0:04.94 telepathy-butte                                            
 9358 root      20   0     0    0    0 S    0  0.0   0:06.71 kworker/4:1                                                
 9466 root      20   0     0    0    0 S    0  0.0   0:04.44 kworker/5:3                                                
 9777 root      20   0     0    0    0 S    0  0.0   0:07.83 kworker/6:1                                                
10004 root      20   0     0    0    0 S    0  0.0   0:03.92 kworker/3:3                                                
10062 shoaibi   20   0  240m  12m 9964 S    0  0.2   0:00.02 gvfsd-http                                                 
10243 root      20   0     0    0    0 S    0  0.0   0:08.29 kworker/1:1                                                
10330 shoaibi   20   0 19484 1448  968 S    0  0.0   1:31.63 top                                                        
10337 root      20   0     0    0    0 S    0  0.0   0:12.67 kworker/0:0                                                
10367 root      20   0     0    0    0 S    0  0.0   0:09.69 kworker/0:1                                                
10379 root      20   0     0    0    0 S    0  0.0   0:01.19 kworker/5:1                                                
10386 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/4:2                                                
10388 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:0                                                
10389 root      20   0     0    0    0 S    0  0.0   0:02.13 kworker/0:2                                                
10396 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/7:0                                                
10402 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:2                                                
10411 root      20   0     0    0    0 S    0  0.0   0:00.68 kworker/4:0                                                
10417 root      20   0     0    0    0 S    0  0.0   0:00.54 kworker/5:0                                                
10424 root      20   0     0    0    0 S    0  0.0   0:00.26 kworker/7:1                                                
10425 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/6:0                                                
10429 root      20   0     0    0    0 S    0  0.0   0:00.03 kworker/4:3                                                
10430 root      20   0     0    0    0 S    0  0.0   0:00.69 kworker/5:2                                                
10433 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:1                                                
10434 shoaibi   20   0 27952 5484 1744 S    0  0.1   0:08.93 bash                                                       
10507 shoaibi   20   0 16296 1612 1160 S    0  0.0   0:00.13 generate-system                                            
10508 root      20   0 25644 1320 1072 S    0  0.0   0:00.06 sudo                                                       


------
iotop

Total DISK READ: 0.00 B/s | Total DISK WRITE: 2.37 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN      IO    COMMAND
  296 be/3 root        0.00 B/s   14.21 K/s  0.00 %  0.36 % [jbd2/sda3-8]
  993 be/3 root        0.00 B/s   23.69 K/s  0.00 %  0.29 % [jbd2/sda5-8]
 9047 be/4 shoaibi     0.00 B/s    4.74 K/s  0.00 %  0.00 % xchat

------
iostat

Linux 2.6.38-10-generic (abacus) 	06/11/2011 	_x86_64_	(8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.68    0.77    1.28    0.10    0.00   94.17

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               2.34     8.41    1.07    8.63    41.72    68.65    22.75     0.10   10.14   42.51    6.14   1.31   1.27



==========================================================================================================





Top:

top - 19:58:55 up  7:11,  3 users,  load average: 1.54, 1.30, 1.06
Tasks: 250 total,   6 running, 242 sleeping,   0 stopped,   2 zombie
Cpu(s):  3.7%us,  1.2%sy,  0.8%ni, 94.1%id,  0.1%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   8175328k total,  3608188k used,  4567140k free,   256868k buffers
Swap: 10485756k total,        0k used, 10485756k free,   963432k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                    
 2613 shoaibi   25   5  882m  66m  16m S   76  0.8   0:33.64 chrome                                                     
 2600 shoaibi   25   5  943m  96m  17m R   64  1.2   3:49.02 chrome                                                     
 2604 shoaibi   25   5  931m 117m  17m R   56  1.5   2:47.40 chrome                                                     
 1178 root      20   0  401m 110m  81m R   34  1.4  22:31.27 Xorg                                                       
 2143 shoaibi   20   0  465m  41m  18m S   34  0.5   1:33.74 /usr/bin/termin                                            
10523 root      20   0 19480 1416  952 R   32  0.0   0:00.64 top                                                        
 2622 shoaibi   20   0  648m  55m  23m R   15  0.7  42:55.95 chrome                                                     
 2462 shoaibi   25   5  902m  75m  17m S   12  0.9   2:42.40 chrome                                                     
 2427 shoaibi   20   0  997m 182m  21m S   11  2.3   9:44.53 chrome                                                     
 1692 shoaibi   20   0  310m  16m  11m S    9  0.2   0:35.55 notify-osd                                                 
 2232 shoaibi   20   0  756m 133m  38m R    8  1.7  23:23.76 chrome                                                     
 2610 shoaibi   20   0  895m  76m  18m S    8  1.0   4:33.36 chrome                                                     
 2435 shoaibi   20   0  978m 162m  19m S    7  2.0   8:34.88 chrome                                                     
 2421 shoaibi   25   5  910m  91m  17m S    5  1.1   3:58.00 chrome                                                     
 9047 shoaibi   20   0  395m  37m  17m S    5  0.5   1:26.60 xchat                                                      
 1645 shoaibi   20   0  316m  12m 8636 S    3  0.2   1:38.27 diodon                                                     
 8241 shoaibi   20   0  288m  92m  21m S    3  1.2   3:57.69 skype                                                      
10431 root      20   0     0    0    0 S    3  0.0   0:00.80 kworker/1:0                                                
 1850 shoaibi   20   0 22740 1212  904 S    1  0.0   0:19.63 syndaemon                                                  
 7899 root      20   0     0    0    0 S    1  0.0   0:06.74 kworker/3:1                                                
 9358 root      20   0     0    0    0 S    1  0.0   0:07.18 kworker/4:1                                                
 9777 root      20   0     0    0    0 S    1  0.0   0:08.21 kworker/6:1                                                
10367 root      20   0     0    0    0 S    1  0.0   0:10.12 kworker/0:1                                                
10430 root      20   0     0    0    0 S    1  0.0   0:01.06 kworker/5:2                                                
    1 root      20   0 24128 2280 1368 S    0  0.0   0:02.88 init                                                       
    2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd                                                   
    3 root      20   0     0    0    0 S    0  0.0   0:01.58 ksoftirqd/0                                                
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                     
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                    
   31 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                      
   33 root      20   0     0    0    0 S    0  0.0   0:00.12 sync_supers                                                
   34 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                
   35 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                
   36 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                    
   37 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpid                                                     
   38 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                               
   39 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                              
   40 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                    
   41 root      20   0     0    0    0 S    0  0.0   0:00.01 khubd                                                      
   42 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                         
   44 root      20   0     0    0    0 S    0  0.0   0:00.02 khungtaskd                                                 
   45 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                    
   46 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                       
   47 root      20   0     0    0    0 S    0  0.0   0:00.00 fsnotify_mark                                              
   48 root       0 -20     0    0    0 S    0  0.0   0:00.00 aio                                                        
   49 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                            
   50 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                     
   54 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                   
   56 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpathd                                                    
   57 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd                                            
   58 root       0 -20     0    0    0 S    0  0.0   0:00.00 kondemand                                                  
   59 root       0 -20     0    0    0 S    0  0.0   0:00.00 kconservative                                              
  182 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                  
  183 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                  
  184 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                  
  185 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                  
  186 root      20   0     0    0    0 S    0  0.0   0:02.30 scsi_eh_4                                                  
  187 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                  
  217 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_6                                                  
  218 root      20   0     0    0    0 S    0  0.0   0:14.79 usb-storage                                                
  235 root      20   0  7200  252  144 S    0  0.0   0:01.02 v86d                                                       
  296 root      20   0     0    0    0 S    0  0.0   0:00.63 jbd2/sda3-8                                                
  297 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
  349 root      20   0 17052  640  456 S    0  0.0   0:00.26 upstart-udev-br                                            
  525 root      20   0 22240 1084  592 S    0  0.0   0:00.09 mount.ntfs                                                 
  529 root      16  -4 21740 1192  352 S    0  0.0   0:00.18 udevd                                                      
  867 root      20   0 15004  388  196 S    0  0.0   0:00.02 upstart-socket-                                            
  870 root       0 -20     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                  
  894 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio0                                                  
  917 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio1                                                  
  948 root      20   0 22240 1128  592 S    0  0.0   0:00.08 mount.ntfs                                                 
  990 root      20   0 22452 1604  748 S    0  0.0   0:00.50 mount.ntfs                                                 
  993 root      20   0     0    0    0 S    0  0.0   0:04.27 jbd2/sda5-8                                                
  994 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
 1013 root      20   0 91592 4916 3748 S    0  0.1   0:00.01 smbd                                                       
 1019 root      20   0 49464 2752 2172 S    0  0.0   0:00.00 sshd                                                       
 1026 syslog    20   0  117m 1648 1112 S    0  0.0   0:01.87 rsyslogd                                                   
 1037 root      20   0 91592 1552  384 S    0  0.0   0:00.00 smbd                                                       
 1039 messageb  20   0 24764 2196  856 S    0  0.0   0:05.74 dbus-daemon                                                
 1049 root      20   0 83168 4016 3084 S    0  0.0   0:00.39 gdm-binary                                                 
 1053 avahi     20   0 32132 1704 1400 S    0  0.0   0:00.19 avahi-daemon                                               
 1054 avahi     20   0 32008  468  212 S    0  0.0   0:00.00 avahi-daemon                                               
 1055 root      20   0  154m 5104 3884 S    0  0.1   0:03.50 NetworkManager                                             
 1057 root      20   0  250m 4096 2756 S    0  0.1   0:00.62 console-kit-dae                                            
 1059 root      20   0 64656 2780 2152 S    0  0.0   0:00.05 modem-manager                                              
 1081 root      20   0  126m 4448 2852 S    0  0.1   0:01.49 polkitd                                                    
 1145 root      20   0 75512 3132 2324 S    0  0.0   0:00.03 cupsd                                                      
 1152 root      20   0 97752 4388 3312 S    0  0.1   0:00.01 gdm-simple-slav                                            
 1172 root      20   0 28812 2960 2448 S    0  0.0   0:02.09 wpa_supplicant                                             
 1229 root      20   0  6196  656  548 S    0  0.0   0:00.00 getty                                                      
 1233 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1240 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1241 root      20   0  6196  656  548 S    0  0.0   0:00.00 getty                                                      
 1244 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1252 root      20   0  4416  896  572 S    0  0.0   0:00.02 acpid                                                      
 1265 mysql     20   0  166m  23m 6692 S    0  0.3   0:11.85 mysqld                                                     
 1266 root      20   0 15780  672  500 S    0  0.0   0:11.34 irqbalance                                                 
 1272 root      20   0 18928 1056  816 S    0  0.0   0:00.10 cron                                                       
 1273 daemon    20   0 16728  376  220 S    0  0.0   0:00.00 atd                                                        
 1301 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1302 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1303 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1327 root      20   0     0    0    0 S    0  0.0   0:03.25 flush-8:0                                                  
 1504 root      20   0  6196  660  552 S    0  0.0   0:00.00 getty                                                      
 1557 root      20   0 99.4m 3808 2884 S    0  0.0   0:00.00 gdm-session-wor                                            
 1566 shoaibi   20   0  237m 8516 6328 S    0  0.1   0:00.55 gnome-session                                              
 1601 shoaibi   20   0 12092  288    0 S    0  0.0   0:00.14 ssh-agent                                                  
 1604 shoaibi   20   0 26400  620  352 S    0  0.0   0:00.00 dbus-launch                                                
 1605 shoaibi   20   0 28284 4440  664 S    0  0.1   0:52.43 dbus-daemon                                                
 1610 shoaibi   20   0 60956 5496 2576 S    0  0.1   0:03.01 gconfd-2                                                   
 1617 shoaibi   20   0  168m  10m 3120 S    0  0.1   0:00.39 gnome-keyring-d                                            
 1622 shoaibi   20   0  466m  19m  10m S    0  0.2   0:17.43 gnome-settings-                                            
 1625 shoaibi   20   0 55956 2468 2056 S    0  0.0   0:00.15 gvfsd                                                      
 1630 shoaibi   20   0 81008 2684 1816 S    0  0.0   0:00.00 gvfs-fuse-daemo                                            
 1636 shoaibi   20   0  294m 6704 3836 S    0  0.1   5:23.41 pulseaudio                                                 
 1638 rtkit     21   1  100m 1324 1080 S    0  0.0   0:00.51 rtkit-daemon                                               
 1641 shoaibi   20   0  401m  17m  12m S    0  0.2   0:29.70 metacity                                                   
 1643 shoaibi   20   0  650m  48m  31m S    0  0.6   0:40.76 nautilus                                                   
 1646 shoaibi   20   0  327m  11m 8288 S    0  0.1   0:00.16 bluetooth-apple                                            
 1648 shoaibi   20   0  217m 5856 4348 S    0  0.1   0:00.34 zeitgeist-datah                                            
 1649 shoaibi   20   0  676m  46m  27m S    0  0.6   1:04.29 unity-2d-launch                                            
 1650 shoaibi   20   0  633m  47m  25m S    0  0.6   1:30.06 unity-2d-panel                                             
 1651 shoaibi   20   0  389m  18m  13m S    0  0.2   0:04.18 nm-applet                                                  
 1655 shoaibi   20   0  226m 7272 5632 S    0  0.1   0:00.14 polkit-gnome-au                                            
 1657 shoaibi   20   0  470m  32m  19m S    0  0.4   0:03.53 synapse                                                    
 1658 shoaibi   20   0  370m  26m  12m S    0  0.3   0:00.27 touchpad-indica                                            
 1659 shoaibi   20   0  443m  35m  15m S    0  0.4   0:06.92 python                                                     
 1661 shoaibi   20   0  358m  10m 7752 S    0  0.1   0:03.44 gnome-power-man                                            
 1664 shoaibi   20   0  182m  20m 7364 S    0  0.3   0:01.44 zeitgeist-daemo                                            
 1693 shoaibi   20   0  177m 3944 3056 S    0  0.0   0:00.00 gconf-helper                                               
 1696 shoaibi   20   0  612m  56m  19m S    0  0.7   0:22.35 dropbox                                                    
 1756 shoaibi   20   0 10848  588  492 S    0  0.0   0:00.00 cat                                                        
 1758 shoaibi   20   0 71904 3748 2908 S    0  0.0   0:00.11 gvfs-gdu-volume                                            
 1760 root      20   0  124m 4004 2960 S    0  0.0   0:00.59 udisks-daemon                                              
 1761 root      20   0 45168 1128  756 S    0  0.0   0:06.02 udisks-daemon                                              
 1764 root      20   0  139m 4424 3304 S    0  0.1   0:02.60 upowerd                                                    
 1826 shoaibi   20   0 77352 2628 2112 S    0  0.0   0:01.26 gvfs-afc-volume                                            
 1832 shoaibi   20   0 63556 2660 1920 S    0  0.0   0:00.00 gvfs-gphoto2-vo                                            
 1846 shoaibi   20   0  220m  10m 6696 S    0  0.1   0:20.03 bamfdaemon                                                 
 1847 shoaibi   20   0     0    0    0 Z    0  0.0   0:00.26 python <defunct>                                           
 1848 shoaibi   20   0     0    0    0 Z    0  0.0   0:00.01 zeitgeist-datah <defunct>                                  
 1902 shoaibi   20   0  183m 2696 2180 S    0  0.0   0:00.02 dconf-service                                              
 1925 shoaibi   20   0 56220 2784 2168 S    0  0.0   0:00.00 gvfsd-burn                                                 
 1952 shoaibi   20   0  234m 6044 4716 S    0  0.1   0:00.26 indicator-sessi                                            
 1954 shoaibi   20   0  202m 5236 3784 S    0  0.1   0:03.32 indicator-appli                                            
 1956 shoaibi   20   0  237m 5104 4024 S    0  0.1   0:00.03 indicator-messa                                            
 1965 shoaibi   20   0  307m 7828 6072 S    0  0.1   0:00.11 indicator-datet                                            
 1969 shoaibi   20   0  331m 6780 5152 S    0  0.1   0:01.19 indicator-sound                                            
 1988 shoaibi   20   0  155m 4796 3716 S    0  0.1   0:00.26 geoclue-master                                             
 2022 shoaibi   20   0  248m 9688 7404 S    0  0.1   0:09.89 gnome-screensav                                            
 2057 root      20   0 61652 1628  752 S    0  0.0   0:02.80 nmbd                                                       
 2072 shoaibi   20   0  175m 7480 5620 S    0  0.1   0:00.08 gdu-notificatio                                            
 2074 shoaibi   20   0  262m 7840 5236 S    0  0.1   0:01.72 unity-applicati                                            
 2076 shoaibi   20   0  176m 4592 3612 S    0  0.1   0:00.78 unity-files-dae                                            
 2124 shoaibi   20   0  232m  23m  10m S    0  0.3   0:12.52 applet.py                                                  
 2131 shoaibi   20   0 60720 3468 2652 S    0  0.0   0:00.03 gvfsd-trash                                                
 2148 shoaibi   20   0 14612  856  692 S    0  0.0   0:00.01 gnome-pty-helpe                                            
 2206 shoaibi   20   0  317m  15m  11m S    0  0.2   0:01.79 update-notifier                                            
 2227 shoaibi   20   0  486m  37m  22m S    0  0.5   0:08.30 gnote                                                      
 2237 shoaibi   20   0  234m  10m 3432 S    0  0.1   0:13.44 chrome                                                     
 2239 shoaibi   20   0  276m  15m 8124 S    0  0.2   0:00.29 chrome                                                     
 2260 shoaibi   20   0  852m  21m 9.9m S    0  0.3   0:03.31 chrome                                                     
 2264 shoaibi   20   0  855m  27m  14m S    0  0.4   0:14.93 chrome                                                     
 2266 shoaibi   20   0  852m  22m 9.9m S    0  0.3   0:11.95 chrome                                                     
 2268 shoaibi   20   0  854m  25m  12m S    0  0.3   0:14.13 chrome                                                     
 2271 shoaibi   20   0  855m  28m  12m S    0  0.4   0:26.65 chrome                                                     
 2274 shoaibi   20   0  869m  41m  15m S    0  0.5   4:17.38 chrome                                                     
 2277 shoaibi   20   0  872m  28m  12m S    0  0.4   0:29.45 chrome                                                     
 2280 shoaibi   20   0  880m  55m  17m S    0  0.7   1:52.09 chrome                                                     
 2284 shoaibi   20   0  859m  34m  16m S    0  0.4   1:20.41 chrome                                                     
 2286 shoaibi   20   0  870m  40m  13m S    0  0.5   1:13.75 chrome                                                     
 2289 shoaibi   20   0  854m  24m  11m S    0  0.3   0:14.48 chrome                                                     
 2292 shoaibi   20   0  854m  24m  10m S    0  0.3   0:13.55 chrome                                                     
 2295 shoaibi   20   0  852m  21m 9976 S    0  0.3   0:03.48 chrome                                                     
 2299 shoaibi   20   0  852m  21m 9.9m S    0  0.3   0:03.47 chrome                                                     
 2301 shoaibi   20   0  852m  22m 9.8m S    0  0.3   0:22.27 chrome                                                     
 2304 shoaibi   20   0  854m  24m  11m S    0  0.3   0:13.02 chrome                                                     
 2307 shoaibi   20   0  854m  25m  11m S    0  0.3   0:18.73 chrome                                                     
 2311 shoaibi   20   0  853m  22m  10m S    0  0.3   0:03.42 chrome                                                     
 2313 shoaibi   20   0  880m  28m  12m S    0  0.4   0:19.94 chrome                                                     
 2316 shoaibi   20   0  853m  22m  10m S    0  0.3   0:03.51 chrome                                                     
 2319 shoaibi   20   0  853m  24m  11m S    0  0.3   0:14.41 chrome                                                     
 2323 shoaibi   20   0  856m  30m  13m S    0  0.4   0:26.73 chrome                                                     
 2326 shoaibi   20   0  856m  28m  12m S    0  0.4   0:24.61 chrome                                                     
 2329 shoaibi   20   0  856m  27m  13m S    0  0.4   0:05.79 chrome                                                     
 2417 shoaibi   25   5  904m  77m  17m S    0  1.0   1:16.30 chrome                                                     
 2424 shoaibi   25   5  890m  78m  17m S    0  1.0   0:51.97 chrome                                                     
 2454 shoaibi   20   0  274m  16m 9248 S    0  0.2   0:00.04 chrome                                                     
 2597 shoaibi   25   5  901m  75m  18m S    0  1.0   1:59.62 chrome                                                     
 2656 shoaibi   20   0  672m  44m  23m S    0  0.6   1:19.61 empathy                                                    
 2658 shoaibi   20   0 59508 5772 3616 S    0  0.1   0:03.56 mission-control                                            
 2665 shoaibi   20   0  159m 5064 4012 S    0  0.1   0:00.16 telepathy-logge                                            
 3188 shoaibi   20   0  549m  93m  29m S    0  1.2   0:25.05 unity-2d-spread                                            
 3193 shoaibi   20   0  542m  54m  25m S    0  0.7   0:11.14 unity-2d-places                                            
 3338 shoaibi   20   0 49728 2232 1812 S    0  0.0   0:00.02 gvfsd-metadata                                             
 5559 shoaibi   20   0 27908 5396 1704 S    0  0.1   0:00.40 bash                                                       
 7190 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                
 7192 root      20   0     0    0    0 S    0  0.0   0:00.27 ksoftirqd/1                                                
 7193 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                                                
 7194 root      20   0     0    0    0 S    0  0.0   0:11.24 kworker/2:3                                                
 7195 root      20   0     0    0    0 S    0  0.0   0:00.15 ksoftirqd/2                                                
 7196 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                                                
 7198 root      20   0     0    0    0 S    0  0.0   0:00.13 ksoftirqd/3                                                
 7199 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/4                                                
 7201 root      20   0     0    0    0 S    0  0.0   0:00.15 ksoftirqd/4                                                
 7202 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/5                                                
 7204 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/5                                                
 7205 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/6                                                
 7206 root      20   0     0    0    0 S    0  0.0   0:01.99 kworker/6:3                                                
 7207 root      20   0     0    0    0 S    0  0.0   0:00.11 ksoftirqd/6                                                
 7210 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/7                                                
 7211 root      20   0     0    0    0 S    0  0.0   0:08.95 kworker/7:3                                                
 7212 root      20   0     0    0    0 S    0  0.0   0:00.29 ksoftirqd/7                                                
 7230 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:28                                               
 7231 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:29                                               
 7276 root       0 -20     0    0    0 S    0  0.0   0:00.00 hci0                                                       
 7295 root      18  -2 21736 1188  344 S    0  0.0   0:00.00 udevd                                                      
 7296 root      18  -2 21736 1116  276 S    0  0.0   0:00.00 udevd                                                      
 7305 root      20   0 23072 1988 1524 S    0  0.0   0:00.01 bluetoothd                                                 
 7317 root       0 -20     0    0    0 S    0  0.0   0:00.00 l2cap                                                      
 7342 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd                                                   
 7408 root      20   0     0    0    0 S    0  0.0   0:00.00 RtmpCmdQTask                                               
 8032 root      20   0  7084 1548 1060 S    0  0.0   0:00.03 dhclient                                                   
 8043 shoaibi   20   0  376m  28m  13m S    0  0.4   0:14.96 telepathy-gabbl                                            
 8047 shoaibi   20   0  214m  13m 8708 S    0  0.2   0:00.46 telepathy-haze                                             
 8185 shoaibi   20   0  133m  27m 5868 S    0  0.3   0:04.95 telepathy-butte                                            
 9466 root      20   0     0    0    0 S    0  0.0   0:04.44 kworker/5:3                                                
10004 root      20   0     0    0    0 S    0  0.0   0:03.92 kworker/3:3                                                
10062 shoaibi   20   0  240m  12m 9964 S    0  0.2   0:00.02 gvfsd-http                                                 
10243 root      20   0     0    0    0 S    0  0.0   0:08.29 kworker/1:1                                                
10330 shoaibi   20   0 19484 1448  968 S    0  0.0   1:33.84 top                                                        
10337 root      20   0     0    0    0 S    0  0.0   0:12.67 kworker/0:0                                                
10352 root      20   0     0    0    0 S    0  0.0   0:07.16 kworker/1:3                                                
10379 root      20   0     0    0    0 S    0  0.0   0:01.19 kworker/5:1                                                
10386 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/4:2                                                
10388 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:0                                                
10389 root      20   0     0    0    0 S    0  0.0   0:02.13 kworker/0:2                                                
10396 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/7:0                                                
10402 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:2                                                
10411 root      20   0     0    0    0 S    0  0.0   0:00.68 kworker/4:0                                                
10417 root      20   0     0    0    0 S    0  0.0   0:00.54 kworker/5:0                                                
10424 root      20   0     0    0    0 S    0  0.0   0:00.64 kworker/7:1                                                
10425 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/6:0                                                
10429 root      20   0     0    0    0 S    0  0.0   0:00.03 kworker/4:3                                                
10432 root      20   0     0    0    0 S    0  0.0   0:01.16 kworker/0:3                                                
10433 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:1                                                
10434 shoaibi   20   0 27952 5484 1744 S    0  0.1   0:08.97 bash                                                       
10521 shoaibi   20   0 16296 1616 1160 S    0  0.0   0:00.13 generate-system                                            
10522 root      20   0 25644 1324 1076 S    0  0.0   0:00.06 sudo                                                       


------
iotop

Total DISK READ: 0.00 B/s | Total DISK WRITE: 18.19 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN      IO    COMMAND

------
iostat

Linux 2.6.38-10-generic (abacus) 	06/11/2011 	_x86_64_	(8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.71    0.78    1.29    0.10    0.00   94.11

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               2.34     8.40    1.07    8.64    41.67    68.63    22.73     0.10   10.13   42.50    6.14   1.31   1.27



==========================================================================================================





Top:

top - 19:59:03 up  7:11,  3 users,  load average: 1.83, 1.37, 1.08
Tasks: 250 total,   5 running, 243 sleeping,   0 stopped,   2 zombie
Cpu(s):  3.7%us,  1.2%sy,  0.8%ni, 94.1%id,  0.1%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   8175328k total,  3606452k used,  4568876k free,   256884k buffers
Swap: 10485756k total,        0k used, 10485756k free,   963464k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                    
 2435 shoaibi   20   0  978m 162m  19m R   93  2.0   8:36.05 chrome                                                     
 2417 shoaibi   25   5  904m  77m  17m S   74  1.0   1:17.15 chrome                                                     
 2143 shoaibi   20   0  465m  41m  18m R   32  0.5   1:35.49 /usr/bin/termin                                            
 2277 shoaibi   20   0  872m  27m  12m S   32  0.4   0:29.81 chrome                                                     
10534 root      20   0 19480 1416  952 R   24  0.0   0:00.60 top                                                        
 1178 root      20   0  401m 110m  81m S   17  1.4  22:35.36 Xorg                                                       
 2622 shoaibi   20   0  648m  55m  23m S   15  0.7  42:57.11 chrome                                                     
 2427 shoaibi   20   0  997m 182m  21m S   12  2.3   9:46.45 chrome                                                     
 2232 shoaibi   20   0  756m 133m  38m S    7  1.7  23:24.27 chrome                                                     
 2610 shoaibi   20   0  895m  76m  18m S    6  1.0   4:33.82 chrome                                                     
 9047 shoaibi   20   0  395m  37m  17m S    6  0.5   1:26.86 xchat                                                      
 1266 root      20   0 15780  672  500 S    5  0.0   0:11.38 irqbalance                                                 
 2421 shoaibi   25   5  910m  91m  17m S    5  1.1   4:02.94 chrome                                                     
 1605 shoaibi   20   0 28284 4440  664 S    4  0.1   0:52.66 dbus-daemon                                                
 2600 shoaibi   25   5  943m  96m  17m S    4  1.2   3:53.49 chrome                                                     
 8241 shoaibi   20   0  288m  92m  21m S    4  1.2   3:57.98 skype                                                      
 1645 shoaibi   20   0  316m  12m 8636 S    2  0.2   1:38.46 diodon                                                     
 2271 shoaibi   20   0  855m  28m  12m S    2  0.4   0:26.76 chrome                                                     
 2295 shoaibi   20   0  852m  21m 9976 S    2  0.3   0:03.68 chrome                                                     
 2597 shoaibi   25   5  901m  75m  18m S    2  1.0   2:02.22 chrome                                                     
 1650 shoaibi   20   0  633m  47m  25m S    1  0.6   1:30.65 unity-2d-panel                                             
 1696 shoaibi   20   0  612m  56m  19m S    1  0.7   0:22.38 dropbox                                                    
 1846 shoaibi   20   0  220m  10m 6696 R    1  0.1   0:20.10 bamfdaemon                                                 
 1850 shoaibi   20   0 22740 1212  904 S    1  0.0   0:19.66 syndaemon                                                  
 7194 root      20   0     0    0    0 S    1  0.0   0:11.32 kworker/2:3                                                
 7899 root      20   0     0    0    0 S    1  0.0   0:06.83 kworker/3:1                                                
 9358 root      20   0     0    0    0 S    1  0.0   0:07.32 kworker/4:1                                                
 9777 root      20   0     0    0    0 S    1  0.0   0:08.34 kworker/6:1                                                
10430 root      20   0     0    0    0 S    1  0.0   0:01.20 kworker/5:2                                                
10431 root      20   0     0    0    0 S    1  0.0   0:00.90 kworker/1:0                                                
10432 root      20   0     0    0    0 S    1  0.0   0:01.25 kworker/0:3                                                
    1 root      20   0 24128 2280 1368 S    0  0.0   0:02.88 init                                                       
    2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd                                                   
    3 root      20   0     0    0    0 S    0  0.0   0:01.58 ksoftirqd/0                                                
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                     
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                    
   31 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                      
   33 root      20   0     0    0    0 S    0  0.0   0:00.12 sync_supers                                                
   34 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                
   35 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                
   36 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                    
   37 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpid                                                     
   38 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                               
   39 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                              
   40 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                    
   41 root      20   0     0    0    0 S    0  0.0   0:00.01 khubd                                                      
   42 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                         
   44 root      20   0     0    0    0 S    0  0.0   0:00.02 khungtaskd                                                 
   45 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                    
   46 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                       
   47 root      20   0     0    0    0 S    0  0.0   0:00.00 fsnotify_mark                                              
   48 root       0 -20     0    0    0 S    0  0.0   0:00.00 aio                                                        
   49 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                            
   50 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                     
   54 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                   
   56 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpathd                                                    
   57 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd                                            
   58 root       0 -20     0    0    0 S    0  0.0   0:00.00 kondemand                                                  
   59 root       0 -20     0    0    0 S    0  0.0   0:00.00 kconservative                                              
  182 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                  
  183 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                  
  184 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                  
  185 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                  
  186 root      20   0     0    0    0 S    0  0.0   0:02.31 scsi_eh_4                                                  
  187 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                  
  217 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_6                                                  
  218 root      20   0     0    0    0 S    0  0.0   0:14.82 usb-storage                                                
  235 root      20   0  7200  252  144 S    0  0.0   0:01.02 v86d                                                       
  296 root      20   0     0    0    0 S    0  0.0   0:00.63 jbd2/sda3-8                                                
  297 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
  349 root      20   0 17052  640  456 S    0  0.0   0:00.26 upstart-udev-br                                            
  525 root      20   0 22240 1084  592 S    0  0.0   0:00.09 mount.ntfs                                                 
  529 root      16  -4 21740 1192  352 S    0  0.0   0:00.18 udevd                                                      
  867 root      20   0 15004  388  196 S    0  0.0   0:00.02 upstart-socket-                                            
  870 root       0 -20     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                  
  894 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio0                                                  
  917 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio1                                                  
  948 root      20   0 22240 1128  592 S    0  0.0   0:00.08 mount.ntfs                                                 
  990 root      20   0 22452 1604  748 S    0  0.0   0:00.50 mount.ntfs                                                 
  993 root      20   0     0    0    0 S    0  0.0   0:04.28 jbd2/sda5-8                                                
  994 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
 1013 root      20   0 91592 4916 3748 S    0  0.1   0:00.01 smbd                                                       
 1019 root      20   0 49464 2752 2172 S    0  0.0   0:00.00 sshd                                                       
 1026 syslog    20   0  117m 1648 1112 S    0  0.0   0:01.87 rsyslogd                                                   
 1037 root      20   0 91592 1552  384 S    0  0.0   0:00.00 smbd                                                       
 1039 messageb  20   0 24764 2196  856 S    0  0.0   0:05.74 dbus-daemon                                                
 1049 root      20   0 83168 4016 3084 S    0  0.0   0:00.39 gdm-binary                                                 
 1053 avahi     20   0 32132 1704 1400 S    0  0.0   0:00.19 avahi-daemon                                               
 1054 avahi     20   0 32008  468  212 S    0  0.0   0:00.00 avahi-daemon                                               
 1055 root      20   0  154m 5104 3884 S    0  0.1   0:03.50 NetworkManager                                             
 1057 root      20   0  250m 4096 2756 S    0  0.1   0:00.62 console-kit-dae                                            
 1059 root      20   0 64656 2780 2152 S    0  0.0   0:00.05 modem-manager                                              
 1081 root      20   0  126m 4448 2852 S    0  0.1   0:01.49 polkitd                                                    
 1145 root      20   0 75512 3132 2324 S    0  0.0   0:00.03 cupsd                                                      
 1152 root      20   0 97752 4388 3312 S    0  0.1   0:00.01 gdm-simple-slav                                            
 1172 root      20   0 28812 2960 2448 S    0  0.0   0:02.09 wpa_supplicant                                             
 1229 root      20   0  6196  656  548 S    0  0.0   0:00.00 getty                                                      
 1233 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1240 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1241 root      20   0  6196  656  548 S    0  0.0   0:00.00 getty                                                      
 1244 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1252 root      20   0  4416  896  572 S    0  0.0   0:00.02 acpid                                                      
 1265 mysql     20   0  166m  23m 6692 S    0  0.3   0:11.88 mysqld                                                     
 1272 root      20   0 18928 1056  816 S    0  0.0   0:00.10 cron                                                       
 1273 daemon    20   0 16728  376  220 S    0  0.0   0:00.00 atd                                                        
 1301 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1302 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1303 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1327 root      20   0     0    0    0 S    0  0.0   0:03.27 flush-8:0                                                  
 1504 root      20   0  6196  660  552 S    0  0.0   0:00.00 getty                                                      
 1557 root      20   0 99.4m 3808 2884 S    0  0.0   0:00.00 gdm-session-wor                                            
 1566 shoaibi   20   0  237m 8516 6328 S    0  0.1   0:00.55 gnome-session                                              
 1601 shoaibi   20   0 12092  288    0 S    0  0.0   0:00.14 ssh-agent                                                  
 1604 shoaibi   20   0 26400  620  352 S    0  0.0   0:00.00 dbus-launch                                                
 1610 shoaibi   20   0 60956 5496 2576 S    0  0.1   0:03.01 gconfd-2                                                   
 1617 shoaibi   20   0  168m  10m 3120 S    0  0.1   0:00.39 gnome-keyring-d                                            
 1622 shoaibi   20   0  466m  19m  10m S    0  0.2   0:17.48 gnome-settings-                                            
 1625 shoaibi   20   0 55956 2468 2056 S    0  0.0   0:00.15 gvfsd                                                      
 1630 shoaibi   20   0 81008 2684 1816 S    0  0.0   0:00.00 gvfs-fuse-daemo                                            
 1636 shoaibi   20   0  294m 6704 3836 S    0  0.1   5:23.41 pulseaudio                                                 
 1638 rtkit     21   1  100m 1324 1080 S    0  0.0   0:00.51 rtkit-daemon                                               
 1641 shoaibi   20   0  401m  17m  12m S    0  0.2   0:29.88 metacity                                                   
 1643 shoaibi   20   0  650m  48m  31m S    0  0.6   0:40.80 nautilus                                                   
 1646 shoaibi   20   0  327m  11m 8288 S    0  0.1   0:00.16 bluetooth-apple                                            
 1648 shoaibi   20   0  217m 5856 4348 S    0  0.1   0:00.34 zeitgeist-datah                                            
 1649 shoaibi   20   0  676m  46m  27m S    0  0.6   1:04.32 unity-2d-launch                                            
 1651 shoaibi   20   0  389m  18m  13m S    0  0.2   0:04.18 nm-applet                                                  
 1655 shoaibi   20   0  226m 7272 5632 S    0  0.1   0:00.14 polkit-gnome-au                                            
 1657 shoaibi   20   0  470m  32m  19m S    0  0.4   0:03.53 synapse                                                    
 1658 shoaibi   20   0  370m  26m  12m S    0  0.3   0:00.27 touchpad-indica                                            
 1659 shoaibi   20   0  443m  35m  15m S    0  0.4   0:06.92 python                                                     
 1661 shoaibi   20   0  358m  10m 7752 S    0  0.1   0:03.44 gnome-power-man                                            
 1664 shoaibi   20   0  182m  20m 7364 S    0  0.3   0:01.44 zeitgeist-daemo                                            
 1692 shoaibi   20   0  310m  16m  11m S    0  0.2   0:36.03 notify-osd                                                 
 1693 shoaibi   20   0  177m 3944 3056 S    0  0.0   0:00.00 gconf-helper                                               
 1756 shoaibi   20   0 10848  588  492 S    0  0.0   0:00.00 cat                                                        
 1758 shoaibi   20   0 71904 3748 2908 S    0  0.0   0:00.11 gvfs-gdu-volume                                            
 1760 root      20   0  124m 4004 2960 S    0  0.0   0:00.59 udisks-daemon                                              
 1761 root      20   0 45168 1128  756 S    0  0.0   0:06.03 udisks-daemon                                              
 1764 root      20   0  139m 4424 3304 S    0  0.1   0:02.60 upowerd                                                    
 1826 shoaibi   20   0 77352 2628 2112 S    0  0.0   0:01.27 gvfs-afc-volume                                            
 1832 shoaibi   20   0 63556 2660 1920 S    0  0.0   0:00.00 gvfs-gphoto2-vo                                            
 1847 shoaibi   20   0     0    0    0 Z    0  0.0   0:00.26 python <defunct>                                           
 1848 shoaibi   20   0     0    0    0 Z    0  0.0   0:00.01 zeitgeist-datah <defunct>                                  
 1902 shoaibi   20   0  183m 2696 2180 S    0  0.0   0:00.02 dconf-service                                              
 1925 shoaibi   20   0 56220 2784 2168 S    0  0.0   0:00.00 gvfsd-burn                                                 
 1952 shoaibi   20   0  234m 6044 4716 S    0  0.1   0:00.26 indicator-sessi                                            
 1954 shoaibi   20   0  202m 5236 3784 S    0  0.1   0:03.32 indicator-appli                                            
 1956 shoaibi   20   0  237m 5104 4024 S    0  0.1   0:00.03 indicator-messa                                            
 1965 shoaibi   20   0  307m 7828 6072 S    0  0.1   0:00.11 indicator-datet                                            
 1969 shoaibi   20   0  331m 6780 5152 S    0  0.1   0:01.19 indicator-sound                                            
 1988 shoaibi   20   0  155m 4796 3716 S    0  0.1   0:00.26 geoclue-master                                             
 2022 shoaibi   20   0  248m 9688 7404 S    0  0.1   0:09.90 gnome-screensav                                            
 2057 root      20   0 61652 1628  752 S    0  0.0   0:02.81 nmbd                                                       
 2072 shoaibi   20   0  175m 7480 5620 S    0  0.1   0:00.08 gdu-notificatio                                            
 2074 shoaibi   20   0  262m 7840 5236 S    0  0.1   0:01.72 unity-applicati                                            
 2076 shoaibi   20   0  176m 4592 3612 S    0  0.1   0:00.78 unity-files-dae                                            
 2124 shoaibi   20   0  232m  23m  10m S    0  0.3   0:12.54 applet.py                                                  
 2131 shoaibi   20   0 60720 3468 2652 S    0  0.0   0:00.03 gvfsd-trash                                                
 2148 shoaibi   20   0 14612  856  692 S    0  0.0   0:00.01 gnome-pty-helpe                                            
 2206 shoaibi   20   0  317m  15m  11m S    0  0.2   0:01.79 update-notifier                                            
 2227 shoaibi   20   0  486m  37m  22m S    0  0.5   0:08.30 gnote                                                      
 2237 shoaibi   20   0  234m  10m 3432 S    0  0.1   0:13.44 chrome                                                     
 2239 shoaibi   20   0  276m  15m 8124 S    0  0.2   0:00.29 chrome                                                     
 2260 shoaibi   20   0  852m  21m 9.9m S    0  0.3   0:03.31 chrome                                                     
 2264 shoaibi   20   0  855m  27m  14m S    0  0.4   0:15.17 chrome                                                     
 2266 shoaibi   20   0  852m  22m 9.9m S    0  0.3   0:11.95 chrome                                                     
 2268 shoaibi   20   0  854m  25m  12m S    0  0.3   0:14.13 chrome                                                     
 2274 shoaibi   20   0  869m  41m  15m S    0  0.5   4:17.38 chrome                                                     
 2280 shoaibi   20   0  880m  55m  17m S    0  0.7   1:52.09 chrome                                                     
 2284 shoaibi   20   0  859m  34m  16m S    0  0.4   1:20.57 chrome                                                     
 2286 shoaibi   20   0  870m  40m  13m S    0  0.5   1:13.75 chrome                                                     
 2289 shoaibi   20   0  854m  24m  11m S    0  0.3   0:14.48 chrome                                                     
 2292 shoaibi   20   0  854m  24m  10m S    0  0.3   0:13.77 chrome                                                     
 2299 shoaibi   20   0  852m  21m 9.9m S    0  0.3   0:03.68 chrome                                                     
 2301 shoaibi   20   0  852m  22m 9.8m S    0  0.3   0:22.27 chrome                                                     
 2304 shoaibi   20   0  854m  24m  11m S    0  0.3   0:13.02 chrome                                                     
 2307 shoaibi   20   0  854m  25m  11m S    0  0.3   0:18.73 chrome                                                     
 2311 shoaibi   20   0  853m  22m  10m S    0  0.3   0:03.42 chrome                                                     
 2313 shoaibi   20   0  880m  28m  12m S    0  0.4   0:19.94 chrome                                                     
 2316 shoaibi   20   0  853m  22m  10m S    0  0.3   0:03.51 chrome                                                     
 2319 shoaibi   20   0  853m  24m  11m S    0  0.3   0:14.41 chrome                                                     
 2323 shoaibi   20   0  856m  30m  13m S    0  0.4   0:26.73 chrome                                                     
 2326 shoaibi   20   0  856m  28m  12m S    0  0.4   0:24.61 chrome                                                     
 2329 shoaibi   20   0  856m  27m  13m S    0  0.4   0:05.87 chrome                                                     
 2424 shoaibi   25   5  890m  78m  17m S    0  1.0   0:54.39 chrome                                                     
 2454 shoaibi   20   0  274m  16m 9248 S    0  0.2   0:00.04 chrome                                                     
 2462 shoaibi   25   5  902m  75m  17m R    0  0.9   2:42.43 chrome                                                     
 2604 shoaibi   25   5  931m 117m  17m S    0  1.5   2:51.75 chrome                                                     
 2613 shoaibi   25   5  882m  66m  16m S    0  0.8   0:33.64 chrome                                                     
 2656 shoaibi   20   0  672m  44m  23m S    0  0.6   1:19.61 empathy                                                    
 2658 shoaibi   20   0 59508 5772 3616 S    0  0.1   0:03.56 mission-control                                            
 2665 shoaibi   20   0  159m 5064 4012 S    0  0.1   0:00.16 telepathy-logge                                            
 3188 shoaibi   20   0  549m  93m  29m S    0  1.2   0:25.07 unity-2d-spread                                            
 3193 shoaibi   20   0  542m  54m  25m S    0  0.7   0:11.16 unity-2d-places                                            
 3338 shoaibi   20   0 49728 2232 1812 S    0  0.0   0:00.02 gvfsd-metadata                                             
 5559 shoaibi   20   0 27908 5396 1704 S    0  0.1   0:00.40 bash                                                       
 7190 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                
 7192 root      20   0     0    0    0 S    0  0.0   0:00.27 ksoftirqd/1                                                
 7193 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                                                
 7195 root      20   0     0    0    0 S    0  0.0   0:00.15 ksoftirqd/2                                                
 7196 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                                                
 7198 root      20   0     0    0    0 S    0  0.0   0:00.13 ksoftirqd/3                                                
 7199 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/4                                                
 7201 root      20   0     0    0    0 S    0  0.0   0:00.15 ksoftirqd/4                                                
 7202 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/5                                                
 7204 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/5                                                
 7205 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/6                                                
 7206 root      20   0     0    0    0 S    0  0.0   0:01.99 kworker/6:3                                                
 7207 root      20   0     0    0    0 S    0  0.0   0:00.11 ksoftirqd/6                                                
 7210 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/7                                                
 7211 root      20   0     0    0    0 S    0  0.0   0:08.95 kworker/7:3                                                
 7212 root      20   0     0    0    0 S    0  0.0   0:00.29 ksoftirqd/7                                                
 7230 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:28                                               
 7231 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:29                                               
 7276 root       0 -20     0    0    0 S    0  0.0   0:00.00 hci0                                                       
 7295 root      18  -2 21736 1188  344 S    0  0.0   0:00.00 udevd                                                      
 7296 root      18  -2 21736 1116  276 S    0  0.0   0:00.00 udevd                                                      
 7305 root      20   0 23072 1988 1524 S    0  0.0   0:00.01 bluetoothd                                                 
 7317 root       0 -20     0    0    0 S    0  0.0   0:00.00 l2cap                                                      
 7342 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd                                                   
 7408 root      20   0     0    0    0 S    0  0.0   0:00.00 RtmpCmdQTask                                               
 8032 root      20   0  7084 1548 1060 S    0  0.0   0:00.03 dhclient                                                   
 8043 shoaibi   20   0  376m  28m  13m S    0  0.4   0:14.99 telepathy-gabbl                                            
 8047 shoaibi   20   0  214m  13m 8708 S    0  0.2   0:00.46 telepathy-haze                                             
 8185 shoaibi   20   0  133m  27m 5868 S    0  0.3   0:04.95 telepathy-butte                                            
 9466 root      20   0     0    0    0 S    0  0.0   0:04.44 kworker/5:3                                                
10004 root      20   0     0    0    0 S    0  0.0   0:03.92 kworker/3:3                                                
10062 shoaibi   20   0  240m  12m 9964 S    0  0.2   0:00.02 gvfsd-http                                                 
10243 root      20   0     0    0    0 S    0  0.0   0:08.29 kworker/1:1                                                
10330 shoaibi   20   0 19484 1448  968 S    0  0.0   1:34.61 top                                                        
10337 root      20   0     0    0    0 S    0  0.0   0:12.67 kworker/0:0                                                
10352 root      20   0     0    0    0 S    0  0.0   0:07.18 kworker/1:3                                                
10367 root      20   0     0    0    0 S    0  0.0   0:10.22 kworker/0:1                                                
10379 root      20   0     0    0    0 S    0  0.0   0:01.19 kworker/5:1                                                
10386 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/4:2                                                
10388 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:0                                                
10389 root      20   0     0    0    0 S    0  0.0   0:02.13 kworker/0:2                                                
10396 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/7:0                                                
10402 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:2                                                
10411 root      20   0     0    0    0 S    0  0.0   0:00.68 kworker/4:0                                                
10417 root      20   0     0    0    0 S    0  0.0   0:00.54 kworker/5:0                                                
10424 root      20   0     0    0    0 S    0  0.0   0:00.80 kworker/7:1                                                
10425 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/6:0                                                
10429 root      20   0     0    0    0 S    0  0.0   0:00.03 kworker/4:3                                                
10433 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:1                                                
10434 shoaibi   20   0 27952 5484 1744 S    0  0.1   0:09.00 bash                                                       
10532 shoaibi   20   0 16296 1620 1164 S    0  0.0   0:00.13 generate-system                                            
10533 root      20   0 25644 1324 1076 S    0  0.0   0:00.06 sudo                                                       


------
iotop

Total DISK READ: 0.00 B/s | Total DISK WRITE: 16.64 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN      IO    COMMAND
  296 be/3 root        0.00 B/s   14.26 K/s  0.00 %  0.17 % [jbd2/sda3-8]
  993 be/3 root        0.00 B/s    4.75 K/s  0.00 %  0.14 % [jbd2/sda5-8]
 8043 be/4 shoaibi     0.00 B/s    4.75 K/s  0.00 %  0.00 % telepathy-gabble

------
iostat

Linux 2.6.38-10-generic (abacus) 	06/11/2011 	_x86_64_	(8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.72    0.79    1.29    0.10    0.00   94.10

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               2.34     8.39    1.07    8.64    41.65    68.63    22.72     0.10   10.13   42.50    6.14   1.31   1.27



==========================================================================================================





Top:

top - 19:59:35 up  7:11,  3 users,  load average: 2.19, 1.49, 1.13
Tasks: 252 total,   4 running, 246 sleeping,   0 stopped,   2 zombie
Cpu(s):  3.8%us,  1.2%sy,  0.8%ni, 94.0%id,  0.1%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   8175328k total,  3625176k used,  4550152k free,   256992k buffers
Swap: 10485756k total,        0k used, 10485756k free,   967148k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                    
 2417 shoaibi   25   5  904m  77m  17m R   96  1.0   1:22.66 chrome                                                     
 2427 shoaibi   25   5  996m 181m  21m R   96  2.3   9:55.78 chrome                                                     
 2435 shoaibi   20   0  978m 162m  19m R   94  2.0   8:50.10 chrome                                                     
 2274 shoaibi   20   0  869m  46m  15m S   42  0.6   4:23.91 chrome                                                     
 1178 root      20   0  404m 113m  84m S   32  1.4  22:50.57 Xorg                                                       
10548 root      20   0 19480 1416  952 R   28  0.0   0:00.63 top                                                        
 2232 shoaibi   20   0  760m 133m  38m S   27  1.7  23:33.67 chrome                                                     
 1641 shoaibi   20   0  401m  17m  12m S   19  0.2   0:31.01 metacity                                                   
 2622 shoaibi   20   0  648m  55m  23m S   12  0.7  43:01.64 chrome                                                     
 2143 shoaibi   20   0  465m  41m  18m S    9  0.5   1:39.89 /usr/bin/termin                                            
 2610 shoaibi   20   0  895m  76m  18m S    8  1.0   4:38.09 chrome                                                     
 2462 shoaibi   20   0  905m  90m  21m S    7  1.1   2:50.74 chrome                                                     
 2421 shoaibi   25   5  910m  90m  17m S    3  1.1   4:09.25 chrome                                                     
 8241 shoaibi   20   0  288m  92m  21m S    3  1.2   3:59.32 skype                                                      
 9047 shoaibi   20   0  395m  37m  17m S    3  0.5   1:28.20 xchat                                                      
10367 root      20   0     0    0    0 S    3  0.0   0:10.99 kworker/0:1                                                
 1645 shoaibi   20   0  316m  12m 8636 S    1  0.2   1:39.13 diodon                                                     
 1696 shoaibi   20   0  612m  56m  19m S    1  0.7   0:22.55 dropbox                                                    
 1850 shoaibi   20   0 22740 1212  904 S    1  0.0   0:19.79 syndaemon                                                  
 2600 shoaibi   25   5  943m  96m  17m S    1  1.2   4:00.02 chrome                                                     
 9358 root      20   0     0    0    0 S    1  0.0   0:07.75 kworker/4:1                                                
 9777 root      20   0     0    0    0 S    1  0.0   0:08.78 kworker/6:1                                                
10352 root      20   0     0    0    0 S    1  0.0   0:07.43 kworker/1:3                                                
10379 root      20   0     0    0    0 S    1  0.0   0:01.42 kworker/5:1                                                
10433 root      20   0     0    0    0 S    1  0.0   0:00.32 kworker/2:1                                                
    1 root      20   0 24128 2280 1368 S    0  0.0   0:02.88 init                                                       
    2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd                                                   
    3 root      20   0     0    0    0 S    0  0.0   0:01.60 ksoftirqd/0                                                
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                     
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                    
   31 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                      
   33 root      20   0     0    0    0 S    0  0.0   0:00.13 sync_supers                                                
   34 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                
   35 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                
   36 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                    
   37 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpid                                                     
   38 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                               
   39 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                              
   40 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                    
   41 root      20   0     0    0    0 S    0  0.0   0:00.01 khubd                                                      
   42 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                         
   44 root      20   0     0    0    0 S    0  0.0   0:00.03 khungtaskd                                                 
   45 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                    
   46 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                       
   47 root      20   0     0    0    0 S    0  0.0   0:00.00 fsnotify_mark                                              
   48 root       0 -20     0    0    0 S    0  0.0   0:00.00 aio                                                        
   49 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                            
   50 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                     
   54 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                   
   56 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpathd                                                    
   57 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd                                            
   58 root       0 -20     0    0    0 S    0  0.0   0:00.00 kondemand                                                  
   59 root       0 -20     0    0    0 S    0  0.0   0:00.00 kconservative                                              
  182 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                  
  183 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                  
  184 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                  
  185 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                  
  186 root      20   0     0    0    0 S    0  0.0   0:02.32 scsi_eh_4                                                  
  187 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                  
  217 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_6                                                  
  218 root      20   0     0    0    0 S    0  0.0   0:14.91 usb-storage                                                
  235 root      20   0  7200  252  144 S    0  0.0   0:01.02 v86d                                                       
  296 root      20   0     0    0    0 S    0  0.0   0:00.64 jbd2/sda3-8                                                
  297 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
  349 root      20   0 17052  640  456 S    0  0.0   0:00.26 upstart-udev-br                                            
  525 root      20   0 22240 1084  592 S    0  0.0   0:00.09 mount.ntfs                                                 
  529 root      16  -4 21740 1192  352 S    0  0.0   0:00.18 udevd                                                      
  867 root      20   0 15004  388  196 S    0  0.0   0:00.02 upstart-socket-                                            
  870 root       0 -20     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                  
  894 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio0                                                  
  917 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio1                                                  
  948 root      20   0 22240 1128  592 S    0  0.0   0:00.08 mount.ntfs                                                 
  990 root      20   0 22452 1604  748 S    0  0.0   0:00.50 mount.ntfs                                                 
  993 root      20   0     0    0    0 S    0  0.0   0:04.36 jbd2/sda5-8                                                
  994 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
 1013 root      20   0 91592 4916 3748 S    0  0.1   0:00.01 smbd                                                       
 1019 root      20   0 49464 2752 2172 S    0  0.0   0:00.00 sshd                                                       
 1026 syslog    20   0  117m 1648 1112 S    0  0.0   0:01.87 rsyslogd                                                   
 1037 root      20   0 91592 1552  384 S    0  0.0   0:00.00 smbd                                                       
 1039 messageb  20   0 24764 2196  856 S    0  0.0   0:05.77 dbus-daemon                                                
 1049 root      20   0 83168 4016 3084 S    0  0.0   0:00.39 gdm-binary                                                 
 1053 avahi     20   0 32132 1704 1400 S    0  0.0   0:00.19 avahi-daemon                                               
 1054 avahi     20   0 32008  468  212 S    0  0.0   0:00.00 avahi-daemon                                               
 1055 root      20   0  154m 5104 3884 S    0  0.1   0:03.56 NetworkManager                                             
 1057 root      20   0  250m 4096 2756 S    0  0.1   0:00.62 console-kit-dae                                            
 1059 root      20   0 64656 2780 2152 S    0  0.0   0:00.05 modem-manager                                              
 1081 root      20   0  126m 4448 2852 S    0  0.1   0:01.49 polkitd                                                    
 1145 root      20   0 75512 3132 2324 S    0  0.0   0:00.03 cupsd                                                      
 1152 root      20   0 97752 4388 3312 S    0  0.1   0:00.01 gdm-simple-slav                                            
 1172 root      20   0 28812 2960 2448 S    0  0.0   0:02.11 wpa_supplicant                                             
 1229 root      20   0  6196  656  548 S    0  0.0   0:00.00 getty                                                      
 1233 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1240 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1241 root      20   0  6196  656  548 S    0  0.0   0:00.00 getty                                                      
 1244 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1252 root      20   0  4416  896  572 S    0  0.0   0:00.02 acpid                                                      
 1265 mysql     20   0  166m  23m 6692 S    0  0.3   0:11.98 mysqld                                                     
 1266 root      20   0 15780  672  500 S    0  0.0   0:11.51 irqbalance                                                 
 1272 root      20   0 18928 1056  816 S    0  0.0   0:00.10 cron                                                       
 1273 daemon    20   0 16728  376  220 S    0  0.0   0:00.00 atd                                                        
 1301 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1302 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1303 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1327 root      20   0     0    0    0 S    0  0.0   0:03.29 flush-8:0                                                  
 1504 root      20   0  6196  660  552 S    0  0.0   0:00.00 getty                                                      
 1557 root      20   0 99.4m 3808 2884 S    0  0.0   0:00.00 gdm-session-wor                                            
 1566 shoaibi   20   0  237m 8516 6328 S    0  0.1   0:00.55 gnome-session                                              
 1601 shoaibi   20   0 12092  288    0 S    0  0.0   0:00.14 ssh-agent                                                  
 1604 shoaibi   20   0 26400  620  352 S    0  0.0   0:00.00 dbus-launch                                                
 1605 shoaibi   20   0 28284 4440  664 S    0  0.1   0:54.84 dbus-daemon                                                
 1610 shoaibi   20   0 60956 5496 2576 S    0  0.1   0:03.01 gconfd-2                                                   
 1617 shoaibi   20   0  168m  10m 3120 S    0  0.1   0:00.39 gnome-keyring-d                                            
 1622 shoaibi   20   0  466m  19m  10m S    0  0.2   0:17.73 gnome-settings-                                            
 1625 shoaibi   20   0 55956 2468 2056 S    0  0.0   0:00.15 gvfsd                                                      
 1630 shoaibi   20   0 81008 2684 1816 S    0  0.0   0:00.00 gvfs-fuse-daemo                                            
 1636 shoaibi   20   0  294m 6704 3836 S    0  0.1   5:23.41 pulseaudio                                                 
 1638 rtkit     21   1  100m 1324 1080 S    0  0.0   0:00.52 rtkit-daemon                                               
 1643 shoaibi   20   0  650m  48m  31m S    0  0.6   0:41.01 nautilus                                                   
 1646 shoaibi   20   0  327m  11m 8288 S    0  0.1   0:00.16 bluetooth-apple                                            
 1648 shoaibi   20   0  217m 5856 4348 S    0  0.1   0:00.34 zeitgeist-datah                                            
 1649 shoaibi   20   0  676m  46m  27m S    0  0.6   1:05.10 unity-2d-launch                                            
 1650 shoaibi   20   0  633m  47m  25m S    0  0.6   1:32.11 unity-2d-panel                                             
 1651 shoaibi   20   0  389m  18m  13m S    0  0.2   0:04.18 nm-applet                                                  
 1655 shoaibi   20   0  226m 7272 5632 S    0  0.1   0:00.14 polkit-gnome-au                                            
 1657 shoaibi   20   0  470m  32m  19m S    0  0.4   0:03.55 synapse                                                    
 1658 shoaibi   20   0  370m  26m  12m S    0  0.3   0:00.27 touchpad-indica                                            
 1659 shoaibi   20   0  443m  35m  15m S    0  0.4   0:06.92 python                                                     
 1661 shoaibi   20   0  358m  10m 7752 S    0  0.1   0:03.45 gnome-power-man                                            
 1664 shoaibi   20   0  182m  20m 7364 S    0  0.3   0:01.44 zeitgeist-daemo                                            
 1692 shoaibi   20   0  310m  16m  11m S    0  0.2   0:36.35 notify-osd                                                 
 1693 shoaibi   20   0  177m 3944 3056 S    0  0.0   0:00.00 gconf-helper                                               
 1756 shoaibi   20   0 10848  588  492 S    0  0.0   0:00.00 cat                                                        
 1758 shoaibi   20   0 71904 3748 2908 S    0  0.0   0:00.11 gvfs-gdu-volume                                            
 1760 root      20   0  124m 4004 2960 S    0  0.0   0:00.59 udisks-daemon                                              
 1761 root      20   0 45168 1128  756 S    0  0.0   0:06.08 udisks-daemon                                              
 1764 root      20   0  139m 4424 3304 S    0  0.1   0:02.60 upowerd                                                    
 1826 shoaibi   20   0 77352 2628 2112 S    0  0.0   0:01.28 gvfs-afc-volume                                            
 1832 shoaibi   20   0 63556 2660 1920 S    0  0.0   0:00.00 gvfs-gphoto2-vo                                            
 1846 shoaibi   20   0  220m  10m 6696 S    0  0.1   0:21.09 bamfdaemon                                                 
 1847 shoaibi   20   0     0    0    0 Z    0  0.0   0:00.26 python <defunct>                                           
 1848 shoaibi   20   0     0    0    0 Z    0  0.0   0:00.01 zeitgeist-datah <defunct>                                  
 1902 shoaibi   20   0  183m 2696 2180 S    0  0.0   0:00.02 dconf-service                                              
 1925 shoaibi   20   0 56220 2784 2168 S    0  0.0   0:00.00 gvfsd-burn                                                 
 1952 shoaibi   20   0  234m 6044 4716 S    0  0.1   0:00.26 indicator-sessi                                            
 1954 shoaibi   20   0  202m 5236 3784 S    0  0.1   0:03.32 indicator-appli                                            
 1956 shoaibi   20   0  237m 5104 4024 S    0  0.1   0:00.03 indicator-messa                                            
 1965 shoaibi   20   0  307m 7828 6072 S    0  0.1   0:00.11 indicator-datet                                            
 1969 shoaibi   20   0  331m 6780 5152 S    0  0.1   0:01.19 indicator-sound                                            
 1988 shoaibi   20   0  155m 4796 3716 S    0  0.1   0:00.26 geoclue-master                                             
 2022 shoaibi   20   0  248m 9688 7404 S    0  0.1   0:09.97 gnome-screensav                                            
 2057 root      20   0 61652 1628  752 S    0  0.0   0:02.83 nmbd                                                       
 2072 shoaibi   20   0  175m 7480 5620 S    0  0.1   0:00.08 gdu-notificatio                                            
 2074 shoaibi   20   0  262m 7840 5236 S    0  0.1   0:01.73 unity-applicati                                            
 2076 shoaibi   20   0  176m 4592 3612 S    0  0.1   0:00.78 unity-files-dae                                            
 2124 shoaibi   20   0  232m  23m  10m S    0  0.3   0:12.82 applet.py                                                  
 2131 shoaibi   20   0 60720 3468 2652 S    0  0.0   0:00.03 gvfsd-trash                                                
 2148 shoaibi   20   0 14612  856  692 S    0  0.0   0:00.01 gnome-pty-helpe                                            
 2206 shoaibi   20   0  317m  15m  11m S    0  0.2   0:01.83 update-notifier                                            
 2227 shoaibi   20   0  486m  37m  22m S    0  0.5   0:08.38 gnote                                                      
 2237 shoaibi   20   0  234m  10m 3432 S    0  0.1   0:13.44 chrome                                                     
 2239 shoaibi   20   0  276m  15m 8124 S    0  0.2   0:00.29 chrome                                                     
 2260 shoaibi   20   0  852m  21m 9.9m S    0  0.3   0:03.51 chrome                                                     
 2264 shoaibi   20   0  855m  27m  14m S    0  0.4   0:15.19 chrome                                                     
 2266 shoaibi   20   0  852m  22m 9.9m S    0  0.3   0:11.98 chrome                                                     
 2268 shoaibi   20   0  854m  25m  12m S    0  0.3   0:14.50 chrome                                                     
 2271 shoaibi   20   0  855m  28m  12m S    0  0.4   0:28.54 chrome                                                     
 2277 shoaibi   20   0  872m  28m  12m S    0  0.4   0:30.35 chrome                                                     
 2280 shoaibi   20   0  880m  55m  17m S    0  0.7   1:54.97 chrome                                                     
 2284 shoaibi   20   0  859m  34m  16m S    0  0.4   1:20.94 chrome                                                     
 2286 shoaibi   20   0  870m  40m  13m S    0  0.5   1:16.75 chrome                                                     
 2289 shoaibi   20   0  854m  24m  11m S    0  0.3   0:14.50 chrome                                                     
 2292 shoaibi   20   0  854m  24m  10m S    0  0.3   0:13.80 chrome                                                     
 2295 shoaibi   20   0  852m  21m 9976 S    0  0.3   0:03.70 chrome                                                     
 2299 shoaibi   20   0  852m  21m 9.9m S    0  0.3   0:03.70 chrome                                                     
 2301 shoaibi   20   0  852m  22m 9.8m S    0  0.3   0:22.29 chrome                                                     
 2304 shoaibi   20   0  854m  24m  11m S    0  0.3   0:13.04 chrome                                                     
 2307 shoaibi   20   0  854m  25m  11m S    0  0.3   0:18.75 chrome                                                     
 2311 shoaibi   20   0  853m  22m  10m S    0  0.3   0:03.61 chrome                                                     
 2313 shoaibi   20   0  880m  28m  12m S    0  0.4   0:19.97 chrome                                                     
 2316 shoaibi   20   0  853m  22m  10m S    0  0.3   0:03.74 chrome                                                     
 2319 shoaibi   20   0  853m  24m  11m S    0  0.3   0:14.77 chrome                                                     
 2323 shoaibi   20   0  856m  30m  13m S    0  0.4   0:27.36 chrome                                                     
 2326 shoaibi   20   0  856m  28m  12m S    0  0.4   0:24.83 chrome                                                     
 2329 shoaibi   20   0  856m  27m  13m S    0  0.4   0:06.13 chrome                                                     
 2424 shoaibi   25   5  890m  78m  17m S    0  1.0   0:54.76 chrome                                                     
 2454 shoaibi   20   0  274m  16m 9248 S    0  0.2   0:00.04 chrome                                                     
 2597 shoaibi   25   5  901m  75m  18m S    0  0.9   2:05.69 chrome                                                     
 2604 shoaibi   25   5  931m 116m  17m S    0  1.5   2:59.12 chrome                                                     
 2613 shoaibi   25   5  882m  66m  16m S    0  0.8   0:37.54 chrome                                                     
 2656 shoaibi   20   0  672m  44m  23m S    0  0.6   1:21.27 empathy                                                    
 2658 shoaibi   20   0 59508 5772 3616 S    0  0.1   0:03.62 mission-control                                            
 2665 shoaibi   20   0  159m 5064 4012 S    0  0.1   0:00.16 telepathy-logge                                            
 3188 shoaibi   20   0  549m  93m  29m S    0  1.2   0:25.43 unity-2d-spread                                            
 3193 shoaibi   20   0  542m  54m  25m S    0  0.7   0:11.50 unity-2d-places                                            
 3338 shoaibi   20   0 49728 2232 1812 S    0  0.0   0:00.02 gvfsd-metadata                                             
 5559 shoaibi   20   0 27908 5396 1704 S    0  0.1   0:00.40 bash                                                       
 7190 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                
 7192 root      20   0     0    0    0 S    0  0.0   0:00.28 ksoftirqd/1                                                
 7193 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                                                
 7194 root      20   0     0    0    0 S    0  0.0   0:11.38 kworker/2:3                                                
 7195 root      20   0     0    0    0 S    0  0.0   0:00.15 ksoftirqd/2                                                
 7196 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                                                
 7198 root      20   0     0    0    0 S    0  0.0   0:00.14 ksoftirqd/3                                                
 7199 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/4                                                
 7201 root      20   0     0    0    0 S    0  0.0   0:00.16 ksoftirqd/4                                                
 7202 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/5                                                
 7204 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/5                                                
 7205 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/6                                                
 7206 root      20   0     0    0    0 S    0  0.0   0:01.99 kworker/6:3                                                
 7207 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/6                                                
 7210 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/7                                                
 7211 root      20   0     0    0    0 S    0  0.0   0:08.95 kworker/7:3                                                
 7212 root      20   0     0    0    0 S    0  0.0   0:00.29 ksoftirqd/7                                                
 7230 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:28                                               
 7231 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:29                                               
 7276 root       0 -20     0    0    0 S    0  0.0   0:00.00 hci0                                                       
 7295 root      18  -2 21736 1188  344 S    0  0.0   0:00.00 udevd                                                      
 7296 root      18  -2 21736 1116  276 S    0  0.0   0:00.00 udevd                                                      
 7305 root      20   0 23072 1988 1524 S    0  0.0   0:00.01 bluetoothd                                                 
 7317 root       0 -20     0    0    0 S    0  0.0   0:00.00 l2cap                                                      
 7342 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd                                                   
 7408 root      20   0     0    0    0 S    0  0.0   0:00.00 RtmpCmdQTask                                               
 7899 root      20   0     0    0    0 S    0  0.0   0:07.30 kworker/3:1                                                
 8032 root      20   0  7084 1548 1060 S    0  0.0   0:00.03 dhclient                                                   
 8043 shoaibi   20   0  376m  28m  13m S    0  0.4   0:15.38 telepathy-gabbl                                            
 8047 shoaibi   20   0  214m  13m 8708 S    0  0.2   0:00.46 telepathy-haze                                             
 8185 shoaibi   20   0  133m  27m 5868 S    0  0.3   0:05.10 telepathy-butte                                            
 9466 root      20   0     0    0    0 S    0  0.0   0:04.44 kworker/5:3                                                
10004 root      20   0     0    0    0 S    0  0.0   0:03.92 kworker/3:3                                                
10062 shoaibi   20   0  240m  12m 9964 S    0  0.2   0:00.02 gvfsd-http                                                 
10243 root      20   0     0    0    0 S    0  0.0   0:08.29 kworker/1:1                                                
10330 shoaibi   20   0 19484 1448  968 S    0  0.0   1:37.15 top                                                        
10337 root      20   0     0    0    0 S    0  0.0   0:12.67 kworker/0:0                                                
10386 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/4:2                                                
10388 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:0                                                
10389 root      20   0     0    0    0 S    0  0.0   0:02.13 kworker/0:2                                                
10396 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/7:0                                                
10402 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:2                                                
10411 root      20   0     0    0    0 S    0  0.0   0:00.68 kworker/4:0                                                
10417 root      20   0     0    0    0 S    0  0.0   0:00.54 kworker/5:0                                                
10424 root      20   0     0    0    0 S    0  0.0   0:01.13 kworker/7:1                                                
10425 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/6:0                                                
10429 root      20   0     0    0    0 S    0  0.0   0:00.03 kworker/4:3                                                
10430 root      20   0     0    0    0 S    0  0.0   0:01.34 kworker/5:2                                                
10431 root      20   0     0    0    0 S    0  0.0   0:01.37 kworker/1:0                                                
10432 root      20   0     0    0    0 S    0  0.0   0:01.39 kworker/0:3                                                
10434 shoaibi   20   0 27952 5484 1744 S    0  0.1   0:09.03 bash                                                       
10541 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/3:0                                                
10543 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:2                                                
10546 shoaibi   20   0 16296 1616 1160 S    0  0.0   0:00.15 generate-system                                            
10547 root      20   0 25644 1320 1076 S    0  0.0   0:00.06 sudo                                                       


------
iotop

Total DISK READ: 0.00 B/s | Total DISK WRITE: 0.00 B/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN      IO    COMMAND
  993 be/3 root        0.00 B/s    4.83 K/s  0.00 %  0.25 % [jbd2/sda5-8]
 2248 be/4 shoaibi     0.00 B/s    7.25 K/s  0.00 %  0.00 % chrome

------
iostat

Linux 2.6.38-10-generic (abacus) 	06/11/2011 	_x86_64_	(8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.76    0.81    1.31    0.10    0.00   94.03

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               2.33     8.39    1.07    8.65    41.60    68.62    22.70     0.10   10.12   42.50    6.13   1.30   1.27



==========================================================================================================





Top:

top - 19:59:44 up  7:11,  3 users,  load average: 2.23, 1.53, 1.15
Tasks: 252 total,   6 running, 244 sleeping,   0 stopped,   2 zombie
Cpu(s):  3.8%us,  1.2%sy,  0.8%ni, 94.0%id,  0.1%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   8175328k total,  3616272k used,  4559056k free,   257004k buffers
Swap: 10485756k total,        0k used, 10485756k free,   963536k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                    
 2604 shoaibi   25   5  931m 117m  17m R   95  1.5   3:01.95 chrome                                                     
 2435 shoaibi   20   0  978m 163m  19m R   65  2.0   8:57.79 chrome                                                     
 2427 shoaibi   25   5  996m 180m  21m S   58  2.3  10:01.00 chrome                                                     
 1178 root      20   0  401m 110m  81m R   39  1.4  22:53.88 Xorg                                                       
 2232 shoaibi   20   0  756m 133m  38m S   35  1.7  23:35.56 chrome                                                     
10559 root      20   0 19480 1416  952 R   28  0.0   0:00.59 top                                                        
 8241 shoaibi   20   0  288m  92m  21m S   22  1.2   3:59.93 skype                                                      
 2143 shoaibi   20   0  465m  41m  18m S   20  0.5   1:41.70 /usr/bin/termin                                            
 1650 shoaibi   20   0  633m  47m  25m R   18  0.6   1:32.34 unity-2d-panel                                             
 2622 shoaibi   20   0  648m  55m  23m S   14  0.7  43:02.98 chrome                                                     
 2462 shoaibi   20   0  902m  86m  17m S   12  1.1   2:51.86 chrome                                                     
 2610 shoaibi   20   0  895m  76m  18m S    9  1.0   4:39.33 chrome                                                     
 9047 shoaibi   20   0  395m  37m  17m S    9  0.5   1:28.63 xchat                                                      
 1605 shoaibi   20   0 28284 4440  664 S    7  0.1   0:55.04 dbus-daemon                                                
 2421 shoaibi   25   5  910m  90m  17m S    5  1.1   4:09.47 chrome                                                     
 2600 shoaibi   25   5  943m  96m  17m S    5  1.2   4:00.25 chrome                                                     
 1641 shoaibi   20   0  401m  17m  12m S    4  0.2   0:31.29 metacity                                                   
 1645 shoaibi   20   0  316m  12m 8636 R    4  0.2   1:39.37 diodon                                                     
 1649 shoaibi   20   0  676m  46m  27m S    3  0.6   1:05.15 unity-2d-launch                                            
 1846 shoaibi   20   0  220m  10m 6696 S    3  0.1   0:21.18 bamfdaemon                                                 
 3188 shoaibi   20   0  549m  93m  29m S    3  1.2   0:25.47 unity-2d-spread                                            
 3193 shoaibi   20   0  542m  54m  25m S    3  0.7   0:11.54 unity-2d-places                                            
10424 root      20   0     0    0    0 S    3  0.0   0:01.27 kworker/7:1                                                
  218 root      20   0     0    0    0 S    1  0.0   0:14.93 usb-storage                                                
 1265 mysql     20   0  166m  23m 6692 S    1  0.3   0:12.02 mysqld                                                     
 1643 shoaibi   20   0  650m  48m  31m S    1  0.6   0:41.06 nautilus                                                   
 1657 shoaibi   20   0  470m  32m  19m S    1  0.4   0:03.56 synapse                                                    
 1692 shoaibi   20   0  310m  16m  11m S    1  0.2   0:36.40 notify-osd                                                 
 1850 shoaibi   20   0 22740 1212  904 S    1  0.0   0:19.83 syndaemon                                                  
 2206 shoaibi   20   0  317m  15m  11m S    1  0.2   0:01.84 update-notifier                                            
 2656 shoaibi   20   0  672m  44m  23m S    1  0.6   1:21.28 empathy                                                    
 9358 root      20   0     0    0    0 S    1  0.0   0:07.87 kworker/4:1                                                
 9777 root      20   0     0    0    0 S    1  0.0   0:08.91 kworker/6:1                                                
10367 root      20   0     0    0    0 S    1  0.0   0:11.14 kworker/0:1                                                
10379 root      20   0     0    0    0 S    1  0.0   0:01.57 kworker/5:1                                                
10431 root      20   0     0    0    0 S    1  0.0   0:01.48 kworker/1:0                                                
10432 root      20   0     0    0    0 S    1  0.0   0:01.51 kworker/0:3                                                
10433 root      20   0     0    0    0 S    1  0.0   0:00.48 kworker/2:1                                                
    1 root      20   0 24128 2280 1368 S    0  0.0   0:02.88 init                                                       
    2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd                                                   
    3 root      20   0     0    0    0 S    0  0.0   0:01.60 ksoftirqd/0                                                
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                     
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                    
   31 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                      
   33 root      20   0     0    0    0 S    0  0.0   0:00.13 sync_supers                                                
   34 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                
   35 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                
   36 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                    
   37 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpid                                                     
   38 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                               
   39 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                              
   40 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                    
   41 root      20   0     0    0    0 S    0  0.0   0:00.01 khubd                                                      
   42 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                         
   44 root      20   0     0    0    0 S    0  0.0   0:00.03 khungtaskd                                                 
   45 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                    
   46 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                       
   47 root      20   0     0    0    0 S    0  0.0   0:00.00 fsnotify_mark                                              
   48 root       0 -20     0    0    0 S    0  0.0   0:00.00 aio                                                        
   49 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                            
   50 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                     
   54 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                   
   56 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpathd                                                    
   57 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd                                            
   58 root       0 -20     0    0    0 S    0  0.0   0:00.00 kondemand                                                  
   59 root       0 -20     0    0    0 S    0  0.0   0:00.00 kconservative                                              
  182 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                  
  183 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                  
  184 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                  
  185 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                  
  186 root      20   0     0    0    0 S    0  0.0   0:02.32 scsi_eh_4                                                  
  187 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                  
  217 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_6                                                  
  235 root      20   0  7200  252  144 S    0  0.0   0:01.02 v86d                                                       
  296 root      20   0     0    0    0 S    0  0.0   0:00.64 jbd2/sda3-8                                                
  297 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
  349 root      20   0 17052  640  456 S    0  0.0   0:00.26 upstart-udev-br                                            
  525 root      20   0 22240 1084  592 S    0  0.0   0:00.09 mount.ntfs                                                 
  529 root      16  -4 21740 1192  352 S    0  0.0   0:00.18 udevd                                                      
  867 root      20   0 15004  388  196 S    0  0.0   0:00.02 upstart-socket-                                            
  870 root       0 -20     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                  
  894 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio0                                                  
  917 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio1                                                  
  948 root      20   0 22240 1128  592 S    0  0.0   0:00.08 mount.ntfs                                                 
  990 root      20   0 22452 1604  748 S    0  0.0   0:00.50 mount.ntfs                                                 
  993 root      20   0     0    0    0 S    0  0.0   0:04.36 jbd2/sda5-8                                                
  994 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
 1013 root      20   0 91592 4916 3748 S    0  0.1   0:00.01 smbd                                                       
 1019 root      20   0 49464 2752 2172 S    0  0.0   0:00.00 sshd                                                       
 1026 syslog    20   0  117m 1648 1112 S    0  0.0   0:01.87 rsyslogd                                                   
 1037 root      20   0 91592 1552  384 S    0  0.0   0:00.00 smbd                                                       
 1039 messageb  20   0 24764 2196  856 S    0  0.0   0:05.77 dbus-daemon                                                
 1049 root      20   0 83168 4016 3084 S    0  0.0   0:00.39 gdm-binary                                                 
 1053 avahi     20   0 32132 1704 1400 S    0  0.0   0:00.19 avahi-daemon                                               
 1054 avahi     20   0 32008  468  212 S    0  0.0   0:00.00 avahi-daemon                                               
 1055 root      20   0  154m 5104 3884 S    0  0.1   0:03.57 NetworkManager                                             
 1057 root      20   0  250m 4096 2756 S    0  0.1   0:00.62 console-kit-dae                                            
 1059 root      20   0 64656 2780 2152 S    0  0.0   0:00.05 modem-manager                                              
 1081 root      20   0  126m 4448 2852 S    0  0.1   0:01.49 polkitd                                                    
 1145 root      20   0 75512 3132 2324 S    0  0.0   0:00.03 cupsd                                                      
 1152 root      20   0 97752 4388 3312 S    0  0.1   0:00.01 gdm-simple-slav                                            
 1172 root      20   0 28812 2960 2448 S    0  0.0   0:02.11 wpa_supplicant                                             
 1229 root      20   0  6196  656  548 S    0  0.0   0:00.00 getty                                                      
 1233 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1240 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1241 root      20   0  6196  656  548 S    0  0.0   0:00.00 getty                                                      
 1244 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1252 root      20   0  4416  896  572 S    0  0.0   0:00.02 acpid                                                      
 1266 root      20   0 15780  672  500 S    0  0.0   0:11.55 irqbalance                                                 
 1272 root      20   0 18928 1056  816 S    0  0.0   0:00.10 cron                                                       
 1273 daemon    20   0 16728  376  220 S    0  0.0   0:00.00 atd                                                        
 1301 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1302 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1303 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1327 root      20   0     0    0    0 S    0  0.0   0:03.30 flush-8:0                                                  
 1504 root      20   0  6196  660  552 S    0  0.0   0:00.00 getty                                                      
 1557 root      20   0 99.4m 3808 2884 S    0  0.0   0:00.00 gdm-session-wor                                            
 1566 shoaibi   20   0  237m 8516 6328 S    0  0.1   0:00.55 gnome-session                                              
 1601 shoaibi   20   0 12092  288    0 S    0  0.0   0:00.15 ssh-agent                                                  
 1604 shoaibi   20   0 26400  620  352 S    0  0.0   0:00.00 dbus-launch                                                
 1610 shoaibi   20   0 60956 5496 2576 S    0  0.1   0:03.02 gconfd-2                                                   
 1617 shoaibi   20   0  168m  10m 3120 S    0  0.1   0:00.39 gnome-keyring-d                                            
 1622 shoaibi   20   0  466m  19m  10m S    0  0.2   0:17.75 gnome-settings-                                            
 1625 shoaibi   20   0 55956 2468 2056 S    0  0.0   0:00.15 gvfsd                                                      
 1630 shoaibi   20   0 81008 2684 1816 S    0  0.0   0:00.00 gvfs-fuse-daemo                                            
 1636 shoaibi   20   0  294m 6704 3836 S    0  0.1   5:23.41 pulseaudio                                                 
 1638 rtkit     21   1  100m 1324 1080 S    0  0.0   0:00.52 rtkit-daemon                                               
 1646 shoaibi   20   0  327m  11m 8288 S    0  0.1   0:00.16 bluetooth-apple                                            
 1648 shoaibi   20   0  217m 5856 4348 S    0  0.1   0:00.34 zeitgeist-datah                                            
 1651 shoaibi   20   0  389m  18m  13m S    0  0.2   0:04.18 nm-applet                                                  
 1655 shoaibi   20   0  226m 7272 5632 S    0  0.1   0:00.14 polkit-gnome-au                                            
 1658 shoaibi   20   0  370m  26m  12m S    0  0.3   0:00.27 touchpad-indica                                            
 1659 shoaibi   20   0  443m  35m  15m S    0  0.4   0:06.92 python                                                     
 1661 shoaibi   20   0  358m  10m 7752 S    0  0.1   0:03.45 gnome-power-man                                            
 1664 shoaibi   20   0  182m  20m 7364 S    0  0.3   0:01.44 zeitgeist-daemo                                            
 1693 shoaibi   20   0  177m 3944 3056 S    0  0.0   0:00.00 gconf-helper                                               
 1696 shoaibi   20   0  612m  56m  19m S    0  0.7   0:22.63 dropbox                                                    
 1756 shoaibi   20   0 10848  588  492 S    0  0.0   0:00.00 cat                                                        
 1758 shoaibi   20   0 71904 3748 2908 S    0  0.0   0:00.11 gvfs-gdu-volume                                            
 1760 root      20   0  124m 4004 2960 S    0  0.0   0:00.59 udisks-daemon                                              
 1761 root      20   0 45168 1128  756 S    0  0.0   0:06.09 udisks-daemon                                              
 1764 root      20   0  139m 4424 3304 S    0  0.1   0:02.60 upowerd                                                    
 1826 shoaibi   20   0 77352 2628 2112 S    0  0.0   0:01.29 gvfs-afc-volume                                            
 1832 shoaibi   20   0 63556 2660 1920 S    0  0.0   0:00.00 gvfs-gphoto2-vo                                            
 1847 shoaibi   20   0     0    0    0 Z    0  0.0   0:00.26 python <defunct>                                           
 1848 shoaibi   20   0     0    0    0 Z    0  0.0   0:00.01 zeitgeist-datah <defunct>                                  
 1902 shoaibi   20   0  183m 2696 2180 S    0  0.0   0:00.02 dconf-service                                              
 1925 shoaibi   20   0 56220 2784 2168 S    0  0.0   0:00.00 gvfsd-burn                                                 
 1952 shoaibi   20   0  234m 6044 4716 S    0  0.1   0:00.26 indicator-sessi                                            
 1954 shoaibi   20   0  202m 5236 3784 S    0  0.1   0:03.32 indicator-appli                                            
 1956 shoaibi   20   0  237m 5104 4024 S    0  0.1   0:00.03 indicator-messa                                            
 1965 shoaibi   20   0  307m 7828 6072 S    0  0.1   0:00.11 indicator-datet                                            
 1969 shoaibi   20   0  331m 6780 5152 S    0  0.1   0:01.19 indicator-sound                                            
 1988 shoaibi   20   0  155m 4796 3716 S    0  0.1   0:00.26 geoclue-master                                             
 2022 shoaibi   20   0  248m 9688 7404 S    0  0.1   0:09.97 gnome-screensav                                            
 2057 root      20   0 61652 1628  752 S    0  0.0   0:02.84 nmbd                                                       
 2072 shoaibi   20   0  175m 7480 5620 S    0  0.1   0:00.08 gdu-notificatio                                            
 2074 shoaibi   20   0  262m 7840 5236 S    0  0.1   0:01.74 unity-applicati                                            
 2076 shoaibi   20   0  176m 4592 3612 S    0  0.1   0:00.78 unity-files-dae                                            
 2124 shoaibi   20   0  232m  23m  10m S    0  0.3   0:12.82 applet.py                                                  
 2131 shoaibi   20   0 60720 3468 2652 S    0  0.0   0:00.03 gvfsd-trash                                                
 2148 shoaibi   20   0 14612  856  692 S    0  0.0   0:00.01 gnome-pty-helpe                                            
 2227 shoaibi   20   0  486m  37m  22m S    0  0.5   0:08.38 gnote                                                      
 2237 shoaibi   20   0  234m  10m 3432 S    0  0.1   0:13.44 chrome                                                     
 2239 shoaibi   20   0  276m  15m 8124 S    0  0.2   0:00.29 chrome                                                     
 2260 shoaibi   20   0  852m  21m 9.9m S    0  0.3   0:03.51 chrome                                                     
 2264 shoaibi   20   0  855m  27m  14m S    0  0.4   0:15.20 chrome                                                     
 2266 shoaibi   20   0  852m  22m 9.9m S    0  0.3   0:11.98 chrome                                                     
 2268 shoaibi   20   0  854m  25m  12m S    0  0.3   0:14.50 chrome                                                     
 2271 shoaibi   20   0  855m  28m  12m S    0  0.4   0:28.56 chrome                                                     
 2274 shoaibi   20   0  869m  43m  15m S    0  0.5   4:26.65 chrome                                                     
 2277 shoaibi   20   0  872m  28m  12m S    0  0.4   0:30.35 chrome                                                     
 2280 shoaibi   20   0  880m  55m  17m S    0  0.7   1:54.97 chrome                                                     
 2284 shoaibi   20   0  859m  34m  16m S    0  0.4   1:21.11 chrome                                                     
 2286 shoaibi   20   0  870m  40m  13m S    0  0.5   1:16.76 chrome                                                     
 2289 shoaibi   20   0  854m  24m  11m S    0  0.3   0:14.51 chrome                                                     
 2292 shoaibi   20   0  854m  24m  10m S    0  0.3   0:13.80 chrome                                                     
 2295 shoaibi   20   0  852m  21m 9976 S    0  0.3   0:03.70 chrome                                                     
 2299 shoaibi   20   0  852m  21m 9.9m S    0  0.3   0:03.70 chrome                                                     
 2301 shoaibi   20   0  852m  22m 9.8m S    0  0.3   0:22.36 chrome                                                     
 2304 shoaibi   20   0  854m  24m  11m S    0  0.3   0:13.12 chrome                                                     
 2307 shoaibi   20   0  854m  25m  11m S    0  0.3   0:18.75 chrome                                                     
 2311 shoaibi   20   0  853m  22m  10m S    0  0.3   0:03.61 chrome                                                     
 2313 shoaibi   20   0  880m  28m  12m S    0  0.4   0:19.98 chrome                                                     
 2316 shoaibi   20   0  853m  22m  10m S    0  0.3   0:03.74 chrome                                                     
 2319 shoaibi   20   0  853m  24m  11m S    0  0.3   0:14.77 chrome                                                     
 2323 shoaibi   20   0  856m  30m  13m S    0  0.4   0:27.36 chrome                                                     
 2326 shoaibi   20   0  856m  28m  12m S    0  0.4   0:24.83 chrome                                                     
 2329 shoaibi   20   0  856m  27m  13m S    0  0.4   0:06.13 chrome                                                     
 2417 shoaibi   25   5  904m  77m  17m S    0  1.0   1:22.89 chrome                                                     
 2424 shoaibi   25   5  890m  78m  17m S    0  1.0   0:58.12 chrome                                                     
 2454 shoaibi   20   0  274m  16m 9248 S    0  0.2   0:00.04 chrome                                                     
 2597 shoaibi   25   5  901m  75m  18m S    0  1.0   2:08.54 chrome                                                     
 2613 shoaibi   25   5  882m  66m  16m S    0  0.8   0:37.55 chrome                                                     
 2658 shoaibi   20   0 59508 5772 3616 S    0  0.1   0:03.62 mission-control                                            
 2665 shoaibi   20   0  159m 5064 4012 S    0  0.1   0:00.16 telepathy-logge                                            
 3338 shoaibi   20   0 49728 2232 1812 S    0  0.0   0:00.02 gvfsd-metadata                                             
 5559 shoaibi   20   0 27908 5396 1704 S    0  0.1   0:00.40 bash                                                       
 7190 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                
 7192 root      20   0     0    0    0 S    0  0.0   0:00.28 ksoftirqd/1                                                
 7193 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                                                
 7194 root      20   0     0    0    0 S    0  0.0   0:11.38 kworker/2:3                                                
 7195 root      20   0     0    0    0 S    0  0.0   0:00.16 ksoftirqd/2                                                
 7196 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                                                
 7198 root      20   0     0    0    0 S    0  0.0   0:00.14 ksoftirqd/3                                                
 7199 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/4                                                
 7201 root      20   0     0    0    0 S    0  0.0   0:00.16 ksoftirqd/4                                                
 7202 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/5                                                
 7204 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/5                                                
 7205 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/6                                                
 7206 root      20   0     0    0    0 S    0  0.0   0:01.99 kworker/6:3                                                
 7207 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/6                                                
 7210 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/7                                                
 7211 root      20   0     0    0    0 S    0  0.0   0:08.95 kworker/7:3                                                
 7212 root      20   0     0    0    0 S    0  0.0   0:00.29 ksoftirqd/7                                                
 7230 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:28                                               
 7231 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:29                                               
 7276 root       0 -20     0    0    0 S    0  0.0   0:00.00 hci0                                                       
 7295 root      18  -2 21736 1188  344 S    0  0.0   0:00.00 udevd                                                      
 7296 root      18  -2 21736 1116  276 S    0  0.0   0:00.00 udevd                                                      
 7305 root      20   0 23072 1988 1524 S    0  0.0   0:00.01 bluetoothd                                                 
 7317 root       0 -20     0    0    0 S    0  0.0   0:00.00 l2cap                                                      
 7342 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd                                                   
 7408 root      20   0     0    0    0 S    0  0.0   0:00.00 RtmpCmdQTask                                               
 7899 root      20   0     0    0    0 S    0  0.0   0:07.47 kworker/3:1                                                
 8032 root      20   0  7084 1548 1060 S    0  0.0   0:00.03 dhclient                                                   
 8043 shoaibi   20   0  376m  28m  13m S    0  0.4   0:15.38 telepathy-gabbl                                            
 8047 shoaibi   20   0  214m  13m 8708 S    0  0.2   0:00.46 telepathy-haze                                             
 8185 shoaibi   20   0  133m  27m 5868 S    0  0.3   0:05.10 telepathy-butte                                            
 9466 root      20   0     0    0    0 S    0  0.0   0:04.44 kworker/5:3                                                
10004 root      20   0     0    0    0 S    0  0.0   0:03.92 kworker/3:3                                                
10062 shoaibi   20   0  240m  12m 9964 S    0  0.2   0:00.02 gvfsd-http                                                 
10243 root      20   0     0    0    0 S    0  0.0   0:08.29 kworker/1:1                                                
10330 shoaibi   20   0 19484 1448  968 S    0  0.0   1:37.93 top                                                        
10337 root      20   0     0    0    0 S    0  0.0   0:12.67 kworker/0:0                                                
10352 root      20   0     0    0    0 S    0  0.0   0:07.44 kworker/1:3                                                
10386 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/4:2                                                
10388 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:0                                                
10389 root      20   0     0    0    0 S    0  0.0   0:02.13 kworker/0:2                                                
10396 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/7:0                                                
10402 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:2                                                
10411 root      20   0     0    0    0 S    0  0.0   0:00.68 kworker/4:0                                                
10417 root      20   0     0    0    0 S    0  0.0   0:00.54 kworker/5:0                                                
10425 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/6:0                                                
10429 root      20   0     0    0    0 S    0  0.0   0:00.03 kworker/4:3                                                
10430 root      20   0     0    0    0 S    0  0.0   0:01.34 kworker/5:2                                                
10434 shoaibi   20   0 27952 5484 1744 S    0  0.1   0:09.07 bash                                                       
10541 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/3:0                                                
10543 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:2                                                
10557 shoaibi   20   0 16296 1620 1164 S    0  0.0   0:00.13 generate-system                                            
10558 root      20   0 25644 1324 1076 S    0  0.0   0:00.06 sudo                                                       


------
iotop

Total DISK READ: 0.00 B/s | Total DISK WRITE: 0.00 B/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN      IO    COMMAND

------
iostat

Linux 2.6.38-10-generic (abacus) 	06/11/2011 	_x86_64_	(8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.77    0.82    1.31    0.10    0.00   94.01

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               2.33     8.38    1.06    8.65    41.59    68.61    22.70     0.10   10.12   42.50    6.13   1.30   1.27



==========================================================================================================





Top:

top - 20:00:14 up  7:12,  3 users,  load average: 2.64, 1.70, 1.22
Tasks: 252 total,   2 running, 248 sleeping,   0 stopped,   2 zombie
Cpu(s):  3.8%us,  1.2%sy,  0.8%ni, 94.0%id,  0.1%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   8175328k total,  3614536k used,  4560792k free,   257080k buffers
Swap: 10485756k total,        0k used, 10485756k free,   963572k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                    
 2597 shoaibi   25   5  901m  75m  18m S   87  1.0   2:11.97 chrome                                                     
 2435 shoaibi   20   0  978m 162m  19m S   57  2.0   9:09.02 chrome                                                     
 2143 shoaibi   20   0  465m  41m  18m R   52  0.5   1:46.50 /usr/bin/termin                                            
10570 root      20   0 19480 1412  952 R   29  0.0   0:00.64 top                                                        
 1178 root      20   0  401m 110m  81m S   26  1.4  23:04.89 Xorg                                                       
 2462 shoaibi   20   0  902m  86m  17m S   17  1.1   2:56.30 chrome                                                     
 2622 shoaibi   20   0  648m  55m  23m S   12  0.7  43:07.55 chrome                                                     
 1696 shoaibi   20   0  612m  56m  19m S    8  0.7   0:22.78 dropbox                                                    
 2232 shoaibi   20   0  756m 133m  38m S    8  1.7  23:38.09 chrome                                                     
 2427 shoaibi   25   5  996m 180m  21m S    8  2.3  10:16.44 chrome                                                     
 2610 shoaibi   20   0  895m  76m  18m S    8  1.0   4:42.84 chrome                                                     
 1605 shoaibi   20   0 28284 4440  664 S    7  0.1   0:55.57 dbus-daemon                                                
 8241 shoaibi   20   0  288m  92m  21m S    4  1.2   4:01.27 skype                                                      
 1645 shoaibi   20   0  316m  12m 8636 S    3  0.2   1:40.18 diodon                                                     
 1650 shoaibi   20   0  633m  47m  25m S    3  0.6   1:33.19 unity-2d-panel                                             
 1846 shoaibi   20   0  220m  10m 6696 S    3  0.1   0:21.40 bamfdaemon                                                 
 2421 shoaibi   25   5  910m  90m  17m S    3  1.1   4:14.97 chrome                                                     
 9047 shoaibi   20   0  395m  37m  17m S    3  0.5   1:29.63 xchat                                                      
10432 root      20   0     0    0    0 S    3  0.0   0:01.80 kworker/0:3                                                
 1265 mysql     20   0  166m  23m 6692 S    1  0.3   0:12.12 mysqld                                                     
 1622 shoaibi   20   0  466m  19m  10m S    1  0.2   0:17.84 gnome-settings-                                            
 1850 shoaibi   20   0 22740 1212  904 S    1  0.0   0:19.96 syndaemon                                                  
 2022 shoaibi   20   0  248m 9688 7404 S    1  0.1   0:09.99 gnome-screensav                                            
 2600 shoaibi   25   5  943m  96m  17m S    1  1.2   4:05.84 chrome                                                     
 7899 root      20   0     0    0    0 S    1  0.0   0:07.73 kworker/3:1                                                
 9358 root      20   0     0    0    0 S    1  0.0   0:08.14 kworker/4:1                                                
 9777 root      20   0     0    0    0 S    1  0.0   0:09.16 kworker/6:1                                                
10352 root      20   0     0    0    0 S    1  0.0   0:07.77 kworker/1:3                                                
10379 root      20   0     0    0    0 S    1  0.0   0:01.82 kworker/5:1                                                
10424 root      20   0     0    0    0 S    1  0.0   0:01.53 kworker/7:1                                                
10431 root      20   0     0    0    0 S    1  0.0   0:01.74 kworker/1:0                                                
10433 root      20   0     0    0    0 S    1  0.0   0:00.76 kworker/2:1                                                
    1 root      20   0 24128 2280 1368 S    0  0.0   0:02.88 init                                                       
    2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd                                                   
    3 root      20   0     0    0    0 S    0  0.0   0:01.62 ksoftirqd/0                                                
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                     
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                    
   31 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                      
   33 root      20   0     0    0    0 S    0  0.0   0:00.13 sync_supers                                                
   34 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                
   35 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                
   36 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                    
   37 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpid                                                     
   38 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                               
   39 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                              
   40 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                    
   41 root      20   0     0    0    0 S    0  0.0   0:00.01 khubd                                                      
   42 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                         
   44 root      20   0     0    0    0 S    0  0.0   0:00.03 khungtaskd                                                 
   45 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                    
   46 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                       
   47 root      20   0     0    0    0 S    0  0.0   0:00.00 fsnotify_mark                                              
   48 root       0 -20     0    0    0 S    0  0.0   0:00.00 aio                                                        
   49 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                            
   50 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                     
   54 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                   
   56 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpathd                                                    
   57 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd                                            
   58 root       0 -20     0    0    0 S    0  0.0   0:00.00 kondemand                                                  
   59 root       0 -20     0    0    0 S    0  0.0   0:00.00 kconservative                                              
  182 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                  
  183 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                  
  184 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                  
  185 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                  
  186 root      20   0     0    0    0 S    0  0.0   0:02.33 scsi_eh_4                                                  
  187 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                  
  217 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_6                                                  
  218 root      20   0     0    0    0 S    0  0.0   0:15.03 usb-storage                                                
  235 root      20   0  7200  252  144 S    0  0.0   0:01.02 v86d                                                       
  296 root      20   0     0    0    0 S    0  0.0   0:00.65 jbd2/sda3-8                                                
  297 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
  349 root      20   0 17052  640  456 S    0  0.0   0:00.26 upstart-udev-br                                            
  525 root      20   0 22240 1084  592 S    0  0.0   0:00.09 mount.ntfs                                                 
  529 root      16  -4 21740 1192  352 S    0  0.0   0:00.18 udevd                                                      
  867 root      20   0 15004  388  196 S    0  0.0   0:00.02 upstart-socket-                                            
  870 root       0 -20     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                  
  894 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio0                                                  
  917 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio1                                                  
  948 root      20   0 22240 1128  592 S    0  0.0   0:00.08 mount.ntfs                                                 
  990 root      20   0 22452 1604  748 S    0  0.0   0:00.50 mount.ntfs                                                 
  993 root      20   0     0    0    0 S    0  0.0   0:04.39 jbd2/sda5-8                                                
  994 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
 1013 root      20   0 91592 4916 3748 S    0  0.1   0:00.01 smbd                                                       
 1019 root      20   0 49464 2752 2172 S    0  0.0   0:00.00 sshd                                                       
 1026 syslog    20   0  117m 1648 1112 S    0  0.0   0:01.87 rsyslogd                                                   
 1037 root      20   0 91592 1552  384 S    0  0.0   0:00.00 smbd                                                       
 1039 messageb  20   0 24764 2196  856 S    0  0.0   0:05.77 dbus-daemon                                                
 1049 root      20   0 83168 4016 3084 S    0  0.0   0:00.39 gdm-binary                                                 
 1053 avahi     20   0 32132 1704 1400 S    0  0.0   0:00.19 avahi-daemon                                               
 1054 avahi     20   0 32008  468  212 S    0  0.0   0:00.00 avahi-daemon                                               
 1055 root      20   0  154m 5104 3884 S    0  0.1   0:03.57 NetworkManager                                             
 1057 root      20   0  250m 4096 2756 S    0  0.1   0:00.62 console-kit-dae                                            
 1059 root      20   0 64656 2780 2152 S    0  0.0   0:00.05 modem-manager                                              
 1081 root      20   0  126m 4448 2852 S    0  0.1   0:01.49 polkitd                                                    
 1145 root      20   0 75512 3132 2324 S    0  0.0   0:00.03 cupsd                                                      
 1152 root      20   0 97752 4388 3312 S    0  0.1   0:00.01 gdm-simple-slav                                            
 1172 root      20   0 28812 2960 2448 S    0  0.0   0:02.11 wpa_supplicant                                             
 1229 root      20   0  6196  656  548 S    0  0.0   0:00.00 getty                                                      
 1233 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1240 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1241 root      20   0  6196  656  548 S    0  0.0   0:00.00 getty                                                      
 1244 root      20   0  6196  660  548 S    0  0.0   0:00.00 getty                                                      
 1252 root      20   0  4416  896  572 S    0  0.0   0:00.02 acpid                                                      
 1266 root      20   0 15780  672  500 S    0  0.0   0:11.67 irqbalance                                                 
 1272 root      20   0 18928 1056  816 S    0  0.0   0:00.10 cron                                                       
 1273 daemon    20   0 16728  376  220 S    0  0.0   0:00.00 atd                                                        
 1301 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1302 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1303 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl                                                     
 1327 root      20   0     0    0    0 S    0  0.0   0:03.32 flush-8:0                                                  
 1504 root      20   0  6196  660  552 S    0  0.0   0:00.00 getty                                                      
 1557 root      20   0 99.4m 3808 2884 S    0  0.0   0:00.00 gdm-session-wor                                            
 1566 shoaibi   20   0  237m 8516 6328 S    0  0.1   0:00.55 gnome-session                                              
 1601 shoaibi   20   0 12092  288    0 S    0  0.0   0:00.15 ssh-agent                                                  
 1604 shoaibi   20   0 26400  620  352 S    0  0.0   0:00.00 dbus-launch                                                
 1610 shoaibi   20   0 60956 5496 2576 S    0  0.1   0:03.02 gconfd-2                                                   
 1617 shoaibi   20   0  168m  10m 3120 S    0  0.1   0:00.39 gnome-keyring-d                                            
 1625 shoaibi   20   0 55956 2468 2056 S    0  0.0   0:00.15 gvfsd                                                      
 1630 shoaibi   20   0 81008 2684 1816 S    0  0.0   0:00.00 gvfs-fuse-daemo                                            
 1636 shoaibi   20   0  294m 6704 3836 S    0  0.1   5:23.41 pulseaudio                                                 
 1638 rtkit     21   1  100m 1324 1080 S    0  0.0   0:00.52 rtkit-daemon                                               
 1641 shoaibi   20   0  401m  17m  12m S    0  0.2   0:31.86 metacity                                                   
 1643 shoaibi   20   0  650m  48m  31m S    0  0.6   0:41.21 nautilus                                                   
 1646 shoaibi   20   0  327m  11m 8288 S    0  0.1   0:00.16 bluetooth-apple                                            
 1648 shoaibi   20   0  217m 5856 4348 S    0  0.1   0:00.34 zeitgeist-datah                                            
 1649 shoaibi   20   0  676m  46m  27m S    0  0.6   1:05.23 unity-2d-launch                                            
 1651 shoaibi   20   0  389m  18m  13m S    0  0.2   0:04.18 nm-applet                                                  
 1655 shoaibi   20   0  226m 7272 5632 S    0  0.1   0:00.14 polkit-gnome-au                                            
 1657 shoaibi   20   0  470m  32m  19m S    0  0.4   0:03.56 synapse                                                    
 1658 shoaibi   20   0  370m  26m  12m S    0  0.3   0:00.27 touchpad-indica                                            
 1659 shoaibi   20   0  443m  35m  15m S    0  0.4   0:06.92 python                                                     
 1661 shoaibi   20   0  358m  10m 7752 S    0  0.1   0:03.45 gnome-power-man                                            
 1664 shoaibi   20   0  182m  20m 7364 S    0  0.3   0:01.44 zeitgeist-daemo                                            
 1692 shoaibi   20   0  310m  16m  11m S    0  0.2   0:36.47 notify-osd                                                 
 1693 shoaibi   20   0  177m 3944 3056 S    0  0.0   0:00.00 gconf-helper                                               
 1756 shoaibi   20   0 10848  588  492 S    0  0.0   0:00.00 cat                                                        
 1758 shoaibi   20   0 71904 3748 2908 S    0  0.0   0:00.11 gvfs-gdu-volume                                            
 1760 root      20   0  124m 4004 2960 S    0  0.0   0:00.59 udisks-daemon                                              
 1761 root      20   0 45168 1128  756 S    0  0.0   0:06.13 udisks-daemon                                              
 1764 root      20   0  139m 4424 3304 S    0  0.1   0:02.60 upowerd                                                    
 1826 shoaibi   20   0 77352 2628 2112 S    0  0.0   0:01.30 gvfs-afc-volume                                            
 1832 shoaibi   20   0 63556 2660 1920 S    0  0.0   0:00.00 gvfs-gphoto2-vo                                            
 1847 shoaibi   20   0     0    0    0 Z    0  0.0   0:00.26 python <defunct>                                           
 1848 shoaibi   20   0     0    0    0 Z    0  0.0   0:00.01 zeitgeist-datah <defunct>                                  
 1902 shoaibi   20   0  183m 2696 2180 S    0  0.0   0:00.02 dconf-service                                              
 1925 shoaibi   20   0 56220 2784 2168 S    0  0.0   0:00.00 gvfsd-burn                                                 
 1952 shoaibi   20   0  234m 6044 4716 S    0  0.1   0:00.26 indicator-sessi                                            
 1954 shoaibi   20   0  202m 5236 3784 S    0  0.1   0:03.32 indicator-appli                                            
 1956 shoaibi   20   0  237m 5104 4024 S    0  0.1   0:00.03 indicator-messa                                            
 1965 shoaibi   20   0  307m 7828 6072 S    0  0.1   0:00.11 indicator-datet                                            
 1969 shoaibi   20   0  331m 6780 5152 S    0  0.1   0:01.19 indicator-sound                                            
 1988 shoaibi   20   0  155m 4796 3716 S    0  0.1   0:00.26 geoclue-master                                             
 2057 root      20   0 61652 1628  752 S    0  0.0   0:02.87 nmbd                                                       
 2072 shoaibi   20   0  175m 7480 5620 S    0  0.1   0:00.08 gdu-notificatio                                            
 2074 shoaibi   20   0  262m 7840 5236 S    0  0.1   0:01.75 unity-applicati                                            
 2076 shoaibi   20   0  176m 4592 3612 S    0  0.1   0:00.78 unity-files-dae                                            
 2124 shoaibi   20   0  232m  23m  10m S    0  0.3   0:12.85 applet.py                                                  
 2131 shoaibi   20   0 60720 3468 2652 S    0  0.0   0:00.03 gvfsd-trash                                                
 2148 shoaibi   20   0 14612  856  692 S    0  0.0   0:00.01 gnome-pty-helpe                                            
 2206 shoaibi   20   0  317m  15m  11m S    0  0.2   0:01.84 update-notifier                                            
 2227 shoaibi   20   0  486m  37m  22m S    0  0.5   0:08.38 gnote                                                      
 2237 shoaibi   20   0  234m  10m 3432 S    0  0.1   0:13.44 chrome                                                     
 2239 shoaibi   20   0  276m  15m 8124 S    0  0.2   0:00.29 chrome                                                     
 2260 shoaibi   20   0  852m  21m 9.9m S    0  0.3   0:03.51 chrome                                                     
 2264 shoaibi   20   0  855m  27m  14m S    0  0.4   0:15.20 chrome                                                     
 2266 shoaibi   20   0  852m  22m 9.9m S    0  0.3   0:12.05 chrome                                                     
 2268 shoaibi   20   0  854m  25m  12m S    0  0.3   0:14.50 chrome                                                     
 2271 shoaibi   20   0  855m  28m  12m S    0  0.4   0:29.00 chrome                                                     
 2274 shoaibi   20   0  869m  39m  15m S    0  0.5   4:26.68 chrome                                                     
 2277 shoaibi   20   0  872m  28m  12m S    0  0.4   0:30.85 chrome                                                     
 2280 shoaibi   20   0  880m  55m  17m S    0  0.7   1:55.02 chrome                                                     
 2284 shoaibi   20   0  859m  34m  16m S    0  0.4   1:22.12 chrome                                                     
 2286 shoaibi   20   0  870m  40m  13m S    0  0.5   1:18.33 chrome                                                     
 2289 shoaibi   20   0  854m  24m  11m S    0  0.3   0:14.51 chrome                                                     
 2292 shoaibi   20   0  854m  24m  10m S    0  0.3   0:13.80 chrome                                                     
 2295 shoaibi   20   0  852m  21m 9976 S    0  0.3   0:03.70 chrome                                                     
 2299 shoaibi   20   0  852m  21m 9.9m S    0  0.3   0:03.70 chrome                                                     
 2301 shoaibi   20   0  852m  22m 9.8m S    0  0.3   0:22.55 chrome                                                     
 2304 shoaibi   20   0  854m  24m  11m S    0  0.3   0:13.34 chrome                                                     
 2307 shoaibi   20   0  854m  25m  11m S    0  0.3   0:18.76 chrome                                                     
 2311 shoaibi   20   0  853m  22m  10m S    0  0.3   0:03.61 chrome                                                     
 2313 shoaibi   20   0  880m  28m  12m S    0  0.4   0:20.32 chrome                                                     
 2316 shoaibi   20   0  853m  22m  10m S    0  0.3   0:03.74 chrome                                                     
 2319 shoaibi   20   0  853m  24m  11m S    0  0.3   0:14.77 chrome                                                     
 2323 shoaibi   20   0  856m  30m  13m S    0  0.4   0:27.36 chrome                                                     
 2326 shoaibi   20   0  856m  28m  12m S    0  0.4   0:25.22 chrome                                                     
 2329 shoaibi   20   0  856m  27m  13m S    0  0.4   0:06.13 chrome                                                     
 2417 shoaibi   25   5  904m  77m  17m S    0  1.0   1:25.91 chrome                                                     
 2424 shoaibi   25   5  890m  78m  17m S    0  1.0   1:01.25 chrome                                                     
 2454 shoaibi   20   0  274m  16m 9248 S    0  0.2   0:00.04 chrome                                                     
 2604 shoaibi   25   5  931m 117m  17m S    0  1.5   3:07.93 chrome                                                     
 2613 shoaibi   25   5  882m  66m  16m S    0  0.8   0:39.92 chrome                                                     
 2656 shoaibi   20   0  672m  44m  23m S    0  0.6   1:21.28 empathy                                                    
 2658 shoaibi   20   0 59508 5772 3616 S    0  0.1   0:03.62 mission-control                                            
 2665 shoaibi   20   0  159m 5064 4012 S    0  0.1   0:00.16 telepathy-logge                                            
 3188 shoaibi   20   0  549m  93m  29m S    0  1.2   0:25.52 unity-2d-spread                                            
 3193 shoaibi   20   0  542m  54m  25m S    0  0.7   0:11.60 unity-2d-places                                            
 3338 shoaibi   20   0 49728 2232 1812 S    0  0.0   0:00.02 gvfsd-metadata                                             
 5559 shoaibi   20   0 27908 5396 1704 S    0  0.1   0:00.40 bash                                                       
 7190 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                
 7192 root      20   0     0    0    0 S    0  0.0   0:00.29 ksoftirqd/1                                                
 7193 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                                                
 7194 root      20   0     0    0    0 S    0  0.0   0:11.38 kworker/2:3                                                
 7195 root      20   0     0    0    0 S    0  0.0   0:00.17 ksoftirqd/2                                                
 7196 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                                                
 7198 root      20   0     0    0    0 S    0  0.0   0:00.14 ksoftirqd/3                                                
 7199 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/4                                                
 7201 root      20   0     0    0    0 S    0  0.0   0:00.17 ksoftirqd/4                                                
 7202 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/5                                                
 7204 root      20   0     0    0    0 S    0  0.0   0:00.13 ksoftirqd/5                                                
 7205 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/6                                                
 7206 root      20   0     0    0    0 S    0  0.0   0:01.99 kworker/6:3                                                
 7207 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/6                                                
 7210 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/7                                                
 7211 root      20   0     0    0    0 S    0  0.0   0:08.95 kworker/7:3                                                
 7212 root      20   0     0    0    0 S    0  0.0   0:00.30 ksoftirqd/7                                                
 7230 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:28                                               
 7231 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:29                                               
 7276 root       0 -20     0    0    0 S    0  0.0   0:00.00 hci0                                                       
 7295 root      18  -2 21736 1188  344 S    0  0.0   0:00.00 udevd                                                      
 7296 root      18  -2 21736 1116  276 S    0  0.0   0:00.00 udevd                                                      
 7305 root      20   0 23072 1988 1524 S    0  0.0   0:00.01 bluetoothd                                                 
 7317 root       0 -20     0    0    0 S    0  0.0   0:00.00 l2cap                                                      
 7342 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd                                                   
 7408 root      20   0     0    0    0 S    0  0.0   0:00.00 RtmpCmdQTask                                               
 8032 root      20   0  7084 1548 1060 S    0  0.0   0:00.03 dhclient                                                   
 8043 shoaibi   20   0  376m  28m  13m S    0  0.4   0:15.42 telepathy-gabbl                                            
 8047 shoaibi   20   0  214m  13m 8708 S    0  0.2   0:00.46 telepathy-haze                                             
 8185 shoaibi   20   0  133m  27m 5868 S    0  0.3   0:05.13 telepathy-butte                                            
 9466 root      20   0     0    0    0 S    0  0.0   0:04.44 kworker/5:3                                                
10004 root      20   0     0    0    0 S    0  0.0   0:03.92 kworker/3:3                                                
10062 shoaibi   20   0  240m  12m 9964 S    0  0.2   0:00.02 gvfsd-http                                                 
10243 root      20   0     0    0    0 S    0  0.0   0:08.29 kworker/1:1                                                
10330 shoaibi   20   0 19484 1448  968 S    0  0.0   1:40.15 top                                                        
10337 root      20   0     0    0    0 S    0  0.0   0:12.67 kworker/0:0                                                
10367 root      20   0     0    0    0 S    0  0.0   0:11.71 kworker/0:1                                                
10386 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/4:2                                                
10388 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:0                                                
10389 root      20   0     0    0    0 S    0  0.0   0:02.13 kworker/0:2                                                
10396 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/7:0                                                
10402 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:2                                                
10411 root      20   0     0    0    0 S    0  0.0   0:00.68 kworker/4:0                                                
10417 root      20   0     0    0    0 S    0  0.0   0:00.54 kworker/5:0                                                
10425 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/6:0                                                
10429 root      20   0     0    0    0 S    0  0.0   0:00.03 kworker/4:3                                                
10430 root      20   0     0    0    0 S    0  0.0   0:01.34 kworker/5:2                                                
10434 shoaibi   20   0 27952 5484 1744 S    0  0.1   0:09.10 bash                                                       
10541 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/3:0                                                
10543 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:2                                                
10568 shoaibi   20   0 16296 1616 1160 S    0  0.0   0:00.14 generate-system                                            
10569 root      20   0 25644 1320 1072 S    0  0.0   0:00.06 sudo                                                       


------
iotop

Total DISK READ: 0.00 B/s | Total DISK WRITE: 0.00 B/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN      IO    COMMAND
  993 be/3 root        0.00 B/s    4.74 K/s  0.00 %  0.38 % [jbd2/sda5-8]
  296 be/3 root        0.00 B/s   14.22 K/s  0.00 %  0.11 % [jbd2/sda3-8]
 2248 be/4 shoaibi     0.00 B/s    7.11 K/s  0.00 %  0.00 % chrome

------
iostat

Linux 2.6.38-10-generic (abacus) 	06/11/2011 	_x86_64_	(8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.79    0.84    1.32    0.10    0.00   93.96

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               2.33     8.38    1.06    8.64    41.54    68.57    22.69     0.10   10.12   42.50    6.13   1.30   1.27



==========================================================================================================



```


I would really appreciate all the help i can get as i have no idea what could be going on here. For my knowledge the three criteria for high cpu load avg (cpu intensive app, ram intensive or I/O intensive app) isn't appearing here, yet load is above normal and resulting is a slow system.

I typed this whole post while system load avg was above 1, so there could be multiple typos, apologies for that.

btw, this issue didn't occur at all in Maverick Meerkat, i removed that yesterday night and did a fresh install of natty followed with upgrade.

---

### Post by Rocket2DMn on 2011-06-11
It looks like Chrome is chewing up your CPU.  I guess each instance of chrome in top is a tab open in the browser, and the CPU load is adding up between them.  Are there videos or flash advertisements in the tabs? Those can eat up CPU time.  Otherwise some addons might be acting up.

---

### Post by shoaibi on 2011-06-11
Only 5,7 extensions are enabled, there is no flash or videos inside tabs. And as i said it also happens with firefox, even with single tab opened. So definitely not chrome issue.

Also, same versions of chrome/firefox worked without any issue on Maverick before i did a fresh install of natty.

---

### Post by VOT Productions on 2011-06-11
Please post the iostat with ONLY one tab.

---

### Post by disc99 on 2011-07-01
Same problem. 11.04, 2.6.39-0, Sandy Bridge based system with 8GB of RAM. 

Several times a day the browser (Chrome or Firefox) grabs 100% of CPU. Only way to cure is to close and restart browser.

---

