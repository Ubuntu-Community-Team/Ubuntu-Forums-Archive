---
title: "Huawei E220 Troubles"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by Green_biri on 2008-06-09
Hi all. I've tried to install the Huawei E220 Modem in Ubuntu 8.04.

Here's my wvdial configuration:

```
[Dialer kanguru]
Phone = *99***1#
Username = myconnection
Password = 8564
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Band = 460800
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FClass=0
Init3 = ATZ
ISDN = 0
Modem Type = Analog Modem
```

When I type "wvdial kanguru", here's the output error that I receive:

```
pedroguerra@LaptopGuerra:~$ wvdial kanguru
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

```

If I change the Modem to /dev/ttyUSB1, it gives me this error:

```
pedroguerra@LaptopGuerra:~$ wvdial kanguru
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB1: Exec format error
--> Cannot open /dev/ttyUSB1: Exec format error
--> Cannot open /dev/ttyUSB1: Exec format error

```

What's the problem? Thank you in advance...

---

### Post by Green_biri on 2008-06-11
Bump... this is urgent guys. :(

---

### Post by redbook4574 on 2008-06-11
try this wvdial.conf

# wvdial for Vodacom Data. Created by Tazz_tux
# Version 1.0

# Change Log:
#
# Added support for HSDPA.
# Added Headers and version control.

[Dialer Defaults]
Phone = *99#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem




Then run sudo modprobe -r airprime.

Then run wvdial hsdpa.

If this works add these lines to your blacklist
# remove e220-conflicting airprime
blacklist airprime

---

### Post by Green_biri on 2008-06-12
> **redbook4574 said:**
> try this wvdial.conf

# wvdial for Vodacom Data. Created by Tazz_tux
# Version 1.0

# Change Log:
#
# Added support for HSDPA.
# Added Headers and version control.

[Dialer Defaults]
Phone = *99#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem




Then run sudo modprobe -r airprime.

Then run wvdial hsdpa.

If this works add these lines to your blacklist
# remove e220-conflicting airprime
blacklist airprime

Thanks for your answer, but it gives me the same error:

```
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
```

---

### Post by Green_biri on 2008-06-12
Bump... :(

---

### Post by redbook4574 on 2008-06-13
Sorry meant to say I get the same errors but after kppp setup although wvdial gives me errors kppp connects perfectly - don't know why but it does.

---

### Post by Sealbhach on 2008-06-13
Hi,

I have an E220 which connects for me when I use the Gnome-PPP dial-up interface. It's a nice little GUI to get you dialed up.

My ISP is three.co.uk and all the config information is already in the modem so all I have to do is connect it using gnome.




> Install Gnome-PPP

```
sudo-apt-get install gnome-ppp
``` 

Or download the DEB file and bring it into your system with a USB drive.

You'll find it in the Applications/Internet Menu.

Click Setup:

Modem Tab:

Device: /dev/ttyUSB0
Type: Analog Modem
Speed: 460800
Phone Line: Tone
Volume: High
NB: Uncheck "Wait for Dialtone" (if checked)

Networking Tab:

Dynamic IP Address
DNS: Automatic DNS

Options Tab:

Check all Connection Options except "Send Custom Reply".

When you connect the modem to the USB, wait till the green light stops flashing, then in terminal type:


Code:
```
sudo wvdialconf
```


This will find your modem.
You may find on start-up that Gnome-PPP cannot detect modem. When this happens I just reboot and it finds it.

Also try:

[HTML]modprobe usbserial vendor=0x12d1 product=0x1003[/HTML]


Let me know if this works.


Also, here's my post showing things I did when I finally got it connected... Your settings may be different, e.g. the phone number and DNS addresses.

[http://ubuntuforums.org/showpost.php?p=4817997&postcount=8](http://ubuntuforums.org/showpost.php?p=4817997&postcount=8)


.

---

### Post by Green_biri on 2008-06-13
> **Sealbhach said:**
> Hi,

I have an E220 which connects for me when I use the Gnome-PPP dial-up interface. It's a nice little GUI to get you dialed up.

My ISP is three.co.uk and all the config information is already in the modem so all I have to do is connect it using gnome.

Also, here's my post showing things I did when I finally got it connected... Your settings may be different, e.g. the phone number and DNS addresses.

[http://ubuntuforums.org/showpost.php?p=4817997&postcount=8](http://ubuntuforums.org/showpost.php?p=4817997&postcount=8)
.

Thanks for your answer. The "modprobe usbserial" doesn't give me any output, but the "sudo wvdialconf" does:

```
pedroguerra@LaptopGuerra:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   USB0 
ttyUSB1<Info>: Exec format error
Modem Port Scan<*1>: USB1 
ttyUSB2<Info>: Exec format error
Modem Port Scan<*1>: USB2 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
pedroguerra@LaptopGuerra:~$ modprobe usbserial vendor=0x12d1 product=0x1003
pedroguerra@LaptopGuerra:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   USB0 
ttyUSB1<Info>: Exec format error
Modem Port Scan<*1>: USB1 
ttyUSB2<Info>: Exec format error
Modem Port Scan<*1>: USB2 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

```

Thanks for your answer anyway, I'm getting closer. :)

More help please? :)

---

### Post by Sealbhach on 2008-06-13
Just post the output of 

```
lsusb
```

It should show up in that.

By the way, have you installed Gnome-PPP?

That works with an E220 for me!

.

---

### Post by Green_biri on 2008-06-13
> **Sealbhach said:**
> Just post the output of 

```
lsusb
```

It should show up in that.

By the way, have you installed Gnome-PPP?

That works with an E220 for me!

.

Thanks for your answer, and yes, I've got it installed...

Here's the output...

```
pedroguerra@LaptopGuerra:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 1532:0007  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

---

### Post by Sealbhach on 2008-06-13
Thanks. You have the same modem as me - so it definitely works.

Who is your ISP? 

In order to connect to your ISP using Gnome-PPP you will need to find out the phone number your modem dials (for me the number is *99#).

I'm just copying here a guide someone gave me when I first tried to get my modem connected. I did all these things and then used Gnome-PPP to connect. I'm not an expert in any of this but just trying to pass on to you how it worked for me.

REMEMBER: You need to find out the phone number your ISP uses. You could find this out by looking at the Dialup.ini file in the folder Program Files/Huawei UMTS Data Card if you have already installed the modem software in Windows.

> 
Here are the steps. There is a lot to remember so I suggest saving it to a memory stick in windows and then when you load up in ubuntu you can copy and paste. Alternatively print it out... if anything is unclear post a message up here asking.



1. Open a terminal window. This can be done by clicking Applications in the top left, then accessories and finally terminal



2 In the terminal window, type sudo gedit /etc/resolv.conf Put in your password when it asks. This will open a window like notepad. In this window you should type



nameserver 172.30.140.69

nameserver 172.31.140.69



3. Click save and close the window.



4. In a terminal window (either the one you already opened or a new one) type sudo gedit /etc/ppp/peers/provider (Again put in your password) In this window you should replace the text you see with..... 



user "user"



connect "/usr/sbin/chat -v -f /etc/chatscripts/pap -T *99#"



# Serial device to which the modem is connected.

/dev/ttyUSB0



# Speed of the serial line.

460800



# Assumes that your IP address is allocated dynamically by the ISP.

noipdefault

# Try to get the name server addresses from the ISP.

#usepeerdns

# Use this connection as the default route.

defaultroute



# Makes pppd "dial again" when the connection is lost.

persist



# Do not ask the remote to authenticate.

noauth






5. In a terminal window type sudo gedit /etc/chatscripts/pap ( again it will ask for password) and replace any text with....



ABORT BUSY

ABORT VOICE

ABORT "NO CARRIER"

ABORT "NO DIALTONE"

ABORT "NO DIAL TONE"

"" ATZ

OK ATE0V1&D2&C1S0=0+IFC=2,2

OK AT+CGDCONT=1,"IP","3ireland.ie"

OK ATDT*99#

CONNECT ""



6. Attach your modem. In a terminal window type modprobe usbserial vendor=0x12d1 product=0x1003

---

### Post by Green_biri on 2008-06-16
Output for "modprobe usbserial vendor=0x12d1 product=0x1003":

```
WARNING: /etc/modprobe.d/blacklist line 40: ignoring bad line starting with '&#8216;blacklist'
```

And if I try wvdial, it gives me the same stupid error... it's always the same error!

```
pedroguerra@LaptopGuerra:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

```

By the way: my ISP is Kanguru, from the "Optimus" company.

Link: [http://www.kanguru.pt/]("http://www.kanguru.pt/")

---

### Post by chmac on 2008-06-17
There's an app called USB_ModeSwitch which might help with the Huawei E220 and E169. You can see a detailed walkthrough for the EEE here:
[http://dalelane.co.uk/blog/?p=254](http://dalelane.co.uk/blog/?p=254)
Then the USB_ModeSwitch site itself (I think) is here:
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by Green_biri on 2008-06-17
> **chmac said:**
> There's an app called USB_ModeSwitch which might help with the Huawei E220 and E169. You can see a detailed walkthrough for the EEE here:
[http://dalelane.co.uk/blog/?p=254](http://dalelane.co.uk/blog/?p=254)
Then the USB_ModeSwitch site itself (I think) is here:
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

Thanks for your answer, but when I try to compile the libusb (necessary for USB_ModeSwitch) it gives me an error:

```
pedroguerra@LaptopGuerra:~/Área de Trabalho/libusb-0.1.12$ sudo make[sudo] password for pedroguerra: 
make  all-recursive
make[1]: Entering directory `/home/pedroguerra/Área de Trabalho/libusb-0.1.12'
Making all in .
make[2]: Entering directory `/home/pedroguerra/Área de Trabalho/libusb-0.1.12'
if /bin/bash ./libtool --mode=compile gcc -DHAVE_CONFIG_H   -I.  -Werror  -g -O2 -g -Wall -MT usb.lo -MD -MP -MF ".deps/usb.Tpo" -c -o usb.lo usb.c; \
	then mv -f ".deps/usb.Tpo" ".deps/usb.Plo"; else rm -f ".deps/usb.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -Werror -g -O2 -g -Wall -MT usb.lo -MD -MP -MF .deps/usb.Tpo -c usb.c  -fPIC -DPIC -o .libs/usb.o
 gcc -DHAVE_CONFIG_H -I. -Werror -g -O2 -g -Wall -MT usb.lo -MD -MP -MF .deps/usb.Tpo -c usb.c -o usb.o >/dev/null 2>&1
if /bin/bash ./libtool --mode=compile gcc -DHAVE_CONFIG_H   -I.  -Werror  -g -O2 -g -Wall -MT error.lo -MD -MP -MF ".deps/error.Tpo" -c -o error.lo error.c; \
	then mv -f ".deps/error.Tpo" ".deps/error.Plo"; else rm -f ".deps/error.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -Werror -g -O2 -g -Wall -MT error.lo -MD -MP -MF .deps/error.Tpo -c error.c  -fPIC -DPIC -o .libs/error.o
 gcc -DHAVE_CONFIG_H -I. -Werror -g -O2 -g -Wall -MT error.lo -MD -MP -MF .deps/error.Tpo -c error.c -o error.o >/dev/null 2>&1
if /bin/bash ./libtool --mode=compile gcc -DHAVE_CONFIG_H   -I.  -Werror  -g -O2 -g -Wall -MT descriptors.lo -MD -MP -MF ".deps/descriptors.Tpo" -c -o descriptors.lo descriptors.c; \
	then mv -f ".deps/descriptors.Tpo" ".deps/descriptors.Plo"; else rm -f ".deps/descriptors.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -Werror -g -O2 -g -Wall -MT descriptors.lo -MD -MP -MF .deps/descriptors.Tpo -c descriptors.c  -fPIC -DPIC -o .libs/descriptors.o
 gcc -DHAVE_CONFIG_H -I. -Werror -g -O2 -g -Wall -MT descriptors.lo -MD -MP -MF .deps/descriptors.Tpo -c descriptors.c -o descriptors.o >/dev/null 2>&1
if /bin/bash ./libtool --mode=compile gcc -DHAVE_CONFIG_H   -I.  -Werror  -g -O2 -g -Wall -MT linux.lo -MD -MP -MF ".deps/linux.Tpo" -c -o linux.lo linux.c; \
	then mv -f ".deps/linux.Tpo" ".deps/linux.Plo"; else rm -f ".deps/linux.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -Werror -g -O2 -g -Wall -MT linux.lo -MD -MP -MF .deps/linux.Tpo -c linux.c  -fPIC -DPIC -o .libs/linux.o
 gcc -DHAVE_CONFIG_H -I. -Werror -g -O2 -g -Wall -MT linux.lo -MD -MP -MF .deps/linux.Tpo -c linux.c -o linux.o >/dev/null 2>&1
/bin/bash ./libtool --mode=link gcc -Werror  -g -O2 -g -Wall   -o libusb.la -rpath /usr/local/lib -version-info 8:4:4 -release 0.1 -export-dynamic   usb.lo error.lo descriptors.lo linux.lo  
rm -fr  .libs/libusb-0.1.so.4 .libs/libusb-0.1.so.4.4.4 .libs/libusb.a .libs/libusb.la .libs/libusb.lai .libs/libusb.so
gcc -shared  .libs/usb.o .libs/error.o .libs/descriptors.o .libs/linux.o   -Wl,-soname -Wl,libusb-0.1.so.4 -o .libs/libusb-0.1.so.4.4.4
(cd .libs && rm -f libusb-0.1.so.4 && ln -s libusb-0.1.so.4.4.4 libusb-0.1.so.4)
(cd .libs && rm -f libusb.so && ln -s libusb-0.1.so.4.4.4 libusb.so)
ar cru .libs/libusb.a  usb.o error.o descriptors.o linux.o
ranlib .libs/libusb.a
creating libusb.la
(cd .libs && rm -f libusb.la && ln -s ../libusb.la libusb.la)
if /bin/bash ./libtool --mode=compile g++ -DHAVE_CONFIG_H   -I.   -g -O2 -MT usbpp.lo -MD -MP -MF ".deps/usbpp.Tpo" -c -o usbpp.lo usbpp.cpp; \
	then mv -f ".deps/usbpp.Tpo" ".deps/usbpp.Plo"; else rm -f ".deps/usbpp.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -g -O2 -MT usbpp.lo -MD -MP -MF .deps/usbpp.Tpo -c usbpp.cpp  -fPIC -DPIC -o .libs/usbpp.o
 g++ -DHAVE_CONFIG_H -I. -g -O2 -MT usbpp.lo -MD -MP -MF .deps/usbpp.Tpo -c usbpp.cpp -o usbpp.o >/dev/null 2>&1
/bin/bash ./libtool --mode=link g++  -g -O2   -o libusbpp.la -rpath /usr/local/lib -version-info 8:4:4 -release 0.1 -export-dynamic  -lusb  usbpp.lo  
g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.2.3/crtbeginS.o  .libs/usbpp.o  -lusb -L/usr/lib/gcc/i486-linux-gnu/4.2.3 -L/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/i486-linux-gnu/4.2.3/../../.. -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.2.3/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crtn.o  -Wl,-soname -Wl,libusbpp-0.1.so.4 -o .libs/libusbpp-0.1.so.4.4.4
**_/usr/bin/ld: cannot find -lusb_**
collect2: ld returned 1 exit status
make[2]: *** [libusbpp.la] Error 1
make[2]: Leaving directory `/home/pedroguerra/Área de Trabalho/libusb-0.1.12'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/pedroguerra/Área de Trabalho/libusb-0.1.12'
make: *** [all] Error 2

```

(This after making ./configure )

Any solution for this? :???:

---

### Post by chmac on 2008-06-17
I haven't followed the instructions myself (just in the process of buying an E220 or E169). But a search in syanptic turned up a few options for libusb, maybe what you need is in one of those and you won't have to compile it yourself.

---

### Post by Green_biri on 2008-06-18
> **chmac said:**
> I haven't followed the instructions myself (just in the process of buying an E220 or E169). But a search in syanptic turned up a few options for libusb, maybe what you need is in one of those and you won't have to compile it yourself.

Thanks again for the answer, the libusb was already in Synaptic. But my device is still not found... :(

```
pedroguerra@LaptopGuerra:~$ usb_modeswitch

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.4 (C) Josua Dietze 2008
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices
 No target device found
Looking for default devices
 No default device found. Is it connected? Bye

```

Thanks again, still waiting for more solutions...

---

### Post by jarl69 on 2008-06-29
My friend spent a couple of weeks trying to sort this problem out, he finally did, and has since set me up on two seperate laptops within minutes. He has written a very good howto which you can find [**[COLOR="Red"]here[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=843973&highlight=e220")

---

### Post by chmac on 2008-06-29
I just received delivery of a Huawei E220. I plugged it in (under Ubuntu 8.04) and it worked like a charm. I had to set the init string to include the APN, but otherwise it worked fine.

I'd recommend upgrading to [NetworkManager 0.7]("http://ubuntuforums.org/showthread.php?t=797059"), then you can manage the modem natively within NetworkManager, which works flawlessly for me.

Just to confirm, I simply plugged in the modem, and it worked. No need for usbswitching or any other fandangledness. Plug and play! :)

---

### Post by mormor on 2008-06-29
[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

link for a gui-prog to get huawei modems to work. The app is made for vodafone, but works for me in norway. and its pretty easy to use. Just download, install and well. Go online. think there are newer versions out there : )

(or just google: vodafone-mobile-connect-card-driver-for-linux

e220 works with this prog for me. : )

---

### Post by chmac on 2008-06-29
I had a lot of hassle with the vodafone program. It woulnd't connect at all for me. However, wvdial or gnome-ppp worked like a charm. No idea what was causing the issue. The vodafone software is nice as it counts your bandwidth usage, lets you send SMSs, manage sim contacts, pin nos, etc. Instead I use vnstat (very easy) to monitor bandwidth usage and forget about sim pins, contacts, sms, etc.

---

### Post by salutis on 2008-08-03
There is also out-of-box solution you can try. Open terminal and enter these installation commands:

```

sudo -s
echo deb [http://repository.salutis.sk/production](http://repository.salutis.sk/production) ./ >> /etc/apt/sources.list
apt-get update
apt-get install salutis-connect

```

After installation click on *Salutis Connect* icon in *Applications* -> *Internet* menu section and enjoy. To disconnect the device, click on *Salutis Connect* again and the device will be disconnected.

---

### Post by sqasl1! on 2008-08-05
Hi

Suspect I've got the same problem as you - posted a new thread here [http://ubuntuforums.org/showthread.php?t=880650]("http://ubuntuforums.org/showthread.php?t=880650")

Does this sound like something that could have happened in your case?

---

### Post by chmac on 2008-08-06
> **sqasl1! said:**
> Hi

Suspect I've got the same problem as you - posted a new thread here [http://ubuntuforums.org/showthread.php?t=880650]("http://ubuntuforums.org/showthread.php?t=880650")

Does this sound like something that could have happened in your case?

Have you tried the upgrade to NetworkManager 0.7? It's a perfectly workable solution. It works fine for me. It will most likely resolve all your issues.

---

### Post by sqasl1! on 2008-08-08
Yo

Upgraded to NetworkManager 0.7 and yes, it seems to have solved my problems.  lol.  Would not have thought it, but there you have it.  You can check [my post]("http://ubuntuforums.org/showthread.php?p=5546813#post5546813") for further details.

Thanks for the suggestion.  Now if you could tel me WHY it worked ... ;-)

---

### Post by chmac on 2008-08-08
> **sqasl1! said:**
> Upgraded to NetworkManager 0.7 and yes, it seems to have solved my problems.  lol.  Would not have thought it, but there you have it.  You can check [my post]("http://ubuntuforums.org/showthread.php?p=5546813#post5546813") for further details.

:)

> **sqasl1! said:**
> Thanks for the suggestion.  Now if you could tel me WHY it worked ... ;-)

NetworkManager doesn't do anything very complicated. You can do the same thing with GnomePPP, but you have to enter more settings by hand. With NetworkManager it has the "rules" already for your modem. So it "just works". Plus NetworkManager deals with all the HAL stuff to tell your system when it's on/offline, which is a big plus for me.

---

### Post by junglejuice on 2008-09-20
> **salutis said:**
>  To disconnect the device, click on *Salutis Connect* again and the device will be disconnected.
hi there i know this post is a little old but none the less i am having a problem disconnecting the device. Huawei E220
the device connects perfectly, thanks for the help on that :-)
however when i click on Salutis Connect, once the connection is active i am simply taken back to the connection options and Salutis tells me
> Wohoo! You're connected, go ahead :)
i am using Salutis Connect 1.2.3 on ubuntu 8.04, Gdm and i am also quite a newbie :-)
thanks in advance

