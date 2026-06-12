---
title: "Firefox, thunderbird, openoffice, tomboy out of order"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by Achilles124 on 2009-07-13
This is the strangest bug that I have encountered. It started with Thunderbird asking if I would like to sync Evolution with Thunderbird. I replied no and then nothing was working anymore.

**Firefox gives the following error:**

> (firefox-bin:7622): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.
main 


checkForUpgrade

getStringPref prefName: Uid val: 4caf4c3b-d0af-44a9-8736-fc00ee0f64e6

getStringPref prefName: Units val: 1

getStringPref prefName: WindUnits val: 1

getStringPref prefName: Placement val: status-bar

getIntegerPref prefName: Position val: -1

getStringPref prefName: NumForecasts val: 1

getBooleanPref prefName: OverlayEnabled val: true

getStringPref prefName: DefaultTab val: 0

getStringPref prefName: ZipCode val: 

getStringPref prefName: CityCode val: 71288

getStringPref prefName: CityName val: Rotterdam

getStringPref prefName: State val: 

getStringPref prefName: Country val: Netherlands

getStringPref prefName: StationId val: EHRD

Mon Jul 13 2009 10:20:43 GMT+0200 (CET)
instanceCount: 1

CommandDataAcquirer.init

CommandDataAcquirer.init url:[http://ffox.weatherbug.com/DataService/GetCommand.ashx?uid=4caf4c3b-d0af-44a9-8736-fc00ee0f64e6&zcode=Z6138&un=1&zip=&cc=71288&stat=EHRD&an=FirefoxExtension&av=2.0.0.4&st=1](http://ffox.weatherbug.com/DataService/GetCommand.ashx?uid=4caf4c3b-d0af-44a9-8736-fc00ee0f64e6&zcode=Z6138&un=1&zip=&cc=71288&stat=EHRD&an=FirefoxExtension&av=2.0.0.4&st=1)

wxBugAsyncHttp - Calling - [http://ffox.weatherbug.com/DataService/GetCommand.ashx?uid=4caf4c3b-d0af-44a9-8736-fc00ee0f64e6&zcode=Z6138&un=1&zip=&cc=71288&stat=EHRD&an=FirefoxExtension&av=2.0.0.4&st=1](http://ffox.weatherbug.com/DataService/GetCommand.ashx?uid=4caf4c3b-d0af-44a9-8736-fc00ee0f64e6&zcode=Z6138&un=1&zip=&cc=71288&stat=EHRD&an=FirefoxExtension&av=2.0.0.4&st=1)

CommandDataAcquirer.getDataFromServer attemptNum: 1 ma 13 jul 2009 10:20:43 CET

CommandDataAcquirer.init setTimeout Fast

Geen ruimte meer over op apparaat
ecmpeek@ecmpeek-desktop:~$ 
(crashreporter:7634): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.

**Thunderbird gives the following error:**
> Segmentation fault

**Openoffice gives the following error:**
> Openoffice cannot store internal information because of not enough space on the following location:
Home/ecmpeek/.openoffice.org/user/backup

I have found a link to the Thunderbird error and it makes me start thunderbird in safe mode, but lightning has disappeared and starting addons crashes thunderbird.

There is enough space on my harddisk. About 38 gig is occupied of the 160 gig. I can use the gnome webbrowser and I can use Opera.

I don't know what this all means. Has anyone a clue?

---

### Post by Achilles124 on 2009-07-13
**This is the error message of tomboy:**
> (tomboy:8443): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.
[DEBUG]: NoteManager created with note path "/home/ecmpeek/.tomboy".

Unhandled Exception: System.IO.IOException: Disk full. Path /home/ecmpeek/.tomboy.log
  at System.IO.FileStream.FlushBuffer () [0x00000] 
  at System.IO.FileStream.Flush () [0x00000] 
  at System.IO.StreamWriter.Flush () [0x00000] 
  at Tomboy.FileLogger.Log (Level lvl, System.String msg, System.Object[] args) [0x00000] 
  at Tomboy.Logger.Log (Level lvl, System.String msg, System.Object[] args) [0x00000] 
  at Tomboy.Logger.Log (System.String msg, System.Object[] args) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory, System.String backup_directory) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 

---

### Post by Elfy on 2009-07-13
Both OO and tomboy are reporting disk full - are you sure that the / or /home if you have a seperate are not full?

What does this report
```
df -h
```

---

### Post by Achilles124 on 2009-07-13
Bestandssysteem            Grtte   Gebr Besch Geb% Aangekoppeld op
/dev/sda1             142G  140G     0 100% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  244K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  176K 1007M   1% /dev
tmpfs                1007M  116K 1007M   1% /dev/shm
lrm                  1007M  2,4M 1005M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1,0M   36K  988K   4% /tmp

so, yes again, my harddisk seems to be full. Incredible. I will write this command down and check from time to time. Will try to transport some files from my harddisk.

---

### Post by Elfy on 2009-07-13
Check the trash - and check for hidden files (Ctrl+H) - also you can check the root trash.

Useful link - [http://ubuntuforums.org/showpost.php?p=5649417&postcount=1](http://ubuntuforums.org/showpost.php?p=5649417&postcount=1)

---

### Post by Achilles124 on 2009-07-13
ah, I found the culprit:

ecmpeek@ecmpeek-desktop:/$ sudo du -h --max-depth=1 / | grep '[0-9]G\>'
48G	/media
du: kan geen toegang krijgen tot `/home/ecmpeek/.gvfs': Toegang geweigerd
36G	/home
6,4G	/usr
94G	/var
du: kan geen toegang krijgen tot `/proc/10016/task/10016/fd/3': Bestand of map bestaat niet
du: kan geen toegang krijgen tot `/proc/10016/task/10016/fdinfo/3': Bestand of map bestaat niet
du: kan geen toegang krijgen tot `/proc/10016/fd/3': Bestand of map bestaat niet
du: kan geen toegang krijgen tot `/proc/10016/fdinfo/3': Bestand of map bestaat niet
184G	/
ecmpeek@ecmpeek-desktop:/$ 

There is 94 Gig of information on /var. Do I read this correctly?

---

### Post by Elfy on 2009-07-13
yes you do - I would now check in /var - particualrly the logs - I know there was a bug a while ago causing that

```
sudo du -h --max-depth=1 /var
```

```
sudo du -h --max-depth=1 /var/log
```

---

### Post by Elfy on 2009-07-13
Check here - [http://ubuntuforums.org/showthread.php?t=984941](http://ubuntuforums.org/showthread.php?t=984941) post#8 is one I was expecting to find

---

### Post by Achilles124 on 2009-07-13
Here are the results: the pain is not in the logs but in the backup:
ecmpeek@ecmpeek-desktop:~$ sudo du -h --max-depth=1 /var
> 
4,0K	/var/opt
2,5M	/var/spool
64K	/var/games
3,3M	/var/tmp
4,0K	/var/local
343M	/var/lib
4,0K	/var/crash
244K	/var/run
93G	/var/backup
29M	/var/log
204K	/var/mail
0	/var/lock
136M	/var/cache
9,5M	/var/backups
94G	/var

I installed **Simple Backup Suite** and something went wrong running it but I didn't paid much attention to it. Now do I have to simply remove the contents of the file?

---

### Post by Elfy on 2009-07-13
Yep - run nautilus as root

```
gksudo nautilus
```

Delete them - I would do shift+delete so they don't go to the trash

---

### Post by Achilles124 on 2009-07-13
How to remove these files?:

root@ecmpeek-desktop:/var/backup# ls
> 
2009-06-19_10.29.50.552012.ecmpeek-desktop.ful
2009-06-19_10.34.57.489779.ecmpeek-desktop.ful
2009-07-02_10.39.54.743104.ecmpeek-desktop.ful
2009-07-03_17.32.38.065295.ecmpeek-desktop.ful
2009-07-05_08.34.14.761257.ecmpeek-desktop.ful
2009-07-06_07.00.40.912238.ecmpeek-desktop.inc
2009-07-07_07.07.42.880685.ecmpeek-desktop.inc
2009-07-08_07.09.41.236888.ecmpeek-desktop.inc
2009-07-09_07.18.26.700540.ecmpeek-desktop.inc
2009-07-10_07.13.58.745650.ecmpeek-desktop.inc
2009-07-11_08.46.04.499648.ecmpeek-desktop.inc
2009-07-13_08.48.48.274035.ecmpeek-desktop.ful

they are all maps and not files. How do I remove these? And when I do it manually, will this not interfere with Simple Backup Suite?

---

### Post by Elfy on 2009-07-13
Only ever had a cursory look at SBS - but is there something in it's preferences to delete old backups?

If you want them you'll need to backup up the backups I suppose.

I would suggest that the .ful are full backups, .inc being incrementals, other than that I can;t be of much more assistance here.

---

### Post by Achilles124 on 2009-07-13
thank you very much, forestpixie. Wouldn't have fixed it myself.:KS

---

### Post by Elfy on 2009-07-13
There appears to be a purge option in the SBS properties - [https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

