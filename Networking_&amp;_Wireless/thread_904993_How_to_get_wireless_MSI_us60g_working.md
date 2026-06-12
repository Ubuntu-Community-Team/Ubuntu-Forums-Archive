---
title: "How to get wireless MSI us60g working"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by natehall on 2008-08-29
First go to this website:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

then download this one:

RT2501USB(RT73:RT2571W/RT2573/RT2671)

Its a compressed file , Follow these steps to get it working. (Also on the READ ME file inside the module folder)

1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz

    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.

    

2> $cp Makefile.4  ./Makefile       # [kernel 2.4]

    or

   $cp Makefile.6  ./Makefile       # [kernel 2.6]

   

3> [kernel 2.4]

    $chmod 755 Configure

    $make config         # config build linux os version



4> $make all            # compile driver source code

4.1> $make install



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



Rather than try and figure out what "YOUR_IP" should be on the very last step I finished with the network manager. 
(System>Administration>network)
One last note: A bunch of those steps need to be done with sudo typed in first.

This very post was made using a ms60g so it really does work.

---

### Post by Crafty Kisses on 2008-08-29
Post results of > iwconfig

---

### Post by rob42 on 2009-01-29
HI
I have been trying this and get to step 4
when I get

> make: *** No rule to make target `config'. Stop.
orac@orac:~/RT73_Linux_STA_Drv1.0.4.0/Module$ 

where I am going wrong?

---

