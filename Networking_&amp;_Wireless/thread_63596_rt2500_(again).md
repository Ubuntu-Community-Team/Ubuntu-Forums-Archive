---
title: "rt2500 (again)"
date: 2005-09-08
forum: Networking &amp; Wireless
---

### Post by errata on 2005-09-08
hi all, i spent the last couple of days getting to grips with ubuntu and installed new packages and stuff but the wireless problem still persists... you guys must be sick of dealing with these issues, i'm sorry!

i got the official ralink linux drivers for the rt2500 usb card from [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

before anyone asks, i definitely have an rt2500 card - and it has a USB interface ;)

i follow the instructions provided and everything goes fine until it starts looking for a network, here's what happens:

root@dave:/home/david/Desktop # cd RT25USB-SRC-V2.0.4.0
root@dave:/home/david/Desktop/RT25USB-SRC-V2.0.4.0 # cp Makefile.6 Makefile
root@dave:/home/david/Desktop/RT25USB-SRC-V2.0.4.0 # make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/david/Desktop/RT25USB-SRC-V2.0.4.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/rtusb_main.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/mlme.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/rtusb_bulk.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/connect.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/sync.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/rtusb_init.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/rtmp_tkip.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/wpa.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/rtmp_wep.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/rtusb_info.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/assoc.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/auth.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/auth_rsp.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/md5.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/rtusb_io.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/sanity.o
  CC [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/rtusb_data.o
  LD [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/rt2570.o
  Building modules, stage 2.
  MODPOST
  CC      /home/david/Desktop/RT25USB-SRC-V2.0.4.0/rt2570.mod.o
  LD [M]  /home/david/Desktop/RT25USB-SRC-V2.0.4.0/rt2570.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
root@dave:/home/david/Desktop/RT25USB-SRC-V2.0.4.0 # insmod rt2570.ko
root@dave:/home/david/Desktop/RT25USB-SRC-V2.0.4.0 # ifconfig rausb0 up
root@dave:/home/david/Desktop/RT25USB-SRC-V2.0.4.0 # dhclient rausb0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/rausb0/00:d0:41:f8:0c:98
Sending on   LPF/rausb0/00:d0:41:f8:0c:98
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

--

it finds the MAC address fine, but it doesnt seem to find a network. i thought at first this had something to do with having the network closed, but when i set it to broadcast, the problem persists.

anyway i then followed the instructions and set up the card to communicate with the network, as per the instructions.. i made it wpa/psk, stuck in the ssid in "", put in the password in... but when i do that it comes up wrong, lets just say there is an & sign in my key and the characters after it dont seem to enter, so next time i put the password in "" and it seemed to enter fine.... i then did 

root@dave:/home/david/Desktop/RT25USB-SRC-V2.0.4.0 # dhclient rausb0 

again, but with the exact same results... 



things that might be causing this off the top of my head:
the card is plugged into a usb extention because my USB ports are recessed, perhaps ubuntu has a problem with that, and maybe that's what this is about:
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776

alternatively i think it might be down to some kind of manufacturer related unique modifications. the card is made by netopia, which doesnt seem to be commonly used by ubuntu users!

at no stage do the LED's on the card light up, but the card is warm so it's being used on some level i guess...

any help would be most appreciated  :grin:

---

### Post by errata on 2005-09-09
hi all... well i got the card working by using ndiswrapper and downloading the wpa extensions...


i couldnt believe it when the green LED came on to tell me i'd connected to the network...

but but but...

while i'm able to connect to my dsl router, i am not able to go onto the internet - if that makes any sense to you?

i'm able to ping my router, i'm able to change the settings on the router, i'm able to do a ping sweep of my local network, but outside of the network nothing works

i dont need mean to be a pain but if someone could just point me in the direction of the solution to this problem i'd really appreciate it, thanks

---

### Post by errata on 2005-09-09
Got it working!

sudo pppoeconf

will detail full steps soon for others

---

