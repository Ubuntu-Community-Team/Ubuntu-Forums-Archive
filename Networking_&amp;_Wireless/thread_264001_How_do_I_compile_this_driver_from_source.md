---
title: "How do I compile this driver from source?"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by Gotou on 2006-09-24
Hi!  I'm trying to install an updated driver for my D-Link DFE-690TXD ethernet card from the source code.  A first for me.  I've tried following the included instructions but they don't work.  I'm not able to make the "dfe690.o" file.

The kernel version has changed since the instructions were written.  That much I've figured out but the rest is left in the fog of ignorance.

Would someone savvy in this stuff, look over the instructions below and help me out.  Pleeeeaaase.


Here are the instructions:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Linux driver for kernel 2.4.X



D-Link DFE-690TXD CardBus PC Card Installation on Linux:



 01.Copy the driver source files to a convenient directory.

 

 02.Compile the source code:

    The instruction for compiling the driver is include at the 

    end of the driver file.If a compile-command is not there use 

    the following compile command:

              

    *compile-command: 

     " gcc -O6 -Wall -DCONFIG_KERNELD -DMODULE -D__KERNEL__ -DLINUX -c 

       dfe690.c -I/usr/include/linux/version.h -I/usr/src/linux-2.4.18-3/include/"

    

    Or you can use the Makefile included in the driver disk \LINUX.

    

    The final file is dfe690.o

 

 03.Copy the module "dfe690.o" to 

    "/lib/modules/{kernel-version}/pcmcia"

 

    *The directory "{kernel-version}" stands for the Linux kernel 

     version you use. 

 

 04.Insert the driver as module:

    insmod dfe690.o

    (Run 'lsmod' to see if the module is inserted)

 

 05.Edit config:

    ->Add 5 lines to the file "/etc/pcmcia/config"

    

    #

    # Device driver definitions

    #

   

    device "dfe690"                                    (==>Add 1/5)

    class "network" module "dfe690"                    (==>Add 2/5) 

   

    :

    :

 

    #

    # CardBus Cards

    #

 

    card "D-Link DFE-690TXD CardBus PC Card"           (==>Add 3/5)

    manfid 0x0149, 0x0000                              (==>Add 4/5)

    bind "dfe690"                                      (==>Add 5/5)

    

    The values 0x0149, 0x0000 are JEDEC ID and can be read by typing 

    "cardctl ident" on console with one card on socket.

 

 06.Restart the computer.

 

 *More information about install: man pcmcia 


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Thanks!

---

### Post by jpkotta on 2006-09-24
I wouldn't expect a driver for 2.4 to compile for 2.6.  And their compile command looks kind of weird, I don't think -O6 is a valid option.

Post the output of the compile command.  If it's really long, attach a file.

---

### Post by Gotou on 2006-09-24
Problem partially solved.

My purpose for wanting to update the driver was to be able to run ethtool to see if the card was running full duplex.  I just bought the card and popped it in assuming it would work.  It didn't.  So I turned to my desktop to find a driver . . . proceeded to waste several hours searching and trying to compile the driver I found.

By poking around (and accidental luck) I found what was wrong.

Originally I had an old Xircom card (Xircom RealPort CardBus Ethernet 10/100+Modem 56 RBEM56G-100 CE 168X) that came with the laptop.  Ethtool and mii-tool couldn't talk to that old card.  According to System > Administration > Networking the Xircom card was eth0, however the new D-Link card was now eth1

Here's the accidental part.

By right clicking on the little network icon next to the clock in the upper right corner and then clicking on "Properties" I saw that it was still set to eth0.  When I changed it to eth1 the D-Link card lit up and connected.  

After a reboot I was able to use ethtool to happily find the card was indeed using full duplex.

OK, so it's working but now I'm curiuos about jpkotta's request for the output of the compile command.

How do I do that?

I'm not going to install the driver now since it's seems to work but I do want to learn more about how to use the command line for outputting so I can post for help with future problems.

Thanks!

---

### Post by jpkotta on 2006-09-24
You open a terminal with Applications -> Accessories -> Terminal.  You type in commands by hand or copy and paste by selecting the command in your web browser and middle clicking in the terminal.  Then you can either copy and paste from the terminal in the same way, or redirect the output to a file.  Example or redirection:
```
echo blah 
echo blah > blah.txt
``` The first line just prints "blah".   The second line redirects what is printed to the screen to the file blah.txt.  Any command can be redirected to a file in this way.  Often you will want error output as well, in that case replace '>' with '>&'.

---

