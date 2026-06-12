---
title: "Received error on make while installing NIC card"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by res14 on 2009-04-05
I replaced an old NIC card, that was in working condition, and upgraded to a gigabit NIC card for a server on 8.04. The card is recognized on lspci command, but there is no internet connection. I started the process of installing the drivers but received an error on make command. It looks like things start going wrong on "Entering an unknown directory" then it ends with
> make: *** [modules] Error 2

There is no ./configure file. The following files are listed in the directory /driver_teg-pcitxr_v3.1b10/LINUX/2.4.x_2.6.x>  Makefile README src

I am a little confused by the README because there is no r1000_linuxdrv_vxx.zip or cd r1000 directory after unzipping,
> 

<Requirements>

  - kernel source tree (supported versions 2.4.x or 2.6.x)
  - compiler/binutils for kernel compilation



<Quick install with proper kernel settings>

  Unpack the tarball :
	unzip r1000_linuxdrv_vxx.zip

  Change to the directory:
	cd r1000

  If you are running the target kernel, then you should be
  able to do :

	make clean modules	(as root or with sudo)
	make install
	depmod -a




<Force Media Speed>

 The media can be forced to one of the 5 modes as follows.

        Cmd: "insmod r1000 media = SET_MEDIA"
        For example:
         "insmod r1000 media = 0x04" will force PHY to operate in 100Mpbs Half-duplex.

         SET_MEDIA can be:
                _10_Half        = 0x01
                _10_Full        = 0x02
                _100_Half       = 0x04
                _100_Full       = 0x08
                _1000_Full      = 0x10


   Force media type for multiple cards could be performed as:

         "insmod r1000 media=0x04,0x10"

   which force PHY to operate at 100Mbps half-duplex and 1000Mbps full-duplex.



<Advanced feature>

  - Supports Jumbo Frame
  - Hardware Tx/Rx flow control


The Trendnet's website lists Driver_TEG-PCITXR_v3.1b10.zip as the most recent zip package of drivers. Unzipping reveals a LINUX directory that was copied to the home directory.

I'm not sure if I'm on the right track. After reading thru a days worth of threads and troubleshooting this is as far as I got. Very fresh to ubuntu, servers and command line. Any assistance is appreciated.

---

### Post by cariboo on 2009-04-06
Did you check to see if the driver was loaded already? In a terminal run:

```
sudo lshw -C netwrok
```

and look at the bottom of the listing. If the driver is loaded you should see something like this:

```
configuration: autonegotiation=on broadcast=yes **driver=skge** driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.200 latency=32 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
```

I have bolded the driver for the nic on my server.

Jim

---

### Post by res14 on 2009-04-06
Thanks Jim. Your suggestion listed an installed driver. After editing iptables from eth0 to eth1, there is now an internet connection.

---