---

### Post by Zenith Gurgel Neto on 2008-09-23
well, if someone understand a little bit of portuguese, this solved all my questions:

[http://ubuntuforum-br.org/index.php/topic,40427.0.html](http://ubuntuforum-br.org/index.php/topic,40427.0.html)

---

### Post by junglejuice on 2008-09-23
hi there Zenith Gurgel Neto
i don't understand a word of portuguese unfortunately, is there anything in that post you linked to about disconnecting the E220 with software once a connection has been established. at he moment to disconnect the modem i literally have to unplug it from my computer, which does not seem to be very sound practice

---

### Post by zenithgurgel on 2008-09-29
> **junglejuice said:**
> hi there Zenith Gurgel Neto
i don't understand a word of portuguese unfortunately, is there anything in that post you linked to about disconnecting the E220 with software once a connection has been established. at he moment to disconnect the modem i literally have to unplug it from my computer, which does not seem to be very sound practice

well, I had this problem when I was using the usbserial module. But the problem solved when using the Airprime Module.... and so with the kppp, everybody works ok.

---

### Post by junglejuice on 2008-09-29
> **zenithgurgel said:**
> well, I had this problem when I was using the usbserial module. But the problem solved when using the Airprime Module.... and so with the kppp, everybody works ok.

hi since i just got the modem i'm pretty much stuck with the usb model, is there absolutely no way of disconnecting the modem using software. i mean like not even through terminal? or something?

---

### Post by chmac on 2008-09-29
> **junglejuice said:**
> hi since i just got the modem i'm pretty much stuck with the usb model, is there absolutely no way of disconnecting the modem using software. i mean like not even through terminal? or something?

Yes, you can disconnect. You're using Salutis Connect I believe. I'm not familiar with that package, so I don't know where it's disconnect feature lies. Try something like this:
`sudo ifconfig ppp0 down` or `sudo ifdown ppp0`

That will probably take the network interface down.

Or, try the upgrade to NewtorkManager 0.7 and there will be a handy "Disconnect" menu icon. :)

