---
title: "[SOLVED] Setup and Configuration of Ericsson F3507g WWAN Card"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by sog on 2008-09-30
Has anyone managed to successfully configured and used an Ericsson F3507g HSPA card? 

My Thinkpad X301 came issued with one, and I confirmed the card as working under Windows before installing Ubuntu Hardy (subsequently upgraded to Intrepid). 

While Intrepid can see the card [1], it will not connect to the AT&T network. I've updated the settings (username = [email]WAP@CINGULARGPRS.COM[/email] and password = cingular1) in NetworkManager with those from scripts that have worked in the past, and these do not work. 

lsusb reveals the following:

```
sog@apone:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0bdb:1900 Ericsson Business Mobile Networks BV 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 17ef:4807 Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

According to the Ericsson datasheet [2], there is a Linux driver available for the card, but Lenovo does not make it available and inquiries to Ericsson have returned with a recommendation to talk to Lenovo. Nor can I find a driver in kernel - modinfo ericsson returns nothing. 

Is there any way to make this device work? Can, for example, ndiswrapper be employed on WWAN cards like this one, or is it wifi only?

Any and all help, suggestions, tips appreciated. 

[1] [http://www.flickr.com/photos/sog/2895856979/](http://www.flickr.com/photos/sog/2895856979/)
[2] [http://www.ericsson.com/solutions/mobile_broadband_modules/docs/mobile_broadband_module_datasheet_print.pdf](http://www.ericsson.com/solutions/mobile_broadband_modules/docs/mobile_broadband_module_datasheet_print.pdf)

---

### Post by nixscripter on 2008-09-30
Looking around, several people are in the same predicament. Google doesn't give any obvious answers.

If you have the windows XP driver (Vista won't work), I would suggest just trying ndiswrapper. It seems a lot of people would like to know if it works.

---

### Post by guhl on 2008-10-03
Hi !

I also got a X301 and this is my standing:

1. I am using a self compiled 2.6.27_rc8 kernel (be careful nor to compile or use the e1000e module for you LAN card as it could damage your cards eeprom, see [http://lkml.org/lkml/2008/10/1/368](http://lkml.org/lkml/2008/10/1/368) and the additional information about this)

2. I used the patch that you can find here [http://www.spinics.net/lists/linux-usb/msg10344.html](http://www.spinics.net/lists/linux-usb/msg10344.html) that makes the card visible to the option kernel module.

3. the result is that after loading the option module i have 4 new tty's.
(see output from my syslog)
```

Oct  3 10:50:52 myx301 usbcore: registered new interface driver usbserial
Oct  3 10:50:52 myx301 usbserial: USB Serial support registered for generic
Oct  3 10:50:52 myx301 usbcore: registered new interface driver usbserial_generic
Oct  3 10:50:52 myx301 usbserial: USB Serial Driver core
Oct  3 10:50:52 myx301 usbserial: USB Serial support registered for GSM modem (1-port)
Oct  3 10:50:52 myx301 option 2-4:1.0: GSM modem (1-port) converter detected
Oct  3 10:50:52 myx301 usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
Oct  3 10:50:52 myx301 option 2-4:1.5: GSM modem (1-port) converter detected
Oct  3 10:50:52 myx301 usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
Oct  3 10:50:52 myx301 option 2-4:1.6: GSM modem (1-port) converter detected
Oct  3 10:50:52 myx301 usb 2-4: GSM modem (1-port) converter now attached to ttyUSB2
Oct  3 10:50:52 myx301 option 2-4:1.7: GSM modem (1-port) converter detected
Oct  3 10:50:52 myx301 usb 2-4: GSM modem (1-port) converter now attached to ttyUSB3
Oct  3 10:50:52 myx301 option 2-4:1.8: GSM modem (1-port) converter detected
Oct  3 10:50:52 myx301 usb 2-4: GSM modem (1-port) converter now attached to ttyUSB4
Oct  3 10:50:52 myx301 usbcore: registered new interface driver option
Oct  3 10:50:52 myx301 option: USB Driver for GSM modems: v0.7.2

```

Now its time to start playing around with the ttys and find out how to communicate with the modem.

---

### Post by guhl on 2008-10-03
New Standing [SOLVED for the UMTS part]:

The device for communication with the Modem is not one of the ttyUSBx ports but ttyACM0 provided by the cdc_acm module!

```

