---
title: "Need help with Speedtouch USB on Dapper"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by SpiralFire on 2007-03-16
Alright..
 Before you say "use search", i wanna say a DID use it
 and found tons of stuff.. but none worked
 i followed some tutorials, tried some scripts and its just not working..

 It's an green Alcatel SpeedTouch USB modem
 Using Dapper Drake

 Both lights stay solid green, but i just cant go online
 dunno if this is wrong but when i go to the network administration tools, it shows eth0 (its onboard and theres nothing connected to it) (active)
and the thingg i forgot the name, to use ppp dial, but i got no dialing-modem installed.. (inactive)

shouldnt the usb modem show here?
i tried the RP-PPPoE-3.8 and i think thats the tool that put me the most near to solve this problem.. but it asks for the address of the card you are gonna use, and i just dont know the usb's address to put in there..

when i type
cat /proc/bus/usb/devices
it shows all the usb ports (4)
and it recognizes the usb modem
heres the output of the modem thing:

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=06b9 ProdID=4061 Rev= 0.00
S:  Manufacturer=ALCATEL
S:  Product=Speed Touch USB
S:  SerialNumber=0090D0259BF2
C:* #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=00 Prot=00 Driver=speedtch
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=50ms
I:  If#= 1 Alt= 0 #EPs= 0 Cls=ff(vend.) Sub=00 Prot=00 Driver=speedtch
I:  If#= 1 Alt= 1 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=speedtch
E:  Ad=06(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=07(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=87(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 1 Alt= 2 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=speedtch
E:  Ad=06(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=07(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=87(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 1 Alt= 3 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=speedtch
E:  Ad=06(O) Atr=02(Bulk) MxPS=  16 Ivl=0ms
E:  Ad=07(O) Atr=02(Bulk) MxPS=  16 Ivl=0ms
E:  Ad=87(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=speedtch
E:  Ad=05(O) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=85(I) Atr=02(Bulk) MxPS=   8 Ivl=0ms


the others are printers and some other stuff



so.. can anyone help me with this?
i'll give any information needed
it's been 4 days trying to go online
but i just cant
:( 

dont wanna go back to windows..


and.. sorry for my english
just not my native language
x)

thanks
:)

---

### Post by Docter on 2007-03-17
More information is required but it sounds like the firmware isn't loading up at boot. I'm no expert but I'll try and help. Look through administration/system log for lines that mention the speedtouch driver. Mine looks like this:
> 
Mar 17 10:33:13 doc-desktop kernel: [   48.522915] usbcore: registered new driver speedtch
Mar 17 10:33:13 doc-desktop kernel: [   48.857718] speedtch 1-2:1.0: found stage 1 firmware speedtch-1.bin
Mar 17 10:33:13 doc-desktop kernel: [   49.578934] speedtch 1-2:1.0: found stage 2 firmware speedtch-2.bin

If it is anything different then make sure you are using the correct firmware for your modem revision. You can easily find out the modem revision by typing in a terminal:
> 
awk '/4061/ { print $5 }' /proc/bus/usb/devices 

Mine spits out "4.00", I have the silver speedtouch so I suspect yours will be earlier (rev 2?).


Because you have a usb modem I would suggest that you follow the instructions for PPPoA unless you know for sure that you have to use PPPoE due to ISP or whatever.
[clicky howto link]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")

If this doesn't get you nudged in the right direction then open up a terminal and tell me the output of these seperate commands:

```
ifconfig
route
```

and post the text from
```

/etc/network/interfaces 
and
/etc/ppp/peers/speedtch (or whatever you called you called it)
```

Oh, and your English is excellent. :)

---

### Post by SpiralFire on 2007-03-17
So.. yeah, you were right
firmware not loading..
at least this time
cuz i reinstalled ubuntu about 4 times
to do it from the begining
and im not using english ubuntu.. so any "translations" u need just ask me :X
 i'll post the results here, then ill try to install the firmware again.. :

the revision is o.oo  the old green one x)

I think my provider demands PPPoE.. at least on windows, only way to connect is using a dialer (RASPPPoE) or the windows dialer... it asks for login/password..

Interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider



The route command gives me no results.. no numbers, just the parameters..

log and ifconfig:

[ [IMG]http://www.imagehosting.com/out.php/t348561_log.PNG[/IMG]](http://www.imagehosting.com/out.php/i348561_log.PNG)

[ [IMG]http://www.imagehosting.com/out.php/t348562_ifconfig.png[/IMG]](http://www.imagehosting.com/out.php/i348562_ifconfig.png)


thanks ;D

---

### Post by SpiralFire on 2007-03-17
Alright...

 installed the firmware (KQD6)
 according to the system log its loading
 just like yours

 but...
 there wasnt an inportant change with ifconfig
[ [IMG]http://www.imagehosting.com/out.php/t348886_ifconfig2.PNG[/IMG]](http://www.imagehosting.com/out.php/i348886_ifconfig2.PNG)

and route didnt change at all...

then i did that tutorial again, the one u posted above..
tried the pppoa tutorial
didnt work..

then i tried the pppoe for the third or fourth time
but this time  saw something.. dont know if its important..

at this point:
"
install the bootscript in /etc/init.d 
make a symbolic link pointing at it from /etc/rc2.d so that it gets run during the boot process 
fix /etc/resolv.conf to sort out domain nameserver lookups 
sudo install -m 744 dial /etc/init.d &&
sudo ln -s ../init.d/dial /etc/rc2.d/S95dial &&
sudo ln -sf ppp/resolv.conf /etc/resolv.conf 
"

the last command show me an error
[ [IMG]http://www.imagehosting.com/out.php/t348938_comerror.PNG[/IMG]](http://www.imagehosting.com/out.php/i348938_comerror.PNG)

then i gone the file
and the ppp/resolv.conf doesn't exist
and the /etc/resolv is "broken"

what now?

---

### Post by Docter on 2007-03-17
okay. The first thing I'd do is edit your /etc/network/interfaces file and comment out any interfaces that you don't use. Also if you use eth0 for a home LAN or something give it a static IP and unique subnet mask. Here is my interfaces file:
```

auto lo
iface lo inet loopback


#iface dsl-provider inet ppp
#provider dsl-provider

iface speedtch inet ppp
provider speedtch

iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto eth0
```

A few things to note here: I have two pc's running ubuntu on a crossover cable sharing my usb modem, so no real router just a couple of ethernet cards. Also you'll notice that I commented out:
```

#iface dsl-provider inet ppp
#provider dsl-provider
```

and replaced it with:

```
iface speedtch inet ppp
provider speedtch
```

dsl-provider is an example script which will not work unless you have edited it. But you should have created a file called speedtch that you saved as /etc/ppp/peers/speedtch from that tutorial. Make sure you have done this, installed it using the correct command from the tutorial and go ahead and change your interfaces file to call this script like I have done. My file will be significantly different from yours because I use PPPoA and obviously we have unique sign in names. yours should look something like:

```
noipdefault
defaultroute
user 'username@isp' #this is your sign in
noauth
updetach
usepeerdns
plugin rp-pppoe.so
nas0

### If the firmware loads but pppd won't
### connect, uncomment this option to make
### pppd be more verbose in the system log

# debug

### For more details (and more options)
### Read man pppd
```

Following these steps should give you a change in your route command; we'll get it connected and online before we worry about the bootscript too much but did you copy and paste the command as one entire line instead of two or three seperate ones?

sudo install -m 744 dial /etc/init.d && sudo ln -s ../init.d/dial /etc/rc2.d/S95dial && sudo ln -sf ppp/resolv.conf /etc/resolv.conf

good luck
Lee

---

### Post by SpiralFire on 2007-03-18
Well, i commented out all connections.. because i dont use any..
 And put this:

 iface speedtch inet ppp
 provider speedtch

 Rebooted...
 ifconfig and route didnt change again
 /etc/ppp/peers/speedtch exists...
 as i removed the eth0, ifconfig only showed the loopback connection..

 i typed the commands separately, not all in one line, it was all togheter cuz i pressed up arrow.. so i didnt need to type it all again :X


 oh hell...
:confused:

---

### Post by Docter on 2007-03-18
So the firmware is loaded.

Have you installed the bridging utility (br2684ctl)?

did you copy the scripts 'speedtch' and 'dial' to /etc/ppp/peers/ and /etc/init.d/ using the correct commands?

if so put the contents of those two files on here. also enable the debug mode by removing the relevant comment in  your /etc/ppp/peers/speedtch file and then show me any relevant logs from /sys/log/messages and /sys/log/debug after a restart. Look for anything to do with pp0, ADSL, LCP, IPCP

---

### Post by SpiralFire on 2007-03-18
Alright...
 Now i saw something interesting
 couldnt find anything using filters: ADSL, LCP, IPCP
 heres the only important part of the log(var/log/messages) i found.. debug had nothing interesting:

[ [IMG]http://www.imagehosting.com/out.php/t355308_logf1.PNG[/IMG]](http://www.imagehosting.com/out.php/i355308_logf1.PNG)

 But when i try to access any site from firefox i get that same error...

 using pp0 filter i only got this:

[ [IMG]http://www.imagehosting.com/out.php/t355378_pp0f.PNG[/IMG]](http://www.imagehosting.com/out.php/i355378_pp0f.PNG)

 Dial and Bridging utility installed :

[ [IMG]http://www.imagehosting.com/out.php/t355309_dialf.PNG[/IMG]](http://www.imagehosting.com/out.php/i355309_dialf.PNG)

[ [IMG]http://www.imagehosting.com/out.php/t355310_brf2.PNG[/IMG]](http://www.imagehosting.com/out.php/i355310_brf2.PNG)

dial content:
```

#!/bin/bash
modprobe ppp_generic
modprobe pppoatm
modprobe br2684
count=0
while [[ $((count++)) -lt 40 ]]
do
  sync=$(dmesg | grep 'ADSL line is up')
  if [ ! -z "$sync" ]
  then
    br2684ctl -b -c 0 -a 0.35
    sleep 3
    ifconfig nas0 192.168.0.1 netmask 255.255.255.0 up
    sleep 10
    pppd call speedtch
    exit 0
  fi
  sleep 1
done
echo "The SpeedTouch firmware did not load" 

```

speedtch content:
```

noipdefault
defaultroute
user 'henri****@brturbo.com' #<- my username is right on the original file :) )
noauth
updetach
usepeerdns
plugin rp-pppoe.so
nas0

### If the firmware loads but pppd won't
### connect, uncomment this option to make
### pppd be more verbose in the system log

debug

### For more details (and more options)
### Read man pppd 

```



i tried running the rp-pppoe-3.8
"./go"
tried to use the interface nas0
as it appears on every file i edited or created..
it fails "timeout"
=\

---

### Post by Docter on 2007-03-18
That all looks good. The factthat your ADSL line is up suggests that your modem is connected and communicating.

What about 'pppd' 'nas0' and 'pppoe' as a filter in your messages log?

I assume your pap and/or chap secrets file is correct and that 0.35 are the correct numbers for your country. In UK its 0.38 are you in Brazil?

/etc/modules

should contain

pppoe

and what is the output of 

cat /proc/net/atm/speed*

[maybe something useful here]("http://www.mail-archive.com/speedtouch@ml.free.fr/")

---

### Post by SpiralFire on 2007-03-18
using pppoe or nas0 as filter i got nothing

 pppd displayed this:

[ [IMG]http://www.imagehosting.com/out.php/t355698_pppdf.PNG[/IMG]](http://www.imagehosting.com/out.php/i355698_pppdf.PNG)


all lines, except the last one, appeared when i tried to connect using RP-PPPoE

the last one.. i dont knoe


cat /proc/net/atm/speed*  output:

[ [IMG]http://www.imagehosting.com/out.php/t355697_catf.PNG[/IMG]](http://www.imagehosting.com/out.php/i355697_catf.PNG)




now...

/etc/modules  doesn't exist here...
maybe because im using dapper and u edgy?

and yes, i'm in brazil
:)

---

### Post by SpiralFire on 2007-03-18
Well.. im writing this from ubuntu !!!

 thanks god i made it !!

:) :) :) 

that site u posted here did the work

remember i didnt have the nas0 interface?
searched there and it was a bridging utility problem
so i created it with this:

typed this (dont know if these are necessary)
modprobe ppp_generic

modprobe pppoatm (this one returned me with an error, as i dont use pppoatm)

modprobe br2684

then:

br2684ctl -b -c 0 -a 0.35

this created the nas0 interface
but i wasnt connected..
so i went to the rp-pppoe folder and ran ir through the terminal using ./go
when it asked me for the interface i'd use, it showed: "(default:nas0)"
so i put it, and it connected.. with no time out..

gonna reboot now, to see what i must do after the boot to connect
and if i can put this automatically
thanks Docter, love ya 4ever
x)~

---

### Post by Docter on 2007-03-19
Good stuff. I knew it'd be somehting I didn't have a clue about :D

I think you just need to make sure that your modules load on startup (sorry, i'm new to linux and edgy is my first experience). 

Once youre up and running I'd leave the debug option enabled and have a look through the debug log for the ppd process. You're looking for [LCP]protrej messages.

example:

rcvd [LCP - ProtRej Compression Control Protocol]

I received somehting like that and was getting kicked off my ADSL line so I addded the option 'noccp' in speedtch.

I also received a

rcvd [LCP ConfReq MRU=1400] (or something like that)

I had to set my MRU and MTU to 1400 in order to maintain a steady connection in /etc/ppp/options.


Type 'man pppd' for all the interesting options. You may not need to do any of that but it may be worth a look.

---

### Post by SpiralFire on 2007-03-19
Things are working..
 but im having trouble with the bootscript
 this is the dial content:

```

#!/bin/bash
modprobe ppp_generic
modprobe pppoatm
modprobe br2684
count=0
while [[ $((count++)) -lt 40 ]]
do
  sync=$(dmesg | grep 'ADSL line is up')
  if [ ! -z "$sync" ]
  then
    br2684ctl -b -c 0 -a 0.35
    sleep 3
    ifconfig nas0 192.168.0.1 netmask 255.255.255.0 up
    sleep 10
    pppd call speedtch
    exit 0
  fi
  sleep 1
done
echo "The SpeedTouch firmware did not load"

```

even with it there..
i have to go to terminal and do:
br2684ctl -b -c 0 -a 0.35
pppd call speedtch

AND connect using RP-PPPoE
...
using these commands:
sudo install -m 744 dial /etc/init.d &&

sudo ln -s ../init.d/dial /etc/rc2.d/S95dial &&

sudo ln -sf ppp/resolv.conf /etc/resolv.conf

returns me with this error:
[img]http://www.imagehosting.com/out.php/i348938_comerror.PNG[/img]
translation (if needed): "ln: creating simbolic link 'etc/rc2.d~~  to '../init.d/~~:  file exists"

ps: nothing to do with this.. how can i remove the examples "folder link" from my /home/polar ?

---

### Post by Docter on 2007-03-19
Having no experience in Dapper or with PPPoE I'm a little worried about sending you down the wrong path. However, I did notice that a bootscript for PPPoE from the below link is subtly different to yours.

[http://www.linux-usb.org/SpeedTouch/LFS/index.html]("http://www.linux-usb.org/SpeedTouch/LFS/index.html")

---

### Post by SpiralFire on 2007-03-19
is that for dapper?
what's that LFS on the link?
:S

couldnt do it..
some folders dont exist here
=\

---

### Post by Docter on 2007-03-20
LFS is just for a generic Linux File System install.

It seems your modules aren't loading at start up. I've heard tell of the pppoeconfig command too.

Also you may not have seen this:

```
wget -c [http://easylinux.info/uploads/rp-pppoe-3.6.tar.gz](http://easylinux.info/uploads/rp-pppoe-3.6.tar.gz)
sudo tar zxvf rp-pppoe-3.6.tar.gz -C /opt/
sudo chown -R root:root /opt/rp-pppoe-3.6/
gksudo gedit /usr/share/applications/RP-PPPoE.desktop

    * Insert the following lines into the new file 

[Desktop Entry]
Name=RP-PPPoE
Comment=RP-PPPoE
Exec=gksudo /opt/rp-pppoe-3.6/go-gui
Icon=pppoeconf.xpm
Terminal=false
Type=Application
Categories=Application;Network;

    * Save the edited file
    * Read #How to refresh GNOME panel
    * Applications -> Internet -> RP-PPPoE
```

[From here]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")

---

### Post by SpiralFire on 2007-03-21
i saw that
but the problem is the dialer
its the
sudo br2684ctl -b -c o -a 0.35
command..
i just need to add that to the boot..
just that command

---

