---
title: "/tmp full?"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Brasil on 2010-10-11
Hi all, I run mythbuntu (installed via Wubi) and I'm running into issues with mysql crashing. I *think* the problem is something to do with /tmp being full, but I can't see the problem...

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             11535376  10948976       432 100% /
tmpfs                   441100         0    441100   0% /lib/init/rw
varrun                  441100       340    440760   1% /var/run
varlock                 441100         0    441100   0% /var/lock
udev                    441100       200    440900   1% /dev
tmpfs                   441100         0    441100   0% /dev/shm
lrm                     441100      2560    438540   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda8            213062368 187995736  25066632  89% /var/lib
overflow                  1024         0      1024   0% /tmp
root@brasil-desktop:/var/lib/mysql/mythconverg# 

when I try

oot@brasil-desktop:/var/lib/mysql/mythconverg# myisamchk -f recordedseek.MYI
Checking MyISAM file: recordedseek.MYI
Data records:       0   Deleted blocks:       0
myisamchk: warning: Table is marked as crashed and last repair failed
- check file-size
myisamchk: warning: Size of indexfile is: 12286976      Should be: 1024
- check record delete-chain
- check key delete-chain
- check index reference
- check data record references index: 1
- recovering (with sort) MyISAM-table 'recordedseek.MYI'
Data records: 0
- Fixing index 1
myisamchk: Disk is full writing '/tmp/STkPRkBy' (Errcode: 28). Waiting for someone to free space... Retry in 60 secs

I've tried manually cleaning tmp, I've tried moving files to a different drive, autoclean etc, I'm obviously missing something, can someone please help?

Grateful any advice!

---

### Post by Bölvaður on 2010-10-11
> overflow                  1024         0      1024   0% /tmp
This looks wrong to me. Am I wrong or is this just 1MB ?

---

### Post by Brasil on 2010-10-12
> **Bölvaður said:**
> This looks wrong to me. Am I wrong or is this just 1MB ?

Well, I didn't exactly set it manually, but that's what it looks like. 

I should note though I've been using this installation fairly successfully for a couple of years, so up until now /tmp size hasn't been an issue, and I haven't modified anything recently that might impact. The only time I've generally had problems is when I run out of space on the disks because I record too much stuff :) Generally then all I've had to do is free some space and fix up the database either as a straight repair or as per [http://ubuntuforums.org/showthread.php?t=507267](http://ubuntuforums.org/showthread.php?t=507267) and off I go again.

---

