---
title: "[SOLVED] Still with no wireless I need heeeeelp"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by beidache on 2008-10-22
Helllo everyone

I have problems with my wireless connection, my computer is dell latitud d620, Im already reboot my laptop change from Ubuntu 8.04 64bit to 32 bit I star the installation and I followed this steps, but still with out wireless connection actually Im doing everything via ethernet 

petacho@petacho-lap:~$ echo -e 'blacklist bcm43xx\nblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist 
[sudo] password for petacho: 
blacklist bcm43xx 
blacklist wl 
petacho@petacho-lap:~$ sudo apt-get install ndiswrapper-utils-1.9 
Leyendo lista de paquetes... Hecho 
Creando árbol de dependencias       
Leyendo la información de estado... Hecho 
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios. 
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19 
Utilice «apt-get autoremove» para eliminarlos. 
Se instalarán los siguientes paquetes extras: 
  ndiswrapper-common 
Paquetes sugeridos: 
  ndiswrapper-source 
Se instalarán los siguientes paquetes NUEVOS: 
  ndiswrapper-common ndiswrapper-utils-1.9 
0 actualizados, 2 se instalarán, 0 para eliminar y 0 no actualizados. 
Necesito descargar 30,4kB de archivos. 
Se utilizarán 213kB de espacio de disco adicional después de desempaquetar. 
¿Desea continuar [S/n]? s 
Des:1 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hardy/main ndiswrapper-common 1.50-1ubuntu1 [11,4kB] 
Des:2 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hardy/main ndiswrapper-utils-1.9 1.50-1ubuntu1 [19,0kB] 
Descargados 30,4kB en 3s (8913B/s)            
Seleccionando el paquete ndiswrapper-common previamente no seleccionado. 
(Leyendo la base de datos ...  
113998 ficheros y directorios instalados actualmente.) 
Desempaquetando ndiswrapper-common (de .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ... 
Seleccionando el paquete ndiswrapper-utils-1.9 previamente no seleccionado. 
Desempaquetando ndiswrapper-utils-1.9 (de .../ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) ... 
Configurando ndiswrapper-common (1.50-1ubuntu1) ... 
Configurando ndiswrapper-utils-1.9 (1.50-1ubuntu1) ... 
petacho@petacho-lap:~$ mkdir ~/bcm43xx; cd ~/bcm43xx 
petacho@petacho-lap:~/bcm43xx$ sudo apt-get install cabextract 
Leyendo lista de paquetes... Hecho 
Creando árbol de dependencias       
Leyendo la información de estado... Hecho 
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios. 
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19 
Utilice «apt-get autoremove» para eliminarlos. 
Se instalarán los siguientes paquetes NUEVOS: 
  cabextract 
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados. 
Necesito descargar 53,9kB de archivos. 
Se utilizarán 188kB de espacio de disco adicional después de desempaquetar. 
Des:1 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) hardy/universe cabextract 1.2-2 [53,9kB] 
Descargados 53,9kB en 2s (19,9kB/s) 
Seleccionando el paquete cabextract previamente no seleccionado. 
(Leyendo la base de datos ...  
114020 ficheros y directorios instalados actualmente.) 
Desempaquetando cabextract (de .../cabextract_1.2-2_i386.deb) ... 
Configurando cabextract (1.2-2) ... 
petacho@petacho-lap:~/bcm43xx$ wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe) 
--00:53:39--  [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe) 
           => `sp34152.exe' 
Resolviendo ftp.compaq.com... 161.114.23.171 
Conectando a ftp.compaq.com|161.114.23.171|:21... conectado. 
Identificándose como anonymous ... ¡Conectado! 
==> SYST ... hecho.    ==> PWD ... hecho. 
==> TYPE I ... hecho.  ==> CWD /pub/softpaq/sp34001-34500 ... hecho. 
==> PASV ... hecho.    ==> RETR sp34152.exe ... hecho. 

    [   <=>                               ] 4,494,456     14.19K/s             

00:57:21(20.19 KB/s) - `sp34152.exe' guardado [4494456] 

petacho@petacho-lap:~/bcm43xx$ cabextract sp34152.exe 
Extracting cabinet: sp34152.exe 
  extracting bcm1xsup.dll 
  extracting bcm43xx.cat 
  extracting bcm43xx64.cat 
  extracting Bcmnpf64.sys 
  extracting bcmwl5.inf 
  extracting bcmwl5.sys 
  extracting bcmwl564.sys 
  extracting bcmwliss.dll 
  extracting bcmwlnpf.sys 
  extracting bcmwlpkt.dll 
  extracting bcmwls.ini 
  extracting bcmwls32.exe 
  extracting bcmwls64.exe 
  extracting bcmwlu00.exe 
  extracting data1.cab 
  extracting data1.hdr 
  extracting data2.cab 
  extracting ikernel.ex_ 
  extracting is.exe 
  extracting launcher.ini 
  extracting layout.bin 
  extracting setup.exe 
  extracting Setup.ini 
  extracting setup.inx 
  extracting setup.iss 
  extracting sp34152.cva 

