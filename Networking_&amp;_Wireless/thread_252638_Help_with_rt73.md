---
title: "Help with rt73"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by beniwtv on 2006-09-07
Hello,

I'm now a edgy user :mrgreen: 

But I have some trouble to get my wifi working. The thing is that I have a 5 letters ASCII WEP key. How can I configure my connection (from the command line) to connect to WEP? :confused:  

I tried almost everything I could find, but my AP keeps rejecting me.

Also, my wifi is a bit strange:

When I plug in the card (USB, conceptronic with rt73), the rt73usb module is correctly loaded. But I get two wifis? :confused: 

One is called wmaster0 and the other wlan0. Also, scanning works only the first time or maybe two or three times I try. After this, "no scan results".

Can anyone help me getting my WEP key to work and bring light to the other issues?

Thanks.


EDIT: network-manager-gnome (nm-applet) gives the error "Some resources could not be found. Will quit now" (Translated from Spain). In the command line there is no error or something. Is it broken in Edgy?

---

### Post by littlespy on 2006-09-15
im having a similar problem getting the rt73 driver to work, any suggestions would be helpful

---

### Post by JAwuku on 2006-09-16
I just successfully got my Sitecom WL-113 (release 002) usb card working using help from the Ubuntu website:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29")

Check the readers comments near the bottom to set up the correct symlinks for compiling first, and also how to set up WEP/WPA correctly.

In fact, I had to boot to Windows and check via the Control Panel, to discover I actually had the rt73 chipset (release 001 actually has the ZD1211 chipset, covered elsewhere in these forums.)

Hope the link is of use.

---

### Post by lupine_nickt on 2006-09-17
The rt73 driver included in Edgy is from the [rt2x00](http://rt2x00.serialmonkey.net/) people; this particular codebase is currently under heavy development, and TBH it's not really ready for production use.

Compiling the latest CVS might help your problems - or it may not! Not all features are set up yet, and it'll be a while before they all are, I'd imagine.

The wlan0/wmaster0 interfaces are normal - it's the new "standard" (if you like) for WLAN devices under Linux. You can use wmaster0 with wlandev, among other programs, for all sorts of things - including setting up other wlan0 devices, under master or monitored mode, etc. 

Setting up WEP, thankfully, is still as easy as ever - "sudo iwconfig wlan0 key <key>"... If ASCII, prefix <key> with "s:". "man iwconfig" for more details on that side of things.

---

### Post by singy on 2006-09-21
Hi!

I have a Belkin USB stick with a ralink chip. With the rt73usb driver from serialmonkey I cant set the key.
I am using the driver from ralink. I had to change one include directive to compile it on amd64, but it works.
I have a shell script on startup which onloads the rt73usb modules and sets up my interface.

greetings

---

### Post by philetusx on 2006-10-01
> **singy said:**
> I had to change one include directive to compile it on amd64, but it works.
greetings

I am also trying to build the ralink rt73 driver on dapper amd64.

which include directive did you change?

---

### Post by singy on 2006-10-01
Hi!

I changed in rt_config.h 
"#include <asm-i386/atomic.h>"  to "#include <asm/atomic.h>"  

I had also add " {USB_DEVICE(0x050d,0x705a)}, /* Belkin */      \"
in "rtmp_def.h" for my blekin stick.

I have problems setting the parameters for the device with gnome.
I start it up with a script after booting by hand.

greetings

---

### Post by uman on 2006-12-17
Hello,
(here are my experiences)
I have the D-Link DWL-G122 version C1. Also the D-Link router DI-524. I have compiled a module from the following article: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29)

from the information in the bottom point 4.2. 

Downloaded rt73-cvs-2006121612 and just did "sudo make all" and then "sudo make install".
My  /etc/modules contains the spec "rt73"
My /etc/modprobe.d/ contains the document "rt73" in which it says "alias rausb0 rt73"

All as stated in article above.

My /etc/network/interfaces looks like this: (after some serious chaning back and forth to get it to work)

auto lo
iface lo inet loopback

auto rausb0
iface rausb0 inet dhcp
        pre-up ifconfig rausb0 up
        pre-up ifconfig rausb0 down
        pre-up ifconfig rausb0 up
        pre-up iwconfig rausb0 mode Managed
        wireless-essid MYNETWORKNAME
        wireless-key s:MYPASSWORD
        pre-up ifconfig rausb0 up

This worked great :) with the kernel 2.6.15-27-386 and WEP ascii password.

Then I upgraded over the net to Ubuntu 6.10.

In 6.10 there is already a module called rt73usb which now loads instead of my own build module. When rebooting my earlier config didnt work. Ofcourse I got the wlan0 and wmaster (or what is was) but the card just didnt connect.

I changed all from rausb0 to wlan0 in all my config files above - no change - still didnt work.

The manually typing "sudo ifup wlan0" gave some information that the card(usb adapter) was kind of hanging on a set command. Didnt have any set command as in my /etc/networks/interfaces. 

Then I tried with the basic stuff and removed all pre-up things above - no change. It didnt connect with router.

In the end to get it to work - I removed the standard 6.10 rt73usb module to not have it loaded, downloaded the rt73-cvs-2006121612 and linux-headers for my new 6.10 kernel. Build the module and kept all files the same as it was when working above.

Rebooted, then it worked fine. Seems like my shell scripts are not compatible with the standard build of rt73usb and I had to build my own. 

Any ideas why this is so?

Regards uman

---

### Post by Cueball696 on 2006-12-17
Hello I have a Fan of Linux.. but I am coming in to a few problem with my Laptop(tobshiba Satellite A35-S159 with linux.

See I have got the new Suse10.1 loved it.. but I got Ubuntu and I was understood that Ubuntu configure my WLan NIC embed better.. I installed ubuntu6.10 and it came with Gnome and KDE3.4 and I in Heaven.. but I am able to get my WLAN to work with any open Router(NON WEPKEY).. so any home user that has wireless like not to turn into a Starbuck and lock there Wireless Router, so I am using a WEP 64H, but when I plug in to KwifiManger it read and hook up to the router, BUT I can get net.... but I am not able to ping the Routers..


thanks for any info and this.

---

