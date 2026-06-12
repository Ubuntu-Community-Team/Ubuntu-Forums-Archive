---
title: "Problem Rsync in LAN"
date: 2017-12-05
forum: Networking &amp; Wireless
---

### Post by chandler1408 on 2017-12-05
Good morning at all,
I recently updated to ubuntu 17.10, with the last kernel 4.13.0-17-generic.
From that moment, my backup script not working... Is a backup script I've been using for years...
My backup script save the document on Windows file server, where I've personal folder...


This is a part of /etc/fstab


```

## PER FILESERVER
//fileserver/utenti/*           /home/*/fileserver/P       cifs    nofail,username=*,domain=*,password=*,uid=1000,gid=1000,vers=2.1 0 0

```


This is the script:


```

#!/bin/sh
## SCRIPT PER BACKUP INCREMENTALE TRAMITE RSYNC
## EFFETTUA UPDATE DELLE DIRECTORY E FILE SU NAS CON CANCELLAZIONE DEGLI STESSI SE NON PIU' ESISTENTI NELL'ORIGINE
set -x


echo Backup in corso `date +"%Y-%m-%d_%H:%M:%S"`
echo Backup in corso `date +"%Y-%m-%d_%H:%M:%S"` > /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log


df -h | grep fileserver/*
VAR_esito_mount=$?


## CONTROLLO CHE LA DIRECTORY DI DESTINAZIONE ESISTA
if [ $VAR_esito_mount -ne "0" ] ; then
echo ------------------------ >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
        echo "`date +"%Y-%m-%d_%H:%M:%S"`: Il mountpoint non e' presente. Esco dalla procedura" >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
        exit 1
else
echo ------------------------ >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
  echo "`date +"%Y-%m-%d_%H:%M:%S"`: Il mountpoint e' presente. Proseguo" >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
fi
echo ------------------------ >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log


## VERIFICO L'ESISTENZA DELLA DIRECTORY DI DESTINAZIONE DEL BACKUP SU NAS
if test -d /home/*/fileserver/P/backup_HP_linux
then
echo "La directory del salvataggio esisteva - non la creo" >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
else
mkdir -p /home/*/fileserver/P/backup_HP_linux
echo "La directory del salvataggio non esisteva - la creo" >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
fi


## EFFETTUO L'ELENCO DEI PACCHETTI INSTALLATI
dpkg -l > /home/*/fileserver/P/backup_HP_linux/dpkg_list.txt


## EFFETTUO L'RSYNC DEI DOCUMENTI DI *
time rsync -va --delete-after /home/*/Scrivania/Documenti_* /home/*/fileserver/P/backup_HP_linux/ --no-owner --no-group >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
VAR_esito_backup_doc_*=$?


##EFFETTUO TEST SUGLI EXIT CODE DOPO OGNI COMANDO (VARIABILI DEFINITE SOPRA)
echo >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
if [ $VAR_esito_backup_doc_* -ne "23" ] ; then
echo ------------------------ >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
        echo "`date +"%Y-%m-%d_%H:%M:%S"`: Rsync terminato con codice diverso da 23. Controlla" >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
else
echo ------------------------ >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
  echo "`date +"%Y-%m-%d_%H:%M:%S"`: Rsync terminato con codice 23. Non necessario controllo" >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
fi
echo ------------------------ >> /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log


tail -n 14 /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log

```


What happens when I start the script:


```

$ ./backup_documenti_*.sh
+ date +%Y-%m-%d_%H:%M:%S
+ echo Backup in corso 2017-11-27_14:57:03
Backup in corso 2017-11-27_14:57:03
+ date +%Y-%m-%d_%H:%M:%S
+ echo Backup in corso 2017-11-27_14:57:03
+ + grep fileserver/*
df -h
//fileserver.*/*  5,0G  168K    5,0G   1% /home/*/fileserver/*
+ VAR_esito_mount=0
+ [ 0 -ne 0 ]
+ echo ------------------------
+ date +%Y-%m-%d_%H:%M:%S
+ echo 2017-11-27_14:57:03: Il mountpoint e' presente. Proseguo
+ echo ------------------------
+ test -d /home/*/fileserver/P/backup_HP_linux
+ echo La directory del salvataggio esisteva - non la creo
./backup_documenti_*.sh: 36: ./backup_documenti_*.sh: cannot create /home/*/fileserver/P/backup_HP_linux/dpkg_list.txt: File name too long
+ dpkg -l
+ time rsync -va --delete-after /home/*/Scrivania/Documenti_* /home/*/fileserver/P/backup_HP_linux/ --no-owner --no-group
rsync: recv_generator: mkdir "/home/*/fileserver/P/backup_HP_linux/Documenti_*" failed: File name too long (36)
*** Skipping any contents from this failed directory ***
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1196) [sender=3.1.2]
Command exited with non-zero status 23
0.01user 0.01system 0:00.03elapsed 96%CPU (0avgtext+0avgdata 2920maxresident)k
0inputs+0outputs (0major+405minor)pagefaults 0swaps
+ VAR_esito_backup_doc_*=23
+ echo
+ [ 23 -ne 23 ]
+ echo ------------------------
+ date +%Y-%m-%d_%H:%M:%S
+ echo 2017-11-27_14:57:03: Rsync terminato con codice 23. Non necessario controllo
+ echo ------------------------
+ tail -n 14 /home/*/Scrivania/Documenti_*/Utility/backup_documenti_*_sh.log
Backup in corso 2017-11-27_14:57:03
------------------------
2017-11-27_14:57:03: Il mountpoint e' presente. Proseguo
------------------------
La directory del salvataggio esisteva - non la creo
Documenti_*/


sent 58,783 bytes  received 207 bytes  117,980.00 bytes/sec
total size is 302,109,145  speedup is 5,121.36


------------------------
2017-11-27_14:57:03: Rsync terminato con codice 23. Non necessario controllo

```


"failed: File name too long (36)"


Ideas? Before the kernel update, it worked...


Thank you!

---

