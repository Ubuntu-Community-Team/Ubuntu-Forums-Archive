---
title: "Edimax"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by will_i_am on 2008-03-05
I am attempting to follow the directions on creating a driver for the edimax EW-7108PCg. The instructions are here:


=======================================================================
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



here is what happens on steps 
3. william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ make config
make: *** No rule to make target `config'.  Stop.

4. william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ make config
make: *** No rule to make target `config'.  Stop.

last step: william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ load
bash: load: command not found


The card is not working. Can someone look to see what I am doing wrong:

total of work

william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ cp Makefile.6  ./Makefile
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ make config
make: *** No rule to make target `config'.  Stop.
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ make all
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/william/IS_Linux_STA_6x_D_1.1.1.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "pci_module_init" [/home/william/IS_Linux_STA_6x_D_1.1.1.0/Module/rt61.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ sudo make all
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/william/IS_Linux_STA_6x_D_1.1.1.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "pci_module_init" [/home/william/IS_Linux_STA_6x_D_1.1.1.0/Module/rt61.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ cp rt2561.bin /etc/Wireless/RT61STA/
cp: cannot create regular file `/etc/Wireless/RT61STA/rt2561.bin': Permission denied
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ sudo cp rt2561.bin /etc/Wireless/RT61STA/
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ sudo cp rt2561s.bin /etc/Wireless/RT61STA/
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ sudo cp rt2661.bin /etc/Wireless/RT61STA/
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ dos2unix rt61sta.dat
The program 'dos2unix' is currently not installed.  You can install it by typing:
sudo apt-get install tofrodos
bash: dos2unix: command not found
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ sudo dos2unix rt61sta.dat
sudo: dos2unix: command not found
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat 
cp: cannot create regular file `/etc/Wireless/RT61STA/rt61sta.dat': Permission denied
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ sudo cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat 
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ load
bash: load: command not found
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ 
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ dos2unix rt61sta.datwilliam@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ sudo cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat 
william@william:~/IS_Linux_STA_6x_D_1.1.1.0/Module$ load
bash: load: command not found


Thanks.

---

### Post by will_i_am on 2008-03-07
bump...no one has ever seen these errors?

William

---

### Post by will_i_am on 2008-03-12
bump. still no takers?

---