All done, no errors. 
petacho@petacho-lap:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf 
installing bcmwl5 ... 
petacho@petacho-lap:~/bcm43xx$ ndiswrapper -l 
bcmwl5 : driver installed 
	device (14E4:4311) present (alternate driver: ssb) 
petacho@petacho-lap:~/bcm43xx$ sudo depmod -a 
petacho@petacho-lap:~/bcm43xx$ sudo modprobe ndiswrapper 
petacho@petacho-lap:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig 
petacho@petacho-lap:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces 
auto lo 
iface lo inet loopback 

petacho@petacho-lap:~/bcm43xx$ sudo ndiswrapper -m 
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ... 

************************************************************************ 
* 
* The update-modules command is deprecated and should not be used! 
* 
************************************************************************ 

petacho@petacho-lap:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules 
ndiswrapper 
petacho@petacho-lap:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant 
ENABLED=0 
petacho@petacho-lap:~/bcm43xx$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Wireless interface 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       logical name: eth1 
       version: 01 
       serial: 00:1b:fc:00:87:b3 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11 
  *-network 
       description: Ethernet interface 
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:18:8b:c6:6c:bb 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5752-v3.19 ip=192.168.1.101 latency=0 module=tg3 multicast=yes


Hope someone can help me thanks in advance

---

### Post by Ayuthia on 2008-10-22
You also need to blacklist b43 and ssb:
```
echo -e 'blacklist b43\nblacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist
```
After that, to test your wireless:
```
sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo iwlist scan
```

Hope that helps.

---

### Post by beidache on 2008-10-22
Thanks for your answer but still not wireless this is what i got:

petacho@petacho-lap:~$ echo -e 'blacklist b43\nblacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist
blacklist b43
blacklist ssb
petacho@petacho-lap:~$ sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
petacho@petacho-lap:~$ sudo modprobe ndiswrapper
petacho@petacho-lap:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:4E:C9:1A
                    ESSID:"wxywpyhome"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:14:78:D8:F9:C8
                    ESSID:"rpyinhua"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:19:E0:C7:76:88
                    ESSID:"TP-LINK"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:15:E9:0C:A4:E0
                    ESSID:"fortune909"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:B0:0C:02:CF:EF
                    ESSID:"ChiLingChi"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

petacho@petacho-lap:~$

---

### Post by Ayuthia on 2008-10-22
It looks like you are able to see wireless sites.  You might try turning off the WEP encryption and see if you can connect or you can try:
```
sudo iwconfig wlan0 essid TP-LINK key <password without brackets>
sudo dhclient wlan0
```

---

### Post by beidache on 2008-10-23
Thank you soooooo much the problem was fix with this:

You also need to blacklist b43 and ssb:
Code:

echo -e 'blacklist b43\nblacklist ssb' | sudo tee -a /etc/modprobe.d/blacklist

After that, to test your wireless:
Code:

sudo modprobe -r b43 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo iwlist scan

Hope that helps.


After that I reboot the reuter and started to work I appreciate so much your info

---

### Post by MakingHeadway on 2008-10-24
This fix also worked for me, except that upon restarting or logging in again, my settings aren't saved and I have to start the process all over again. Both on 8.04 and 8.10. 

Any assistance?

---

### Post by Ayuthia on 2008-10-24
Please post the results of the following:
```
cat /etc/modprobe.d/blacklist|grep -e b43 -e ssb -e ndiswrapper -e wl -e bcm43xx
cat /etc/modules|grep -e b43 -e ssb -e ndiswrapper -e wl -e bcm43xx
```
From there, we can determine what needs to be blacklisted and what needs to be added to the module loading file.

---

### Post by MakingHeadway on 2008-10-25
> **Ayuthia said:**
> Please post the results of the following:
```
cat /etc/modprobe.d/blacklist|grep -e b43 -e ssb -e ndiswrapper -e wl -e bcm43xx
cat /etc/modules|grep -e b43 -e ssb -e ndiswrapper -e wl -e bcm43xx
```
From there, we can determine what needs to be blacklisted and what needs to be added to the module loading file.

First is:
blacklist b43
blacklist b43
blacklist ssb
blacklist b43
blacklist ssb

The next command returns nothing.

---

### Post by Ayuthia on 2008-10-25
> **MakingHeadway said:**
> First is:
blacklist b43
blacklist b43
blacklist ssb
blacklist b43
blacklist ssb

The next command returns nothing.

You definitely have b43 and ssb blacklisted but you are missing bcm43xx and wl.  You just need to have ndiswrapper loaded:
```

echo -e 'blacklist bcm43xx\nblacklist wl'|sudo tee -a /etc/modprobe.d/blacklist
echo ndiswrapper|sudo tee -a /etc/modules
```

---

### Post by MakingHeadway on 2008-10-25
Thanks, I'll give that a shot when I get back to the homestead.

---

