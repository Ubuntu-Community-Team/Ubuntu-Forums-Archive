---
title: "Minidlna: Configuring minidlna.conf file"
date: 2015-03-20
forum: Networking &amp; Wireless
---

### Post by ozark_hillbilly on 2015-03-20
Ok, let me preface this thread w/ the fact that I am a "paste and try it" level Linux user. Limited experience but I can navigate directories and operate inside Terminal mode.

After installing Minidlna I need to finish setting up the configuration file. Goal: establish communication between a Yamaha network stereo receiver and my PC, via common router. I know it's pathetic
that I can't even enter the correct pathway info, call me whatever you like. I just need some help. 

****************************************************************************************************

Here is the conf file, 1st part anyway:

#network_interface=eth0         # Self-discovers if commented (good with NetworkManager)
media_dir= A,/home/ed/Music    # Use A, P, and V to restrict media 'type' in directory

friendly_name=Laptop            # Optional
db_dir=/var/cache/minidlna      # Needs to be un-commented
log_dir=/var/log                # Needs to be un-commented
inotify=yes                     # 'no' for less resources, restart required for new media

****************************************************************************************************
Under Terminal, it is erroring out on directory info after restarting file with changes:

ed@ed-G41MT-S2PT:~$ sudo service minidlna restart
 * Restarting DLNA/UPnP-AV media server minidlna                                [2015/03/20 21:02:42] minidlna.c:594: error: Media directory "**A,/home/ed/Music **   # Use A, P, and V to restrict media 'type' in directory" not accessible [No such file or directory]
[2015/03/20 21:02:42] utils.c:292: warn: make_dir: cannot create directory '/var/cache/minidlna      # Needs to be un-commented'
[2015/03/20 21:02:42] minidlna.c:638: fatal: Database path not accessible! [/var/cache/minidlna      # Needs to be un-commented]
                                                                         [fail]
ed@ed-G41MT-S2PT:~$ 

******************************************************************************************************
My directory info from Terminal :

ed@ed-G41MT-S2PT:~$ cd
ed@ed-G41MT-S2PT:~$ cd /home/ed/Music
ed@ed-G41MT-S2PT:~/Music$ dir
Audacity      Dwight\ Yoakam  INXS		      Neil\ Young  Sade
Diana\ Krall  Eagles	      Marshall\ Tucker\ Band  Pink\ Floyd  Tom\ Petty
ed@ed-G41MT-S2PT:~/Music$

---

### Post by SeijiSensei on 2015-03-21
Just delete the hash marks and the text after them:
```

media_dir= A,/home/ed/Music
friendly_name=Laptop
db_dir=/var/cache/minidlna
log_dir=/var/log
inotify=yes

```

---

### Post by ozark_hillbilly on 2015-03-21
thanks SeijiSensei..... ijust learned something new about Linux code.... :p

---

### Post by ozark_hillbilly on 2015-03-21
OK, I have established communication between the network receiver and my PC!!!

I'll close this out.....

---

