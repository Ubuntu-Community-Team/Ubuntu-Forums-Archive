---
title: "BT Voyager Probs"
date: 2005-10-21
forum: Networking &amp; Wireless
---

### Post by Grimlock on 2005-10-21
[IMG]images/icons/icon5.gif[/IMG]  				**Connection woes** -   				  				  				  					18 Hours Ago  				  				  				  			    			 
   			  		  		  		 Hi,
I am a Linux newbie and I am loving the product so far my only problem si those blasted BT Voyager drivers. I have installed the drivers and the synch.bin but I cannot get a data connection. I get synch no problem I can not get a data transfer here is my errors from the terminal server.

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

OK eciadsl-synch: success 
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

using channel 19
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
sent [LCP ConfReq id=0x1 <magic 0x4b72a2c7>]
LCP: timeout sending Config-Requests
Connection terminated.
using channel 20
Failed to set PPP kernel option flags: Inappropriate ioctl for device
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15012), status = 0xf9
Modem hangup
Couldn't get channel number: Input/output error
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15036), status = 0xf9
Couldn't get channel number: Input/output error
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15042), status = 0xf9
Couldn't get channel number: Input/output error
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15047), status = 0xf9
using channel 21
in make_ppp_unit, already had /dev/ppp open?
Failed to set PPP kernel option flags: Inappropriate ioctl for device
Using interface ppp0
Connect: ppp0 <--> /dev/pts/3
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15052), status = 0xf9
Modem hangup
Connection terminated.
using channel 22
Failed to set PPP kernel option flags: Inappropriate ioctl for device
Using interface ppp0
Connect: ppp0 <--> /dev/pts/4
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15081), status = 0xf9
Modem hangup
Connection terminated.
Couldn't get channel number: Input/output error
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15099), status = 0xf9
Couldn't get channel number: Input/output error
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15104), status = 0xf9
Couldn't get channel number: Input/output error
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15109), status = 0xf9
using channel 23
Using interface ppp0
Connect: ppp0 <--> /dev/pts/5
Script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 15114), status = 0xf9
Modem hangup
Connection terminated.
Waiting for 1 child processes...
  script /usr/bin/eciadsl-pppoeci -vpi 0 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364, pid 14986
sending SIGTERM to process 14986
ERROR: failed to connect


This means absolutely nothing to me [IMG]images/smilies/confused.gif[/IMG] Doesn anyone have any ideas or experience of this?? It is driving me mad as I have been fiddling for hours now.

Thanks

---

### Post by Bukunut on 2006-04-06
Grimlock

I had the same problem with my BT Voyager USB adsl. The originating page for the drivers said the default was synch01.bin...yeah and a bear can fly Navy jets..I got results like yours.
I started to go through the list of synch bins one after the other (sorry no other way!!) and got fed up and went straight to the last one, you know sods law? synch55.bin... It worked!
I will say be aware that it is a bit hit and miss, when I first turn the PC on the script works till [I][EciAdsl 4/5] Connecting to provider...
[/I] so I ctrl-c and start again, and the next time it will go through all stages, don't know why it does that. 

Only last thing now is to work out an automation for starting and stopping the script without using the command line, I would love to know what programme you could use, tried Knet but kept dying on me...

Bukunut:-D

---

