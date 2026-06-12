---
title: "Wireless on Xubuntu"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by dansm15 on 2007-04-12
I just installed Xubuntu on a Dell laptop. It boots just fine and I can connect to Internet using hardwire ethernet. However, I can't seem to get things working using the wireless set up. Can anyone help me a bit?

Thanks.. Brand new to Linux and not a programmer.

---

### Post by solar george on 2007-04-12
Open a terminal and type 
```
lspci
```
Post the results.

---

### Post by dansm15 on 2007-04-13
Thx, I will try this tonight. What is it I should be expecting to see?

---

### Post by solar george on 2007-04-13
Lspci will list all of the equipment attached to the pci on your computer (including built-in stuff), if your wireless is on a usb stick use lsusb instead.

Using lspci you can find out what chipset your wireless card is,

for me it shows,
```
# lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420
02:00.1 CardBus bridge: Texas Instruments PCI1420
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
**07:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**

```

The bit in bold is the wireless card (yours will probably be different). The chipset is not the same as the model number, my card is a Linksys WPC54GS v2, but the chipset is a broadcom.

Once you know what chipset your card is using it is possible to work out how to install it.

---

### Post by dansm15 on 2007-04-13
Here's the list I got. Looks like a Broadcom board:


dansm15@dandell:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0000:02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
**0000:02:02.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)**
0000:02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
0000:02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller

---

### Post by solar george on 2007-04-13
OK,

I'll try and write some instructions,

Edit /etc/modprobe.d/blacklist
```
sudo nano /etc/modprobe.d/blacklist
```
and add the line
```
blacklist bcm43xx
```
 This prevents the incorrect driver being loaded automatically.

Unload the driver if loaded,
```
sudo rmmod bcm43xx
```
If you get an error just continue.

Install ndiswrapper and cabextract,
```
sudo aptitude install ndiswrapper ndisgtk cabextract
```

Download the windows drivers from a manufacturer website,

According to [this thread]("http://ubuntuforums.org/showthread.php?t=399820&highlight=BCM4303") the ones from the [HP website]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-31559-1&lc=en&cc=us&dlc=en&product=437690&os=228&lang=en") work best.


Use cabextract to extract the files,
in the same directory as the download,
```
cabextract ./SP30379.exe 
```

n.b. This extracts all of the files into the current directory so it would be best to move the download to its own directory first.

Install the drivers into ndiswrapper,
```
ndiswrapper -i ./bcmwl5.inf 
```
Check that you have the correct driver,
```
ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 

```

Load the ndiswrapper module manually,
```
sudo modprobe ndiswrapper
```

Check it is working,
```
iwconfig
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:24 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Set ndiswrapper to be loaded at boot,
```
sudo ndiswrapper -m
```

Use the network manager to connect to your network.

---

### Post by dansm15 on 2007-04-13
Okay, George, Thanks for the help. I'm so new to this that I need the instructions broken down a bit. I assumed that I should input your instruction steps in the Terminal. When I did, here's what I got: 

dansm15@dandell:~$ edit/etcmodprobe.d/blacklist
bash: edit/etcmodprobe.d/blacklist: No such file or directory
dansm15@dandell:~$

Any suggestions? What did I do wrong?

---

### Post by dansm15 on 2007-04-14
George, I figured out how to clean out the current settings, such that I now have this following listing upon doing an iwconfig:

dansm15@dandell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

dansm15@dandell:~$

I downloaded SP30379.exe as suggested. I created a new directory at home/dansm15/extracted/SP30379.exe

I tried using the cabextract command but cannot seem to get it to work. This is the message I get:

dansm15@dandell:~$ cabextract.home/dansm15/extracted/SP0379.exe
bash: cabextract.home/dansm15/extracted/SP0379.exe: No such file or directory

Not sure where to go from here

Thx

Dan

---

### Post by solar george on 2007-04-14
> ```
dansm15@dandell:~$ cabextract.home/dansm15/extracted/SP0379.exe
bash: cabextract.home/dansm15/extracted/SP0379.exe: No such file or directory
```
I wrote all of the commands assuming that you are in the directory that the file was downloaded to,
to get there type,
```
cd ~/extracted/
```
The ~ symbol refers to your home directory.


the command that you wrote would be correctly formated,
```
cabextract /home/dansm15/extracted/SP0379.exe
```
You must leave a space between the name of the command and the location of the file, also ./ tells the command line to look in the current directory for the file.

---

### Post by dansm15 on 2007-04-14
George, Now I feel like a stooge, but here's where I am.. I know.. one step at a time:

If I've ~cd to the extracted directory should my code read something like this:


dansm15@dandell:~/extracted$ cabextract /SP30379.exe


I know that I'm close! Thanks again for all your assistance :)

---

### Post by andguent on 2007-04-14
George: Thanks for the directions. They worked great for my Presario V2000 & BCM4318.

Dan: Check the directions one more time. There is a period before the /SP30379

Type:
```

cd ~/extracted/
cabextract ./SP30379.exe

```

You should get something like this:
```

Extracting cabinet: ./SP30379.exe
  extracting bcm43xx.cat
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl5a.ini
  extracting bcmwld2k.exe
  extracting bcmwlhoa.ini
  extracting bcmwlhom.exe
  extracting bcmwlhom.ini
  extracting bcmwlntp.sys
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
  extracting setupa.ini
  extracting setupd.ini
  extracting sp30379.cva

All done, no errors.

```

You are very close for sure. Just double check all punctuation, I think George has everything right if you take each command exactly as he has it.

Quick tip: If you select a block of text with your mouse, you can then paste it by middle clicking (usually pressing down on your wheel). It makes it easier to get all of the syntax strait.

---

### Post by dansm15 on 2007-04-15
Here what I got. still not working:

dansm15@dandell:~/extracted$ cabextract ./SP30379.exe
bash: cabextract: command not found

---

### Post by solar george on 2007-04-15
```
sudo aptitude install cabextract
```

---

### Post by dansm15 on 2007-04-15
Looks like it worked!

dansm15@dandell:~/extracted$ cabextract ./SP30379.exe
Extracting cabinet: ./SP30379.exe
  extracting bcm43xx.cat
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl5a.ini
  extracting bcmwld2k.exe
  extracting bcmwlhoa.ini
  extracting bcmwlhom.exe
  extracting bcmwlhom.ini
  extracting bcmwlntp.sys
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
  extracting setupa.ini
  extracting setupd.ini
  extracting sp30379.cva

All done, no errors.

---

### Post by dansm15 on 2007-04-15
George,

Thanks so much for sticking with me. I am happy to say that I am now wireless on my Dell. Not too bad for a nubee.

Thanks again!::D

---

