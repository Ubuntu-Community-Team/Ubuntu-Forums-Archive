---
title: "The final thing keeping me from adopting Ubuntu,,,,"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by AdrianStrays on 2008-04-05
So I've been battling with Ubuntu for two straight weeks (technically a month, I got angry and deleted Ubuntu, and then reinstalled it, but was able to set up faster since I wasn't waiting for people to respond) now (I won't make the "windows is easier" argument) and now I have nearly won.  I have one final complaint with Ubuntu, and that is in regards to wireless.

I've got a laptop, I'm dependent on wireless internet, however with Ubuntu my ability to connect is spotty at best.  Some days I will be in the exact same place and be unable to connect at all, others I will gain and lose connection.  While I have no trouble when I am say....five feet away from the wireless router (like now) most of the time its terrible.  Additionally, Ubuntu seems to have memory problems, because it can't remember my WEP key for more than a few log-ons.  So here are my questions:

1) Will Hardy address some of these issues, or will I have to wait till Intrepid?

2) Does anyone have any ideas on how to fix these problems?

I am using a Broadcom chip, which I am aware that Ubuntu apparently has issues with according to Hardware Manager it is: BCM4401- B0 100Base-TX

Thanks for any help

---

### Post by AdrianStrays on 2008-04-05
Anyone?

---

### Post by Eiríkr on 2008-04-05
1) No idea about Hardy.  I'm not keeping track of development roadmaps.
2) I don't use any wireless with Ubuntu myself, but several other threads I've run across suggest that the default Network Manager app is quite trouble-prone, and various folks have recommended replacing Network Manager with WICD instead.  I don't know if it would solve your issues, but it might be worth a look.  WICD isn't included in the Ubuntu repositories, so you'll have to download it from its [Sourceforge page](http://wicd.sourceforge.net/).

Good luck,

Eiríkr

---

### Post by kutjara on 2008-04-05
Wireless is still a challenge for Linux, largely because the wireless card manufacturers (a) use a wide range of different hardware, even in cards that are outwardly identical, (b) keep their wifi drivers closely guarded secrets, and (c) are constantly "upgrading" their product ranges with new models. This makes it very hard for the Linux community to stay on top of all the changes.

The end result is that ndiswrapper may work with your card, or madwifi may work, or your card may (miraculously) work out of the box, or it may never work. Personally, I've been fortunate with the machine I'm using now and found a very straightforward solution using madwifi. My HP tx1420us, however, is still running Windows Vista 64bit, because the 64bit version of Ubuntu won't work with the available drivers.

One way around all this is to use an external USB card, selected from the list of compatible hardware you can find on the forums. That way, your card will work, independent of the version of Ubuntu you're using.

---

