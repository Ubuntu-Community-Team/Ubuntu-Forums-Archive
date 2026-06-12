---
title: "Trouble with Atheros wireless on HP DV9702EA."
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by Zombie13UK on 2008-09-27
I'd like to use wireless on my laptop, but the device isn't showing under Network Manager. However, under Hardware Drivers, it does say "Atheros Hardware Access Layer (HAL)" and is ticked and "in use". Could anyone give me a few pointers on how to configure the device? I can only see eth0 for configuration at the moment, and no wlan0.

Cheers!

---

### Post by Shlompy on 2008-09-27
Star by downloading "madwifi" from [this link]("http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.bz2?modtime=1202880171&big_mirror=0")

Download it to your home folder, and extract it.
Now, open your terminal and navigate to that folder, and run the following commands:

```
sudo ifconfig ath0 down (You'll be asked to enter your password)
sudo ifconfig wifi0 down
cd scripts
./madwifi-unload
./find-madwifi-modules.sh $(uname -r)
cd ..
sudo make
sudo make install
sudo modprobe ath_pci
```

now reboot, and check for wireless network trought the Network tray icon.

---

### Post by Zombie13UK on 2008-10-07
Thanks for the reply, but I got nothing but errors when trying that. I guess this has screwed up my new hour-old Ubuntu installation now, as something has now been removed that was there from a fresh install.

```
rich@laptop-z13:~/madwifi-0.9.4$ sudo ifconfig ath0 down
[sudo] password for rich: 
ath0: ERROR while getting interface flags: No such device
rich@laptop-z13:~/madwifi-0.9.4$ sudo ifconfig wifi0 down
wifi0: ERROR while getting interface flags: No such device
rich@laptop-z13:~/madwifi-0.9.4$ cd scripts
rich@laptop-z13:~/madwifi-0.9.4/scripts$ ./madwifi-unload
bash: ./madwifi-unload: No such file or directory
rich@laptop-z13:~/madwifi-0.9.4/scripts$ 
rich@laptop-z13:~/madwifi-0.9.4/scripts$ ./find-madwifi-modules.sh $(uname -r)

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
r
rm: cannot remove `/lib/modules/2.6.24-19-generic/volatile/ath_hal.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.24-19-generic/madwifi/wlan_scan_sta.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.24-19-generic/madwifi/wlan_tkip.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.24-19-generic/madwifi/ath_rate_sample.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.24-19-generic/madwifi/wlan_scan_ap.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.24-19-generic/madwifi/wlan_ccmp.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.24-19-generic/madwifi/wlan_acl.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.24-19-generic/madwifi/ath_rate_onoe.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.24-19-generic/madwifi/wlan_xauth.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.24-19-generic/madwifi/wlan.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.24-19-generic/madwifi/wlan_wep.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.24-19-generic/madwifi/ath_rate_amrr.ko': Permission denied
rm: cannot remove `/lib/modules/2.6.24-19-generic/madwifi/ath_pci.ko': Permission denied
rich@laptop-z13:~/madwifi-0.9.4/scripts$ sudo ./find-madwifi-modules.sh $(uname -r)

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
r
rich@laptop-z13:~/madwifi-0.9.4/scripts$ cd ..
rich@laptop-z13:~/madwifi-0.9.4$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/rich/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/rich/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /home/rich/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /home/rich/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /home/rich/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /home/rich/madwifi-0.9.4/ath_hal/uudecode
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c: At top level:
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/rich/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/rich/madwifi-0.9.4/ath_hal/uudecode] Error 1
make[2]: *** [/home/rich/madwifi-0.9.4/ath_hal] Error 2
make[1]: *** [_module_/home/rich/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
rich@laptop-z13:~/madwifi-0.9.4$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.24-19-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/rich/madwifi-0.9.4/ath'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install ath_pci.ko //lib/modules/2.6.24-19-generic/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/rich/madwifi-0.9.4/ath'
make: *** [install-modules] Error 1
rich@laptop-z13:~/madwifi-0.9.4$ sudo modprobe ath_pci
WARNING: Could not open '/lib/modules/2.6.24-19-generic/volatile/ath_hal.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.24-19-generic/madwifi/wlan.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.24-19-generic/madwifi/ath_pci.ko': No such file or directory

```

---

### Post by Shlompy on 2008-10-07
sorry, may bad.
about these lines you've typed:
```
rich@laptop-z13:~/madwifi-0.9.4/scripts$ ./madwifi-unload
bash: ./madwifi-unload: No such file or directory
rich@laptop-z13:~/madwifi-0.9.4/scripts$ 
rich@laptop-z13:~/madwifi-0.9.4/scripts$ ./find-madwifi-modules.sh $(uname -r)

```
I guess I had a mistake with the first script's file name, I don't have my ubuntu next to me, so please check in the "scripts" folder the exact "./madwifi-unload" file name and replace it with my little guide. (the "./" is a part of the file name as far as I remember.
about the second line, please write "sudo" before the line.
when it asks to remove the old files, press "r". (this is the important part, otherwise the installation won't succeed.)

sorry for my mistakes. but please don't give up so quickly because of this. it was just a mistyped errors.
please post back.
if you don't succeed with the first command, I think you can skip it at your situation.
!!!!
[B]Oh! I've Almost forgot. The most important thing before you start all the process again:
Delete the extracted folder and extract the archive again.
The files in that folder got messed up because the "make" command ended with errors.[/B]

---

### Post by Zombie13UK on 2008-10-07
Great stuff! I'll give it a go tomorrow night. I did try and restore a backup of Ubuntu using the Windows-based Acronis. I'll never try that again for my Linux backups, it completely destoyed my Ubuntu partition during the restore process.

Word of warning, folks. ;)

---

### Post by Shlompy on 2008-10-07
Please read again my edited reply above (the bolded lines)

---

