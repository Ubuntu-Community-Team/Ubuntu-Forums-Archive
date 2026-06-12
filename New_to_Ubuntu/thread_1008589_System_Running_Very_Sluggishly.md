---
title: "System Running Very Sluggishly"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Tux_2008 on 2008-12-11
Hi,

I've recently noticed a significant decrease in performance on Ubuntu, for example, starting Photoshop CS2 through Wine now takes ~70 seconds, whereas it earlier took only one or two. Pretty much all other functions and programs are also very noticeably slower.

I tried reinstalling the last kernel that worked fine (2.6.27_7) but noticed no difference. Other than that I haven't tried much, I'm by no means familiar with the inner workings of computers.

Apologies if the answer has already been posted, I tried searching but did not find anything.

Thanks!
-Tux_2008

---

### Post by Michael.Godawski on 2008-12-11
You know it is hard to guess... :p

Check your free RAM with

```
free
```

Check the current processes and cpu usage and other jazz with

```
top
```

Anything suspicious?

---

### Post by Tux_2008 on 2008-12-11
Hm, I don't really know; having used Windows exclusively for many years I couldn't say what should be there and what should not.
This is what I got:

```

free           
                      total       used       free     shared    buffers     cached
Mem:       1033524     994592      38932          0      40932     550080
-/+ buffers/cache:     403580     629944
Swap:      3028212       1860    3026352

top
top - 00:24:18 up 24 min,  2 users,  load average: 0.12, 0.24, 0.24
Tasks: 135 total,   2 running, 132 sleeping,   0 stopped,   1 zombie
Cpu(s):  4.0%us,  1.0%sy,  0.0%ni, 95.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1033524k total,   995740k used,    37784k free,    40952k buffers
Swap:  3028212k total,     1860k used,  3026352k free,   550176k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5232 root      20   0  349m  48m  17m R 12.5  4.8   0:49.41 Xorg                                                                                            
 6273 totti     20   0  132m  48m  28m S  7.6  4.8   0:08.14 amarokapp                                                                                       
 6308 totti     20   0 84716  30m  17m S  2.0  3.1   0:01.42 gnome-terminal                                                                                  
 5727 totti     20   0 21288 2756 1420 S  0.7  0.3   0:03.08 gnome-screensav                                                                                 
    1 root      20   0  3056 1884  564 S  0.0  0.2   0:01.28 init                                                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.20 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0                                                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                         
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                   
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0                                                                                       
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                          
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                    
  151 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                          
  155 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                         
  196 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                         
  197 root      20   0     0    0    0 S  0.0  0.0   0:00.02 pdflush                                                                                         
  198 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 kswapd0                                                                                         
  240 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                           
 1209 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1215 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                           
 1230 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 ata/0                                                                                           
 1233 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                         
 1236 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                        
 1810 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                       
 1812 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                                       
 1983 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                                       
 1984 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_3                                                                                       
 2000 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                     
 2004 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_4                                                                                       
 2005 root      15  -5     0    0    0 S  0.0  0.0   0:00.32 scsi_eh_5                                                                                       
 2035 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_6                                                                                       
 2037 root      15  -5     0    0    0 S  0.0  0.0   0:00.20 usb-storage                                                                                     
 2200 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 kjournald                                                                                       
 2376 root      16  -4  2536 1028  400 S  0.0  0.1   0:00.34 udevd                                                                                           
 4353 root      20   0  1780  532  468 S  0.0  0.1   0:00.00 getty                                                                                           
 4354 root      20   0  1780  536  468 S  0.0  0.1   0:00.00 getty                                                                                           
 4361 root      20   0  1780  540  468 S  0.0  0.1   0:00.00 getty                                                                                           
 4362 root      20   0  1780  540  468 S  0.0  0.1   0:00.00 getty                                                                                           
 4363 root      20   0  1780  532  468 S  0.0  0.1   0:00.00 getty                                                                                           

```

Thanks for any further help!
I really appreciate it!

-Tux_2008

---

