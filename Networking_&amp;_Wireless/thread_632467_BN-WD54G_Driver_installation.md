---
title: "BN-WD54G Driver installation"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by dringof1 on 2007-12-05
Hi,

Im a complete Linux newbie and I am trying to install some linux drivers via the terminal but I am not having any success. The readme that comes with the drivers gives no hint of what to do should you run in to any problems. I have only got on to step two as the "go to" command is not recognised. The instructions are as followed:

Build Instructions:  
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

If anyone could shed any light on this id be very grateful.

Thanks.

---

### Post by csat on 2007-12-05
Well, I don't know what kind of drivers are trying to install and for what purpose but, in general, after untar a gzip file, creating its folder, we do:

  cd created_folder
  
Check for a file named INSTALL  using capital  letters.  It is better than README if available.  Next steps are, in general, to configure the "make file" accordingly to your system.  At that time dependencies are checked and if not found would produce an error report.  So you should fix those dependencies before going on.  

./configure  # pay attention that this command starts with a dot and a slash #

After "zero error" you can go further and perform

make
 
sudo make install

(for installation you should have power enough)

Those steps are most the same to all files that we want to install.

I'd like to suggest you, though, alternative steps like checking whether you can find "deb" files that are appropriate to Ubuntu so that you could manage to put those drivers to work.

Cheers

---

### Post by csat on 2007-12-05
I've been looking for this topic using Google and found a thread regarding the same problem.  Check it because might help.

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4465&start=0&sid=d5e2f012312b99bae4b4f03be8bfebde](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4465&start=0&sid=d5e2f012312b99bae4b4f03be8bfebde)

---