Oct  3 10:31:58 myx301 usb 2-4: new high speed USB device using ehci_hcd and address 3
Oct  3 10:31:58 myx301 usb 2-4: configuration #1 chosen from 2 choices
Oct  3 10:31:58 myx301 option 2-4:1.0: GSM modem (1-port) converter detected
Oct  3 10:31:58 myx301 usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
Oct  3 10:31:58 myx301 cdc_acm 2-4:1.1: ttyACM0: USB ACM device
Oct  3 10:31:58 myx301 cdc_acm 2-4:1.3: ttyACM1: USB ACM device
Oct  3 10:31:58 myx301 option 2-4:1.5: GSM modem (1-port) converter detected
Oct  3 10:31:58 myx301 usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
Oct  3 10:31:58 myx301 option 2-4:1.6: GSM modem (1-port) converter detected
Oct  3 10:31:58 myx301 usb 2-4: GSM modem (1-port) converter now attached to ttyUSB2
Oct  3 10:31:58 myx301 option 2-4:1.7: GSM modem (1-port) converter detected
Oct  3 10:31:58 myx301 usb 2-4: GSM modem (1-port) converter now attached to ttyUSB3
Oct  3 10:31:58 myx301 option 2-4:1.8: GSM modem (1-port) converter detected
Oct  3 10:31:58 myx301 usb 2-4: GSM modem (1-port) converter now attached to ttyUSB4
Oct  3 10:31:58 myx301 cdc_acm 2-4:1.9: ttyACM2: USB ACM device

```

Then i used cu to connect to the port:
```

cu -l /dev/ttyACM0

```
And then i started to communicate with the modem:
```

AT+CFUN=1
OK
AT+CPIN="4310"
OK

*ESTKSMENU: A1-Dienste,0,6
254,News
253,Freizeit & Fun
252,B-FREE
251,TOOLBOX
250,Service
249,Hotlines


*EMWI: 1,0

+PACSP0

*ESTKDISP: 1,0,0,SIM Card PRO

AT+CGDCONT=1,"IP","A1.net"
OK

ATDT*99***1#
CONNECT

```

The important thing is that the GSM-Module has to be turned on by the AT+CFUN=1 command because it will not respond to any other commend without this. You can use AT+CFUN=0 to turn it off and save energy. 
So put this in the init settings of the software that you use to connect.

Have fun !

And now the next quest: How to use the GSM part of the module ?

---

### Post by sog on 2008-10-03
@guhl: fantastic! thanks for documenting your work. i'm debating whether to roll my own kernel or simply wait for that diff to trickle down into mainline. should i go the former, i'll definitely follow your lead here. outstanding.

---

### Post by nixscripter on 2008-10-03
Great. Please mark the thread as solved (under the thread tools menu).

---

### Post by sog on 2008-10-09
anybody else try that patch and have success? i just tried to apply it to the 2.6.27 source and got the following:

```
patching file drivers/usb/serial/option.c
patch: **** malformed patch at line 6: *tty, struct usb_serial_port *po

```

if anyone's got a fix, i'm all ears.

---

### Post by guhl on 2008-10-15
> **sog said:**
> anybody else try that patch and have success? i just tried to apply it to the 2.6.27 source and got the following:

```
patching file drivers/usb/serial/option.c
patch: **** malformed patch at line 6: *tty, struct usb_serial_port *po

```

if anyone's got a fix, i'm all ears.

Hi !

I think that you made a mistake when copying the patch source.
You can download my version of the patch from [http://www.thinkthinkdo.com/linux/option_F3507g.patch](http://www.thinkthinkdo.com/linux/option_F3507g.patch) (right click and save to)
Save it somewhere and then do the following:
```

cd /usr/src/linux-2.6.27 (your kernel source directory)
cat <path_to_patch>/option_F3507g.patch | patch -p1

