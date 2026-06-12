---
title: "help installing brother all in one printer scanner fax"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by czig49 on 2010-10-19
i am trying to install printer/scanner/fax for a brother mfc-j410w all in one. downloaded drivers from brother for printer and scanner. sp far i can print (only when connected by usb) and cannot scan at all went to brothers support  what they asked me to type in  idid  and get permission denied.  im new to all this  and would appriciate help  am using 10.04 scanner error is no device

---

### Post by patrik k on 2010-10-20
Just installed a Brother mfc myself.
Only glitch was in the scanner. Loading drivers alone does not do it.
Started out @ this site-
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
This site is for LInux drivers.
I started with the printer then scanner drivers.
You must find your exact machine amongst all of them.
 Poke around this site.
You will find this code under scanner instructions to add in terminal; it is the actual instruction/code for your machine but verify @ site.

```
Ubuntu 9.10, 10.04 **1.** Open "/lib/udev/rules.d/40-libsane.rules" file.**2.**Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
  
  
  The lines to be added---------------------------               # Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"        **3.** Restart the OS.
```It took a bit for me but all is working.
And you will need to use sudo with your command to have root (administrator) rights.
I too am learning so best you double check at this site for correct code.

---

### Post by patrik k on 2010-10-20
this is the page with your machines (mfc-j410w) instructions
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)
scroll down to bottom under brscan3 models and take it from there.
Best of luck

---

### Post by czig49 on 2010-10-20
i am very new  so be patient  with me  but this is what i tried and got back in terminal

dave@dave-laptop:~$ sudo"/lib/udev/rules.d/40-libsane.rules"
bash: sudo/lib/udev/rules.d/40-libsane.rules: No such file or directory
dave@dave-laptop:~$ sudo "/lib/udev/rules.d/40-libsane.rules"
[sudo] password for dave: 
Sorry, try again.
[sudo] password for dave: 
sudo: /lib/udev/rules.d/40-libsane.rules: command not found
dave@dave-laptop:~$ "/lib/udev/rules.d/40-libsane.rules"
bash: /lib/udev/rules.d/40-libsane.rules: Permission denied
dave@dave-laptop:~$ 

im doing something wrong i just dont know  what....,,.dave  ubuntu 10.04 LTS

---

### Post by patrik k on 2010-10-20
Try-
```
 sudo pico /lib/udev/rules.d/40-libsane.rules
```
Don't use quotations in command

pico is used to open/edit 
No worries.

---

### Post by czig49 on 2010-10-20
ok now i g et  this  what and how do i add    thanks GNU nano 2.2.2                                    File: /lib/udev/rules.d/40-libsane.rules                                                                                

# Hewlett-Packard ScanJet 5470c
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="1105", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet 5550C
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="1205", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet 4570C
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="1305", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet 5590
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="1705", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet 7650
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="1805", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet 3530C | Hewlett-Packard ScanJet 3570C
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="2005", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet 3500C
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="2205", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet 3970c
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="2305", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet 4070 Photosmart
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="2405", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet 3800
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="2605", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet G2710
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="2805", ENV{libsane_matched}="yes"
# Hewlett-Packard LaserJet M1005 MFP
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="3b17", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet 4370
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="4105", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet G3010
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="4205", ENV{libsane_matched}="yes"
# Hewlett-Packard ScanJet G3110
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="4305", ENV{libsane_matched}="yes"
# Hewlett-Packard LaserJet M1120 MFP
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="5617", ENV{libsane_matched}="yes"
# Hewlett-Packard LaserJet M1120n MFP
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="5717", ENV{libsane_matched}="yes"
# Mustek BearPaw 1200
ATTRS{idVendor}=="0400", ATTRS{idProduct}=="1000", ENV{libsane_matched}="yes"
# Mustek BearPaw 1200 | Mustek BearPaw 2400
ATTRS{idVendor}=="0400", ATTRS{idProduct}=="1001", ENV{libsane_matched}="yes"
# Kodak i30
ATTRS{idVendor}=="040a", ATTRS{idProduct}=="6001", ENV{libsane_matched}="yes"
# Kodak i40
ATTRS{idVendor}=="040a", ATTRS{idProduct}=="6002", ENV{libsane_matched}="yes"
# Kodak i50
ATTRS{idVendor}=="040a", ATTRS{idProduct}=="6003", ENV{libsane_matched}="yes"
# Kodak i60
ATTRS{idVendor}=="040a", ATTRS{idProduct}=="6004", ENV{libsane_matched}="yes"
# Kodak i80
ATTRS{idVendor}=="040a", ATTRS{idProduct}=="6005", ENV{libsane_matched}="yes"
# Creative WebCam Go Mini
ATTRS{idVendor}=="041e", ATTRS{idProduct}=="4007", ENV{libsane_matched}="yes"
et this

---

### Post by patrik k on 2010-10-20
You have to add the command
```
 # Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"



```

