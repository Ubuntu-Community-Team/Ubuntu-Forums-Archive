---
title: "3 Mobile Broadband USB Modem"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by scorpia1275 on 2007-11-11
Hi Guys.

I was just wondering if anyone has and has managed to get working one of these new mobile broadband USB modems that the mobile network operators are offering at the moment?  Strictly speaking the software that comes with them only supports Windows and OSX, just wondering if anyone has been able to get one working in Linux - specifically Ubuntu?  I know most networks do them now, but as I am with the 3 network in the UK I would probably get their one.

My circumstances are changing shortly and I am going to need completely wireless broadband, If it is not possible to get one of these things working under Linux, then I'll regretably have to go back to Vista.

Any ideas?

Cheers

Scorpia

---

### Post by scorp123 on 2007-11-11
> **scorpia1275 said:**
>  I was just wondering if anyone has and has managed to get working one of these new mobile broadband USB modems that the mobile network operators are offering at the moment?  Yes, no problem whatsoever. Works even better on Linux than under Windows.

> **scorpia1275 said:**
>   Strictly speaking the software that comes with them only supports Windows and OSX, You don't need that stupid software. Linux already has everything you need out of the box, more or less. If any parts are missing it's easy to install them via Synaptic.

> **scorpia1275 said:**
>  but as I am with the 3 network in the UK I would probably get their one. How about offering some technical details? For starters: What make and modem do they offer? 