### Post by LowSky on 2008-12-11
Turn off indexing and tracker from start up, its under system>pref>session

it might speed things up

---

### Post by oldos2er on 2008-12-11
What are your hardware specs?

---

### Post by jamesrl on 2008-12-11
Can you post the output of 'df -h' (how much disk space you have free (-h is for human-readable units) and 'cat /proc/cpuinfo' (Your cpu info).

I have found that amarok is sort of a resource hog (especially in gnome as it loads lots of kde shared libraries that you have equivalent gnome libraries already open), so you might want to see how responsive your system is with amarok off (also check that its actually off in top).

---

### Post by Tux_2008 on 2008-12-12
Hi again, sorry for the late reply, unfortunately one cannot escape such necessities as work and sleep.:wink:


> **LowSky said:**
> Turn off indexing and tracker from start up, its under system>pref>session

it might speed things up
I tried your tip, and it did speed things up a little but not a great deal I'm afraid.
In any case, thanks for your help!


> **jamesrl said:**
> Can you post the output of 'df -h' (how much disk space you have free (-h is for human-readable units) and 'cat /proc/cpuinfo' (Your cpu info).

I have found that amarok is sort of a resource hog (especially in gnome as it loads lots of kde shared libraries that you have equivalent gnome libraries already open), so you might want to see how responsive your system is with amarok off (also check that its actually off in top).

Hi, unfortunately there was no evident difference with Amarok on/off.
Here are the hard drive and cpu infos:

df-h:
```

totti@HEM-PC:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              91G   32G   55G  38% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  212K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  176K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-9-generic/volatile

```

cat /proc/cpuinfo:
```

totti@HEM-PC:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 47
model name    : AMD Athlon(tm) 64 Processor 3200+
stepping    : 2
cpu MHz        : 1000.000
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips    : 2010.26
clflush size    : 64
power management: ts fid vid ttp tm stc

```


Many thanks to you all for helping me sort this out!

Best regards,
-Tux_2008

---

### Post by jamesrl on 2008-12-12
Have you checked for rootkits?  Top might not be showing all processes if your system has been compromised.
That is 
```
sudo apt-get install chkrootkit
chkrootkit

```

---

### Post by jamesrl on 2008-12-12
I should add that if chkrootkit doesn't find anything that doesn't necessarily mean you are safe, as (see [chkrootkit FAQ]("http://www.chkrootkit.org/faq/#5"):
> 
# Which commands does chkrootkit use?

The following commands are used by the chkrootkit script:

awk, cut, echo, egrep, find, head, id, ls, netstat, ps, strings, sed, uname
# Can I trust these commands on a compromised machine?

Probably not. We suggest you follow one of the alternatives below:

   1. Use the `-p path' option to supply an alternate path to binaries you trust:

      # ./chkrootkit -p /cdrom/bin


   2. Mount the compromised machine's disk on a machine you trust and specify a new rootdir with the `-r rootdir' option:

      # ./chkrootkit -r /mnt




---

### Post by Tux_2008 on 2008-12-13
Hello again,
I ran the chkrootkit, these are the only ones to come out 'out of the ordinary', that is not saying "Not infected" or the like.
I've no idea what they mean so if anyone can decode them for me I'd be grateful!

```

Checking `aliens'... 
/dev/shm/pulse-shm-3135975547

Searching for suspicious files and dirs, it may take a while... 
/usr/lib/xulrunner-1.9.0.4/.autoreg /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/.systemPrefs /usr/lib/jvm/.java-1.5.0-sun.jinfo /usr/lib/jvm/java-6-sun-1.6.0.10/.systemPrefs /usr/lib/jvm/.java-6-openjdk.jinfo /usr/lib/jvm/.java-6-sun.jinfo /usr/lib/firefox-3.0.4/.autoreg /lib/init/rw/.ramfs /lib/modules/2.6.27-9-generic/volatile/.mounted

Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[5362])

Checking `z2'... user totti deleted or never logged from lastlog!
user root deleted or never logged from lastlog!
```

Thankk you for any further assistance!
-Tux_2008

---

