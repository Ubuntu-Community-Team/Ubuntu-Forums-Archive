---
title: "Help me install Ralink Wireless USB Adapter"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by Chewiesw on 2008-01-31
Please help I have been at this for hours, I have tried searching the forums but there was no answer to the one similar posting. This is what I have to do.....

Makefile.6 ./MakefileBuild Instructions:  

====================

1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz

    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.

    

2> $cp Makefile.4  ./Makefile       # [kernel 2.4]

    or

   $cp Makefile.6  ./Makefile       # [kernel 2.6]

   

3> [kernel 2.4]

    $chmod 755 Configure

    $make config         # config build linux os version



4> $make all            # compile driver source code



5> $cp rt73.bin /etc/Wireless/RT73STA/	    # copy firmware

 

6>  $dos2unix rt73sta.dat

    $cp rt73sta.dat  /etc/Wireless/RT73STA/rt73sta.dat       

    # !!!check if it is a binary file before loading !!!  

    

7> $load                

    #[kernel 2.4]

    #    $/sbin/insmod rt73.o

    #    $/sbin/ifconfig rausb0 inet YOUR_IP up

        

    #[kernel 2.6]

    #    $/sbin/insmod rt73.ko

    #    $/sbin/ifconfig rausb0 inet YOUR_IP up



This is what happen when I try.....

andrew@PVRBOX:~/RT73_Linux_STA_Drv1.0.3.6/Module$ cp Makefile.6  ./Makefile
cp: cannot create regular file `./Makefile': Permission denied
andrew@PVRBOX:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo cp Makefile.6  ./Makefile
andrew@PVRBOX:~/RT73_Linux_STA_Drv1.0.3.6/Module$ chmod 755 Configure
chmod: changing permissions of `Configure': Operation not permitted
andrew@PVRBOX:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo chmod 755 Configure
andrew@PVRBOX:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo make Configure
make: Nothing to be done for `Configure'.
andrew@PVRBOX:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo make all
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/andrew/RT73_Linux_STA_Drv1.0.3.6/Module modules
make: *** /lib/modules/2.6.22-14-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2
andrew@PVRBOX:~/RT73_Linux_STA_Drv1.0.3.6/Module$

---

### Post by kevdog on 2008-01-31
Perhaps this thread will help you:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

---