to the bottom of the list.
Basically, you are just adding this machine to the printer device list.
See my first message.
Look at the list and you will see this command is the same other than the "04f9" portion.
Add in exactly the same format as all the others, save, re-boot and scanner should work.
Will follow up tomorrow.

---

### Post by czig49 on 2010-10-20
absolutely  no luck   still says no devices connected.  have not done the terminal thing before  and  it just isnt doing anything for me.  again thanks for your patience.   please  anyone  that can make this easy   Help

---

### Post by patrik k on 2010-10-20
Go to terminal and type in-
```
 sudo cat /lib/udev/rules.d/40-libsane.rules
```
Then post the results
 I need to see if you have added the scanner

---

### Post by czig49 on 2010-10-20
ok

ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2204", ENV{libsane_matched}="yes"
# Canon CanoScan N650U/N656U
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2206", ENV{libsane_matched}="yes"
# Canon CanoScan N1220U
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2207", ENV{libsane_matched}="yes"
# Canon CanoScan D660U
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2208", ENV{libsane_matched}="yes"
# Canon CanoScan N670U/N676U/LiDE20
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="220d", ENV{libsane_matched}="yes"
# Canon CanoScan N1240U/LiDE30
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="220e", ENV{libsane_matched}="yes"
# Canon CanoScan LiDE 35 | Canon CanoScan LiDE 40 | Canon CanoScan LiDE 50
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2213", ENV{libsane_matched}="yes"
# Canon CanoScan LiDE 60
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="221c", ENV{libsane_matched}="yes"
# Canon CanoScan LiDE25
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2220", ENV{libsane_matched}="yes"
# Canon DR-1210C
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2222", ENV{libsane_matched}="yes"
# Canon MultiPASS MP730
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="262f", ENV{libsane_matched}="yes"
# Canon MultiPASS MP700
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2630", ENV{libsane_matched}="yes"
# Canon SmartBase MP360
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="263c", ENV{libsane_matched}="yes"
# Canon SmartBase MP370
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="263d", ENV{libsane_matched}="yes"
# Canon SmartBase MP390
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="263e", ENV{libsane_matched}="yes"
# Canon PIXMA MP740
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="264c", ENV{libsane_matched}="yes"
# Canon PIXMA MP710
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="264d", ENV{libsane_matched}="yes"
# Canon imageCLASS MF5630
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="264e", ENV{libsane_matched}="yes"
# Canon laserBase MF5650
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="264f", ENV{libsane_matched}="yes"
# Canon imageCLASS MF8170c
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2659", ENV{libsane_matched}="yes"
# Canon imageCLASS MF5730
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="265d", ENV{libsane_matched}="yes"
# Canon imageCLASS MF5750
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="265e", ENV{libsane_matched}="yes"
# Canon imageCLASS MF5770
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="265f", ENV{libsane_matched}="yes"
# Canon imageCLASS MF3110
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2660", ENV{libsane_matched}="yes"
# Canon imageCLASS MF3240
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2684", ENV{libsane_matched}="yes"
# Canon imageCLASS MF6500 series
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2686", ENV{libsane_matched}="yes"
# Canon imageCLASS MF4120 | Canon imageCLASS MF4122 | Canon imageCLASS MF4140
# Canon imageCLASS MF4150
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="26a3", ENV{libsane_matched}="yes"
# Canon imageCLASS MF4690
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="26b0", ENV{libsane_matched}="yes"
# Canon imageCLASS MF4010 | Canon imageCLASS MF4018
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="26b4", ENV{libsane_matched}="yes"
# Canon imageCLASS MF4270
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="26b5", ENV{libsane_matched}="yes"
# Nikon LS 40 ED | Nikon LS 40 ED | Nikon Coolspan IV
ATTRS{idVendor}=="04b0", ATTRS{idProduct}=="4000", ENV{libsane_matched}="yes"
# Nikon LS 50 ED | Nikon Coolscan V ED | Nikon LS 50 ED
# Nikon Coolscan V ED
ATTRS{idVendor}=="04b0", ATTRS{idProduct}=="4001", ENV{libsane_matched}="yes"
# Nikon Super Coolscan LS-5000 ED | Nikon Super Coolscan LS-5000 ED
ATTRS{idVendor}=="04b0", ATTRS{idProduct}=="4002", ENV{libsane_matched}="yes"
# Epson Perfection 636U | Epson Perfection 636U
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0101", ENV{libsane_matched}="yes"
# Epson Perfection 610 | Epson Perfection 610
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0103", ENV{libsane_matched}="yes"
# Epson Perfection 1200U | Epson Perfection 1200Photo | Epson Perfection 1200U / 1200 Photo
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0104", ENV{libsane_matched}="yes"
# Epson Expression 1600 | Epson Expression 1600
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0107", ENV{libsane_matched}="yes"
# Epson Perfection 1640 | Epson Perfection 1640
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="010a", ENV{libsane_matched}="yes"
# Epson Perfection 1240 | Epson Perfection 1240
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="010b", ENV{libsane_matched}="yes"
# Epson Perfection 640 | Epson Perfection 640
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="010c", ENV{libsane_matched}="yes"
# Epson Expression 1680 | Epson Expression 1680
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="010e", ENV{libsane_matched}="yes"
# Epson Perfection 1250 | Epson Perfection 1250Photo
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="010f", ENV{libsane_matched}="yes"
# Epson Perfection 1650 | Epson Perfection 1650
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0110", ENV{libsane_matched}="yes"
# Epson Perfection 2450 | Epson Perfection 2450
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0112", ENV{libsane_matched}="yes"
# Epson Perfection 660
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0114", ENV{libsane_matched}="yes"
# Epson Perfection 2400 | Epson Perfection 2400
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="011b", ENV{libsane_matched}="yes"
# Epson Perfection 3200 | Epson Perfection 3200
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="011c", ENV{libsane_matched}="yes"
# Epson Perfection 1260 | Epson Perfection 1260Photo
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="011d", ENV{libsane_matched}="yes"
# Epson Perfection 1660 | Epson Perfection 1660
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="011e", ENV{libsane_matched}="yes"
# Epson Perfection 1670
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="011f", ENV{libsane_matched}="yes"
# Epson Perfection 1270
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0120", ENV{libsane_matched}="yes"
# Epson Perfection 2480 | Epson Perfection 2580
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0121", ENV{libsane_matched}="yes"
# Epson Perfection 3490 | Epson Perfection 3590
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0122", ENV{libsane_matched}="yes"
# Epson Perfection 4870 | Epson Perfection 4870
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0128", ENV{libsane_matched}="yes"
# Epson Perfection 4990 | Epson Perfection 4990
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="012a", ENV{libsane_matched}="yes"
# Epson V700 | Epson V750 | Epson V700
# Epson V750
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="012c", ENV{libsane_matched}="yes"
# Epson CX-5200 | Epson CX-5400 | Epson CX-5200
# Epson CX-5400
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0801", ENV{libsane_matched}="yes"
# Epson CX-3200 | Epson CX-3200
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0802", ENV{libsane_matched}="yes"
# Epson CX-6300 | Epson CX-6400 | Epson CX-6300
# Epson CX-6400
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0805", ENV{libsane_matched}="yes"
# Epson RX-600 | Epson RX-600
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0806", ENV{libsane_matched}="yes"
# Epson RX-500 | Epson RX-500
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0807", ENV{libsane_matched}="yes"
# Epson CX-5400 | Epson CX-5400
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0808", ENV{libsane_matched}="yes"
# Epson Stylus CX-1500
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="080c", ENV{libsane_matched}="yes"
# Epson CX-4600 | Epson CX-4600
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="080d", ENV{libsane_matched}="yes"
# Epson CX-3600 | Epson CX-3650 | Epson CX-3600
# Epson CX-3650
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="080e", ENV{libsane_matched}="yes"
# Epson RX-425 | Epson RX-425
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="080f", ENV{libsane_matched}="yes"
# Epson RX-700 | Epson RX-700
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0810", ENV{libsane_matched}="yes"
# Epson RX-620 | Epson RX-620
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0811", ENV{libsane_matched}="yes"
# Epson CX-6500 | Epson CX-6600 | Epson CX-6500
# Epson CX-6600
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0813", ENV{libsane_matched}="yes"
# Epson AcuLaser CX11 | Epson AcuLaser CX11NF | Epson AcuLaser CX11 series
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0815", ENV{libsane_matched}="yes"
# Epson DX-3850 | Epson CX-3700 | Epson CX-3800
# Epson DX-3800 | Epson DX-3850 | Epson CX-3700
# Epson CX-3800 | Epson DX-3800
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0818", ENV{libsane_matched}="yes"
# Epson CX-4800 | Epson CX-4800
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0819", ENV{libsane_matched}="yes"
# Epson CX-4200 | Epson CX-4200
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0820", ENV{libsane_matched}="yes"
# Epson CX-5000 | Epson DX-5000 | Epson DX-5050
# Epson CX-5000 | Epson DX-5000 | Epson DX-5050
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="082b", ENV{libsane_matched}="yes"
# Epson DX-6000 | Epson DX-6000
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="082e", ENV{libsane_matched}="yes"
# Epson DX-4050 | Epson DX-4050
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="082f", ENV{libsane_matched}="yes"
# Epson DX-7400 | Epson DX-7400
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0838", ENV{libsane_matched}="yes"
# Fujitsu fi-4010C
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1029", ENV{libsane_matched}="yes"
# Fujitsu fi-4110CU/SSF
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1033", ENV{libsane_matched}="yes"
# Fujitsu fi-4120C
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1041", ENV{libsane_matched}="yes"
# Fujitsu fi-4220C
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1042", ENV{libsane_matched}="yes"
# Fujitsu fi-4530C
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1078", ENV{libsane_matched}="yes"
# Fujitsu fi-5750C
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1095", ENV{libsane_matched}="yes"
# Fujitsu fi-5110EOX/2
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1096", ENV{libsane_matched}="yes"
# Fujitsu fi-5110C
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1097", ENV{libsane_matched}="yes"
# Fujitsu fi-5650C
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="10ad", ENV{libsane_matched}="yes"
# Fujitsu fi-4120C2
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="10ae", ENV{libsane_matched}="yes"
# Fujitsu fi-4220C2
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="10af", ENV{libsane_matched}="yes"
# Fujitsu fi-60F
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="10c7", ENV{libsane_matched}="yes"
# Fujitsu fi-4340C
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="10cf", ENV{libsane_matched}="yes"
# Fujitsu fi-5120C
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="10e0", ENV{libsane_matched}="yes"
# Fujitsu fi-5220C
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="10e1", ENV{libsane_matched}="yes"
# Fujitsu fi-5530C
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="10e2", ENV{libsane_matched}="yes"
# Fujitsu fi-5110EOX3
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="10e6", ENV{libsane_matched}="yes"
# Fujitsu fi-5900C
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="10e7", ENV{libsane_matched}="yes"
# Fujitsu fi-5110EOXM
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="10f2", ENV{libsane_matched}="yes"
# Fujitsu ScanSnap S500
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="10fe", ENV{libsane_matched}="yes"
# Fujitsu ScanSnap S500M
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1135", ENV{libsane_matched}="yes"
# Fujitsu fi-5530C2
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="114a", ENV{libsane_matched}="yes"
# Fujitsu fi-6140
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="114d", ENV{libsane_matched}="yes"
# Fujitsu fi-6240
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="114e", ENV{libsane_matched}="yes"
# Fujitsu fi-6130
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="114f", ENV{libsane_matched}="yes"
# Fujitsu fi-6230
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1150", ENV{libsane_matched}="yes"
# Fujitsu ScanSnap S510
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1155", ENV{libsane_matched}="yes"
# Fujitsu ScanSnap S300
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1156", ENV{libsane_matched}="yes"
# Fujitsu ScanSnap S510M
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="116f", ENV{libsane_matched}="yes"
# Fujitsu fi-6770
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1174", ENV{libsane_matched}="yes"
# Fujitsu fi-6770A
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1175", ENV{libsane_matched}="yes"
# Fujitsu fi-6670
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1176", ENV{libsane_matched}="yes"
# Fujitsu fi-6670A
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1177", ENV{libsane_matched}="yes"
# Fujitsu fi-6750S
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1178", ENV{libsane_matched}="yes"
# Fujitsu ScanSnap S300M
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="117f", ENV{libsane_matched}="yes"
# Fujitsu ScanSnap S1500
ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="11a2", ENV{libsane_matched}="yes"
# Konica e-mini
ATTRS{idVendor}=="04c8", ATTRS{idProduct}=="0722", ENV{libsane_matched}="yes"
# Samsung SCX-4200
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="341b", ENV{libsane_matched}="yes"
# Samsung SCX4725-FN
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="341f", ENV{libsane_matched}="yes"
# Samsung SCX-4500
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="3426", ENV{libsane_matched}="yes"
# Samsung CLX-3170fn
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="342a", ENV{libsane_matched}="yes"
# Samsung SCX-4300
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="342e", ENV{libsane_matched}="yes"
# Aiptek Aiptek Pencam
ATTRS{idVendor}=="0553", ATTRS{idProduct}=="0202", ENV{libsane_matched}="yes"
# Mustek ScanExpress 1200 CU
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="0001", ENV{libsane_matched}="yes"
# Mustek ScanExpress 600 CU
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="0002", ENV{libsane_matched}="yes"
# Mustek ScanExpress 1200 UB | Trust Compact Scan USB 19200
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="0006", ENV{libsane_matched}="yes"
# Mustek ScanExpress 1200 CU Plus
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="0008", ENV{libsane_matched}="yes"
# Mustek BearPaw 1200 F
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="0010", ENV{libsane_matched}="yes"
# Mustek ScanExpress A3 USB
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="0210", ENV{libsane_matched}="yes"
# Mustek BearPaw 2400 CS | Mustek BearPaw 2400 TA | Trust 240TH Easy Webscan Gold
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="0218", ENV{libsane_matched}="yes"
# Mustek BearPaw 2400 CS Plus | Mustek BearPaw 2400 TA Plus | Mustek Plug-n-Scan 2400 MT
# Mustek Plug-n-Scan 2400 M | Packard Bell Diamond 2450
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="0219", ENV{libsane_matched}="yes"
# Mustek BearPaw 2448 CS Plus | Mustek BearPaw 2448 TA Plus
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="021a", ENV{libsane_matched}="yes"
# Mustek BearPaw 1200 CU Plus | Packard Bell Diamond 1200 Plus
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="021b", ENV{libsane_matched}="yes"
# Mustek BearPaw 1200 CU Plus | Mustek BearPaw 1248 CU | Packard Bell Diamond 1200 Plus
# Trust Direct WebScan 19200
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="021c", ENV{libsane_matched}="yes"
# Mustek BearPaw 2400 CU Plus
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="021d", ENV{libsane_matched}="yes"
# Mustek BearPaw 1200 CS | Mustek BearPaw 1200 TA
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="021e", ENV{libsane_matched}="yes"
# Mustek ScanExpress 1248 UB
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="021f", ENV{libsane_matched}="yes"
# Mustek BearPaw 2448TA Pro
ATTRS{idVendor}=="055f", ATTRS{idProduct}=="0409", ENV{libsane_matched}="yes"
# Artec/Ultima Ultima 2000 | Artec/Ultima Ultima 2000 e+ | Boeder Sm@rtScan Slim Edition
# Fujitsu 1200CUS | Googlegear 2000 | Medion/Lifetec/Tevion/Cytron MD 4394
# Medion/Lifetec/Tevion/Cytron MD/LT 9375 | Medion/Lifetec/Tevion/Cytron MD/LT 9385 | Medion/Lifetec/Tevion/Cytron LT 9452
# Medion/Lifetec/Tevion/Cytron MD 9458 | Mustek BearPaw 1200 CU | Mustek BearPaw 2400 CU
# Mustek ScanExpress 1200 UB Plus | Mustek ScanExpress 2400 USB | Mustek ScanMagic 1200 UB Plus
# Packard Bell Diamond 1200 | Trust Compact Scan USB 19200 | Trust Flat Scan USB 19200
ATTRS{idVendor}=="05d8", ATTRS{idProduct}=="4002", ENV{libsane_matched}="yes"
# Artec/Ultima E+ 48U | Medion/Lifetec/Tevion/Cytron MD9693 | Medion/Lifetec/Tevion/Cytron MD9705
# Medion/Lifetec/Tevion/Cytron MD4394 | Microstar MR 9791
ATTRS{idVendor}=="05d8", ATTRS{idProduct}=="4003", ENV{libsane_matched}="yes"
# Artec/Ultima E+ Pro
ATTRS{idVendor}=="05d8", ATTRS{idProduct}=="4004", ENV{libsane_matched}="yes"
# Memorex MEM 48U
ATTRS{idVendor}=="05d8", ATTRS{idProduct}=="4005", ENV{libsane_matched}="yes"
# Trust Easy Webscan 19200
ATTRS{idVendor}=="05d8", ATTRS{idProduct}=="4006", ENV{libsane_matched}="yes"
# Trust 240H Easy Webscan Gold
ATTRS{idVendor}=="05d8", ATTRS{idProduct}=="4007", ENV{libsane_matched}="yes"
# UMAX AstraSlim SE
ATTRS{idVendor}=="05d8", ATTRS{idProduct}=="4009", ENV{libsane_matched}="yes"
# UMAX AstraSlim 1200 SE
ATTRS{idVendor}=="05d8", ATTRS{idProduct}=="4010", ENV{libsane_matched}="yes"
# Yakumo Scan50
ATTRS{idVendor}=="05d8", ATTRS{idProduct}=="4011", ENV{libsane_matched}="yes"
# Microtek ScanMaker X6USB
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="0099", ENV{libsane_matched}="yes"
# Microtek SlimScan C6
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="009a", ENV{libsane_matched}="yes"
# Microtek ScanMaker V6USL
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="00a3", ENV{libsane_matched}="yes"
# Microtek ScanMaker V6UPL
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="00b6", ENV{libsane_matched}="yes"
# Microtek ScanMaker 4800
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="30cf", ENV{libsane_matched}="yes"
# Microtek ScanMaker 3840
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="30d4", ENV{libsane_matched}="yes"
# Microtek ScanMaker 3600
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="40b3", ENV{libsane_matched}="yes"
# Microtek ScanMaker 3700
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="40b8", ENV{libsane_matched}="yes"
# Microtek ScanMaker 3600
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="40ca", ENV{libsane_matched}="yes"
# Microtek ScanMaker 3700
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="40cb", ENV{libsane_matched}="yes"
# Microtek ScanMaker 3750
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="40dd", ENV{libsane_matched}="yes"
# Microtek ScanMaker 3600
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="40ff", ENV{libsane_matched}="yes"
# Microtek ScanMaker V6USL
ATTRS{idVendor}=="05da", ATTRS{idProduct}=="80a3", ENV{libsane_matched}="yes"
# iVina 1200U
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0268", ENV{libsane_matched}="yes"
# Minolta Dimage Scan Dual II
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="026a", ENV{libsane_matched}="yes"
# Avision AV600U
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a13", ENV{libsane_matched}="yes"
# Minolta-QMS SC-110
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a15", ENV{libsane_matched}="yes"
# Avision DS610CU Scancopier | Minolta-QMS SC-215
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a16", ENV{libsane_matched}="yes"
# Avision AV600U Plus
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a18", ENV{libsane_matched}="yes"
# Avision AV610
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a19", ENV{libsane_matched}="yes"
# Avision AV220
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a23", ENV{libsane_matched}="yes"
# Avision AV210
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a24", ENV{libsane_matched}="yes"
# Avision AV210
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a25", ENV{libsane_matched}="yes"
# Avision AV120
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a27", ENV{libsane_matched}="yes"
# Avision AV220C2 | Avision AV220C2
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a2a", ENV{libsane_matched}="yes"
# Avision AV122
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a33", ENV{libsane_matched}="yes"
# Avision AV210C2
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a3a", ENV{libsane_matched}="yes"
# Avision AV121
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a3c", ENV{libsane_matched}="yes"
# Avision AV8300
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a40", ENV{libsane_matched}="yes"
# Avision AM3000 Series
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a41", ENV{libsane_matched}="yes"
# Avision @V5100
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a45", ENV{libsane_matched}="yes"
# Avision IT8300
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a61", ENV{libsane_matched}="yes"
# Avision AV3850SU
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a66", ENV{libsane_matched}="yes"
# Avision AV8350
ATTRS{idVendor}=="0638", ATTRS{idProduct}=="0a68", ENV{libsane_matched}="yes"
# Minolta Elite II
ATTRS{idVendor}=="0686", ATTRS{idProduct}=="4004", ENV{libsane_matched}="yes"
# Minolta Dimage Scan Dual III
ATTRS{idVendor}=="0686", ATTRS{idProduct}=="400d", ENV{libsane_matched}="yes"
# Minolta Dimage Scan Elite 5400
ATTRS{idVendor}=="0686", ATTRS{idProduct}=="400e", ENV{libsane_matched}="yes"
# AGFA SnapScan 1212U
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="0001", ENV{libsane_matched}="yes"
# AGFA SnapScan 1236u
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="0002", ENV{libsane_matched}="yes"
# Agfa Snapscan Touch
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="0100", ENV{libsane_matched}="yes"
# AGFA SnapScan 1212U_2
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="2061", ENV{libsane_matched}="yes"
# AGFA SnapScan e40
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="208d", ENV{libsane_matched}="yes"
# AGFA SnapScan e50
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="208f", ENV{libsane_matched}="yes"
# AGFA SnapScan e20
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="2091", ENV{libsane_matched}="yes"
# AGFA SnapScan e10
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="2093", ENV{libsane_matched}="yes"
# AGFA SnapScan e25
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="2095", ENV{libsane_matched}="yes"
# AGFA SnapScan e26
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="2097", ENV{libsane_matched}="yes"
# AGFA SnapScan e52
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="20fd", ENV{libsane_matched}="yes"
# AGFA SnapScan e42
ATTRS{idVendor}=="06bd", ATTRS{idProduct}=="20ff", ENV{libsane_matched}="yes"
# UMAX Astra 4900
ATTRS{idVendor}=="06dc", ATTRS{idProduct}=="0020", ENV{libsane_matched}="yes"
# Plustek OpticPro U12 | Plustek OpticPro UT12 | Plustek OpticPro 1212U
# RevScan RevScan Orange R48Ti | Genius ColorPage Vivid III USB
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0001", ENV{libsane_matched}="yes"
# Plustek OpticPro U12
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0010", ENV{libsane_matched}="yes"
# Plustek OpticPro U24
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0011", ENV{libsane_matched}="yes"
# Plustek OpticPro UT12
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0013", ENV{libsane_matched}="yes"
# Plustek OpticPro U24
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0015", ENV{libsane_matched}="yes"
# Plustek OpticPro UT12 | Plustek OpticPro UT16 | Plustek OpticPro UT24
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0017", ENV{libsane_matched}="yes"
# Plustek OpticPro 1248U | RevScan 19200i
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0400", ENV{libsane_matched}="yes"
# Plustek OpticPro 1248U
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0401", ENV{libsane_matched}="yes"
# Plustek OpticPro U16B
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0402", ENV{libsane_matched}="yes"
# Plustek OpticPro U16B+ | Plustek OpticPro UT16B
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0403", ENV{libsane_matched}="yes"
# Nortek MyScan 1200 | Plustek OpticPro S12 | Plustek OpticPro ST12
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="040b", ENV{libsane_matched}="yes"
# Plustek OpticPro S24
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="040e", ENV{libsane_matched}="yes"
# NeatReceipts Scanalizer Professional 2.5 | Plustek OpticSlim M12
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0412", ENV{libsane_matched}="yes"
# Plustek OpticSlim 1200
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0413", ENV{libsane_matched}="yes"
# Plustek OpticSlim 2400
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0422", ENV{libsane_matched}="yes"
# Plustek OpticSlim 2400 plus
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0454", ENV{libsane_matched}="yes"
# NeatReceipts Mobile Scanner
ATTRS{idVendor}=="07b3", ATTRS{idProduct}=="0462", ENV{libsane_matched}="yes"
# Corex 800c
ATTRS{idVendor}=="08f0", ATTRS{idProduct}=="0005", ENV{libsane_matched}="yes"
# Xerox Phaser 6110MFP
ATTRS{idVendor}=="0924", ATTRS{idProduct}=="3d5d", ENV{libsane_matched}="yes"
# Xerox Phaser 3200MFP
ATTRS{idVendor}=="0924", ATTRS{idProduct}=="3da4", ENV{libsane_matched}="yes"
# Xerox WorkCentre 3119 Series
ATTRS{idVendor}=="0924", ATTRS{idProduct}=="4265", ENV{libsane_matched}="yes"
# Portable Peripheral Co., Ltd. Q-Scan USB001 (A4 portable scanner)
ATTRS{idVendor}=="0a53", ATTRS{idProduct}=="1000", ENV{libsane_matched}="yes"
# Syscan TravelScan 460/464 | Ambir Visigo A4
ATTRS{idVendor}=="0a82", ATTRS{idProduct}=="4600", ENV{libsane_matched}="yes"
# Syscan TravelScan 662
ATTRS{idVendor}=="0a82", ATTRS{idProduct}=="6620", ENV{libsane_matched}="yes"
# Canon CR-55
ATTRS{idVendor}=="1083", ATTRS{idProduct}=="160c", ENV{libsane_matched}="yes"
# Canon DR-1210C
ATTRS{idVendor}=="1083", ATTRS{idProduct}=="160f", ENV{libsane_matched}="yes"
# Canon DR-4010C
ATTRS{idVendor}=="1083", ATTRS{idProduct}=="1614", ENV{libsane_matched}="yes"
# Canon DR-2510C
ATTRS{idVendor}=="1083", ATTRS{idProduct}=="1617", ENV{libsane_matched}="yes"
# Canon DR-X10C
ATTRS{idVendor}=="1083", ATTRS{idProduct}=="1618", ENV{libsane_matched}="yes"
# Canon CR-25
ATTRS{idVendor}=="1083", ATTRS{idProduct}=="161a", ENV{libsane_matched}="yes"
# Canon DR-2010C
ATTRS{idVendor}=="1083", ATTRS{idProduct}=="161b", ENV{libsane_matched}="yes"
# Canon DR-3010C
ATTRS{idVendor}=="1083", ATTRS{idProduct}=="161d", ENV{libsane_matched}="yes"
# Canon DR-7090C
ATTRS{idVendor}=="1083", ATTRS{idProduct}=="1620", ENV{libsane_matched}="yes"
# Digital Dream l' espion XS
ATTRS{idVendor}=="1183", ATTRS{idProduct}=="0001", ENV{libsane_matched}="yes"
# UMAX Astra 1220U
ATTRS{idVendor}=="1606", ATTRS{idProduct}=="0010", ENV{libsane_matched}="yes"
# UMAX Astra 1600U | UMAX Astra 2000U
ATTRS{idVendor}=="1606", ATTRS{idProduct}=="0030", ENV{libsane_matched}="yes"
# Umax UMAX 3400
ATTRS{idVendor}=="1606", ATTRS{idProduct}=="0050", ENV{libsane_matched}="yes"
# Umax UMAX 3400 | Umax UMAX Astranet ia101 | Umax UMAX 3450
ATTRS{idVendor}=="1606", ATTRS{idProduct}=="0060", ENV{libsane_matched}="yes"
# UMAX Astra 4400 | UMAX Astra 4450
ATTRS{idVendor}=="1606", ATTRS{idProduct}=="0070", ENV{libsane_matched}="yes"
# UMAX Astra 2100U
ATTRS{idVendor}=="1606", ATTRS{idProduct}=="0130", ENV{libsane_matched}="yes"
# Umax UMAX 5400
ATTRS{idVendor}=="1606", ATTRS{idProduct}=="0160", ENV{libsane_matched}="yes"
# UMAX Astra 2200 (SU)
ATTRS{idVendor}=="1606", ATTRS{idProduct}=="0230", ENV{libsane_matched}="yes"
# Dell A920
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="5105", ENV{libsane_matched}="yes"
# Dell Dell MFP Laser Printer 1815dn
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="5124", ENV{libsane_matched}="yes"
# Dell 1600n
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="5250", ENV{libsane_matched}="yes"

