---
title: "Hard Disk Spinning Nonstop"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-11-02
Hey community,

I just did a total fresh installation of Ubuntu 9.10. Runs great :popcorn:

But I'm concerned about my hard disk. It's got one bad sector, with no spares left. This means the average read/write speed has dropped a little bit.

Since reinstalling, my hard disk has been "thinking" non-stop for over 4 hours straight. There's nothing even running in the background.

EDIT: The drive isn't failing. I don't hear the "click of death", everything on the drive is still there. Its had this 1 bad sector for over 8 months with no troubles. 

Output of Top:
```
5418 root      20   0  195m  38m  16m S   11  1.9   2:26.81 Xorg               
 7452 jake      20   0  512m  75m  27m S    5  3.8   0:44.68 firefox            
 1984 jake      20   0 34932 2204 1644 D    3  0.1   5:20.02 gvfsd-metadata     
 6990 jake      20   0  199m  16m  10m R    2  0.8   0:04.17 gnome-terminal     
 7011 root      20   0 10756 2036 1016 S    1  0.1   0:09.85 powertop           
 5711 jake      20   0  175m  11m 8916 S    1  0.6   0:03.36 gtk-window-deco    
 5630 jake      20   0  200m  15m   9m S    0  0.8   0:02.12 notify-osd         
 5707 jake      20   0  450m  35m  16m S    0  1.8   0:16.78 gnome-panel        
 8879 jake      20   0 19132 1352  980 R    0  0.1   0:00.24 top                
    1 root      20   0 19428 1672 1188 S    0  0.1   0:00.77 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:07.23 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    9 root      15  -5     0    0    0 S    0  0.0   0:01.51 events/0           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper       
```

I have firefox and a terminal running. Is there some hard disk setting that isn't set up correctly? It's hard to believe it needs to be on this much. 

I have 4 GB of swap and 2GB of RAM.

Any suggestions?

---

### Post by aktiwers on 2009-11-02
I don't know much about this stuff, but I know of an app called iotop that might help.

Try it out:
```
sudo apt-get install iotop
```
and run it
```
iotop
```

It's like top, it just shows apps using your disk instead :)

---

### Post by asuastrophysics on 2009-11-02
> **aktiwers said:**
> I don't know much about this stuff, but I know of an app called iotop that might help.

Try it out:
```
sudo apt-get install iotop
```
and run it
```
iotop
```

It's like top, it just shows apps using your disk instead :)

output of iotop:
```
Total DISK READ: 0.00 B/s | Total DISK WRITE: 447.75 K/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND        
 1984 be/4 jake        0.00 B/s   79.01 K/s  0.00 %  0.00 % gvfsd-metadata
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init
    2 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd]
    3 rt/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/0]
    4 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/0]
    5 rt/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/0]
 5640 be/4 jake        0.00 B/s    0.00 B/s  0.00 %  0.00 % sh /usr/bin/compiz
    9 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [events/0]
   11 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [cpuset]
   12 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khelper]
   13 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [netns]
   14 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [async/mgr]
   15 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kintegrityd/0]
   17 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kblockd/0]
   19 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kacpid]
   20 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kacpi_notify]
   21 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kacpi_hotplug]
   22 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ata/0]
   24 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ata_aux]
   25 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksuspend_usbd]
   26 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khubd]
   27 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kseriod]

```
Something appears to be writing to the disk all the time... gvfsd-metadata seems to be causing part of it.

---

### Post by cariboo on 2009-11-02
If you only have one relocatable sector left, I'd start backing up my important data and be checking out hard drive prices. Hard drives don't always start clicking before they die, one of these days you will start your system and it just won't boot.

---

### Post by asuastrophysics on 2009-11-02
Swappiness has been upped to 60 in /etc/sysctl.conf