```
Then you should be able to build the option module.

Remark:
The option module is not necessary to use the modem.
You can use the modem without the option module via device /dev/ttyACM0 that is created by the cdc_acm module (Kernel option -> Device Drivers -> USB support -> USB Modem (CDC ACM) support)

The option module adds another 5 tty's (/dev/ttyUSB0 - /dev/ttyUSB4) but i did not find out how and what fore they can be used yet.

good luck !

---

### Post by sog on 2008-10-16
> Remark:
The option module is not necessary to use the modem.
You can use the modem without the option module via device /dev/ttyACM0 that is created by the cdc_acm module (Kernel option -> Device Drivers -> USB support -> USB Modem (CDC ACM) support)

Fascinating. I did a make menuconfig on /usr/src/linux, and that CDC ACM was actually already present as a module, so I did a:

```
cu -l /dev/ttyACM0
```

And sure enough, it connected, and the LED symbol for the modem lit up for the first time. 

Unfortunately, the:

```
AT+CPIN="4310"
```

Generated an error. Nor did any of the three listings in NetworkManager successfully connect to AT&T's service. 

But still, this is progress! Thanks much for answering my earlier question.

---

### Post by guhl on 2008-10-16
> **sog said:**
> 

Unfortunately, the:

```
AT+CPIN="4310"
```

Generated an error. Nor did any of the three listings in NetworkManager successfully connect to AT&T's service. 



BE CAREFUL (and i am sorry that i thought this was obvious)!

4310 is the PIN-Code of my SIM-Card !!!
If you entered your SIM-Card and sent the PIN 4310 (which is probably not the PIN of your SIM-Card) more the 3 times then your SIM-Card is very likely locked now!
You will have to put the SIM-Card in a cell phone and unlock the SIM using your PUK-Code. (At least this is how this would work her in Austria).

Of course you also could put the SIM-Card into a phone and use the phone to disable the PIN-request for your SIM than you do not have to send the 
AT+CPIN='xxxx' (where xxxx is your PIN ;-) ) at all!

And just another remark:
The command AT+CGDCONT=1,"IP","A1.net" is for my carrier (Mobilkom Austria aka as A1) where the "A1.net" is the APN for my carrier. You will have to use the APN for AT&T (whatever that is).
The command ATDT*99***1# is the code to dial in. The number *99***1# could differ for AT&T.

I hope this helps!

---

### Post by sog on 2008-10-19
@guhl: ah, thanks. i hadn't known that, since none of the previous scripts i've used have asked for or required a PIN. but i should be ok, since i only tried to feed it the incorrect PIN once. that's a big help. 

now i just need to determine what the correct PIN is, as i have all information (EMEI, etc) for the device except that. i'm told the default for Cingular devices (which this is) is 1234, but if i only have two more attempts before the SIM is locked, i'm hesitant to experiment. 

incidentally, the card is being used successfully on a T500 using the following instructions from Bob Lees [see [http://redmonk.com/sogrady/2008/09/24/apone/#comment-480392]("http://redmonk.com/sogrady/2008/09/24/apone/#comment-480392"): 

> You need to load the cdc_acm module and the device appears as ttyACM[0-2]. Turn it on with at+cfun=1 and use umtsmon to control it

hope this helps.

---

### Post by puppywhacker on 2008-10-19
Just as background information

ATDT*99***1#

99 is the special code for dialing a data-connection. The 1 stands for data-profile 1. You could use the same if you connect a mobile phone for instance via bluetooth.

---

### Post by ccc1 on 2008-11-07
i have a few questions concerning the  Ericsson F3507g card:

does this card support GPS and if so is it working under ubuntu?
is it necessary to compile a kernel from kernel.org to get it working?

ccc1

---

### Post by sog on 2008-11-08
> does this card support GPS and if so is it working under ubuntu?

the answer appears to be yes. see the link [here]("http://redmonk.com/sogrady/2008/09/24/apone/#comment-483236").

---

### Post by ccc1 on 2008-11-09
> **sog said:**
> the answer appears to be yes. see the link [here]("http://redmonk.com/sogrady/2008/09/24/apone/#comment-483236").

nice :D and to get the card working under intrepid i have to patch the ubuntu kernel or do i have to get a kernel from kernel.org?

---

### Post by sog on 2008-11-09
i do not have the card "working," per se, because i have been unable to determine my SIM PIN, but i can activate the device and communicate with it using the stock Intrepid kernel.

---

### Post by ccc1 on 2008-11-09
> **sog said:**
> i can activate the device and communicate with it using the stock Intrepid kernel.

perfect :)

---

### Post by seiser on 2008-11-24
Hi, this all looks quite promising. But I'm still not getting it right. Maybe someone can help:
I'm using the latest Intrepid Ubuntu and the correct module (_not_ patched) seems to come up fine automatically:

```
martin@martin-laptop:~$ lsmod | grep cdc_acm
cdc_acm                23456  0 
usbcore               148848  9 zaurus,cdc_ether,usbnet,cdc_acm,btusb,usbhid,ehci_hcd,uhci_hcd
```

```
martin@martin-laptop:~$ ls /dev/ttyACM*
/dev/ttyACM0  /dev/ttyACM1  /dev/ttyACM2
```

```