# The following rule will disable USB autosuspend for the device
ENV{libsane_matched}=="yes", RUN+="/bin/sh -c 'test -e /sys/$env{DEVPATH}/power/level && echo on > /sys/$env{DEVPATH}/power/level'"
LABEL="libsane_rules_end"
dave@dave-laptop:~$

---

### Post by patrik k on 2010-10-20
K. You still need to add the device to the list.
Once you have done that, your file should look like this-
( I scrolled to bottom of file for this view. )

# Dell Dell MFP Laser Printer 1815dn
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="5124", ENV{libsane_matched}="yes"
# Dell 1600n
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="5250", ENV{libsane_matched}="yes"
[B]#Brothers scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/B]
# The following rule will disable USB autosuspend for the device
ENV{libsane_matched}=="yes", RUN+="/bin/sh -c 'test -e /sys/$env{DEVPATH}/power/level && echo on > /sys/$env{DEVPATH}/power/level'"
LABEL="libsane_rules_end"

I have high lighted the addition you need to make to the file 
No blank lines between entries.
So, sudo pico the file, make entry at bottom of list after the
 # Dell 1600n
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="5250", ENV{libsane_matched}="yes" entry , 
press control key and W simultaneously, hit enter key then control key and X simultaneously. That will save file.
Re-boot and try simple scan.
If it still does not work, you may have incorrect scanner drivers installed.

