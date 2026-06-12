---
title: "Looking for help w/ installing PCI wireless card"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by Raoc3 on 2010-04-05
First, let me say that I am completely clueless when it comes to linux or Ubuntu.  It has been very humbling to feel completely inept in my attempts to do anything useful at all with Ubuntu ](*,) LOL.

I just installed Ubuntu 9.10

I have a PCI wireless card that I installed (read: plugged in) so that I can connect to the internet and install more things so that I can actually do something.  I have found a Linux driver on the card manufacturer's website (Azio).  The .tar contains a readme, and I think I may just need some help interpreting what the readme is trying to tell me.

Contents of the Readme file:

> RTL8185 Linux Driver v1027.0823.2007 for linux kernel 2.6

  - Support Client mode for either infrastructure or adhoc mode
  - Support WEP and WPAPSK/WPA2PSK connection

===============================================================================================
< Component >
The driver is composed of several parts:
    (1)source code
    rtl8185.tar.gz
    stack.tar.gz

    (2)Script ot build the modules
        makedrv

    (3)Script to load/unload modules
        wlan0up
        wlan0down

    (4)Script and configuration for DHCP
    wlan0dhcp
        ifcfg-wlan0

    (5)Supplicant source code
    wpa_supplicant-0.4.9.tar.gz
        
    (6)Example of supplicant configuration file
    wpa1.conf




< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:

    (1)Build up the driver from the source code
             ./makedrv

        (2)Load the driver module to kernel and start up nic
            ./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
            ./wlan0rmv
        ./wlan0down
        ./wlan0up
        should be OK.
       )
    (3)Refer to < Set wireless lan MIBs > to set Wireless LAN specific parameters.

...
The rest is configuration stuff for the card.  Lets get the thing installed first, then worry about that.
I can recognize all the parts in "Components" as files inside the .tar file, but the "Installation" part has got me lost.  I have no idea what it is trying to tell me.  Can anyone translate for me?  Thanks.

---

### Post by patchwork on 2010-04-05
It's giving you step by step instructions on how to compile the source code into a workable driver binary in the terminal.

After extracting the .tar archive, open a terminal (Applications > Accessories > Terminal) , enter ```
cd /path/to/extracted/tar/archive
sudo ./makedrv
``` This should compile the driver module. When that completes, enter the next command```
sudo ./wlan0up
``` and so on.

The sudo preface tells the computer that you have administrator rights (to install the driver).

---

### Post by Raoc3 on 2010-04-05
[FONT=monospace]ok I compiled the driver module.  I'm still having trouble with the second part.
[/FONT]
> (2)Load the driver module to kernel and start up nic
            ./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
            ./wlan0rmv
        ./wlan0down
        ./wlan0up
        should be OK.
       )

I ran the "sudo ./wlan0up"

and recieved a different set of error codes.  

What does this mean?:
*Load the driver module to kernel and start up nic*

---

### Post by patchwork on 2010-04-06
Drivers in linux have to be compiled with or inserted into the kernel.  You have built a driver module to load into the kernel and , presumably, your script wlanoup then loads the driver module to enable your nic (network interface card).  

What errors are you getting when you try to use the wlan0up script?  Have you tried running the set of three scripts for the error condition?

---