martin@martin-laptop:~$ cu -l /dev/ttyACM0
Connected.
AT+CFUN=1
OK

*ESTKSMENU: BASE Dienste,0,3
1,SMS Info
2,Sprach Info
3,Multimedia


*EMWI: 1,0

+PACSP0

AT+CGDCONT=1,"IP","internet.eplus.de"
OK

```

now, when I type "ATDT*99***1#", I get this (the command itself gets cleared):

```
~&#65533;}#&#65533;!}!}!} }9}#}%&#65533;#}%}(}"}'}"}"}&} } } } }%}&&#65533;&#65533;}6Y&#1696;~
CONNECT
~&#65533;}#&#65533;!}!}"} }9}#}%&#65533;#}%}(}"}'}"}"}&} } } } }%}&&#65533;&#65533;}6Y}6M~~&#65533;}#&#65533;!}!}#} }9}#}%&#65533;#}%}(}"}'}"}"}&} } } } }%}&&#65533;&#65533;}6YR}6~~&#65533;}#&#65533;!}!}$} }9}#}%&#65533;#}%}(}"}'}"}"}&} } } } }%}&&#65533;&#65533;}6Y&#65533;&#65533;~~&#65533;}#&#65533;!}!}%} }9}#}%&#65533;#}%}(}"}'}"}"}&} } } } }%}&&#65533;&#65533;}6Y&#65533;&#65533;~~&#65533;}#&#65533;!}!}&} }9}#}%&#65533;#}%}(}"}'}"}"}&} } } } }%}&&#65533;&#65533;}6Y}7(~~&#65533;}#&#65533;!}!}'} }9}#}%&#65533;#}%}(}"}'}"}"}&} } } } }%}&&#65533;&#65533;}6YSs~~&#65533;}#&#65533;!}!}(} }9}#}%&#65533;#}%}(}"}'}"}"}&} } } } }%}&&#65533;&#65533;}6Y&#65533;1~~&#65533;}#&#65533;!}!})} }9}#}%&#65533;#}%}(}"}'}"}"}&} } } } }%}&&#65533;&#65533;}6Y&#65533;j~~&#65533;}#&#65533;!}!}*} }9}#}%&#65533;#}%}(}"}'}"}"}&} } } } }%}&&#65533;&#65533;}6Y}4&#65533;~
NO CARRIER
```

I don't really know what the last two commands mean or if I need to adjust them to my provider. Where can I find any information about that data? Or, where did you, guhl, find them?

guten Abend

---

### Post by glowbus on 2008-11-27
> **guhl said:**
> New Standing [SOLVED for the UMTS part]:

The important thing is that the GSM-Module has to be turned on by the AT+CFUN=1 command because it will not respond to any other commend without this. You can use AT+CFUN=0 to turn it off and save energy. 
**So put this in the init settings of the software that you use to connect.**
?

Hi,

does somebody know where I could change the init script for the networkmanager in intrepid?

Kind regards

Andreas

---

### Post by sog on 2008-12-14
I can't help you on the NetworkManager front - as I haven't seen anybody get that to work yet, but there's a UMTSMON method here:

[http://www.bjw.me.uk/2008/12/howto-ubuntu-810-dell-5530-3gwwan-and.html](http://www.bjw.me.uk/2008/12/howto-ubuntu-810-dell-5530-3gwwan-and.html)

If you're comfortable with the command line, I've written up a HowTo using instructions from a Thinkwiki.org user here:

[http://redmonk.com/sogrady/2008/12/07/how-to-use-an-att-ericsson-f3507g-card-on-ubuntu-intrepid/](http://redmonk.com/sogrady/2008/12/07/how-to-use-an-att-ericsson-f3507g-card-on-ubuntu-intrepid/)

Enjoy.

---

### Post by Siúlóir on 2008-12-30
> **seiser said:**
> Hi, this all looks quite promising. But I'm still not getting it right. Maybe someone can help:
I'm using the latest Intrepid Ubuntu and the correct module (_not_ patched) seems to come up fine automatically:

I just got E-Plus (Base) running with the F3507g using wvdial.

> **seiser said:**
> now, when I type "ATDT*99***1#", I get this (the command itself gets cleared):

The dial string for E-Plus is "*99#".

See my wvdial.conf:

```
[Dialer Defaults]
New PPPD = yes
Stupid Mode = 1
Modem Type = USB Modem

