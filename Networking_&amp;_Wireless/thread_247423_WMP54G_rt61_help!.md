---
title: "WMP54G rt61 help!"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by gannic on 2006-08-30
I am trying to compile the drivers from the ralink website for the rt61 chipset. I am use to windows - and as soon as a step fales I am sunk.

I keep failing on the "make all" (step 4) with


clueless@computer:~/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module$ make all
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/clueless/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [all] Error 2

Here are the instructions I am using([http://www.ralinktech.com/supp-1.htm)](http://www.ralinktech.com/supp-1.htm))...

Build Instructions:  

====================



1> $tar -xvzf RT61_Linux_STA_Drv_x.x.x.x.tar.gz

    go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.

    

2> $cp Makefile.4  ./Makefile       # [kernel 2.4]

    or

   $cp Makefile.6  ./Makefile       # [kernel 2.6]

    or

   $cp Makefile.RTL865x ./Makefile  #  big endian platform

   

3> [kernel 2.4]

    $chmod 755 Configure

    $make config         # config build linux os version



4> $make all            # compile driver source code



5> $cp rt2561.bin /etc/Wireless/RT61STA/	# copy firmware

   $cp rt2561s.bin /etc/Wireless/RT61STA/

   $cp rt2661.bin /etc/Wireless/RT61STA/



6>  $dos2unix rt61sta.dat

    $cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat       

    # !!!check if it is a binary file before loading !!!  

    

7> $load                

    #[kernel 2.4]

    #    $/sbin/insmod rt61.o

    #    $/sbin/ifconfig ra0 inet YOUR_IP up

        

    #[kernel 2.6]

    #    $/sbin/insmod rt61.ko

    #    $/sbin/ifconfig ra0 inet YOUR_IP up



        

Note: Script functionality:

load            load module to kernel

unload          unload module from kernel

Configure       retrieve linux version

---

### Post by JebusWankel on 2006-09-24
perhaps this will help: [https://help.ubuntu.com/community/Rt61WirelessCardsHowTo](https://help.ubuntu.com/community/Rt61WirelessCardsHowTo)

---