---

### Post by junglejuice on 2008-09-30
hi there chmac
thanks i'll give those commands a try, hope they work or i'll have to upgrade networkmanager. this is probably not such a bad idea too :-)
jj

---

### Post by junglejuice on 2008-09-30
hi there chmac
well i tried the commands you recommended the 2nd command 
```
sudo ifdown ppp0
``` 
gave me this error
```
ifdown: interface ppp0 not configured
```
the first command 
```
sudo ifconfig ppp0 down
```
worked but would not let me reconnect with salutis after issuing the command. any idea why this might happen?

---

### Post by chmac on 2008-09-30
> **junglejuice said:**
> ```
sudo ifconfig ppp0 down
```
worked but would not let me reconnect with salutis after issuing the command. any idea why this might happen?

Hmm, I'm not sure what's going on to be honest. I'm not very familiar with ppp connections in Linux. I was just guessing that ifconfig down might work. You could also try to figure out what program is running that is creating the connection, and then kill that. Try
```
ps aux
```

That will produce a huge output of all the running applications on the machine. To make some sense of it, you can put it into a text file like this:
```
ps aux > ~/sometextfile.txt
```

You can filter the output using grep like this:
```
ps aux | grep ppp
```

Change ppp to anything you like. You can run that command a few times. I'd look for things like wvdial, salutis, and so on. If you can figure out which one is controlling the connection, find it's process id, and then you can try:
```
kill pid
```