### Post by Bubba64 on 2008-04-05
The dlink wna 1330 works straight out of the box it is a plug in external wireless card.
[http://ubuntuforums.org/showthread.php?t=490718](http://ubuntuforums.org/showthread.php?t=490718)

---

### Post by kevdog on 2008-04-05
Struggle through wireless for about a week, and then once you get it, it will be like a lightbulb went on.  You will most likely not have any problems after that.  Its a struggle in the beginning however.

---

### Post by AdrianStrays on 2008-04-06
Wicd didn't work for me.  I couldn't figure out how to install madwifi (this whole compiling programs thing NEEDS to stop) and synaptic wouldn't accept my installation disk to install ndiswrapper

---

### Post by AdrianStrays on 2008-04-06
So I installed Ndiswrapper, and I think I installed the drivers.  How do I know if I'm using them?

---

### Post by Bubba64 on 2008-04-06
> **AdrianStrays said:**
> So I installed Ndiswrapper, and I think I installed the drivers.  How do I know if I'm using them?

I think if you look in system-administrative-hardware drivers, this is what it is called in Hardy. it will tell you what you using. I know there is a terminal input that will tell you but I don't know what it is.

---

### Post by upthelum on 2008-04-06
You may get a better response if you print the output of some commands.
lspci
iwlist scan
iwconfig
ndiswrapper -l

---

### Post by AdrianStrays on 2008-04-06
adrian@Alpha-60-Workstation:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
adrian@Alpha-60-Workstation:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:39:66:B5:48
                    ESSID:"The Wells Family Network"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=97/100  Signal level=-44 dBm  Noise level=-67 dBm
                    Extra: Last beacon: 42ms ago
          Cell 02 - Address: 00:0A:DB:03:A6:20
                    ESSID:"MetroFi-Free"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=74/100  Signal level=-85 dBm  Noise level=-67 dBm
                    Extra: Last beacon: 4189ms ago
          Cell 03 - Address: 00:0A:DB:03:A6:22
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=75/100  Signal level=-84 dBm  Noise level=-67 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 7054ms ago

adrian@Alpha-60-Workstation:~$ ndiswrapper -l
b44win : driver installed
        device (14E4:170C) present (alternate driver: b44)
bcmwl6 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
adrian@Alpha-60-Workstation:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"The Wells Family Network"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:18:39:66:B5:48   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=75/100  Signal level=-50 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:139  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by tad1073 on 2008-04-06
> **AdrianStrays said:**
> Wicd didn't work for me.  I couldn't figure out how to install madwifi (this whole compiling programs thing NEEDS to stop) and synaptic wouldn't accept my installation disk to install ndiswrapper
download madwifi to you /usr/src and extract there, then:
```

cd /usr/src/madwifi-0.9.4
make
sudo make install
reboot

```

---

### Post by kutjara on 2008-04-06
> **tad1073 said:**
> download madwifi to you /usr/src and extract there, then:
```

cd /usr/src/madwifi-0.9.4
make
sudo make install
reboot

```

Before you reboot, type:

sudo modprobe ath_pci

If you find the card isn't recognized after the reboot, type:

sudo gedit /etc/modules

and then add "ath_pci" (without the quotation marks) to the end of the document. That'll make sure the driver loads with every reboot. Some people don't need to do it, but I did. It seems to vary by installation.

---

### Post by AdrianStrays on 2008-04-08
It won't let me move the tar to /usr/src because I don't have enough privileges.

---

### Post by Eiríkr on 2008-04-08
If you've already downloaded the tar, then just move it with the "sudo" prefix to gain root (super-user) privileges:
```
sudo mv /home/adrian/madwifi-0.9.4 /usr/src/
```

Adjust the left-hand source path to the madwifi package as appropriate.

Cheers,

Eiríkr

---

### Post by AdrianStrays on 2008-04-08
Yeah, I figured that out.  New problem is as follows:

> adrian@Alpha-60-Workstation:~$ cd /usr/src/madwifi-0.9.4
adrian@Alpha-60-Workstation:/usr/src/madwifi-0.9.4$ make
cd: 1: can't cd to /lib/modules/2.6.22-14-rt/build
Makefile.inc:66: *** /lib/modules/2.6.22-14-rt/build is missing, please set KERNELPATH.  Stop.
adrian@Alpha-60-Workstation:/usr/src/madwifi-0.9.4$ sudo make install


---

### Post by Eiríkr on 2008-04-08
If "make" fails out, "make install" will certainly fail out too, so there's no need to proceed.  

The specific error here seems to indicate that you don't have the kernel headers for your specific build.  I just found the package you'll need in the Synaptic list, so either fire that up or use apt-get to grab the **linux-headers-2.6.22-14-rt** package.  Once that is in place, try again with the "make" and "sudo make install" commands.  

Cheers,

Eiríkr

---

### Post by AdrianStrays on 2008-04-08
Whoa...this one is a doozy.

> root@Alpha-60-Workstation:/home/adrian# cd /usr/src/madwifi-0.9.4
root@Alpha-60-Workstation:/usr/src/madwifi-0.9.4# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-rt/build SUBDIRS=/usr/src/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-rt'
  CC [M]  /usr/src/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /usr/src/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /usr/src/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /usr/src/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /usr/src/madwifi-0.9.4/ath_hal/uudecode
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c: At top level:
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/usr/src/madwifi-0.9.4/ath_hal/uudecode] Error 1
make[2]: *** [/usr/src/madwifi-0.9.4/ath_hal] Error 2
make[1]: *** [_module_/usr/src/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-rt'
make: *** [modules] Error 2
root@Alpha-60-Workstation:/usr/src/madwifi-0.9.4# sudo make install


> adrian@Alpha-60-Workstation:/usr/src/madwifi-0.9.4$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.22-14-rt 

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
r
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/usr/src/madwifi-0.9.4/ath'
test -d //lib/modules/2.6.22-14-rt/net || mkdir -p //lib/modules/2.6.22-14-rt/net
install ath_pci.ko //lib/modules/2.6.22-14-rt/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/usr/src/madwifi-0.9.4/ath'
make: *** [install-modules] Error 1
adrian@Alpha-60-Workstation:/usr/src/madwifi-0.9.4$ 


---

### Post by AdrianStrays on 2008-04-08
Bump

---

### Post by heyho on 2008-04-08
Hi Adrian,

I know what you are going through, as I have had similar issues with a broadcom card.  I did get it working with ndiswrapper, then later on using fwcutter, but got fed up "playing" with the system for hours after fresh installs.  Good for learning teminal, but not so good for the sanity.

Bite the bullet, get a fully supported card.  I'm not saying that you won't get it working, but for the cost of a few cups of coffee, it's really not worth the headache, especially if it's the only issue you have.

Good luck.

---

### Post by Eiríkr on 2008-04-08
Again, if "make" fails out, "make install" will *definitely* fail out.  "make" is where the actual compilation of the driver code specific to your machine is supposed to take place.  If "make" fails, there's no driver created, so there's no need to proceed with "make install", and in fact proceeding might be a bad idea.  

Cheers,

Eiríkr

---

### Post by moore.bryan on 2008-04-08
as far as i can tell
(1) your chipset [doesn't]("http://madwifi.org/wiki/Compatibility") use madwifi, it needs ndiswrapper.
(2) [this]("http://ubuntuforums.org/showthread.php?p=4216379&highlight=driver%3Db43-pci-bridge#post4216379") other thread might be of help.

---

### Post by koenn on 2008-04-08
> **AdrianStrays said:**
> Whoa...this one is a doozy.

/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/usr/src/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory


those errors suggest you're system doesn't have essential files required to compile C programes (so-called C header files). All (or at least most) of the errors that follow result from those files being absent. 

install these packages, then try again :
```
sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)
```

linux-headers-$(uname -r)[ is a generic way to get the header files that match your kernel, similar to the one Eirikr gave.

---

### Post by AdrianStrays on 2008-04-08
First I need to make it clear that my wifi card DOES work.  That was never the problem, the problem was a spotty connection.

> nstall these packages, then try again

I did what you said, it appears to have worked...however I don't see anything.  No new programs in Menu or anything.  How can I double check to see if Madwifi was installed.

> (1) your chipset doesn't use madwifi, it needs ndiswrapper.

I tried installing Ndiswrapper, however I'm unsure if installed the proper drivers, and how to use it.

---

### Post by moore.bryan on 2008-04-09
> **AdrianStrays said:**
> First I need to make it clear that my wifi card DOES work.  That was never the problem, the problem was a spotty connection.
ah, that does change things a bit, doesn't it.
> I tried installing Ndiswrapper, however I'm unsure if installed the proper drivers, and how to use it.
maybe these two pages can help:
[WifiDocs/Driver/Ndiswrapper - Community Ubuntu Documentation]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")
[WifiDocs/Device/Broadcom - Community Ubuntu Documentation]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")
i'm not entirely sure the second one suits your needs perfectly, but it may lead you down the "right" road.

---

### Post by dstew on 2008-04-09
> the problem was a spotty connection.I have heard that disabling Roaming (Network --> your interface --> Properties) helps with spotty connection sometimes...

---

### Post by AdrianStrays on 2008-04-09
The problem with the Ndiswrapper installation is I'm not sure which driver I am suppose to use.


I have turned off roaming, and that has helped some, but the downside to that is icon in my tray doesn't show connection strength, only "manual configuration" and that is more difficult to switch networks when I AM roaming.  I was hoping to sort of clean this all up with a fell swoop.

---

### Post by moore.bryan on 2008-04-10
> **AdrianStrays said:**
> The problem with the Ndiswrapper installation is I'm not sure which driver I am suppose to use.
the driver for your wireless card...
> I have turned off roaming, and that has helped some, but the downside to that is icon in my tray doesn't show connection strength, only "manual configuration" and that is more difficult to switch networks when I AM roaming.  I was hoping to sort of clean this all up with a fell swoop.
are you still using network-manager? [wicd]("http://wicd.sourceforge.net/") might be the better way to go.

---