It's killing my hard drive! Every now and then for the past 8 months, it's made this weird metal grinding sound intermittently while "thinking". It's doing it a lot now because it's always on. (The noise isn't a concern, like I said I have backups)

If this doesn't stop Ubuntu is going to run my hard drive into the ground for good. It's getting really hot working nonstop for 6 hours.

---

### Post by asuastrophysics on 2009-11-02
> **cariboo907 said:**
> If you only have one relocatable sector left, I'd start backing up my important data and be checking out hard drive prices. Hard drives don't always start clicking before they die, one of these days you will start your system and it just won't boot.

Everything has been backed up. I make several backups every day. :D

Something's wrong though. Ubuntu is using 0% of my ram and just using the hard disk as virtual memory. (you can see from iotop above). This is putting unnecessary wear on the drive.

---

### Post by asuastrophysics on 2009-11-02
Oh, what do you know??? :D ;) :popcorn:

I just issued 
```
sudo killall gvfsd-metadata
```

Problem solved! ;)

This is definitely a full-blown BUG though. Whatever gvfsd-metadata is, it's got a bug and it's making hard disks work like prisoners in a chain gang. (non stop, till you die) 

I'm definitely going to report this on launchpad. anyone know what gvfsd-metadata is?

---

### Post by aktiwers on 2009-11-02
I have no idea what it is..   all I could find was this:

 >    This daemon singleton handles updates to metadata stores.  All clients that wishes to write metadata should talk to it via dbus.
[http://mail.gnome.org/archives/svn-commits-list/2009-June/msg06280.html](http://mail.gnome.org/archives/svn-commits-list/2009-June/msg06280.html)

Sounds important? :D

Its not bugging here, but a bug report might be good, if your system is fully up-to date.

---

### Post by asuastrophysics on 2009-11-02
> **aktiwers said:**
> I have no idea what it is..   all I could find was this:

 
[http://mail.gnome.org/archives/svn-commits-list/2009-June/msg06280.html](http://mail.gnome.org/archives/svn-commits-list/2009-June/msg06280.html)

Sounds important? :D

Its not bugging here, but a bug report might be good, if your system is fully up-to date.

heh, seems to be running OK without it :D
Just shows how stable Linux is. It can function even with an essential piece of software missing. I'll never go back to windows! :lolflag:

---

### Post by aktiwers on 2009-11-02
Haha true :)
GVFS seams to be [explained here]("http://en.wikipedia.org/wiki/GVFS")

And bugs related to GVFS here:
[https://launchpad.net/ubuntu/+source/gvfs/+bugs](https://launchpad.net/ubuntu/+source/gvfs/+bugs)

---

### Post by asuastrophysics on 2009-11-02
> **aktiwers said:**
> Haha true :)
GVFS seams to be [explained here]("http://en.wikipedia.org/wiki/GVFS")

And bugs related to GVFS here:
[https://launchpad.net/ubuntu/+source/gvfs/+bugs](https://launchpad.net/ubuntu/+source/gvfs/+bugs)

hey thanks for your help!

---

### Post by aktiwers on 2009-11-02
> **asuastrophysics said:**
> hey thanks for your help!

Cheers ;)

---

### Post by DeadStarXt on 2009-12-15
Hello,

A friend of mine experienced the same problem on the same release (ubuntu-9.10-64 bits). The process 'gvfsd-metadata' uses 100% of CPU as soon as she copies files from a location to another on the hard drive. The process goes on after the copy for 10 minutes and the system temperature increases dramatically. 

Sorry, I think loud... Since I did not understand the error, I tried to reproduce it on my own laptop. She wanted to copy 35000 files splitted into 7 directories into a single one. As I was doing it I've seen the process appearing and slowing the whole system down. Killing the process even with sudoer rights did not succeed as nautilus recreate it systematically!

The solution consists in manipulating such heavy batches of files using a terminal... Which is not a reflex for my colleague... Yet! The copy is faster and uses far less CPU.

Maybe nautilus could be improved to be able to deal with such heavy batches of files in a lighter way for the CPU...

Thank you for reading me.

---

### Post by LowSky on 2009-12-15
I'm just putting 2 and 2 together and your issue is your many backups though the day. What exactly are you backing up the who hard drive or just a few files, or somewhere in between.

Realistically the only thing you should back up is your /home folder, and a few times a day? why? how often is your data changing? Maybe find the exact file you need and just back that up if it is mission critical

If you really need it all backed up look into using a RAID 1 setup for better data storage

---

