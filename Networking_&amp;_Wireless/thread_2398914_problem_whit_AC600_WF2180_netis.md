---
title: "problem whit AC600 WF2180 netis"
date: 2018-08-19
forum: Networking &amp; Wireless
---

### Post by nino-c on 2018-08-19
Hello,
I'am new in this forum.
I have a problem whit AC600 wireless dual band USB adapter WF2180 Netis, it's seem not work... now I'am connected whit another wireless adapter powerless. This adapter work perfectly on my pc Win10.

nino@Linux:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 010: ID 0ace:1215 ZyDAS ZD1211B 802.11g
Bus 001 Device 004: ID 1a2c:2124 China Resource Semico Co., Ltd 
Bus 001 Device 003: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. Hub
[COLOR=#ff0000]Bus 001 Device 012: ID 0bda:0811 Realtek Semiconductor Corp[/COLOR]. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

whit hardinfo I can't find it...

this it my wireless configuration: [https://pastebin.com/GMZiXLSK](https://pastebin.com/GMZiXLSK)

I try to use the install.sh, this is the result:
```
nino@Linux:~$ #!/bin/bash
nino@Linux:~$ # Auto install for 8192cu
nino@Linux:~$ # September, 1 2010 v1.0.0, willisTang
nino@Linux:~$ # 
nino@Linux:~$ # Add make_drv to select chip type
nino@Linux:~$ # Novembor, 21 2011 v1.1.0, Jeff Hung
nino@Linux:~$ ################################################################################
nino@Linux:~$ 
nino@Linux:~$ echo "##################################################"
##################################################
nino@Linux:~$ echo "Realtek Wi-Fi driver Auto installation script"
Realtek Wi-Fi driver Auto installation script
nino@Linux:~$ echo "Novembor, 21 2011 v1.1.0"
Novembor, 21 2011 v1.1.0
nino@Linux:~$ echo "##################################################"
##################################################
nino@Linux:~$ 
nino@Linux:~$ ################################################################################
nino@Linux:~$ #Decompress the driver source tal ball
nino@Linux:~$ ################################################################################
nino@Linux:~$ cd driver
bash: cd: driver: File o directory non esistente
nino@Linux:~$ Drvfoulder=`ls |grep .tar.gz`
nino@Linux:~$ echo "Decompress the driver source tar ball:"
Decompress the driver source tar ball:
nino@Linux:~$ echo ""$Drvfoulder
wireless-info.tar.gz
nino@Linux:~$ tar zxvf $Drvfoulder
wireless-info.txt
nino@Linux:~$ 
nino@Linux:~$ Drvfoulder=`ls |grep -iv '.tar.gz'`
nino@Linux:~$ echo "$Drvfoulder"
Blocco traffico Milano Ottobre 2017.odt
Documenti
etc
examples.desktop
Foto Cresima Jordan
Immagini
Modelli
Musica
Pubblici
quotidiani luglio 2016
Reader XI   Manuale Monitor 24T390
Registrazioni
Ricerche ottobre 2016
Scaricati
Scrivania
Video
wireless-info
wireless-info.txt
nino@Linux:~$ cd  $Drvfoulder
bash: cd: Blocco: File o directory non esistente
nino@Linux:~$ 
nino@Linux:~$ ################################################################################
nino@Linux:~$ #If makd_drv exixt, execute it to select chip type
nino@Linux:~$ ################################################################################
nino@Linux:~$ if [ -e ./make_drv ]; then
> ./make_drv
> fi
nino@Linux:~$ 
nino@Linux:~$ ################################################################################
nino@Linux:~$ #                       make clean
nino@Linux:~$ ################################################################################
nino@Linux:~$ echo "Authentication requested [root] for make clean:"
Authentication requested [root] for make clean:
nino@Linux:~$ if [ "`uname -r |grep fc`" == " " ]; then
>         sudo su -c "make clean"; Error=$?
> else
>         su -c "make clean"; Error=$?
> fi
Password: 
make: ***  Nessuna regola per generare l'obiettivo "clean".  Arresto.
```

I try to download new driver for this link: [http://www.netis-systems.com/Suppory/de_details/id/1/de/126.html](http://www.netis-systems.com/Suppory/de_details/id/1/de/126.html)
but the file seems not work...

can you help me?
thanks
Nino

---

### Post by jeremy31 on 2018-08-19
Try
```
 sudo apt-get install dkms git build-essential
 git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
 cd rtl8812AU_8821AU_linux
 sudo make -f Makefile.dkms install
```

Check ```
mokutil --sb-state
```
If that shows Secure Boot enabled, then reboot and disable Secure Boot in UEFI/BIOS and see if wireless then works in Ubuntu

---

### Post by nino-c on 2018-08-20
Thank you Jeremy! It's works perfectly!

Nino

---

### Post by nino-c on 2018-11-24
Hello,
sorry but from update of ubuntu (22 October - version 18.04) I have a problem whit 5GHZ wireless, the dongle is dual band and 2,4Ghz works perfectly, I try to reinstall dongle, to verifiy router but other client works on 5GHz... wha'ts wrong?

thanks

---

