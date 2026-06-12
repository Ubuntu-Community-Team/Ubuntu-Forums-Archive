---
title: "RAM buffers ate up available memory?"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by leviathan8 on 2011-02-02
Hi. I was playing yesterday KMahjongg, and after a while, suddenly the X server froze. I believe that it happened because of a buffer overflow. Now when I boot up my laptop, I notice that the data buffers ate up 80 MB of total RAM, even if no program is running. 

The memtotal is alright, but you see, the data buffers, as far as I know, use abnormally too much RAM even if no program is running.

```
mono@mono-laptop:~$ cat /proc/meminfo
MemTotal:        1923168 kB
MemFree:         1310680 kB
Buffers:           89424 kB
Cached:           287312 kB
SwapCached:            0 kB
Active:           224628 kB
Inactive:         322732 kB
Active(anon):     180316 kB
Inactive(anon):    71864 kB
Active(file):      44312 kB
Inactive(file):   250868 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       1047640 kB
HighFree:         575608 kB
LowTotal:         875528 kB
LowFree:          735072 kB
SwapTotal:       1952760 kB
SwapFree:        1952760 kB
Dirty:                 8 kB
Writeback:             0 kB
AnonPages:        170632 kB
Mapped:            64228 kB
Shmem:             81556 kB
Slab:              21932 kB
SReclaimable:      11332 kB
SUnreclaim:        10600 kB
KernelStack:        2184 kB
PageTables:         4468 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2914344 kB
Committed_AS:     755148 kB
VmallocTotal:     122880 kB
VmallocUsed:       34748 kB
VmallocChunk:      37884 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       16376 kB
DirectMap4M:      892928 kB

```Same with free:

```
mono@mono-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1878        628       1249          0         87        312
-/+ buffers/cache:        228       1649
Swap:         1906          0       1906

```Is it normal that the data buffers use up to 87 mb ram right after boot? Before this happened, my total memory was 1950 or so, and now it decreased to 1870. Also to note that on desktop the data buffers after boot up only use 12 MB, not 87...

---

### Post by leviathan8 on 2011-02-02
The problem seems to persist. I am running Ubuntu 10.04 on a Dell N5010. The X server crashed again while browsing the web. However, now my buffers actually use 100 MB instead of 80 MB. I have no idea why, but apparently the system will halt probably because the RAM memory is overheated? I will try uninstalling some programs that might cause this (powertop, acpi, etc.). If not, I will reformat and install 10.10 version. I don't want my laptop dead in just a few months I used it. I am also waiting for other solutions, thanks.

---

### Post by NightwishFan on 2011-02-02
To be quite honest I doubt this is the issue. Did you try browsing the logs for information? Both Ubuntu and Kubuntu have a log file viewer available. Check the time when the crash happened for information.

Also, what kind of graphics card do you have? Does the system "hard lock" as in unable to ctrl alt del?

---

### Post by leviathan8 on 2011-02-02
> **NightwishFan said:**
> To be quite honest I doubt this is the issue. Did you try browsing the logs for information? Both Ubuntu and Kubuntu have a log file viewer available. Check the time when the crash happened for information.

Also, what kind of graphics card do you have? Does the system "hard lock" as in unable to ctrl alt del?

Yes it is a hardlock, and I do not have graphics card driver installed on my laptop. Can you tell me exactly which sections of log file viewer should I browse?

---

### Post by NightwishFan on 2011-02-02
Yes, you have a graphics card, which model it is may help debug the issue. I did not mean if you specifically installed a driver.

For Ubuntu, the log file is: system->administration->log file viewer
For Kubuntu, just search "log" in the menu.

The specific log you want is either syslog, or messages. An older log might be called "syslog.0" or etc. Either is fine. Simply find the time (best guess) when the system crashed in the log and paste a few lines here that seem suspicious.

---

### Post by leviathan8 on 2011-02-02
> **NightwishFan said:**
> Yes, you have a graphics card, which model it is may help debug the issue. I did not mean if you specifically installed a driver.

For Ubuntu, the log file is: system->administration->log file viewer
For Kubuntu, just search "log" in the menu.

The specific log you want is either syslog, or messages. An older log might be called "syslog.0" or etc. Either is fine. Simply find the time (best guess) when the system crashed in the log and paste a few lines here that seem suspicious.

Oh, I misunderstood, my graphics card is an integrated Intel GMA HD.
I will leave the system untouched a while until it crashes again, and i'll post the output of log here.

I've also read on forums that these things could solve my issue:

> 
1. Disable advanced configuration options in BIOS for CPU fan.
2. Set Compiz effects to none in System->Preferences->Appearance->Visual effects.

Could this help?

---

### Post by NightwishFan on 2011-02-02
The first one I have no idea, the second, perhaps. Though the display freezing does make me thing this is graphics related.

---

### Post by leviathan8 on 2011-02-02
In syslog, all I can see is this:

> Feb  2 12:23:42 mono-laptop AptDaemon: INFO: Initializing daemon
Feb  2 12:28:43 mono-laptop AptDaemon: INFO: Quiting due to inactivity
Feb  2 12:28:43 mono-laptop AptDaemon: INFO: Shutdown was requestedThis is the moment when I requested the forced shutdown. Before this, syslog only shows a series of notifications about the network manager - nothing wrong with it.

Oh, this is strange. Look what it told me right now:

```
Feb  2 17:45:13 mono-laptop AptDaemon: INFO: Quiting due to inactivity
Feb  2 17:45:13 mono-laptop AptDaemon: INFO: Shutdown was requested
Feb  2 17:52:22 mono-laptop avahi-daemon[974]: Invalid query packet.
Feb  2 17:53:05 mono-laptop avahi-daemon[974]: last message repeated 5 times
Feb  2 18:00:20 mono-laptop avahi-daemon[974]: Invalid query packet.
Feb  2 18:01:36 mono-laptop avahi-daemon[974]: last message repeated 2 times
```I'll return with more info.


So, apparently *crosses fingers* ubuntu worked fine in the past 1  hour. Disabled saned, cups and bluetooth, purged powertop and acpi, and  I no longer use GDM to login. Let's hope it will continue working. What  I doubt, is that when the data buffers on RAM reaches values higher  than 100, the laptop will halt. 
*to note is that the laptop is now running with AC power. Didn't tried on battery yet.

---

### Post by NightwishFan on 2011-02-02
Yeah, I assumed that would tell me little, though sometimes it really explains what happens. I guess not in this case.

---