---

### Post by czig49 on 2010-10-20
i get it in  but it wont save it

0", ENV{libsane_matched}="yes"
 # Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
# The following rule will disable USB autosuspend for the device
ENV{libsane_matched}=="yes", RUN+="/bin/sh -c 'test -e /sys/$env{DEVPATH}/power$
LABEL="libsane_rules_end"





File Name to Write: /lib/udev/rules.d/40-libsane.rules                          
^G Get Help         M-D DOS Format      M-A Append          M-B Backup File
^C Cancel           M-M Mac Format      M-P Prepend

---

### Post by czig49 on 2010-10-20
thankyou  for sticking with me all this time patrik.  it saved  and  functions well now.  i deeply appriciate your help.  ubuntu  is still fun,  learn a lil everyday..  yeehaw  i can scan and print.    now i just gotta remember how to  find the solved button lol

---

### Post by patrik k on 2010-10-20
Happy days Dave!
There is alot of online help with commands
[http://ss64.com/bash/](http://ss64.com/bash/)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Glad I could help

---

### Post by raashell on 2010-12-05
I just bought the Brother MFC-J410W also.  I'm very pleased with it, but just wanted to add my notes to this thread for anyone else who buys it.

I have 10.04 with x64 architecture.  The printing drivers are for i386 architecture.  You can use dpkg and force architecture to install them and it will work.  The scanner drivers are available for x64.

Brother's linux area has a page on this as well as on installing the drivers and making sure you have the necessary folder structure.

Once the scanner and printer drivers are installed, I was able to connect through X-Sane to scan and was able to set up a new network printer through System > Administration > Printing

For the scanning portion, you have to affix the scanner's ip address to one of the commands when you're going through Brother's online instructions to set up the scanner.  Assuming you've already set up the MFC-J410W (as in, installed the ink cartridges, etc) and gone through it's accompanying booklet on getting it network ready, on the device, you can go to Menu > Network > TCP/IP > IP Address and it will list where the device is on your network.

I was able to get both the scanner and the printer up over the network without having to physically connect it to my client computer.

--- Update ---

This last week (Jan 17) the scanner stopped working after updates to 10.04 Ubuntu install.  I re-installed the deb packages for my 64 bit arch. and re-did the install process provided by Brother and I got it back up.

---

### Post by jmatthews13 on 2011-05-11
Just wanted to throw a bit on this thread with the step by step for a network setup in Ubuntu x86_64. (raashell hits it right on the head!)

1. Setup printer (for networking, etc. No need for USB cable)
2. Ensure cups is installed and running (installed by default in Ubuntu 10.04+, makes it 10x easier) ... [dpkg -l | grep cups; ps -ef | grep cups]
3. Download lpd & cups drivers (deb format since we're in Ubuntu) ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html))
3. Create directories [sudo mkdir -p /var/spool/lpd/mfcj410w]
4. Install them! (dpkg -i --force-all [driver]) (as raashell said, we need to use "force-all" since the drivers are 32-bit)
5. Check to make sure it worked [dpkg -l | grep Brother]
6. Go to cups web interface and add the printer ([http://localhost:631/admin](http://localhost:631/admin))
7. Test something!

1. For the Scanner
2. Download the 64-bit brscan3 drivers ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html))
3. Install them (we don't need to force this time!) (dpkg -i [driver])
4. Check to make sure it worked [dpkg -l | grep Brother]
5. Use the brother tool for adding a new scanner (brsaneconfig3 -a name=SomeName model=MFC-NOLOWERCASELETTERSALLOWEDHERE ip=xxx.xxx.xxx.xxx)
6. Open your favorite scanning program and try it out!

---