[Dialer signal]
Modem = /dev/ttyACM0
Init1 = AT+CSQ
Init2 = AT+COPS?

[Dialer gps]
Modem = /dev/ttyACM2
Init1 = AT*E2GPSCTL=1,10,1
Init2 = AT*E2GPSNPD

[Dialer on]
Modem = /dev/ttyACM0
Init1 = AT+CFUN=1

[Dialer off]
Modem = /dev/ttyACM0
Init1 = AT+CFUN=4

[Dialer connect]
Modem = /dev/ttyACM1
Init1 = AT+CGDCONT=1,"IP","internet.eplus.de"
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Baud = 460800
ISDN = 0
Phone = *99#
Username = eplus
Password = gprs

```

Now I can connect using **wvdial on** followed by **wvdial connect**.

Currently I am still fiddling with the GPS feature. I grabbed the GPS settings (as most of the others) from [this post]("http://ubuntuforums.org/showthread.php?t=979587"), however, in [this ThinkWiki article]("http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module#Using_the_card_as_GPSr"), the author describes how to utilize GPS using separate TTYs.

Cheers

Siúlóir

---

### Post by avilella on 2009-01-17
Hi all,

I took the liberty of creating a launchpad team for the people who own or develop for the Lenovo X301 laptops, so that we can have more visibility upstream when having to ask for patches or support.

[https://launchpad.net/~x301](https://launchpad.net/~x301)

I'll be sending a couple of messages to ubuntuforums and notebookreview forums to gather the ~10 users I've identified so far.

Cheers,

Albert.

---

### Post by michael.sacher on 2009-04-02
Hi there,

I've been able to communicate with the card (communication device was /dev/ttyUSB0 though)

I've played a little with the gps setting and all of a sudden the card stopped working.

Now I can't see it anymore with lsusb or dmesg | grep GSM

I don't have the tools here at the moment to check for loose cables.

Could it be damaged?


Thanks
Michael

---

### Post by torgnyj on 2009-06-24
There is now a sourceforge project developing software for the Ericsson mobile broadband modules. Currently you can find information and code (even Ubuntu packages) for getting NetworkManager (with modem-manager support, PPP dialup should be working already in Ubuntu Jaunty) working with the modules. GPS software is coming too.

Details are available here: [http://sourceforge.net/apps/mediawiki/mbm/](http://sourceforge.net/apps/mediawiki/mbm/)

---

### Post by gillianreynolds on 2011-05-09
Okay Dear, I put code hare.

Code:
     [Dialer Defaults]
New PPPD = yes
Stupid Mode = 1
Modem Type = USB Modem

[Dialer signal]
Modem = /dev/ttyACM0
Init1 = AT+CSQ
Init2 = AT+COPS?

[Dialer gps]
Modem = /dev/ttyACM2
Init1 = AT*E2GPSCTL=1,10,1
Init2 = AT*E2GPSNPD

[Dialer on]
Modem = /dev/ttyACM0
Init1 = AT+CFUN=1

[Dialer off]
Modem = /dev/ttyACM0
Init1 = AT+CFUN=4

[Dialer connect]
Modem = /dev/ttyACM1
Init1 = AT+CGDCONT=1,"IP","internet.eplus.de"
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Baud = 460800
ISDN = 0
Phone = *99#
Username = eplus
Password = gprs



----------------------------------------
Thanks
  [cheap   oostende hotels](http://www.oostendehotelsstay.com/cheap-hotels-in-oostende.html)

---

