---
title: "D-link DWA-547 Wireless N PCI-adapter problem"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Butcher_swe on 2007-04-23
Hi:) 
i have downloaded the latest Madwifi driver... and trying to compile it, but i get errors then i doing it:confused:  im going to post the errors then im get home(working now) then i use make thete is 1 error and in make install i get 2 ore more:( 
//Butcher

---

### Post by Butcher_swe on 2007-04-23
> **Butcher_swe said:**
> Hi:) 
i have downloaded the latest Madwifi driver... and trying to compile it, but i get errors then i doing it:confused:  im going to post the errors then im get home(working now) then i use make thete is 1 error and in make install i get 2 ore more:( 
//Butcher

Here is whats going wrong:( any one that nows why?

julia@julia-desktop:~$ sudo apt-get install linux-restricted-modules-$(uname -r)Läser paketlistor... Färdig
Bygger beroendeträd         
Läser in tillståndsinformation... Färdig
linux-restricted-modules-2.6.20-15-generic är redan den senaste versionen.
0 uppgraderade, 0 nyinstallerade, 0 att ta bort och 2 ej uppgraderade.
julia@julia-desktop:~$ cd /home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410
julia@julia-desktop:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ sudo make clean
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i clean; \
        done
make[1]: Entering directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath'
make[1]: Entering directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal'
rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal'
make[1]: Entering directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
                make -C $i clean; \
        done
make[2]: Entering directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_rate/amrr'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_rate/amrr'
make[2]: Entering directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_rate/onoe'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_rate/onoe'
make[2]: Entering directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_rate/sample'
make[2]: Entering directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_rate/minstrel'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_rate/minstrel'
make[1]: Leaving directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_rate'
make[1]: Entering directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/net80211'
make -C ./tools  clean
make[1]: Entering directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig core a.out
make[1]: Leaving directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/tools'
rm -rf .tmp_versions
rm -f *.symvers svnversion.h
julia@julia-desktop:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath/if_ath.o
  CC [M]  /home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath/if_ath_pci.o
  LD [M]  /home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath/ath_pci.o
  CC [M]  /home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/ah_os.o
  HOSTCC  /home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c: At top level:
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c: In function 'main':
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode] Error 1
make[2]: *** [/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal] Error 2
make[1]: *** [_module_/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Fel 2
julia@julia-desktop:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.20-15-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath'
test -d //lib/modules/2.6.20-15-generic/net || mkdir -p //lib/modules/2.6.20-15-generic/net
cp ath_pci.ko //lib/modules/2.6.20-15-generic/net
cp: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/julia/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath'
make: *** [install-modules] Fel 1
julia@julia-desktop:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ 


//Butcher

---

### Post by Butcher_swe on 2007-04-24
Anyone now that to do?

---

### Post by Butcher_swe on 2007-04-25
i get it to work:guitar:  but i had to install gcc and a lot of progs to get it to work:KS 
//Butcher

---

### Post by GeirG on 2007-05-01
Does this mean the DWA-547 is supported and working?
Have you checked what transfer rates you are able to get?

I am just thinking of getting one myself :-)

---

### Post by DO55 on 2007-08-16
i have same problem , please help

---

