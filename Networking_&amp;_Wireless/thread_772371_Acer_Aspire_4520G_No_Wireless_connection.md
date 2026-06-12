---
title: "Acer Aspire 4520G No Wireless connection"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Stoneface on 2008-04-28
Hi there,

I spent the entire day yesterday installing the latest version of Ubuntu on My Acer Aspire 4520G. Partitioning wouldn't work using the Ubuntu CD nor Partition Magic. I got errors all the time. In the end Acronis Disk Director Suite did the trick. I made a swamp and Ex3 partition and was able install Ubuntu. 
Now my Wireless connection won't work. I fooled around a bit with Madwifi, but no luck yet. But I am not a coder either...
When I enter lspci I get:

```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2) 
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2) 
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2) 
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2) 
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2) 
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) 
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) 
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) 
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) 
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) 
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1) 
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) 
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) 
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2) 
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) 
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) 
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12) 
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) 
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1) 
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

Any ideas what I am missing and how I can get the Atheros AR5007EG to connect to the web? Now I am Using Windows (Dual Boot) to surf the web. So I read something....reboot and give it a shot. All help will be appreciated.

---

### Post by chili555 on 2008-04-28
Try here: [http://ubuntuforums.org/showthread.php?t=771527&highlight=AR5007](http://ubuntuforums.org/showthread.php?t=771527&highlight=AR5007)

---

### Post by Stoneface on 2008-04-28
I will do that and let you know if when there are some new developments.

---

### Post by Stoneface on 2008-04-28
How can I update or apt-get install when I have no wireless connection using the Ubuntu OS? I guess I will need a lan connection to acomplish a wireless one...?

---

### Post by chili555 on 2008-04-28
Download it on the machine you are replying on and put it on a USB key or burn a CD. When you drag-n-drop it to your Ubuntu machine, it may be 'read only,' so, once you have it in your /home/user directory, you can open a terminal and do:```
sudo chmod 777 /home/user/file.tar.gz
```Substitute your user name and file name as needed. Call Dr. Chili (post back!) as needed.

---

### Post by Stoneface on 2008-04-28
Went ahead. Downloaded the file. Did all the commands:

```
Sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop/
tar -xf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007
make
sudo unload
sudo make install

``` in Bash and received the following errors:


```
root@jasper-laptop:/home/jasper/Desktop/madwifi# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/jasper/Desktop/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/jasper/Desktop/madwifi/ath/if_ath.o
  CC [M]  /home/jasper/Desktop/madwifi/ath/if_ath_radar.o
  CC [M]  /home/jasper/Desktop/madwifi/ath/if_ath_pci.o
  LD [M]  /home/jasper/Desktop/madwifi/ath/ath_pci.o
  CC [M]  /home/jasper/Desktop/madwifi/ath_hal/ah_os.o
  HOSTCC  /home/jasper/Desktop/madwifi/ath_hal/uudecode
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c: At top level:
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c: In function 'main':
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/jasper/Desktop/madwifi/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/jasper/Desktop/madwifi/ath_hal/uudecode] Error 1
make[2]: *** [/home/jasper/Desktop/madwifi/ath_hal] Error 2
make[1]: *** [_module_/home/jasper/Desktop/madwifi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2



```

And then when I copied the code and wanted to restart Ubuntu hanged...

---

### Post by chili555 on 2008-04-28
If you get an error in 'make,' stop. Any further action will also be in error. Do you have libc6-dev installed? I think that's where all these missing items are provided.```
sudo apt-get install libc6-dev
```Then try 'make' again. Proceed if there are no errors; warnings are generally OK.

---

### Post by Stoneface on 2008-04-29
How do I check if I have libc6-dev? I searched for the libc6-dev in case I need it. I found packages on [this ]("http://packages.debian.org/libc6-dev") page. Which one to choose? When I have it on my Ubuntu Desktop I install it using dpkg or make too? I am still getting used to shell commands so please be patient with me...

---

### Post by chili555 on 2008-04-29
The Debian packages are not the ideal for Ubuntu. In many cases they will work, but in some cases, they don't quite. You really want packages.ubuntu.com/hardy. The last time I checked it was so clogged with our fellow Ubuntians that I couldn't even open a page.

I really don't quite understand, because when you did:```
sudo apt-get install build-essential
```libc6-dev, and a whole lot more, should have been a dependency that you should have installed by default. Did *build-essential* go perfectly? Were you connected to ethernet, or how did you do it?

You can open up System -> Administration -> Synaptic and search for build-essential and libc6-dev, if the little box next to it is green, it's installed. It may be on the install CD. In Synaptic, select Settings -> Repositories and add your install CD as a source. You should then be able to install many packages from the CD.

---

### Post by Stoneface on 2008-04-30
I did update and installed build-essential. Then I did make in madwifi again. It all went smoothly. Thanks for that! But when I right click connections and go to wireless nothing shows.... How come?

---

### Post by Stoneface on 2008-04-30
I forgot to install after the 'make'.... Stupid me. It is working now!!! Thanks a lot Chili555!!!

---

### Post by Stoneface on 2008-04-30
Hmm. I am at a place of a friend of mine. I started up Ubuntu. Now Ubuntu cannot find any wireless networks, but Windows gets connected to my friend's  network (not a secure one) immediatedly. I wonder why. I mean the wireless network option is in place, but no networks are shown. Strange. Any idea what is going on? Maybe I need to start up madwifi again?

---

### Post by Stoneface on 2008-04-30
Well I restarted and now the networks do show up. False alarm I guess.

---

### Post by Stoneface on 2008-05-01
Well. Twice I restarted Ubuntu today to hopefully get a wireless connection again, but to no avail. Do I need to restart the wireless network or something?

---

### Post by Stoneface on 2008-05-01
Well, I did do some more reading. I guess the fact that HAL was still running was the culprit. I have disabled it and after restarting it did work right away. Let's hope it stays that way!

---

### Post by Stoneface on 2008-05-01
Well the story continues. I did turn of the Atheros HAL, but twice after a fresh startup no wireless network showed up. I don't understand why it does sometimes work and sometimes it doesn't. It seems that Ubuntu/madwifi cannot guarantee a steady wireless network access.
Anybody any other ideas what might be wrong?

---

### Post by Stoneface on 2009-06-07
Ubuntu Jaunty support Atheros wireless card for my Acer Aspire. I no longer need madwifi. Nice since I had to fix wifi every time I updated my kernel.

---