In this command pid is a number, the process id. Be careful with this command though, if you pick the wrong number, you kill the wrong process! :)

---

### Post by junglejuice on 2008-10-01
excellent! thanks chmac that will certainly help :-)
i think salutis uses Wvdial. will let you know as soon as i get it working.
thanks again
jj

---

### Post by junglejuice on 2008-10-01
hey there chmac 
tried out the commands you mentioned, worked like a charm!
was also able to reconnect without any worries after killing wvdial pid.
only thing is it seems a bit cumbersome to have to search for wvdials pid everytime i need to drop the connection. since i know the process i want to kill is wvdial is there perhaps another way of killing it without having to know it's pid, that you know of? thanks for the help, i really appreciate it :-)
jj

---

### Post by chmac on 2008-10-01
This should do the trick:
`pkill wvdial`

---

### Post by junglejuice on 2008-10-01
awesome chmac! you rock solid dude, thanks for helping me out with that. i really appreciate it.
it's all working 100% the way i want it to now. connection/disconnection/reconnection is a breeze.
thanks again man that's great :-)
jj

---

### Post by chmac on 2008-10-01
Glad you've got it working. I'd still recommend upgrading to NetworkManager 0.7 as then you can connect / disconnect through the menu, and it notifies applications of your on/offline status so Firefox / Evolution / etc will connect / disconnect automatically. :)

