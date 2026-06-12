---
title: "ADSL USB modem in pppoe"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by dileepa on 2006-07-17
[LEFT] 
[SIZE=2]Hi all [/SIZE]


[SIZE=2]i'm a new user to kubuntu i've got the latest installed in to a partion in my windows box,, i used to use different linux versions including debian, but unfortunatly my ADSL modem never worked with any of those releases,my modem([/SIZE][[SIZE=2]http://www.cnet.com.tw/product/cnad800-ef.htm[/SIZE]]("http://www.cnet.com.tw/product/cnad800-ef.htm")[SIZE=2]) is not sold in europe (i'm from Sri Lanka) i guess, but like most common ADSL usb modems it runs on Conexant accessrunner chipset , i've been to various sites including the most famous one in sourceforge to get help. but i'm stuck somewhere. for my relife the kubuntu recognize the modem (so usb problem is solved) but my ISP has a big bottleneck they provide me the ADSL connection via pppoe my modem control panel in windows read (Encapsulation Mode :- PPP over Ethernet LLCSNAP (RFC2516) ) to make it worst it has VPI and VCI (which is 8 and 35 respectively) i went through few of the how to's in the forum , it gave me some courage to try it out i extracted the firmware, it worked very well (but most of the walkthorughs are for pppoa connections) anyway i'm stuck with the pppoe, i'm connected via RJ11 telephone line not to a ethernet cable . i hope that any of you could help me in this [/SIZE][SIZE=2] :grin: [/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]regards[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Dileepa[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]The pic below shows the windows adsl configuration[/SIZE]
 [/LEFT]

---

### Post by dileepa on 2006-07-19
Hi People it's me again i'm happy to tell you that i'm posting this message from my kubuntu desktop :), i managed to install my Accessrunner based modem using a tutorial written for a alcatel modem anyone whos interested in this i will supply details to configur the modem to work with pppoe
regards
Dileepa :-D

---

### Post by dileepa on 2006-07-21
Hi 

This is the way to configure the above modem

Please read this before you do anything and download all the neccesery files from a machine which you have internet and save it to disk or partion and access later from the machine youre going to install the modem to get all the files please...

first of all you should find out what's your kernel, my one is 2.6.15 (kubuntu Dapper Drake) that would make things easier, this kernel can recognize the modemeasily so you dont have to meddle with the usb..

when you boot in to kubuntu or ubunto you should see 2 of the 3 LED's turned on (in my modem [ Cnet CNAD800ef] there are 3 LED's 1 for Power which shows the modem is getting power through the USB, middle one or number 2 is blinking whenever the ADSL is connected it start blinking 3rd one shows the usb connectivity whenthe firmware loads it will commiunicate with the isp and will stay on without blinking)LED no 1 and 3 should stay on after booting.. then startup a console an type this ($ cat /proc/bus/usb/devices) the result will be similar to this


T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0572 ProdID=cb00 Rev= 0.01
S:  Manufacturer=-
S:  Product=ADSL USB MODEM
S:  SerialNumber=46962291
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 7 Cls=00(>ifc ) Sub=00 Prot=00 Driver=cxacru
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=84(I) Atr=03(Int.) MxPS=   8 Ivl=200ms

if it's not that means your modem is not recognized (a kernel upgrade would fix this)

next is to download the firmware extractor

Download it from here

[http://accessrunner.cvs.sourceforge.net/accessrunner/utils/](http://accessrunner.cvs.sourceforge.net/accessrunner/utils/)

there are two files 
Makefile and cxacru-fw.c 
get them to a seperate folder and compile, you will need to install gcc if you dont have it. it's in the drapper CD 
open up a console and go to the folder of the extractor 
type this 

$ make cxacru-fw 

you will get file named cxacru-fw it's a executable just leave it as it is. now get your modem installer cd for windows find a file named  CnxEtU.sys put it in to the same folder.

now type this on the console 

$ ./cxacru-fw CnxEtU.sys cxacru-fw.bin

the out put will be similar to this

found firmware in `CnxEtU.sys' at offset 0x41c0

now you'll have another file inside th folder copy that to 
/lib/firmware/

now go to /etc/ppp/

there are two files chap-secrets and pap-secrets
backup those two files to a folder then edit the originals delete all the contents in them and enter the same text to both of them.

'username@isp' * 'password'

try to stck to this format

save them

this is for PPPOE only 
download this file ([http://linux-usb.sourceforge.net/SpeedTouch/mandrake/br2684ctl](http://linux-usb.sourceforge.net/SpeedTouch/mandrake/br2684ctl))

in console brows to the folder where you downloaded the file 

$sudo install -m 755 br2684ctl /usr/sbin

now copy this to a text file and save it as access
replace username@isp with your username to the adsl login


noipdefault
defaultroute
user 'username@isp'
noauth
updetach
usepeerdns
plugin /usr/lib/pppd/2.4.4b1/rp-pppoe.so
nas0

### If the firmware loads but pppd won't
### connect, uncomment this option to make
### pppd be more verbose in the system log

# debug

### For more details (and more options)
### Read man pppd

copy this to the /etc/ppp/peers

or use this command

$sudo install -m 600 access /etc/ppp/peers

copy this to a file and name it (dial) save it in your home folder


#!/bin/bash
modprobe ppp_generic
modprobe pppoatm
modprobe br2684

    br2684ctl -b -c 0 -a 8.35
    sleep 3
    ifconfig nas0 192.168.0.1 netmask 255.255.255.0 up
    sleep 5
    pppd call access


goto console type

$chmod +x dial

now restart the computer, boot in to ubuntu or kubuntu  open up a console 

then type 
$ sudo ./dial

result will look like this

RFC1483/2684 bridge: Interface "nas0" created successfully
RFC1483/2684 bridge: Communicating over ATM 0.8.35, encapsulation: LLC
RFC1483/2684 bridge: Interface configured
Plugin /usr/lib/pppd/2.4.4b1/rp-pppoe.so loaded.
Plugin /usr/lib/pppd/2.4.4b1/rp-pppoe.so loaded.
PADS: Service-Name: ''
PPP session is 6743
using channel 1
Using interface ppp0
Connect: ppp0 <--> nas0
sent [LCP ConfReq id=0x1 <mru 1492> <magic 0xb55a3d2e>]
rcvd [LCP ConfReq id=0x51 <mru 1492> <auth pap> <magic 0x4c1225a2>]
sent [LCP ConfAck id=0x51 <mru 1492> <auth pap> <magic 0x4c1225a2>]
rcvd [LCP ConfAck id=0x1 <mru 1492> <magic 0xb55a3d2e>]
sent [LCP EchoReq id=0x0 magic=0xb55a3d2e]
sent [PAP AuthReq id=0x1 user="rm2605694@sltadsl.lk" password=<hidden>]
rcvd [LCP EchoRep id=0x0 magic=0x4c1225a2]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
peer from calling number 00:90:1A:41:AE:3E authorized
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0xde <addr 220.247.232.7>]
sent [IPCP ConfAck id=0xde <addr 220.247.232.7>]
rcvd [IPCP ConfNak id=0x1 <addr 222.165.176.233> <ms-dns1 203.115.0.18> <ms-dns3
 203.115.0.1>]
sent [IPCP ConfReq id=0x2 <addr 222.165.176.233> <ms-dns1 203.115.0.18> <ms-dns3
 203.115.0.1>]
rcvd [IPCP ConfAck id=0x2 <addr 222.165.176.233> <ms-dns1 203.115.0.18> <ms-dns3
 203.115.0.1>]
local  IP address 222.165.176.233
remote IP address 220.247.232.7
primary   DNS address 203.115.0.18
secondary DNS address 203.115.0.1

then type 

$ ifconfg
the result look similar to this but can be different. 

nas0      Link encap:Ethernet  HWaddr 00:D0:DA:52:1A:4A
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:daff:fe52:1a4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:924066 (902.4 KiB)  TX bytes:239768 (234.1 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:222.165.176.233  P-t-P:220.247.232.7  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:828122 (808.7 KiB)  TX bytes:127767 (124.7 KiB)

nas0 and  ppp0 should be there if not there is soething wrong check back  whether you missed anything. if everythings okay just open up the browser and see you'll be online...

Good Luck

regards 

Dileepa
:-D

---

### Post by dileepa on 2006-10-06
Hi Again

I'm writing this to apologise to anyone who had tried my script and got stuck, i found an error on the last script I'll correct this for your convenience,

#!/bin/bash
 modprobe ppp_generic
 modprobe pppoatm
 modprobe br2684
 
br2684ctl -b -c 0 -a 8.35  
# here the number 8 is for the VPI and 35 for VCI
 sleep 3
#correct script
 ifconfig nas0 up 

 sleep 5
 pppd call access

---

### Post by pitrs on 2007-01-28
ifconfig:
lo
....

eth0
....

nas0
.....

but I havent ppp0.

Can you help me.Thanks

---

### Post by dileepa on 2007-03-07
> **pitrs said:**
> ifconfig:
lo
....

eth0
....

nas0
.....

but I havent ppp0.

Can you help me.Thanks

Hi pitrs,

Did you try the rewritten script done by me, it's posted after the first long post.

Regards,

Dileepa.

---

### Post by nalsur on 2007-03-08
dileepa:

this error after install
$ sudo ./dial
[IMG]http://www.geocities.com/gambak_gambo/dial-error.PNG[/IMG]
$ ifconfig
[IMG]http://www.geocities.com/gambak_gambo/dial-ifconfig.PNG[/IMG]

---

### Post by nalsur on 2007-03-08
yuuhooooo now is okey my modem run smoothly
thankz guys....

but... my problem now is i need to connect manually
type all this commands

sudo modprobe ppp_generic

sudo modprobe pppoatm

sudo modprobe br2684

sudo 
br2684ctl -b -c 0 -a 0.0.35

sudo sleep 3

sudo ifconfig nas0 192.168.0.1 netmask 255.255.255.0 up

sudo sleep 5

sudo pppd call access

---

### Post by ZuruxKakyn on 2007-08-04
same as nalsur, i have to run it manually, but unlike nalsur, i cannot connect.the connection icon at the tray show (x) and when i try to browse the net using konqueror, i can't.

i am using bluethunder usb modem (which i think uses conexant driver), trying with both gnome and kde ubuntu.

---

### Post by merci_b on 2007-09-24
I've tried this with my USB ADSL Modem. ( Here's my original post : [Conexant USB ADSL Modem]("http://ubuntuforums.org/showthread.php?p=3417262") )

1. */proc/bus/usb/devices* has the following entry:

> T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0915 ProdID=8102 Rev= 1.00
S:  Manufacturer=Conexant, Inc.
S:  Product=USB-ADSL Modem
S:  SerialNumber=4A2916
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=83(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=3ms
I:  If#= 0 Alt= 1 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=82(I) Atr=01(Isoc) MxPS=1008 Ivl=1ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=3ms
I:  If#= 0 Alt= 2 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=82(I) Atre 01(Isoc) MxPS= 912 Ivl=1ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=3ms
I:  If#= 0 Alt= 3 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=82(I) Atr=01(Isoc) MxPS= 736 Ivl=1ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=3ms
I:  If#= 0 Alt= 4 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=82(I) Atr=01(Isoc) MxPS= 448 Ivl=1ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=3ms
I:  If#= 0 Alt= 5 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=82(I) Atr=01(Isoc) MxPS= 240 Ivl=1ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=3ms
I:  If#= 0 Alt= 6 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=82(I) Atr=01(Isoc) MxPS=  80 Ivl=1ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS=  32 Ivl=3ms

2. When I copy *cxacru-fw.bin* to */lib/firmware* the modem light doesn't turn on at all.

3. I don't have a folder called */usr/lib/pppd/2.4.4b1*, the folder that I have is */usr/lib/pppd/2.4.4* - so I changed that line in */etc/ppp/peers/access* to */usr/lib/pppd/2.4.4/rp-pppoe.so*, where my *rp-pppoe.so* file is located.

4. *sudo ./dial* gives a list of errors, so I proceeded one by one as in nalsur's post : 
	(i)  sudo modprobe ppp_generic => works
	(ii) sudo modprobe pppoatm => works
	(iii)sudo modprobe br2684 => works
	(iv) sudo br2684ctl -b -c 0 -a 0.0.35 => error : 
> *br2684ctl: error while loading shared libraries: libatm.so.1: cannot open shared object file: No such file or directory*
	(v)  sudo sleep 3 => works
	(vi) sudo ifconfig nas0 192.168.0.1 netmask 255.255.255.0 up => error:
> [I]SIOCSIFADDR: No such device
nas0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
nas0: ERROR while getting interface flags: No such device[/I]
	(vii)sudo sleep 5 => works ( I'm curious - why the 3 sec and 5 sec sleeps? I'm a newbie so, be gentle :D )
	(viii)sudo pppd call access => error :
> *pppd: In file /etc/ppp/peers/access: unrecognized option 'nas0'*

5. I looked for *libatm* in the Synaptics packade manager and came up with two entries : *libatm1* and *libatm1-dev*; The manager gives the homepage as [linux-atm.sourceforge.net]("http://linux-atm.sourceforge.net/"), but that site is confusing to me, so I wonder if can download the necessary packages from [packages.ubuntu.com]("http://packages.ubuntu.com") - but one package depends on another, so I'm checking out how many I have to download.

Any suggestions?

Thanks in advance.

:popcorn:

---

### Post by merci_b on 2007-09-24
**UPDATE**

I managed to install the *libatm1* package from the CD. Now the results are:

	(i)  sudo modprobe ppp_generic => works
	(ii) sudo modprobe pppoatm => works
	(iii)sudo modprobe br2684 => works
	(iv) sudo br2684ctl -b -c 0 -a 8.35 => error : 
> [b]RFC1483/2684 bridge: Interface "nas0" created successfully
RFC1483/2684 bridge: Communicating over ATM 0.8.35, encapsulation: LLC
RFC1483/2684 bridge: Fatal: failed to connect on socket[/b]
	(v)  sudo sleep 3 => works
	(vi) sudo ifconfig nas0 192.168.0.1 netmask 255.255.255.0 up => works
	(vii)sudo sleep 5 => works 
	(viii)sudo pppd call access => error :
> [b]Plugin /usr/lib/pppd/2.4.4/rp-pppoe.so loaded.
Timeout waiting for PADO packets
Unable to complete PPPoE Discovery[/b]

Then I ran *./dial* - here is the code in *dial* :
> [i]#!/bin/bash
modprobe ppp_generic
modprobe pppoatm
modprobe br2684

br2684ctl -b -c 0 -a 8.35
# here the number 8 is for the VPI and 35 for VCI
sleep 3
#correct script
ifconfig nas0 up

sleep 5
pppd call access[/i]

And the results:
> root@mercib-laptop:/home/mercib/Driver/Dileepa# ./dial
[b]RFC1483/2684 bridge: Interface "nas0" could not be created, reason: File exists
RFC1483/2684 bridge: Communicating over ATM 0.8.35, encapsulation: LLC
RFC1483/2684 bridge: Fatal: failed to connect on socket
Plugin /usr/lib/pppd/2.4.4/rp-pppoe.so loaded.
Timeout waiting for PADO packets
Unable to complete PPPoE Discovery[/b]
root@mercib-laptop:/home/mercib/Driver/Dileepa#

p.s. Still the modem light doesn't turn on.

---

### Post by merci_b on 2007-09-24
:popcorn:

---

### Post by Faust_UA on 2007-09-25
I did everything by this manual and when I type in console

sudo ./dial

the result is
> RFC1483/2684 bridge: Interface "nas0" created successfully
RFC1483/2684 bridge: Communicating over ATM 0.1.50, encapsulation: LLC
RFC1483/2684 bridge: Interface configured
Plugin /usr/lib/pppd/2.4.4b1/rp-pppoe.so loaded.
[color=red]Timeout waiting for PADO packets
Unable to complete PPPoE Discovery[/color]

I've got no idea what's the problem... please help me! :(

---