I myself have a **Novatel Ovation MC950D** (GPRS, EDGE, UMTS, HSDPA modem for USB) and it works tip top. Other folks I know have a **Huawei E220** USB modem (I originally wanted that one ... but the shop didn't have them anymore so instead I took the risk and bought the Novatel MC950D instead .... and to my positive surprise it just worked :) ) and that one is known to work as well.

Some links ... 

_**Huawei E220:**_
[http://ske.sourceforge.net/html/projects/huawei/huawei_tre.html](http://ske.sourceforge.net/html/projects/huawei/huawei_tre.html)
[http://oozie.fm.interia.pl/pro/huawei-e220/index.html](http://oozie.fm.interia.pl/pro/huawei-e220/index.html)
[http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/](http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/)
[http://ubuntu.frankenberger.at/Huawei_E220.html](http://ubuntu.frankenberger.at/Huawei_E220.html)

My own posting over at the Mint forums regarding the **_Novatel Ovation MC950D:_**
... :lolflag: ... their site is down again. How typical :)
[B][U]
Instead I will post my stuff here again:[/U][/B]

Basically all what I know about the **Novatel Ovation MC950D USB stick** is deducted from here where they explain how to get a similar model working -- kudos to Sprint for this PDF:
[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

_So let's jump fast forward:_

I insert the stick, the virtual CD-ROM part with the Windoze drivers shows up and then I execute (with "sudo") this script below (I have it as icon in my panel): ```
#! /bin/bash
sudo modprobe -r usbserial
sudo eject /dev/scd1
sudo modprobe usbserial vendor=0x1410 product=0x4400 
```

Once you did above steps the modem works tip top as a PPP modem. I use wvdial for my purposes. My **/etc/wvdial.conf** for the Swiss provider SUNRISE looks like this: ```
[Dialer Sunrise]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0&C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = USB Modem
Phone = *99#
Username = ''
Password = ''
Carrier Check = no
Stupid Mode = yes  
``` Chances are that above config file will work pretty much with any provider as all the options up there are pretty much generic and not provider-dependant. So now, when I want to connect via the modem, I have another script ready that executes this command for me: **sudo wvdial Sunrise**  ... and voila, I am connected with the Internet.

**_Something I forgot to add:_**

In my case I had to get a new SIM card. So originally you'd insert the SIM card into the modem, insert the stick into a running Windoze system and then use the special software the modem comes with to activate the SIM card. In one of those forums about the Huawei modem (see my links up there) I read that you can just as well use your mobile phone to activate the SIM card. That's precisely how I did it. I first inserted my shiny new SIM into a mobile phone and went through the activation procedures of my provider (they sent me three or so SMS with infos I needed wo write down and confirm ... totally easy!). After that I deactivated the PIN dialogue via the phone's setup so I don't have to write special scripts that would send the PIN code every time I insert the modem into my Linux system (it can be done by sending modem commands such as **AT+CPIN="1234"** ... But I didn't want to bother with this). So after the SIM is activated I inserted it into the modem and everything was good to go.

Hope this helped? :)

---

### Post by Lem on 2007-11-11
Also look at;

[http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php](http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php)

---

### Post by scorpia1275 on 2007-11-11
Hey guys thanks for the responses very helpful.  Just ordered my package so just got to wait for it to arrive now and then see how things go.

Cheers

Scrorpia

---

### Post by spydon on 2007-11-17
Is it working? I'm curious... :P

---

### Post by mips on 2007-11-17
[http://ubuntuforums.org/showthread.php?t=569767](http://ubuntuforums.org/showthread.php?t=569767)
[http://ubuntuforums.org/showthread.php?t=262867](http://ubuntuforums.org/showthread.php?t=262867)

You should be able to get the 1st link above to work with networks other than vodafone as that is what some people in the second thread did. Much easier than stuffing around with config files etc.

---

### Post by CrackersKeenan on 2007-11-18
I got it working with the modprobe commands, but I also had to connect it to a friend's Windows machine first to somehow activate the card.  I tried putting the SIM in my phone but that didn't do anything.  Works fine now.

---

### Post by adm1968 on 2007-11-20
Hi!
I have followed the instructions provided above, with no success.

This is what I get in the terminal window:

adm@mivaio:~$ sudo modprobe -r usbserial 
adm@mivaio:~$ sudo modprobe usbserial vendor=0x1410 product= 0x4400 
FATAL: Error inserting usbserial (/lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument

Am I doing something wrong?

I am using Ubuntu 7.10 with all latest updates.

:confused:

---

### Post by scorp123 on 2007-11-20
> **adm1968 said:**
>  This is what I get in the terminal window:

adm@mivaio:~$ sudo modprobe -r usbserial 
adm@mivaio:~$ sudo modprobe usbserial vendor=0x1410 product= 0x4400  That was an example which works for the **NOVATEL OVATION MC950D** modem ... if you have a different modem (e.g Huawei E220), then the "vendor=" and "product=" parameters will be different. So I'd suggest you tell us about your modem a little? 

Another idea. Remove any USB devices from your PC and then cold-start it (= total poweroff!). Then start it again. Then connect your device.

Question here: Does the virtual CD-ROM part with the Windows drivers show up? (it should ...)

Once you get there unmount the virtual "CD-ROM" device and open a terminal and then type this command: **lsusb**  (if it says something like "command not found" then please install its package first: **apt-get install usbutils** ...) ... And now let's watch the output you get!

If I do that here on my laptop I get this:
```
:~ > lsusb
Bus 005 Device 009: ID 0c45:62c0 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
**[COLOR="Red"]Bus 002 Device 005: ID _1410_:_4400_[/COLOR]**  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000
``` See that output above? The "Microdia" device is my USB web cam ... so we can ignore that. All devices with all the zeros "0000:0000" can be ignored too. What's interesting here is the line I marked red ... that's my Novatel Ovation MC950D (that's how I found the right parameters!).

So there you go for the right values for the command line above and how you can find these yourself if you need to.

BTW, "**sudo lsusb -v**" generates even more output ... just in case you really really want to be sure you really caught the right device. In my case:
```
Bus 002 Device 005: ID **[COLOR="Red"]1410:4400[/COLOR]**  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  id**[COLOR="Red"]Vendor           0x1410[/COLOR]** 
  id**[COLOR="Red"]Product          0x4400[/COLOR]** 
  bcdDevice            0.00
  [B]iManufacturer           1 [COLOR="Red"]Novatel Wireless[/COLOR]
  iProduct                2 [COLOR="Red"]Novatel Wireless HSUPA Modem[/COLOR][/B]
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           62
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             128
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)
``` Again ... important sections are highlighted red here. That output tells me I caught the right device and the parameters for "vendor=" and "product=" are right there.

Chances are that the values for your modem might be different but as you can see it's not that hard to find these values yourself.

Hope this helped? :)

---

### Post by adm1968 on 2007-11-20
My modem is in fact the Novatel MC950D 
Thanks a lot, that looks like a fully comprehensive answer

I'll give it a try tomorrow to see how it goes ...
Can't wait to stop using Windoze again

:popcorn:

---

### Post by scorp123 on 2007-11-20
> **adm1968 said:**
>  My modem is in fact the Novatel MC950D  Ah OK ... I thought you maybe had a different one. You see, there are many models and they are all very similar, but they all have different vendor and product ID's. I took all the infos I know from this PDF I found at Sprint's side (kudos to you guys for posting this type of "Linux How To"!! I wish more telecom providers did that!):
[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

They provide an example with another Novatel-something card (which I suppose is being sold in North America and Asia?) which has an only slightly different product and vendor ID than the MC950D .... So "inspired" by this and "armed" with their examples from above PDF I found it's easy to get my MC950D working.

> **adm1968 said:**
>  Thanks a lot, that looks like a fully comprehensive answer. I'll give it a try tomorrow to see how it goes ... I know that for example the Huawei E220 has sometimes different vendor and product ID's ... I guess it depends on the factory and "production batch" the modem is from. So maybe it's something similar in your case and those numbers are now different in your case? You should try out "lsusb" and see what numbers it will spit out.

Just watch out for typos. I noticed that in your posting you had a space between the "=" sign and the hexadecimal address of the "product=" part .... that too may cause error messages. Sorry if this sounds "snobbish" or something, it's just to exclude any typo errors ... :)

---

### Post by beemerbiker on 2007-11-20
I have a UK 3-mobile broadband modem Huawei E220 that works fine with Windows.  I can't get it to work in Gutsy Gibbon following the advice in this thread and elsewhere, however.  Help and advice much appreciated -- I am complete novice at Linux and I have only until Saturday 23 Nov to get this working, when my daughter comes to pick up her laptop, and I have praised Ubuntu to the skies (it is fast and uncluttered compared to bloated Win XP).  I also emailed Three asking for Linux support (you never know!) and got the reply "As there are many requests for Mobile Broad Band services on Linux, it has been forwarded to the relevant department and when it’s available we’ll update it on our website www.three.co.uk".

My story so far ...

(1) The modem doesn't come up as a USB stick when I plug it in under Ubuntu, as this thread seems to suggest it should. 
(2) When I do the command
sudo modprobe -r usbserial
it responds fatal error that usbserial is in use.
(3) sudo eject /dev/scd1 
responds there is no such device.
(4) sudo modprobe usbserial vendor=0x12d1 product=0x1003
gives no response (is that good?).  (I got the vendor and product codes from Device Manager variables usb.vendor_id and usb.product_id)
(5) I've edited wvdial.config to include (mostly gobbledegook to me, I'm afraid)
[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","three.co.uk"
(6) When I then do the command
wvdial hsdpa
it responds ..
WvDial<*1>: Wvdial: Internet dialer version 1.56
WvDial<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending ATQ0
WvDial<*1>: Re-sending ATZ
WvDial<Err>: Modem not responding.

Any suggestions very welcome.  Thanks, guys.

---

### Post by scorp123 on 2007-11-20
> **beemerbiker said:**
> I have a UK 3-mobile broadband modem Huawei E220  1. Open a terminal window and leave it open ...
2. plug-in your Huawei USB stick
3. *immediately* go back to the terminal window and type this command: **dmesg**

Can you post (copy & paste) that output here? Maybe you have to type "**dmesg**" several times just to make sure we get some useful output.

Could be that you have a flaky USB port and the Huawei doesn't get recognized in that port.

Those modems when they are inserted into any PC should at first show up as a virtual "CD-ROM" device which contains all the Windows drivers. Only when you u(n)mount the "CD drive" it switches into the modem mode.

But we'd need the "dmesg" output to really be able to tell what's going on.

---

### Post by beemerbiker on 2007-11-21
> **scorp123 said:**
> 1. Open a terminal window and leave it open ...
2. plug-in your Huawei USB stick
3. *immediately* go back to the terminal window and type this command: **dmesg**

Thanks.  Done that -- it gives over 400 lines of output(!!), which I guess is too big to include here, but I have pasted below the last several lines, which seem interesting:
============
[  215.648000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  215.808000] usb 1-1: configuration #1 chosen from 1 choice
[  216.336000] usbcore: registered new interface driver usbserial
[  216.336000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  216.340000] usbcore: registered new interface driver usbserial_generic
[  216.340000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  216.376000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[  216.376000] option 1-1:1.0: GSM modem (1-port) converter detected
[  216.380000] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[  216.380000] usbcore: registered new interface driver option
[  216.380000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
[  216.408000] usbcore: registered new interface driver libusual
==============

I don't think it can be a flaky USB port, as the same port works OK in Windows with this modem and with a USB flash stick.  But the modem definitely doesn't "mount" itself as a media device in Ubuntu (whereas an ordinary flash stick does). 

Thanks for the help and interest in my problem.

---

### Post by scorp123 on 2007-11-21
> **beemerbiker said:**
>  [  216.380000] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0 Well ... that line tells pretty much all there is to tell. :)  Your modem already gets instantly recognised as modem ... you can skip messing with those "usbserial" commands and use your modem right away. :)

---

### Post by beemerbiker on 2007-11-21
Thanks, scorp123, that's good news!  But I'm still adrift.  Do I now edit etc/wvdial.conf along the lines of ...

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","three.co.uk"

and then "sudo wvdial hsdpa" to connect to my ISP?

That fails with the edits listed above.  The problem is, being a complete novice, I don't know which lines on the dialer edits above are appropriate or even what they try to do.  the first two seem understandable, but I haven't a clue what some of the others do (I got them form a post where someone was connecting a Huawei E220 to the '3' network in Ireland). 

Any advice?  Which lines are optional?  Which should be trial and errored, and with what sort of alternatives?

Thanks for your time.

---

### Post by scorp123 on 2007-11-21
> **beemerbiker said:**
>  Any advice?  Did you activate your SIM card already and deactivate the need for having the PIN entered? You could use a program such as **minicom** and have it connect to the modem on **/dev/ttyUSB0** and test if the modem will react at all. You will find a "minicom" tutorial here:
[http://www.cisl.ucar.edu/nets/intro/staff/siemsen/tools/minicom.html](http://www.cisl.ucar.edu/nets/intro/staff/siemsen/tools/minicom.html)

Just follow the instructions regarding "minicom -s"  (because we are on Ubuntu you'd type: **sudo minicom -c on -s**  ) and have "minicom" point at **/dev/ttyUSB0** .... Don't change any of the speed setting though. I didn't have to do that either and the 9600 suggested on that page are insanely slow. Just leave the speed settings untouched.

Once everything is setup (your config is pointing to **/dev/ttyUSB0** as "modem" device) you can ask your modem stuff via **AT** commands and it should respond with "OK". Example from my system (stuff I typed is highlighted red ... the rest are answers from the system): ```
Welcome to minicom 2.2

OPTIONS: I18n 
Compiled on Apr 27 2007, 15:50:20.
Port /dev/ttyUSB0

                 Press CTRL-A Z for help on special keys
                                                       
AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0                       
OK                                                     
[COLOR="Red"]ati1[/COLOR]                                                   
Manufacturer: Novatel Wireless Incorporated
Model: Ovation MC950D Card
Revision: 3.10.00.0-00  [2007-08-13 08:59:23]
+GCAP: +CGSM,+DS
[COLOR="Red"]at+cgdcont?[/COLOR]
+CGDCONT: 1,"IP","internet","",0,0
``` If you can get that far than everything else should work too .... But my suspicion is that your card is waiting for PIN code entry and until that happens it is refusing to do anything ....

PIN codes can be entered with an "AT" command too .... you could even put it into your wvdial.conf file as "Init1" string (just move all the init stuff up by one number):
**AT+CPIN="xxxx"**  .... Where xxxx would be your PIN code.

If you're not sure if the PIN entry is needed you can ask it to tell you:
**AT+CPIN?**

If it responds with "**+CPIN: READY**" then PIN entry is not needed and something else is the problem ...  If it however responds with something like:
[B]+CPIN: SIM PIN?
+CPIN: SIM PUK?[/B] ... Then you'd need to enter the appropriate PIN or PUK code. Your modem should instantly work afterwards. ... or so I hope ...

:)

---

### Post by adm1968 on 2007-11-22
Well, my MC950D did get identified by lsusb -v:

Bus 001 Device 004: ID 1410:4400  
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               1.10 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64 
  idVendor           0x1410 
  idProduct          0x4400 
  bcdDevice            0.00 
[B]  iManufacturer           1 Novatel Wireless 
  iProduct                2 Novatel Wireless HSUPA Modem[/B] 
  iSerial                 4 356846010358811 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength          108 
    bNumInterfaces          4 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0xa0 
      (Bus Powered) 
      Remote Wakeup 
    MaxPower              500mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           3 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              3 Data Interface 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x81  EP 1 IN 
        bmAttributes            3 
          Transfer Type            Interrupt 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0010  1x 16 bytes 
        bInterval             128 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x82  EP 2 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x02  EP 2 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               0 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        1 
      bAlternateSetting       0 
      bNumEndpoints           2 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              3 Data Interface 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x84  EP 4 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x04  EP 4 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               0 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        2 
      bAlternateSetting       0 
      bNumEndpoints           2 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              3 Data Interface 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x86  EP 6 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x06  EP 6 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               0 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        3 
      bAlternateSetting       0 
      bNumEndpoints           2 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              3 Data Interface 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x87  EP 7 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x07  EP 7 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0040  1x 64 bytes 
        bInterval               0 
Device Status:     0x0002 
  (Bus Powered) 
  Remote Wakeup Enabled 

However, it still doesn´t work
Will double check for typing errors ...

The problem is, I have to go back to windows every time, as I have no other connection for the time being

:(

---

### Post by scorp123 on 2007-11-22
See my other answer in this thread. Can you try and do the same? e.g. use **minicom** and try if you can talk to the modem?

---

### Post by adm1968 on 2007-11-22
> **scorp123 said:**
> See my other answer in this thread. Can you try and do the same? e.g. use **minicom** and try if you can talk to the modem?

My dmesg output:
[ 1257.504000] usbserial: `' invalid for parameter `product' 
[ 1275.408000] usbserial: `' invalid for parameter `product' 
[ 1399.628000] usbserial: `' invalid for parameter `product' 

I did check for spelling. I pasted your own command, no success.

However, I'll do what you are saying, if the output above doesn't suggest otherwise. 
I have just restarted my laptop and downloaded minicom and its tutorial from Windoze.

THANKS!

---

### Post by scorp123 on 2007-11-22
> **adm1968 said:**
>  My dmesg output:
[ 1257.504000] usbserial: `' invalid for parameter `product'   Can you please post again the *exact* command you executed in order to get this error? According to your "lsusb" output your modem should have the same parameters as mine. Taken from your post above:```
Bus 001 Device 004: ID **1410:4400**
 ...
 idVendor **0x1410**
idProduct **0x4400** 
```

---

### Post by adm1968 on 2007-11-22
> **scorp123 said:**
> Can you please post again the *exact* command you executed in order to get this error? According to your "lsusb" output your modem should have the same parameters as mine. Taken from your post above:```
Bus 001 Device 004: ID **1410:4400**
 ...
 idVendor **0x1410**
idProduct **0x4400** 
```

Indeed. I copied and pasted _your own_ command, as shown in page 1 of this thread.
And yes, my modem should have the same parameters as yours.

If we manage to resolve this, I have no doubt that a chilled beer will be waiting for you in Madrid :)

---

### Post by scorp123 on 2007-11-22
> **adm1968 said:**
> Indeed. I copied and pasted _your own_ command Hmmm .... can you try and type this stuff by hand? Maybe there is something wrong e.g. some weird invisible character that somehow made its way into the posting and which causes the error. I had such weird things already happen to me on other forums.

But just to make sure we're on the right track:
- You do get the virtual CD-ROM part when you plugin your Novatel modem, right?
- You don't get any error when you unmount that CD-ROM part?
- In your case it's still the "usbserial" part fails, right?
- The modem works tip top on Windows, right?

Just to make sure I still got everything right .... :)

---

### Post by adm1968 on 2007-11-22
> **scorp123 said:**
> Hmmm .... can you try and type this stuff by hand? Maybe there is something wrong e.g. some weird invisible character that somehow made its way into the posting and which causes the error. I had such weird things already happen to me on other forums.

But just to make sure we're on the right track:
- You do get the virtual CD-ROM part when you plugin your Novatel modem, right?
- You don't get any error when you unmount that CD-ROM part?
- In your case it's still the "usbserial" part fails, right?
- The modem works tip top on Windows, right?

Just to make sure I still got everything right .... :)

The CD-ROM part does turn up, it is mounted by Ubuntu, and all the files are visible
I don't get any errors when unmounting
That's right, it's only the "usbserial" part that fails
The modem works perfectly in Windows

---

### Post by scorp123 on 2007-11-22
> **adm1968 said:**
>  I don't get any errors when unmounting
That's right, it's only the "usbserial" part that fails So it's most likely a typo or some other mysterious error somewhere somehow in that part. :confused:

Are you using a script of some sorts to execute all those commands in a row or are you typing them by hand? Can you please post that again? Just to be sure ...

---

### Post by adm1968 on 2007-11-22
> **scorp123 said:**
> 
Are you using a script of some sorts to execute all those commands in a row or are you typing them by hand? Can you please post that again? Just to be sure ...
I am not using any scripts, everything is either copied or pasted.
I will give it a try later today or over the weekend, as I have no other connection than the modem on Windoze.

Cheers!

---

### Post by scorp123 on 2007-11-22
> **adm1968 said:**
> I am not using any scripts, everything is either copied or pasted. Let's try typing that stuff by hand (it isn't so hard). I suspect that there might be some "hidden characters" or other UTF / ISO-8859-1 / whatever weirdness, somewhere between my "copy & paste" and my browser and your "copy & paste" and your browser. This has already happened to me too on other forums ... copy & paste looked OK, but whatever I copied just didn't work because there were some sort of "invisible control characters" and some other font weirdnesses .... Typing stuff myself fixed it then. I suspect this might work here too? Other than that I am really running out of ideas now, because your modem really should work.

So after you insert your modem and the virtual CD-ROM part shows up let's type these three lines into a terminal (unless copy & paste would work all of a sudden?). It's not that hard. Just make sure you don't put any spaces where there aren't any. And it's all written in lower case.

```
[SIZE="4"]sudo modprobe -r usbserial
sudo eject /dev/scd1
sudo modprobe usbserial vendor=0x1410 product=0x4400[/SIZE]

```

---

### Post by adm1968 on 2007-11-24
Will do exactly that 
I'll keep all fingers crossed ...

---

### Post by adm1968 on 2007-11-26
Scorp, I'm afraid I followed your directions, and still got the same error
Will something enlighten us?
It really is sad that I be forced to go back to Windoze
:sad:

---

### Post by scorp123 on 2007-11-26
> **adm1968 said:**
> Scorp, I'm afraid I followed your directions, and still got the same error  Can you please copy & paste your entire terminal session from start to end, incl. everything you typed and everything the system returned? Also the complete output from "dmesg" would be helpful. Please put it here.

---

### Post by adm1968 on 2007-11-27
Here it goes:

Laptop switched ON

Logitech USB mouse inserted
Console
arturo@mivaio:~$ lsusb 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c00f Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  	

Novatel MC950D USB Modem inserted
Console
arturo@mivaio:~$ lsusb 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c00f Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 1410:5010  
Bus 001 Device 001: ID 0000:0000 

2 minutes later the output is different ...
arturo@mivaio:~$ lsusb 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c00f Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1410:4400  
Bus 001 Device 001: ID 0000:0000 

IMPORTANT
The file manager in Ubuntu opens the USB device folder, showing all the files, and then CLOSES it with no intervention on my part
(the device is shown as a CD in the desktop for a minute; after this it 'dissapears') 

arturo@mivaio:~$ dmesg
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1]) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1]) 
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0]) 
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
[    0.000000] ACPI: IRQ0 used by override. 
[    0.000000] ACPI: IRQ2 used by override. 
[    0.000000] ACPI: IRQ9 used by override. 
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
[    0.000000] Using ACPI (MADT) for SMP configuration information 
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000) 
[    0.000000] Built 1 zonelists.  Total pages: 127635 
[    0.000000] Kernel command line: root=UUID=4dbcda3d-8c30-4ef0-a7eb-d09c3ae132eb ro quiet splash locale=es_ES 
[    0.000000] mapped APIC to ffffd000 (fee00000) 
[    0.000000] mapped IOAPIC to ffffc000 (fec00000) 
[    0.000000] Enabling fast FPU save and restore... done. 
[    0.000000] Enabling unmasked SIMD FPU exception support... done. 
[    0.000000] Initializing CPU#0 
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes) 
[    0.000000] Detected 1064.034 MHz processor. 
[   13.388227] Console: colour VGA+ 80x25 
[   13.388413] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) 
[   13.388690] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) 
[   13.406109] Memory: 498316k/514560k available (2015k kernel code, 15648k reserved, 916k data, 364k init, 0k highmem) 
[   13.406124] virtual kernel memory layout: 
[   13.406126]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB) 
[   13.406128]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
[   13.406130]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB) 
[   13.406132]     lowmem  : 0xc0000000 - 0xdf680000   ( 502 MB) 
[   13.406134]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB) 
[   13.406137]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB) 
[   13.406139]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB) 
[   13.406144] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
[   13.406195] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1 
[   13.486198] Calibrating delay using timer specific routine.. 2130.82 BogoMIPS (lpj=4261642) 
[   13.486235] Security Framework v1.0.0 initialized 
[   13.486247] SELinux:  Disabled at boot. 
[   13.486268] Mount-cache hash table entries: 512 
[   13.486442] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000 
[   13.486455] monitor/mwait feature present. 
[   13.486460] using mwait in idle threads. 
[   13.486466] CPU: L1 I cache: 32K, L1 D cache: 32K 
[   13.486470] CPU: L2 cache: 2048K 
[   13.486474] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000 
[   13.486488] Compat vDSO mapped to ffffe000. 
[   13.486507] Checking 'hlt' instruction... OK. 
[   13.502358] SMP alternatives: switching to UP code 
[   13.502619] Freeing SMP alternatives: 11k freed 
[   13.503025] Early unpacking initramfs... done 
[   14.063922] ACPI: Core revision 20070126 
[   14.064016] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found. 
[   14.081708] CPU0: Intel Genuine Intel(R) CPU           U1300  @ 1.06GHz stepping 08 
[   14.081748] Total of 1 processors activated (2130.82 BogoMIPS). 
[   14.081964] ENABLING IO-APIC IRQs 
[   14.082202] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
[   14.225994] Brought up 1 CPUs 
[   14.226136] Booting paravirtualized kernel on bare hardware 
[   14.226236] Time: 11:20:43  Date: 10/27/107 
[   14.226263] NET: Registered protocol family 16 
[   14.226365] EISA bus registered 
[   14.226387] ACPI: bus type pci registered 
[   14.226550] PCI: PCI BIOS revision 2.10 entry at 0xfd823, last bus=7 
[   14.226554] PCI: Using configuration type 1 
[   14.226557] Setting up standard PCI resources 
[   14.232451] ACPI: EC: Look up EC in DSDT 
[   14.233230] ACPI: EC: GPE=0x17, ports=0x66, 0x62 
[   14.234572] ACPI: System BIOS is requesting _OSI(Linux) 
[   14.234576] ACPI: Please test with "acpi_osi=!Linux" 
[   14.234578] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email] 
[   14.234981] ACPI: Interpreter enabled 
[   14.234985] ACPI: (supports S0 S3 S4 S5) 
[   14.235010] ACPI: Using IOAPIC for interrupt routing 
[   14.242494] ACPI: EC: GPE=0x17, ports=0x66, 0x62 
[   14.242561] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[   14.242581] PCI: Probing PCI hardware (bus 00) 
[   14.243449] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO 
[   14.243455] PCI quirk: region 1180-11bf claimed by ICH6 GPIO 
[   14.244354] PCI: Firmware left 0000:06:08.0 e100 interrupts enabled, disabling 
[   14.244469] PCI: Transparent bridge - 0000:00:1e.0 
[   14.244608] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[   14.245060] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT] 
[   14.245274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT] 
[   14.249132] ACPI: PCI Interrupt Link [LNKA] (IRQs *10) 
[   14.249273] ACPI: PCI Interrupt Link [LNKB] (IRQs *10) 
[   14.249412] ACPI: PCI Interrupt Link [LNKC] (IRQs 10) *0, disabled. 
[   14.249551] ACPI: PCI Interrupt Link [LNKD] (IRQs *10) 
[   14.249688] ACPI: PCI Interrupt Link [LNKE] (IRQs *10) 
[   14.249825] ACPI: PCI Interrupt Link [LNKF] (IRQs *10) 
[   14.249997] ACPI: PCI Interrupt Link [LNKG] (IRQs *10) 
[   14.250139] ACPI: PCI Interrupt Link [LNKH] (IRQs *10) 
[   14.250283] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   14.250296] pnp: PnP ACPI init 
[   14.250306] ACPI: bus type pnp registered 
[   14.252937] pnp: PnP ACPI: found 10 devices 
[   14.252940] ACPI: ACPI bus type pnp unregistered 
[   14.252947] PnPBIOS: Disabled by ACPI PNP 
[   14.253006] PCI: Using ACPI for IRQ routing 
[   14.253010] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
[   14.292365] NET: Registered protocol family 8 
[   14.292369] NET: Registered protocol family 20 
[   14.292437] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved 
[   14.292443] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved 
[   14.292448] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved 
[   14.292454] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved 
[   14.293926] Time: tsc clocksource has been installed. 
[   14.322859] PCI: Bridge: 0000:00:1c.0 
[   14.322864]   IO window: 2000-2fff 
[   14.322873]   MEM window: d2000000-d3ffffff 
[   14.322880]   PREFETCH window: d0000000-d1ffffff 
[   14.322897] PCI: Bus 7, cardbus bridge: 0000:06:04.0 
[   14.322900]   IO window: 00003400-000034ff 
[   14.322907]   IO window: 00003800-000038ff 
[   14.322914]   PREFETCH window: 30000000-33ffffff 
[   14.322921]   MEM window: 34000000-37ffffff 
[   14.322928] PCI: Bridge: 0000:00:1e.0 
[   14.322932]   IO window: 3000-3fff 
[   14.322941]   MEM window: d4000000-d40fffff 
[   14.322948]   PREFETCH window: 30000000-33ffffff 
[   14.322986] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16 
[   14.322996] PCI: Setting latency timer of device 0000:00:1c.0 to 64 
[   14.323015] PCI: Setting latency timer of device 0000:00:1e.0 to 64 
[   14.323043] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 20 (level, low) -> IRQ 17 
[   14.323063] NET: Registered protocol family 2 
[   14.361939] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
[   14.361986] TCP established hash table entries: 16384 (order: 5, 196608 bytes) 
[   14.362210] TCP bind hash table entries: 16384 (order: 5, 131072 bytes) 
[   14.362364] TCP: Hash tables configured (established 16384 bind 16384) 
[   14.362368] TCP reno registered 
[   14.374052] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0 
[   14.916534]  it is 
[   15.485356] Freeing initrd memory: 7337k freed 
[   15.485523] Simple Boot Flag at 0x37 set to 0x1 
[   15.485980] audit: initializing netlink socket (disabled) 
[   15.485998] audit(1196162444.776:1): initialized 
[   15.488814] VFS: Disk quotas dquot_6.5.1 
[   15.488883] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[   15.489012] io scheduler noop registered 
[   15.489016] io scheduler anticipatory registered 
[   15.489019] io scheduler deadline registered 
[   15.489042] io scheduler cfq registered (default) 
[   15.489060] Boot video device is 0000:00:02.0 
[   15.489271] PCI: Setting latency timer of device 0000:00:1c.0 to 64 
[   15.489346] assign_interrupt_mode Found MSI capability 
[   15.489351] Allocate Port Service[0000:00:1c.0:pcie00] 
[   15.489416] Allocate Port Service[0000:00:1c.0:pcie02] 
[   15.489628] isapnp: Scanning for PnP cards... 
[   15.844402] isapnp: No Plug & Play device found 
[   15.877094] Real Time Clock Driver v1.12ac 
[   15.877274] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   15.878855] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   15.879159] input: Macintosh mouse button emulation as /class/input/input0 
[   15.879268] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[   15.882167] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   15.882175] serio: i8042 AUX port at 0x60,0x64 irq 12 
[   15.882404] mice: PS/2 mouse device common for all mice 
[   15.882557] EISA: Probing bus 0 at eisa.0 
[   15.882567] Cannot allocate resource for EISA slot 1 
[   15.882571] Cannot allocate resource for EISA slot 2 
[   15.882575] Cannot allocate resource for EISA slot 3 
[   15.882602] EISA: Detected 0 cards. 
[   15.882740] TCP cubic registered 
[   15.882759] NET: Registered protocol family 1 
[   15.882793] Using IPI No-Shortcut mode 
[   15.883009]   Magic number: 15:496:328 
[   15.883457] Freeing unused kernel memory: 364k freed 
[   15.921239] input: AT Translated Set 2 keyboard as /class/input/input1 
[   17.176484] AppArmor: AppArmor initialized<5>audit(1196162446.276:2):  type=1505 info="AppArmor initialized" pid=1218 
[   17.188304] fuse init (API version 7.8) 
[   17.195993] Failure registering capabilities with primary security module. 
[   17.211654] ACPI: CPU0 (power states: C1[C1] C2[C2]) 
[   17.211662] ACPI: Processor [CPU0] (supports 8 throttling states) 
[   17.211681] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126] 
[    3.696000] Marking TSC unstable due to: possible TSC halt in C2. 
[    3.696000] ACPI: Thermal Zone [ATF0] (59 C) 
[    3.696000] ACPI: Thermal Zone [DTS0] (60 C) 
[    3.700000] Time: acpi_pm clocksource has been installed. 
[    3.700000] ACPI: Thermal Zone [DTS1] (60 C) 
[    4.312000] usbcore: registered new interface driver usbfs 
[    4.312000] usbcore: registered new interface driver hub 
[    4.312000] usbcore: registered new device driver usb 
[    4.312000] USB Universal Host Controller Interface driver v3.0 
[    4.312000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 17 (level, low) -> IRQ 18 
[    4.312000] PCI: Setting latency timer of device 0000:00:1d.0 to 64 
[    4.312000] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[    4.312000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
[    4.312000] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001820 
[    4.312000] usb usb1: configuration #1 chosen from 1 choice 
[    4.312000] hub 1-0:1.0: USB hub found 
[    4.312000] hub 1-0:1.0: 2 ports detected 
[    4.416000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19 
[    4.416000] PCI: Setting latency timer of device 0000:00:1d.1 to 64 
[    4.416000] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[    4.416000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
[    4.416000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840 
[    4.416000] usb usb2: configuration #1 chosen from 1 choice 
[    4.416000] hub 2-0:1.0: USB hub found 
[    4.416000] hub 2-0:1.0: 2 ports detected 
[    4.504000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI 
[    4.504000] e100: Copyright(c) 1999-2006 Intel Corporation 
[    4.520000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 21 (level, low) -> IRQ 20 
[    4.520000] PCI: Setting latency timer of device 0000:00:1d.2 to 64 
[    4.520000] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[    4.520000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
[    4.520000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00001860 
[    4.520000] usb usb3: configuration #1 chosen from 1 choice 
[    4.520000] hub 3-0:1.0: USB hub found 
[    4.520000] hub 3-0:1.0: 2 ports detected 
[    4.548000] SCSI subsystem initialized 
[    4.556000] libata version 2.21 loaded. 
[    4.624000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 17 (level, low) -> IRQ 18 
[    4.624000] PCI: Setting latency timer of device 0000:00:1d.3 to 64 
[    4.624000] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
[    4.624000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4 
[    4.624000] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00001880 
[    4.624000] usb usb4: configuration #1 chosen from 1 choice 
[    4.624000] hub 4-0:1.0: USB hub found 
[    4.624000] hub 4-0:1.0: 2 ports detected 
[    4.728000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 21 
[    4.728000] PCI: Setting latency timer of device 0000:00:1d.7 to 64 
[    4.728000] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    4.728000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5 
[    4.728000] ehci_hcd 0000:00:1d.7: debug port 1 
[    4.728000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7 
[    4.728000] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xd4444000 
[    4.764000] usb 2-1: new low speed USB device using uhci_hcd and address 2 
[    4.764000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[    4.764000] usb usb5: configuration #1 chosen from 1 choice 
[    4.764000] hub 5-0:1.0: USB hub found 
[    4.764000] hub 5-0:1.0: 8 ports detected 
[    4.868000] ACPI: PCI Interrupt 0000:06:04.1[B] -> GSI 21 (level, low) -> IRQ 20 
[    4.916000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[d4006000-d40067ff]  Max Packet=[2048]  IR/IT contexts=[4/8] 
[    4.916000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 20 (level, low) -> IRQ 17 
[    4.968000] e100: eth0: e100_probe: addr 0xd4005000, irq 17, MAC addr 00:13:A9:3E:8F:0F 
[    4.976000] ata_piix 0000:00:1f.1: version 2.11 
[    4.976000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 22 (level, low) -> IRQ 22 
[    4.976000] PCI: Setting latency timer of device 0000:00:1f.1 to 64 
[    4.976000] scsi0 : ata_piix 
[    4.976000] scsi1 : ata_piix 
[    4.976000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14 
[    4.976000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15 
[    5.304000] ata1.00: ATA-6: TOSHIBA MK8007GAH, BG011A, max UDMA/100 
[    5.304000] ata1.00: 156301488 sectors, multi 16: LBA48 
[    5.304000] ata1.01: ATAPI: MATSHITAUJ-832D, 1.61, max UDMA/33 
[    5.308000] usb 2-1: new low speed USB device using uhci_hcd and address 3 
[    5.312000] ata1.00: configured for UDMA/100 
[    5.484000] usb 2-1: configuration #1 chosen from 1 choice 
[    5.484000] ata1.01: configured for UDMA/33 
[    5.484000] ata2: port disabled. ignoring. 
[    5.484000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8007GA BG01 PQ: 0 ANSI: 5 
[    5.488000] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-832D          1.61 PQ: 0 ANSI: 5 
[    5.504000] usbcore: registered new interface driver hiddev 
[    5.520000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB) 
[    5.520000] sd 0:0:0:0: [sda] Write Protect is off 
[    5.520000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    5.520000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    5.520000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB) 
[    5.520000] sd 0:0:0:0: [sda] Write Protect is off 
[    5.520000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    5.520000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    5.520000]  sda:<6>input: Logitech USB-PS/2 Optical Mouse as /class/input/input2 
[    5.528000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1 
[    5.528000] usbcore: registered new interface driver usbhid 
[    5.528000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver 
[    5.552000]  sda1 sda2 sda3 < sda5 sda6 sda7 sda8 > 
[    5.620000] sd 0:0:0:0: [sda] Attached SCSI disk 
[    5.628000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray 
[    5.628000] Uniform CD-ROM driver Revision: 3.20 
[    5.628000] sr 0:0:1:0: Attached scsi CD-ROM sr0 
[    5.640000] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    5.640000] sr 0:0:1:0: Attached scsi generic sg1 type 5 
[    6.140000] Attempting manual resume 
[    6.140000] swsusp: Resume From Partition 8:8 
[    6.140000] PM: Checking swsusp image. 
[    6.140000] PM: Resume from disk failed. 
[    6.188000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460302252756] 
[    6.192000] kjournald starting.  Commit interval 5 seconds 
[    6.192000] EXT3-fs: mounted filesystem with ordered data mode. 
[   15.668000] Linux agpgart interface v0.102 (c) Dave Jones 
[   15.688000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   15.924000] agpgart: Detected an Intel 945GM Chipset. 
[   15.924000] agpgart: Detected 7932K stolen memory. 
[   15.944000] agpgart: AGP aperture is 256M @ 0xc0000000 
[   15.948000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   16.124000] NET: Registered protocol family 17 
[   16.484000] intel_rng: FWH not detected 
[   16.540000] iTCO_vendor_support: vendor-support=0 
[   16.540000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007) 
[   16.540000] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware 
[   16.540000] iTCO_wdt: No card detected 
[   17.520000] ieee80211_crypt: registered algorithm 'NULL' 
[   17.520000] ieee80211: 802.11 data/management/control stack, git-1.1.13 
[   17.520000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com> 
[   17.572000] Yenta: CardBus bridge found at 0000:06:04.0 [104d:8207] 
[   17.572000] Yenta: Enabling burst memory read transactions 
[   17.572000] Yenta: Using CSCINT to route CSC interrupts to PCI 
[   17.572000] Yenta: Routing CardBus interrupts to PCI 
[   17.572000] Yenta TI: socket 0000:06:04.0, mfunc 0x01a21b22, devctl 0x64 
[   17.764000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1 
[   17.764000] ipw3945: Copyright(c) 2003-2006 Intel Corporation 
[   17.804000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17 
[   17.804000] Socket status: 30000006 
[   17.804000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a 
[   17.804000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff 
[   17.804000] cs: IO port probe 0x3000-0x3fff: clean. 
[   17.804000] pcmcia: parent PCI bridge Memory window: 0xd4000000 - 0xd40fffff 
[   17.804000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff 
[   17.820000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16 
[   17.820000] PCI: Setting latency timer of device 0000:02:00.0 to 64 
[   17.820000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection 
[   17.984000] input: PS/2 Mouse as /class/input/input3 
[   18.004000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4 
[   18.488000] ACPI: PCI Interrupt 0000:06:04.2[C] -> GSI 22 (level, low) -> IRQ 22 
[   18.488000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 19 
[   18.488000] PCI: Setting latency timer of device 0000:00:1b.0 to 64 
[   18.688000] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS... 
[   18.736000] cs: IO port probe 0x100-0x3af: clean. 
[   18.740000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7 
[   18.740000] cs: IO port probe 0x820-0x8ff: clean. 
[   18.740000] cs: IO port probe 0xc00-0xcf7: clean. 
[   18.744000] cs: IO port probe 0xa00-0xaff: clean. 
[   19.892000] lp: driver loaded but no devices found 
[   19.964000] usbserial: `' invalid for parameter `product' 
[   20.284000] ipw3945: Radio Frequency Kill Switch is On: 
[   20.284000] Kill switch must be turned off for wireless networking to work. 
[   20.284000] Adding 594364k swap on /dev/sda8.  Priority:-1 extents:1 across:594364k 
[   20.872000] EXT3 FS on sda6, internal journal 
[   36.832000] kjournald starting.  Commit interval 5 seconds 
[   36.832000] EXT3 FS on sda7, internal journal 
[   36.832000] EXT3-fs: mounted filesystem with ordered data mode. 
[   38.212000] PPP generic driver version 2.4.2 
[   38.296000] NET: Registered protocol family 10 
[   38.296000] lo: Disabled Privacy Extensions 
[   38.296000] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   40.444000] ACPI: AC Adapter [ACAD] (on-line) 
[   40.464000] No dock devices found. 
[   40.556000] ACPI: Battery Slot [BAT1] (battery absent) 
[   40.692000] input: Lid Switch as /class/input/input5 
[   40.696000] ACPI: Lid Switch [LID0] 
[   40.756000] input: Power Button (CM) as /class/input/input6 
[   40.760000] ACPI: Power Button (CM) [PWRB] 
[   42.380000] ppdev: user-space parallel port driver 
[   42.712000] audit(1196158885.983:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4865 profile="/usr/sbin/cupsd" 
[   42.904000] apm: BIOS not found. 
[   43.364000] sonypi: Sony Programmable I/O Controller Driver v1.26. 
[   43.368000] sonypi: please try the sony-laptop module instead and report failures, see also [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_drivers) 
[   43.368000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on 
[   43.368000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084 
[   43.368000] sonypi: device allocated minor is 63 
[   43.432000] input: Sony Vaio Jogdial as /class/input/input7 
[   43.496000] input: Sony Vaio Keys as /class/input/input8 
[   43.572000] sony-laptop: Sony Notebook Control Driver v0.5. 
[   43.604000] input: Sony Vaio Keys as /class/input/input9 
[   43.620000] input: Sony Vaio Jogdial as /class/input/input10 
[   44.036000] Failure registering capabilities with primary security module. 
[   44.500000] Bluetooth: Core ver 2.11 
[   44.500000] NET: Registered protocol family 31 
[   44.500000] Bluetooth: HCI device and connection manager initialized 
[   44.500000] Bluetooth: HCI socket layer initialized 
[   44.564000] Bluetooth: L2CAP ver 2.8 
[   44.564000] Bluetooth: L2CAP socket layer initialized 
[   44.636000] Bluetooth: RFCOMM socket layer initialized 
[   44.636000] Bluetooth: RFCOMM TTY layer initialized 
[   44.636000] Bluetooth: RFCOMM ver 1.8 
[   49.964000] [drm] Initialized drm 1.1.0 20060810 
[   49.996000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16 
[   49.996000] [drm] Initialized i915 1.6.0 20060119 on minor 0 
[  327.944000] usb 1-1: new full speed USB device using uhci_hcd and address 2 
[  328.108000] usb 1-1: configuration #1 chosen from 1 choice 
[  328.552000] usbcore: registered new interface driver libusual 
[  328.672000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
[  328.672000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
[  328.724000] Initializing USB Mass Storage driver... 
[  328.728000] scsi2 : SCSI emulation for USB Mass Storage devices 
[  328.732000] usb-storage: device found at 2 
[  328.732000] usb-storage: waiting for device to settle before scanning 
[  328.732000] usbcore: registered new interface driver usb-storage 
[  328.732000] USB Mass Storage support registered. 
[  333.732000] usb-storage: device scan complete 
[  333.736000] scsi 2:0:0:0: CD-ROM            Novatel  Mass Storage     1.00 PQ: 0 ANSI: 2 
[  333.744000] sr1: scsi3-mmc drive: 0x/0x caddy 
[  333.744000] sr 2:0:0:0: Attached scsi CD-ROM sr1 
[  333.744000] sr 2:0:0:0: Attached scsi generic sg2 type 5 
[  334.236000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  334.500000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  334.764000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  335.028000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  335.188000] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00 
[  335.188000] sr: Sense Key : No Sense [current] 
[  335.188000] sr: Add. Sense: No additional sense information 
[  335.308000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  335.572000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  335.836000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  336.100000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  336.456000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  336.720000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  336.984000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  337.248000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  338.080000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  338.344000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  338.608000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  338.872000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  339.032000] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00 
[  339.032000] sr: Sense Key : No Sense [current] 
[  339.032000] sr: Add. Sense: No additional sense information 
[  339.040000] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 28 00 00 00 00 10 00 
[  339.040000] sr: Sense Key : No Sense [current] 
[  339.040000] sr: Add. Sense: No additional sense information 
[  339.048000] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 20 00 00 00 00 18 00 
[  339.048000] sr: Sense Key : No Sense [current] 
[  339.048000] sr: Add. Sense: No additional sense information 
[  339.180000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  339.444000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  339.728000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  339.992000] usb 1-1: reset full speed USB device using uhci_hcd and address 2 
[  340.152000] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00 
[  340.152000] sr: Sense Key : No Sense [current] 
[  340.152000] sr: Add. Sense: No additional sense information 
[  340.300000] UDF-fs: Partition marked readonly; forcing readonly mount 
[  340.316000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Movistar', timestamp 2007/08/08 09:52 (103c) 
[  374.816000] usb 1-1: USB disconnect, address 2 
[  374.916000] scsi 2:0:0:0: rejecting I/O to dead device 
[  374.916000] scsi 2:0:0:0: rejecting I/O to dead device 
[  376.316000] usb 1-1: new full speed USB device using uhci_hcd and address 3 
[  376.484000] usb 1-1: configuration #1 chosen from 1 choice 


Then

arturo@mivaio:~$ sudo modprobe -r usbserial 
[sudo] password for arturo: 
arturo@mivaio:~$ sudo modprobe usbserial vendor=0x410 product=0x4400 
FATAL: Error inserting usbserial (/lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument 

Gnomeppp is started

/home/arturo/.wvdial.conf<Warn>: Ignoring malformed input line: ";Do NOT edit this file by hand!" 
WvDial<*1>: WvDial: Internet dialer version 1.56 
WvDial<Err>: Cannot open /dev/ttyS0: Input/output error 
WvDial<Err>: Cannot open /dev/ttyS0: Input/output error 
WvDial<Err>: Cannot open /dev/ttyS0: Input/output error

And that's it
I've tried every single choice for 
/dev/* (/dev/ttyS0, /dev/ttyS1, ...)

---

### Post by scorp123 on 2007-11-27
> **adm1968 said:**
>  arturo@mivaio:~$ sudo modprobe usbserial vendor=_[COLOR="Red"]0x4[/COLOR]_10 product=0x4400  There still is a typo (marked red). It should be [COLOR="Red"]**0x1410**[/COLOR] .... but OK, maybe you just mistyped that here? Other than that I am really running out of ideas, all your messages are identical to what I get on my system and here the Novatel MC950D pretty much "just works".

EDIT: Also, you do get the virtual CD-ROM with the drivers when you plugin the modem? You have to unmount it first ("sudo umount /dev/scd1" ....) before you can use the "sudo modprobe usbserial vendor=0x1410 vendor=0x4400" command. Again ... just to be sure you did that. I am really out of ideas here. Sorry about that.

---

### Post by adm1968 on 2007-11-27
> **scorp123 said:**
> There still is a typo (marked red). It should be [COLOR="Red"]**0x1410**[/COLOR] .... but OK, maybe **you just mistyped that here?** Other than that I am really running out of ideas, all your messages are identical to what I get on my system and here the Novatel MC950D pretty much "just works".

[COLOR="Navy"]Yeah, I mistyped it just this time[/COLOR]

EDIT: Also, you do get the virtual CD-ROM with the drivers when you plugin the modem? **You have to unmount it first **("sudo umount /dev/scd1" ....) before you can use the "sudo modprobe usbserial vendor=0x1410 vendor=0x4400" command. Again ... just to be sure you did that. I am really out of ideas here. Sorry about that.

[COLOR="Navy"]Why do you think I should unmount the virtual CD-ROM first?
Ubuntu does it by itself without asking (read my message above on that)  ...

Thanks a million, anyway, for being so supportive[/COLOR]



**

---

### Post by scorp123 on 2007-11-27
> **adm1968 said:**
> Why do you think I should unmount the virtual CD-ROM first?  Because the USB device will be in the wrong mode then. The system sees it as a "CD-ROM" device and not as a "USB Serial" device. And on my laptop it doesn't automatically unmount anything. On both Feisty and now Gutsy: I put the modem in and the virtual CD drive shows up and stays ... it doesn't go away automatically. I have to close the Nautilus folder that opened and then I have to get rid of the drive icon on my desktop by issueing the unmount command. Only then the "modprobe usbserial" command will work ... in my case.

Could you boot in Live CD mode and try it out there? Just to be sure that you don't have any config changes in your personal settings that cause all the troubles you have had ...

---

### Post by adm1968 on 2007-11-27
I see ...
Will check tomorrow with the Live CD

Good night!

---

### Post by adm1968 on 2007-11-28
OK
I restarted with the Live CD

As before, the virtual CD gets mounted AND unmounted without me doing anything
However, _there is no error_ when the final command is inserted

sudo modprobe usbserial vendor= ...

What do those 2 things make you think the problem is with my Ubuntu HDD installation?


I also did this:
Downloaded gnome-ppp and 'installed' with Live CD
Issued command

ubuntu@ubuntu:~$ gnome-ppp 
WVCONF: /home/ubuntu/.wvdial.conf 
GNOME PPP: Conectando... 
GNOME PPP: STDERR: /home/ubuntu/.wvdial.conf<Warn>: Ignoring malformed input line: ";Do NOT edit this file by hand!" 
GNOME PPP: STDERR: WvDial<*1>: WvDial: Internet dialer version 1.56 
GNOME PPP: STDERR: WvModem<*1>: Cannot get information for serial port. 
GNOME PPP: STDERR: WvDial<*1>: Initializing modem. 
GNOME PPP: STDERR: WvDial<*1>: Sending: ATX3 
GNOME PPP: STDERR: WvDial Modem<*1>: ATX3 
GNOME PPP: STDERR: WvDial Modem<*1>: OK 
GNOME PPP: STDERR: WvDial<*1>: Sending: ATZ 
GNOME PPP: STDERR: WvDial Modem<*1>: ATZ 
GNOME PPP: STDERR: WvDial Modem<*1>: OK 
GNOME PPP: STDERR: WvDial<*1>: Modem initialized. 
GNOME PPP: STDERR: WvDial<*1>: Sending: ATM1L3DT*99***1# 
GNOME PPP: STDERR: WvDial<*1>: Waiting for carrier. 
GNOME PPP: STDERR: WvDial Modem<*1>: ATM1L3DT*99***1# 
GNOME PPP: STDERR: WvDial Modem<*1>: CONNECT HSDPA 7.2 
GNOME PPP: STDERR: WvDial<*1>: Carrier detected.  Waiting for prompt. 
GNOME PPP: STDERR: WvDial<Err>: Connected, but carrier signal lost!  Retrying... 
GNOME PPP: STDERR: WvDial<*1>: Sending: ATM1L3DT*99***1# 
GNOME PPP: STDERR: WvDial<*1>: Waiting for carrier. 
GNOME PPP: STDERR: WvDial<Warn>: Timed out while dialing.  Trying again. 
GNOME PPP: STDERR: WvDial<Warn>: Maximum Attempts Exceeded..Aborting!! 
GNOME PPP: STDERR: WvDial<*1>: Disconnecting at Wed Nov 28 20:56:45 2007 

Never got this far with my installed Ubuntu, but no connection seems to be possible with the Live CD

????

---

### Post by adm1968 on 2007-12-04
Are you still around, Scorp?
:)

---

### Post by scorp123 on 2007-12-04
> **adm1968 said:**
>   Never got this far with my installed Ubuntu, but no connection seems to be possible with the Live CD  So if you get farther with the Live CD than with your installed system then I'd say it's safe to say that your installed system was altered / misconfigured somehow so your Novatel USB modem won't work there.

---

### Post by Swab on 2007-12-04
> WvDial<Err>: Cannot open /dev/ttyS0: Input/output error
WvDial<Err>: Cannot open /dev/ttyS0: Input/output error
WvDial<Err>: Cannot open /dev/ttyS0: Input/output error

Excuse me for interrupting, but is this not the wrong device?  Shouldn't it be trying to use ttyUSB0 ?   Feel free to ignore me if I am talking rubbish, I can't get my E220 to work either! :)

---

### Post by adm1968 on 2007-12-07
> **scorp123 said:**
> So if you get farther with the Live CD than with your installed system then I'd say it's safe to say that your installed system was altered / misconfigured somehow so your Novatel USB modem won't work there.

I haven't configured my installation in any different way than the one I got using the Live CD, that's why I feel a bit lost

> **Swab said:**
> Excuse me for interrupting, but is this not the wrong device?  Shouldn't it be trying to use ttyUSB0 ?   Feel free to ignore me if I am talking rubbish, I can't get my E220 to work either! :)

The Live CD does use ttyUSB0, the HDD installation doesn't
No idea why ...

---

### Post by Swab on 2007-12-08
> **adm1968 said:**
> 
The Live CD does use ttyUSB0, the HDD installation doesn't
No idea why ...

Is that not the problem then?  Isn't ttyS0 a serial port?

---

### Post by Dooley on 2007-12-08
Hey just wondering if anyone has managed to share their 3g connection via wifi.
It would be really handy if possible.

Cheers

---

### Post by mips on 2007-12-08
> **Dooley said:**
> Hey just wondering if anyone has managed to share their 3g connection via wifi.
It would be really handy if possible.

Cheers

Anything is possible, it's just a question of HOW. If I had a 3G adapter I would be more than willing to get something like this tested.

---

### Post by scorp123 on 2007-12-09
> **Swab said:**
>  Isn't ttyS0 a serial port? "ttyS*" devices are classic serial devices in Linux speak, e.g. anything that connects to plain old RS-232 connectors (e.g. plain old external analogue dial-up modems). Serial-over-USB devices should receive a device name something like "ttyUSB*" .... or "ttyACM*" in case of some mobile phones.

---

### Post by scorp123 on 2007-12-09
> **Dooley said:**
> Hey just wondering if anyone has managed to share their 3g connection via wifi. Turn your laptop into an access point, e.g. via "hostap" package, and then enable routing and TCP/IP forwarding. That's about it. WLAN clients will see your laptop as access point, connect to it, and the routing and TCP/IP packet forwarding will make sure that traffic from those clients will get through to the Internet and vice versa.

This might work for maybe 3-4 clients in case you have a HSDPA or HSUPA connection, other than that it might get very very slow.

---

### Post by Dooley on 2007-12-09
> **scorp123 said:**
> Turn your laptop into an access point, e.g. via "hostap" package, and then enable routing and TCP/IP forwarding. That's about it. WLAN clients will see your laptop as access point, connect to it, and the routing and TCP/IP packet forwarding will make sure that traffic from those clients will get through to the Internet and vice versa.

This might work for maybe 3-4 clients in case you have a HSDPA or HSUPA connection, other than that it might get very very slow.

Cheers, ill give it a go and see if it works.

---

### Post by scorp123 on 2007-12-09
> **Dooley said:**
> Cheers, ill give it a go and see if it works. Seems the name changed slightly ... the needed package is now called "hostapd". You can find and install it via Synaptic. As how it works .... I personally don't know it that well, but there is a web page explaining all the details:
[http://hostap.epitest.fi/hostapd/](http://hostap.epitest.fi/hostapd/)

If I interpret the info correctly, only a few selected WiFi chipsets are supported??

Should that be the case you could still create a so called "ad Hoc" WLAN network (where computers connect to each other in a peer-to-peer fashion), that should work too.

---

### Post by mips on 2007-12-09
> **scorp123 said:**
> 
If I interpret the info correctly, only a few selected WiFi chipsets are supported??


Yes, Prism chipset based cards only.

---

### Post by Dooley on 2007-12-09
Yep sadly I don't have a prism based wireless card. 

I tried to use firestarter and all went well on the modem side but it doesn't like my wireless card, says it isn't up. 

Its a common problem apparently.

scorp123, do you happen to know a decent guide for ad-hoc off hand?

---

### Post by mips on 2007-12-09
> **Dooley said:**
> 
scorp123, do you happen to know a decent guide for ad-hoc off hand?

I'm installing Kubuntu 7.10 amd64 on my desktop tomorrow which has a RT2500 chipset wireless card. I do not have an AP but I'm going to attempt to get my laptop to gain internet from my desktop via wireless with MAC filtering & OpenVPN for security.

I dunno how long it will take but I could probably help if you are willing to wait a bit. This will be for adsl & not 3g though.

---

### Post by Dooley on 2007-12-09
> **mips said:**
> I'm installing Kubuntu 7.10 amd64 on my desktop tomorrow which has a RT2500 chipset wireless card. I do not have an AP but I'm going to attempt to get my laptop to gain internet from my desktop via wireless with MAC filtering & OpenVPN for security.

I dunno how long it will take but I could probably help if you are willing to wait a bit. This will be for adsl & not 3g though.

Yeah that would be great. I'm going off on hols for a week 2moro. :D

---

### Post by scorp123 on 2007-12-09
> **Dooley said:**
>  scorp123, do you happen to know a decent guide for ad-hoc off hand?  [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

---

### Post by adm1968 on 2007-12-10
Well, it seems to me I have to give up on this one, at least for the time being ...
Thanks a lot for your help, _Scorp_ :)

---

### Post by jczorglub on 2008-05-11
> **scorp123 said:**
> 
I insert the stick, the virtual CD-ROM part with the Windoze drivers shows up and then I execute (with "sudo") this script below (I have it as icon in my panel): ```
#! /bin/bash
sudo modprobe -r usbserial
sudo eject /dev/scd1
sudo modprobe usbserial vendor=0x1410 product=0x4400 
```

Once you did above steps the modem works tip top as a PPP modem. I use wvdial for my purposes. My **/etc/wvdial.conf** for the Swiss provider SUNRISE looks like this: ```
[Dialer Sunrise]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0&C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = USB Modem
Phone = *99#
Username = ''
Password = ''
Carrier Check = no
Stupid Mode = yes  
``` Chances are that above config file will work pretty much with any provider as all the options up there are pretty much generic and not provider-dependant. So now, when I want to connect via the modem, I have another script ready that executes this command for me: **sudo wvdial Sunrise**  ... and voila, I am connected with the Internet.

**_Something I forgot to add:_**

In my case I had to get a new SIM card. So originally you'd insert the SIM card into the modem, insert the stick into a running Windoze system and then use the special software the modem comes with to activate the SIM card. In one of those forums about the Huawei modem (see my links up there) I read that you can just as well use your mobile phone to activate the SIM card. That's precisely how I did it. I first inserted my shiny new SIM into a mobile phone and went through the activation procedures of my provider (they sent me three or so SMS with infos I needed wo write down and confirm ... totally easy!). After that I deactivated the PIN dialogue via the phone's setup so I don't have to write special scripts that would send the PIN code every time I insert the modem into my Linux system (it can be done by sending modem commands such as **AT+CPIN="1234"** ... But I didn't want to bother with this). So after the SIM is activated I inserted it into the modem and everything was good to go.

Hope this helped? :)

Hello !

I tried to follow this "recipe" to use my own Novatel Ovation, also a Swiss Sunrise one.
Unfortunately, the USB key did not mount automatically, and is not visible with sudo fdisk -l 
I am using the new Hardy Ubuntu version... maybe the cause of the problem, because I tried to configure some weeks ago with Gutsy, unsuccessfully, not with your "recipe", but at that time I was able to see the mounted key (/media/NVTL_AICD).

Do anybody have an idea ?
Thanks in advance for help !

JCZ

---

### Post by scorp123 on 2008-05-11
> **jczorglub said:**
>   Unfortunately, the USB key did not mount automatically, and is not visible with sudo fdisk -l Hmmm... 

OK, let's try a few things. Unplug the modem if its plugged in and shutdown your PC. Just to make sure that all hardware has been properly reset. Then power it on again and let it boot. Once it has booted please login and open a terminal. Prepare to execute this command: ```
dmesg
``` ... What I mean here is that you type "dmesg" into the terminal but you DO NOT press the "Enter" key yet. Instead you will plugin your modem into your PC, wait 1-2 seconds until it starts blinking (mine does that: It starts blinking red as soon as I insert it into an USB port) and *NOW* press enter in that terminal window ...  There probably will be many messages flying over your screen. What's important here are the last few lines: they should mention finding a new USB device! Can you copy and paste those lines here please? You could execute "dmesg" multiple times, just to see if new messages are being generated after a few seconds.

After that: Can you please do this command and copy & paste the result here? ```
sudo lsusb
``` ... That should show what USB devices are seen by your PC. Please copy & paste the entire output here.

---

### Post by jczorglub on 2008-05-12
Hello scorp123 !

Thanks for the info.
I was able to see that the key was present with dmesg, even if it didn't anymore mount automatically.
No problem.
I was also able to use wvdial to connect to the provider, which seemed to be ok.
I use a slightly different wvdial.conf :
```
[Dialer Defaults]
New PPPD = yes
Modem = /dev/ttyUSB0
Password = ''
Username = ''
Dial command = ATDT
Stupid Mode = yes

[Dialer reset]
Init1 = AT

[Dialer Pin]
Init2 = ATZ
Init3 = AT+CPIN="7614"
Init4 = ATZ
Stupid Mode = yes
Modem Type = USB Modem
ISDN = 0
Carrier Check = no
Baud = 460800

[Dialer Sunrise]
Init5 = ATZ
Init6 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = yes
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
Carrier Check = yes
Carrier = Sunrise
Baud = 460800
Init7 = AT+CGDCONT=1,"IP","internet";

```
I use a carrier check because I live in the border area... and some foreign ISP have strong emitters forcing sometimes an unwanted roaming (at a prohibitive cost!)
For the first connection I must start with
```
sudo wvdial Pin
```
to unlock the sim card, and then
```
sudo wvdial Sunrise
```

The problem I am now investigating is that it seems always to be correctly connected, local IP and DNS automatically set, but the use of the network not always works.
I have to make some deeper tests, but it seems to work only if I connect before to a network (LAN or Wifi), then disconnect, then connect via the Novatel USB key ! I use wicd to connect, network-manager is not suitable for my configuration.

Any idea for a suitable diagnostic tool ?

Sorry for the silly questions, but I am quite new to Ubuntu.

---

### Post by scorp123 on 2008-05-12
> **jczorglub said:**
>  The problem I am now investigating is that it seems always to be correctly connected, local IP and DNS automatically set, but the use of the network not always works. That's because your system is trying to be nice to you and tries to use the fastest network first :)  I have the same problem. What I do is that I unplug any Ethernet cables from my Ethernet interface and then disable WiFi networking by right-clicking on my Network-Manager icon and then unticking the "Enable Wireless" option. This will make sure that any TCP/IP package now *must* go out via my PPP-dialup connection. 

Works tip top for me. E.g. when I know I have to use my Novatel modem I untick my WiFi networking, and while Network-Manager is shutting down my WLAN I can grab my Novatel modem from my laptop bag, and when I plug it into my laptop everything is already "ready to go" and I just need to wait until it starts blinking ... And as soon as the virtual CD-ROM drive shows up I click on my "Sunrise" icon (which executes "wvdial" in the background) and voila, I'm in. Easier even than in Windows, IMHO. :)

> **jczorglub said:**
>  I have to make some deeper tests, but it seems to work only if I connect before to a network (LAN or Wifi), then disconnect, then connect via the Novatel USB key ! I use wicd to connect, network-manager is not suitable for my configuration.  Try my method above. I never used WiCD but I imagine it too offers an option to shutdown WiFi networking via a right-click menu similar to Network-Manager? I am sure that the problems will go instantly away if you disable your 'normal' network interfaces and then do your dial-up. 

What you can do to analyse the problem: Check your routing! 

Example: This is my laptop using an Ethernet connection:
```
~ > route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
[COLOR="Red"]**0.0.0.0**[/COLOR]         192.168.1.1     0.0.0.0         UG    0      0        0 [COLOR="Red"]**eth0**[/COLOR]
``` See what I mean? The **default gateway** (**= 0.0.0.0** in TCP/IP terms) is pointing to my Ethernet interface "eth0".

And now let's unplug my Ethernet and let's repeat the command:```

~ > route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
[COLOR="Red"]**0.0.0.0**[/COLOR]         192.168.1.1     0.0.0.0         UG    0      0        0 [COLOR="Red"]**ath0**[/COLOR]
``` Oooops. Network-Manager just got active and has changed my routing to the fastest working network interface: My WLAN on interface "ath0" (this is an Atheros chip so the devices are named "ath*" ... others might get another "eth-" something interface here, e.g. "eth1" or "eth2")

Now let's see what happens if I activate my Novatel modem but I DO NOT de-activate my WiFi first:
```
~ > route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[COLOR="DarkOrchid"]**10.64.64.64**[/COLOR]     **[COLOR="Red"]0.0.0.0[/COLOR]**         255.255.255.255 UH    0      0        0 [COLOR="DarkOrchid"]**ppp0**[/COLOR]
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
[COLOR="Red"]**0.0.0.0**[/COLOR]         192.168.1.1     0.0.0.0         UG    0      0        0 [COLOR="Red"]**ath0**[/COLOR]
```

See what happened? Yes, I get a PPP connection to Sunrise, but because "ppp0" is not the fastest connection, Network-Manager has decided that the default-gateway for all traffic should still be my WLAN interface "ath0". I am pretty sure that this is what you experience.

Now, same experiment again. But this time I tell Network-Manager to shutdown my WiFi interface first. Result before using the modem:
```
~ > route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
``` Bingo! With WiFi being shutdown and Ethernet being unplugged, there is no network left. No network == No routing. The packets have nowhere to go.

Let's turn on the Novatel modem:
```
~ > route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
[COLOR="Red"]**0.0.0.0**[/COLOR]         0.0.0.0         0.0.0.0         U     0      0        0 [COLOR="Red"]**ppp0**[/COLOR]
``` Voila! With "ppp0" being the 'fastest' and only network interface left, the default-gateway is now pointing to the PPP connection and now all communication is done correctly via the modem.

I am sure that this is the effect you are experiencing and that it will likely go away if you manually disable your other network interfaces before using the modem. :)

Hope this helped? ;)
.
.
.
.

---

### Post by jczorglub on 2008-05-13
Waouh !

Thanks for the explanations.
Its exactly what I am doing now. The only difference is that I must first start the wicd, disconnect, and then plugin the Novatel.
But it's not important... because it works !
Also thanks for your time !

Best regards.

---

### Post by scorp123 on 2008-05-13
You're welcome ;)

---

### Post by lpd2000 on 2008-05-25
Hi everybody. When I'm trying to dial by using pppd or wvdial i got the same message "failed to  open /dev/ttyUSB0 No such file or directory" . 
Please help to figure out. It's 8.04.

The output of the lsusb is here:

root@paull:/etc/ppp/peers# lsusb
Bus 005 Device 003: ID 05ac:8501 Apple Computer, Inc. Built-in iSight [Micron]
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 05ac:1000 Apple Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 05ac:8240 Apple Computer, Inc. IR Receiver [build-in]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 008: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 05ac:021a Apple Computer, Inc. 
Bus 001 Device 001: ID 0000:0000  
root@paull:/etc/ppp/peers# ls -ls /dev/ttyU*
0 crw-rw---- 1 root dialout 188, 0 2008-05-25 10:27 /dev/ttyUSB0
0 crw-rw---- 1 root dialout 188, 1 2008-05-25 10:27 /dev/ttyUSB1
0 crw-rw---- 1 root dialout 188, 2 2008-05-25 10:27 /dev/ttyUSB2
0 crw-r--r-- 1 root root    188, 0 2008-05-24 17:49 /dev/ttyUSBo

---

### Post by scorp123 on 2008-05-25
> **lpd2000 said:**
>  Hi everybody. When I'm trying to dial by using pppd or wvdial i got the same message "failed to  open /dev/ttyUSB0 No such file or directory" .  Follow my advice in posting #55
[http://ubuntuforums.org/showpost.php?p=4935187&postcount=55](http://ubuntuforums.org/showpost.php?p=4935187&postcount=55)

Let's see what your system reports when you plugin the modem after a cold restart.

> **lpd2000 said:**
>  Bus 002 Device 008: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem  So far so good.

---

### Post by sbutton on 2008-06-06
> **scorp123 said:**
> Follow my advice ...
 So far so good.

Holy Moly, this has been going on quite some time. I was thinking of getting a "three" USB Wireless Broadband model (REALLY stupid name, everyone seems to think it's wireless 802.11 router attached to broadband).

I *was* hoping I could use this with my Eee and my Sony laptop (Win/Lin) when working away from home , and part of my "working away" project was to move everything away from the Win side on my laptop. (in the evenings)

Sheesh, this looks like a major sticking point after extensive googling around there's not a lot of people using these gizmos with Linux. 

I'll take this as a personal challenge though, and post back with the results.

Looks like the OP has dropped off the face of the earth... probably starved to death 'cos he couldn't face booting onto Win to order pizza. 

Steve

---

### Post by scorp123 on 2008-06-06
> **sbutton said:**
>  after extensive googling around there's not a lot of people using these gizmos with Linux. You're just hanging out with the wrong people then ;)

I hardly know any serious IT technician or IT consultant not having one of those gizmos + Linux.

Here in Switzerland the two providers Swisscom and Sunrise have pushed the idea of "Internet anywhere, anytime" so much that now nearly everyone has a Huawei E220 or the newer Novatel MC950D here.

And the reason why I got a Novatel MC950D is that the Huawei E220's were sold out :)

---

### Post by daithi81 on 2008-06-15
Hey guys, I'm trying to use a E170 for O2 Broadband for Ubuntu. I totally new to Linux so any help would be greatly appreciated!

:)

---

### Post by scorp123 on 2008-06-15
> **daithi81 said:**
> Hey guys, I'm trying to use a E170 for O2 Broadband for Ubuntu.  O2 ... Germany?

Please read posting #55 here and post the results you get:
[http://ubuntuforums.org/showpost.php?p=4935187&postcount=55](http://ubuntuforums.org/showpost.php?p=4935187&postcount=55)

---