---

### Post by theplasticbag on 2008-10-01
Didn't realise this was posted hours ago.  whoops.


This may not help but I had issues with installing an E160G type usb modem.

I use 3 mobile pay as you go in the uk and now it working thanks to Fingers & Thumbs - in his post HUAWEI E220 USB MODEM FOR BEGINNERS.

Had a couple of issues so I hope what I tell you works for you.

Go to **APPLICATIONS>ACCESSORIES>TERMINAL**

first type 

**sudo apt-get install wvdial**

then

**sudo ./etc/wvdial.conf**

then

**sudo gedit ./etc/wvdial.conf/**

Remove the semicolon at the beginning -change your phone number to the one that your service provider gives (I believe that vodafone and 3 use *99#)
and do the same for username and password.  For 3 I put username - anything and for password I did the same as they are blank.

Also look at what it says after [dialer _______]  the standard is defaults.

so if you go back to your terminal again and type wvdial defaults it should click in after a couple of minutes and will list something about secondary DNS entries.  When it appears to have doen evertything it can see if you can fire up your web browser.

---

### Post by junglejuice on 2008-10-02
hi chmac
thanks for the advice i'll definitely give it a try, infact i have already tried through synaptic but it won't let me upgrade it. i think this might work though
```
sudo apt get-upgrade network-manager
```
actually i don't really know i'll have to look around some more.
thanks again chmac :-)
jj

---

### Post by chmac on 2008-10-02
See this thread on [upgrading to NetworkManager 0.7]("http://ubuntuforums.org/showthread.php?t=797059"). It's not included in the regular repositories.

---

### Post by junglejuice on 2008-10-02
excellent
thanks for the help i'll check it out, but i'm pretty much happy with the current configuration i'm using :-)
peace 
jj

---

### Post by JustTCO on 2008-10-17
hi,
i just read your post and i would like to expose my wvdial code that i find here and there around the net.

before i edit wvdial.conf i enable de mod
```

modprobe usbserial vendor=0x12d1 product=0x1003

```

and then edit wvdial.conf

```

[Dialer Defaults]
Phone = *99***1#
#Phone = *99# (is not enable but it works as well)
Username = (this is username that they ask at first connection)
Password = (this is password that they ask at first connection)
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]
Int1 = AT+CPIN=(this is the pin for your kanguru card)

[Dialer modem]
Modem = /dev/ttyUSB0
Baud = 7200000 (this is the bandwith - 7.2Mbps)
Int2 = ATZ
Int3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Area code =
Compuserve = 0
Force Address =
Idle Seconds = 0
DialMessage1 =
DialMessage2 =
ISDN = 0
Auto DNS = 1
Modem Type = Analog Modem

[Dialer myconnection]
Int5 = AT+CGDCONT=1,"IP","myconnection"


```

Now we just connect with shell
```

alias Kanguru

code: sudo wvdial pin modem

```

after all that i writing this post :lolflag:

ho one more thing for you junglejuice. to disconnect just press Ctrl+C he disconect quitely... you see

---

### Post by anet on 2009-04-05
> **chmac said:**
> See this thread on [upgrading to NetworkManager 0.7]("http://ubuntuforums.org/showthread.php?t=797059"). It's not included in the regular repositories.

Hi, a Noobie Ubuntu user here...I've read through several threads trying to get more info on getting my Huawei EC325 modem setup on Ubuntu.

Have managed to get Ubuntu to see it, and the settings written to wvdial.conf file...

when I try to connect...no Carrier.

Anyway, sorry I can't post the exact info at this point as I'm back on the WinXP portion of my laptop just so I can read these forums.

Which brings me to my REAL QUESTION. Several times in this thread you suggest that users install the latest Network Manager. I've gone to the link you list...but that only tells how to install via Synaptic. If I can't get on the internet with Ubuntu but only when in WinXP, what do I download and how do I install it when in Ubuntu? Your link doesn't lead me to a clear download link. 

Would it be possible for you to find the exact page where a download exists and explain exactly what file needs to be downloaded, like the exact name, please? Remember if you spell out every single thing it won't hurt, I'm a complete Noob, but nobody seems to be answering any of the questions I post in the Beginner SEction...:D

Thanks in advance!!

---

### Post by GeorgeVita on 2009-04-05
Hi **anet**,

> **anet said:**
> ...
I'm a complete Noob, but **nobody seems to be answering** any of the questions I post in the Beginner SEction...:D


Are you sure for the above? There is an answer waiting for 7 hours!
[http://ubuntuforums.org/showthread.php?t=1097161&page=2](http://ubuntuforums.org/showthread.php?t=1097161&page=2)

Please note that you cannot be sure that a person who can help you is online the same time you are... so use the **Thread Tools** (up right) to **Subscribe to a thread** and later from your **Quick Links** you can see your **Subscribed Threads** for new messages (you can setup also an email notification.

Regards,
George

EDIT: another one answer waits more than 12 hours... [http://ubuntuforums.org/showthread.php?t=990950](http://ubuntuforums.org/showthread.php?t=990950)

---

