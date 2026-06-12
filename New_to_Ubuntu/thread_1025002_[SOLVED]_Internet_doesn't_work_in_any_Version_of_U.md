---
title: "[SOLVED] Internet doesn't work in any Version of Ubuntu."
date: 2008-12-29
forum: New to Ubuntu
---

### Post by retskrad on 2008-12-29
Please guys, please. I have made several threads and tried to bump them (I shouldn't have done that, since ppeople here ignore you then), but still nobody answer.

I hav a discussion in this thread: [COLOR="Red"][http://ubuntuforums.org/showthread.php?t=1020106](http://ubuntuforums.org/showthread.php?t=1020106)[/COLOR]

I have tried ifconfig, lspci, all those commands inside uubntu and pasted in that thread, so if you answer and want me to paste the output of the commands, I will now let you know that I ' ve already done that.

A couple of weeks ago internet worked while dual booting ubuntu. Now when i do that, internet doesn't work.

When I dual boot windows, internet works.

I'm using a wired modem. Here it is:

[COLOR="Red"][http://www.powertv.com/products/consumers/images/DPX2203.jpg](http://www.powertv.com/products/consumers/images/DPX2203.jpg)
[http://homepage.mac.com/nobodyhere/Sites/modemlights/WS_EPX2203/2203back.JPG](http://homepage.mac.com/nobodyhere/Sites/modemlights/WS_EPX2203/2203back.JPG)[/COLOR]

model: EPX2203.

[COLOR="Red"]My Network Card (on motherboard):
  Realtek RTL8139/810x Family Fast[/COLOR]

I believe its the most supported card on the planet.

Also, I have tried LIVE-CD, still no internet.


Please guys, please try to help me out. I really want to get away from windows. I tried with ubuntu 8.04, still no internet. I tired with 8.10, no internet.

But the weird thing is, hat internet works in windows while dual booting, but not uubntu.

---

### Post by dk21 on 2008-12-29
Have you tried to re-install modem?

---

### Post by albandy on 2008-12-29
ensure you've got the same hw address in Linux and Windows. Have you changed your lan card? 

put ipconfig /all in Windows and paste it here
put ifconfig in Linux and paste it here.

Some cable providers block your connection to a specific computer name and/or hardware address.

---

### Post by retskrad on 2008-12-29
C: \ Documents and Settings \ Admin2> ipconfig / all

IP Configuration for Windows

         Host Name. . . . . . . . . . : User-13cc7a18f0
         Primary DNS Suffix. . . . . . . :
         Nodtyp. . . . . . . . . . . . . : Unknown
         IP routing enabled. . . . . . : No
         WINS Proxy Enabled. . . . . . : No

Ethernet card the Local Area Connection:

         Connection-specific DNS Suffix. :
         Description. . . . . . . . . . . : Realtek RTL8139/810x Family Fast Eth
ernet NIC
         Physical Address. . . . . . . . . . : 00-11-09-6C-CD-5E
         DHCP enabled. . . . . . . . . : Yes
         Auto Configuration enabled. . . : Yes
         IP address. . . . . . . . . . . . : 83.255.63.166
         Subnet Mask. . . . . . . . . . . . . : 255.255.240.0
         Default Gateway. . . . . . . . : 83.255.48.1
         DHCP server. . . . . . . . . . . : 10.125.1.11
         DNS servers. . . . . . . . . . . : 83.255.245.10
                                             83.255.249.10
         The loan was obtained. . . . . . . . . . : December 30, 2008 00:06:15
         The loan expires. . . . . . . . . . : December 30, 2008 06:06:12

C: \ Documents and Settings \ Admin2>

---

### Post by retskrad on 2008-12-29
ubuntu@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:11:09:6c:cd:5e
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:23 Base address:0xa000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:216 errors:0 dropped:0 overruns:0 frame:0
TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:13536 (13.5 KB) TX bytes:13536 (13.5 KB)

---

### Post by albandy on 2008-12-29
could you paste your /etc/network/interfaces file?

cat /etc/network/interfaces

---

### Post by retskrad on 2008-12-29
Ok, don't go away lol, seems like only you answears man, really appreciate it. Ill just restart and dualboot ubuntu.

---

### Post by retskrad on 2008-12-29
Here is what it was in interfaces:

> auto lo
iface lo inet loopback

---

### Post by albinootje on 2008-12-29
> **retskrad said:**
>  [COLOR="Red"]My Network Card (on motherboard):
  Realtek RTL8139/810x Family Fast[/COLOR]

I believe its the most supported card on the planet. 

The RTL8139 B/C/D probably are, yes.
Don't remember the exact chipset of your card.

Realtek is also known for making relatively crappy network-cards.
But they're cheap.
Nowadays in shops over here they cost 6 euros for the 100 Mbit ones, the 1000 Mbit ones are a bit more expensive.

3Com makes quality network-cards, years ago they came with manuals and software to change options for the card.

Is your machine a laptop or a desktop-machine ?
Do you have a lot of devices in (or attached to) your machine ?
Can you post the output of :
```

cat /boot/grub/menu.lst
cat /proc/interrupts 

```

---

### Post by albandy on 2008-12-29
ok, edit it with the command sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

then save it. now edit /etc/hostname
change the computer name to User-13cc7a18f0
save and reboot the computer

---

### Post by retskrad on 2008-12-29
[B][COLOR="Red"]Ok, I have a PC, no laptop

and thank you all for helping me out, I will just write down the commands you told me and daul boot to uubntu again, dont go away ;)[/COLOR][/B]

---

### Post by retskrad on 2008-12-29
I only have a USB mouse connected .

---

### Post by albinootje on 2008-12-29
> **retskrad said:**
> [B][COLOR="Red"]Ok, I have a PC, no laptop
[/COLOR][/B]

Okay, good! :)

Do you remember whether someone installed the internet-connection in Windows on your machine ?
Or did you have to use a cdrom from your ISP ?

Because your ipconfig /all output from your Windows-computer shows that you are directly connected to the internet, your modem or router doesn't do NAT.

---

### Post by albandy on 2008-12-29
> **albinootje said:**
> Okay, good! :)

Do you remember whether someone installed the internet-connection in Windows on your machine ?
Or did you have to use a cdrom from your ISP ?

Because your ipconfig /all output from your Windows-computer shows that you are directly connected to the internet, your modem or router doesn't do NAT.

Before having adsl I was connected to internet with a cable connection, with a modem like he has. In my case they register the first computer that was connected and I solved it using the same computer name and mac address in Linux.

Usually this kind of modem works directly without drivers (you don't need a ppp connection) only need drivers when you connect throught usb but this is not the case.

I think it could be a RX/TX negotiation problem or a computer name problem/mac address problem.

Lets wait if it works with the suggested configuration changes.

---

### Post by albinootje on 2008-12-29
> **albandy said:**
> Before having adsl I was connected to internet with a cable connection, with a modem like he has. In my case they register the first computer that was connected and I solved it using the same computer name and mac address in Linux. 

Yes. I'm asking this because I wondered whether the MAC-address is being faked in the Windows installation, not very likely, but that could explain why it doesn't get an ip-address in Linux.

And concerning not needing username/password :
Sweden is not far away from Holland, and here in Holland one of the biggest ISP-es uses passwords for connecting through a DSL-router :(

---

### Post by retskrad on 2008-12-29
here is cat /boot/grub/menu.lst

> admin3@admin3-desktop:~$ sudo cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=DCF8B6ABF8B68376 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=DCF8B6ABF8B68376 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=DCF8B6ABF8B68376 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1

admin3@admin3-desktop:~$ 



---

### Post by retskrad on 2008-12-29
I have been using other WINDOWS install cds. I chose to connect to internet with a network, instead of directly tto internet.

---

### Post by retskrad on 2008-12-29
Here is sudo cat /proc/interrupts

> admin3@admin3-desktop:~$ sudo cat /proc/interrupts
           CPU0       
  0:        306   IO-APIC-edge      timer
  1:        554   IO-APIC-edge      i8042
  4:          2   IO-APIC-edge    
  7:          0   IO-APIC-edge      parport0
  8:          3   IO-APIC-edge      rtc
  9:          1   IO-APIC-fasteoi   acpi
 14:      57550   IO-APIC-edge      libata
 15:       4702   IO-APIC-edge      libata
 16:          0   IO-APIC-fasteoi   uhci_hcd:usb1
 17:      20948   IO-APIC-fasteoi   uhci_hcd:usb2
 18:      32592   IO-APIC-fasteoi   uhci_hcd:usb3
 19:          5   IO-APIC-fasteoi   ehci_hcd:usb4, ohci1394, eth0
 20:        456   IO-APIC-fasteoi   Intel 82801DB-ICH4
NMI:          0   Non-maskable interrupts
LOC:     148196   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0
admin3@admin3-desktop:~$ 



---

### Post by abn91c on 2008-12-29
have you tried the command **[COLOR="Red"]dhclient eth0[/COLOR]**

---

### Post by retskrad on 2008-12-29
done, I changed my name froma dmin3-desktop, to the one you told me.

---

### Post by retskrad on 2008-12-29
Whats [COLOR="Red"]dhclient eth0[/COLOR] good for?

---

### Post by albinootje on 2008-12-29
> **retskrad said:**
> Whats [COLOR="Red"]dhclient eth0[/COLOR] good for?

dhclient eth0 will request an ip-address from a DHCP-server.
DHCP-servers hand out ip-addresses to machines that request for it.

I don't remember whether your NIC == eth0 or eth1,
in that case :
```

sudo dhclient

```
would make more sense.

---

### Post by albinootje on 2008-12-29
By the way.
In another thread you wrote that blank cdroms are expensive in Sweden.
What about network-cards ? Are they expensive too ?

---

### Post by abn91c on 2008-12-29
> **albinootje said:**
> dhclient eth0 will request an ip-address from a DHCP-server.
DHCP-servers hand out ip-addresses to machines that request for it.

I don't remember whether your NIC == eth0 or eth1,
in that case :
```

sudo dhclient

```
would make more sense.

from his previous post it is eth0

---

### Post by retskrad on 2008-12-29
> **albinootje said:**
> dhclient eth0 will request an ip-address from a DHCP-server.
DHCP-servers hand out ip-addresses to machines that request for it.

I don't remember whether your NIC == eth0 or eth1,
in that case :
```

sudo dhclient

```
would make more sense.

Here it is:

> **admin3@User-13cc7a18f0:~$ sudo dhclient eth0**
sudo: unable to resolve host User-13cc7a18f0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:09:6c:cd:5e
Sending on   LPF/eth0/00:11:09:6c:cd:5e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
admin3@User-13cc7a18f0:~$ 





---

### Post by retskrad on 2008-12-29
> **albinootje said:**
> By the way.
In another thread you wrote that blank cdroms are expensive in Sweden.
What about network-cards ? Are they expensive too ?

Lol I'm not sure. I can't afford one.

---

### Post by abn91c on 2008-12-29
you probably need to go to your modem setup and check the configuration settings, also check if it has a reset button that will load the factory settings and that your SSID and security keys are working. Also just for fun try using the usb port in the cable modem just in case you have NIC going bad or the network cable bad.

---

### Post by retskrad on 2008-12-29
I don't have a clue about moedems..

My moden model is Webstar EPX2203.
[http://www.powertv.com/products/cons...es/DPX2203.jpg](http://www.powertv.com/products/cons...es/DPX2203.jpg)
[http://homepage.mac.com/nobodyhere/S...3/2203back.JPG](http://homepage.mac.com/nobodyhere/S...3/2203back.JPG)

But I have tried to reset it, like turn it off and the computer and that and wait one minute then login to ubuntu, still noi nternet.

---

### Post by OldTimeTech on 2008-12-29
Actually if your using 8.10, it's the Network Manager error that has been turned into Launchpad many times and the only fix that has been found is to add into Network Manager ....actually check this out...yes the last one is my rant...LOL

[http://ubuntuforums.org/showthread.php?t=1024524](http://ubuntuforums.org/showthread.php?t=1024524)

---

### Post by retskrad on 2008-12-29
No man, I'm using 8.04.

---

### Post by albinootje on 2008-12-29
> **retskrad said:**
> Lol I'm not sure. I can't afford one.

If you want I can send you an old 3Com network-card by postal mail.
But I need to test them first, I have quite a bunch of network-cards around.

First please try my suggestion about loading the module for your NIC (and blacklisting another module) in another (long) thread by you.

---

### Post by abn91c on 2008-12-29
some modems have a small button in the back or a small home where you  have to press for a few seconds for example my linksys is for 30 seconds to  reboot the modem to manufacturers settings.

---

### Post by retskrad on 2008-12-29
> **albinootje said:**
> If you want I can send you an old 3Com network-card by postal mail.
But I need to test them first, I have quite a bunch of network-cards around.

First please try my suggestion about loading the module for your NIC (and blacklisting another module) in another (long) thread by you.

I have no idea what you just said, as I said I aint so good with modem. I dont why now suddenly internet isnt working in ubuntu, a couple of weks agi it did, without any of these, comamnds and all.. it worked directly out of the box

---

### Post by retskrad on 2008-12-29
> **abn91c said:**
> some modems have a small button in the back or a small home where you  have to press for a few seconds for example my linksys is for 30 seconds to  reboot the modem to manufacturers settings.

Nah man, there isnt anyt button that switches the modem off.

---

### Post by albinootje on 2008-12-29
> **retskrad said:**
> I have no idea what you just said, as I said I aint so good with modem. I dont why now suddenly internet isnt working in ubuntu, a couple of weks agi it did, without any of these, comamnds and all.. it worked directly out of the box

In another thread you showed the output of :
```

lsmod

```
And that showed 2 different modules for your network-card loaded, the 8139too and the 8139cp.

Here's another (old) thread about the same problem :
[http://ubuntuforums.org/showthread.php?t=169633](http://ubuntuforums.org/showthread.php?t=169633)
and :
[http://ubuntuforums.org/showthread.php?t=1200](http://ubuntuforums.org/showthread.php?t=1200)

You only need to have 1 of those modules loaded!
So.. find out how to blacklist on of them.

---

### Post by retskrad on 2008-12-29
> **albinootje said:**
> In another thread you showed the output of :
```

lsmod

```
And that showed 2 different modules for your network-card loaded, the 8139too and the 8139cp.

Here's another (old) thread about the same problem :
[http://ubuntuforums.org/showthread.php?t=169633](http://ubuntuforums.org/showthread.php?t=169633)
and :
[http://ubuntuforums.org/showthread.php?t=1200](http://ubuntuforums.org/showthread.php?t=1200)

You only need to have 1 of those modules loaded!
So.. find out how to blacklist on of them.

Is there a possibility that if I unload one of these modules, internet will work? And is there a possibility that you know how to unload one?:(

---

### Post by abn91c on 2008-12-29
your reset button is a small hole near the power cord, you will have to stick a small pin in there. Your web based modem set up is here [http://192.168.100.1](http://192.168.100.1)

---

### Post by retskrad on 2008-12-29
> **abn91c said:**
> your reset button is a small hole near the power cord, you will have to stick a small pin in there. Your web based modem set up is here [http://192.168.100.1](http://192.168.100.1)

Dang man, how did you find it? Google? Dang, what a brain lol

One sec, let me check if I can find it.

---

### Post by albinootje on 2008-12-29
> **retskrad said:**
> Is there a possibility that if I unload one of these modules, internet will work? And is there a possibility that you know how to unload one?:(
Yes.
Please try the following :
```

sudo gedit /etc/modprobe.d/blacklist

```
and add at the bottom a line with :

blacklist 8139cp

Save the file, and reboot Ubuntu.

---

### Post by retskrad on 2008-12-29
> **abn91c said:**
> your reset button is a small hole near the power cord, you will have to stick a small pin in there. Your web based modem set up is here [http://192.168.100.1](http://192.168.100.1)

Is it possible that the reset thing can be this:

[http://rapidshare.com/files/178011197/namnloes.bmp.html](http://rapidshare.com/files/178011197/namnloes.bmp.html)

---

### Post by retskrad on 2008-12-29
> **albinootje said:**
> Yes.
Please try the following :
```

sudo gedit /etc/modprobe.d/blacklist

```
and add at the bottom a line with :

blacklist 8139cp

Save the file, and reboot Ubuntu.

I love your help man! Thank you! I hope it works, Ill just restart and dualboot ubuntu again.
[COLOR="Red"]
Also, which one is better, 8139too  or 8139cp?[/COLOR]

---

### Post by abn91c on 2008-12-29
> **retskrad said:**
> Is it possible that the reset thing can be this:

[http://rapidshare.com/files/178011197/namnloes.bmp.html](http://rapidshare.com/files/178011197/namnloes.bmp.html)
yes thats the one

---

### Post by albinootje on 2008-12-29
> **retskrad said:**
> Is it possible that the reset thing can be this:

[http://rapidshare.com/files/178011197/namnloes.bmp.html](http://rapidshare.com/files/178011197/namnloes.bmp.html)

Yes, quite likely.

---

### Post by retskrad on 2008-12-29
I blacklisted the module you told me to do and I restarted the computer and logged into ubuntu, still no internet... also i did reset the modem... 

Should I use roam mode (orsomething. cant emmeber what its called) or should I use DHCP in network settings?

---

### Post by abn91c on 2008-12-29
> **retskrad said:**
> I blacklisted the module you told me to do and I restarted the computer and logged into ubuntu, still no internet... also i did reset the modem... 

Should I use roam mode (orsomething. cant emmeber what its called) or should I use DHCP in network settings?

disable the roaming, other distros i used connected after unchecking the roaming mode

---

### Post by retskrad on 2008-12-29
When I first logged in, it was DHCP, then I changed to roaming, because thatss what it was when I installed ubuntu in first place..

---

### Post by retskrad on 2008-12-29
albinootje, you told me to blacklist one of the modules and I did, restartd and internet isnt working, still.

---

### Post by retskrad on 2008-12-29
bump

---

### Post by albinootje on 2008-12-29
> **retskrad said:**
> albinootje, you told me to blacklist one of the modules and I did, restartd and internet isnt working, still.

Thanks for trying that, can you post the output of the following please :
```

lsmod|grep rtl
lshw -c network
sudo dhclient
ifconfig -a
route -n
cat /etc/resolv.conf

```

And please use "bumping" after 24 hours of waiting. 
Thanks.

---

### Post by retskrad on 2008-12-29
> **albinootje said:**
> Thanks for trying that, can you post the output of the following please :
```

lsmod|grep rtl
lshw -c network
sudo dhclient
ifconfig -a
route -n
cat /etc/resolv.conf

```

And please use "bumping" after 24 hours of waiting. 
Thanks.


I just removed both ubuntu and windows and installed windows again. I will now install uubntu.

In ubuntu, should I blacklist again or directly iive you the output of these commands?

Also can you add me as a friend? Because only you can help me. Thanks.

---

### Post by retskrad on 2008-12-30
> **retskrad said:**
> I just removed both ubuntu and windows and installed windows again. I will now install uubntu.

In ubuntu, should I blacklist again or directly iive you the output of these commands?

Also can you add me as a friend? Because only you can help me. Thanks.

I asked thr question here: [https://answers.launchpad.net/ubuntu/+question/55840](https://answers.launchpad.net/ubuntu/+question/55840)

And the guy "arman" told me some instructions thatn I didint understand really.. do you know what he said?

> hi retskrad,

I read your problem and i thought may be i can help u. I m not sure but may be i can help u becoz i was also facing the same problem of network a few months back in ubuntu 7.04 as u r facing right now.

But now i have successfully installed my network. :)

Actually i have same lan cards as u r having on ur machine but a different modem. And ur problem is exactly the same as was mine. You are having 2 differents lan cards 1) onboard lan card (which should be known as eth0 in ur machine) 2) realtek lan card(which should be known as eth1 in ur machine).

Actually the problem with your ubuntu is that your ubuntu is not recognizing your 2nd lancard i.e. eth1 or realtek lancard.

When i was facing this problem i installed ubuntu twice to make it right. If your ubuntu detects your lan card correctly then your problem will be over in minutes.

**Or u can make another try, Just switch your ethernet cable which is plugged into the realtek lancard(eth1) to the other lancard i.e. onboard lancard(eth0) and just configure it. Enter all the information required in the lancard i.e. if u r using static ip then u need to specify ur IP, subnet mask, gateway and DNS servers etc...**

and configure ur modem also correctly.

I told u this becoz ur ubuntu detects your onboard lancard i.e. eth0. As u can see ur entry of that file(/etc/network/interfaces). There is only two interfaces one is lo and other is eth0 but there is no eth1.

And after this your internet should work perfectly fine. And after that if u want to use realtek lancard then u can reinstall ubuntu or if there is anyother way that u know, u can use that way.

Best of luck. :)

---

### Post by retskrad on 2008-12-30
> retskrad u said that u have 2 network cards/lancards i.e.1) Your Network Card (on motherboard) 2) Realtek TL8139/810x Family Fast

I told u that your Network Card (on motherboard) is eth0 and Realtek RTL8139/810x Family Fast is eth1.

I m assuming that u have connected your modem with eth1 i.e. Realtek RTL8139/810x Family Fast. And i m saying that connect your modem to eth0 i.e. your Network Card (on motherboard).

And then make neccessary entries in the network card such as your ip, subnet mask, gateway, DNS servers etc...

And then have fun with your internet. :)

Lol, I'm really not good with computers... I didint udnerstand.

---

### Post by albinootje on 2008-12-30
For the first time I read in your postings/comments that you have an onboard card and another NIC in your computer.
That makes thing a bit different, and explains some things.
Just hang on for a while. Back in about one hour or less than one hour :| :)

---

### Post by retskrad on 2008-12-30
> **albinootje said:**
> For the first time I read in your postings/comments that you have an onboard card and another NIC in your computer.
That makes thing a bit different, and explains some things.
Just hang on for a while. Back in about one hour or less than one hour :| :)

Thanks manm Ill stay here,:):popcorn:

---

### Post by albinootje on 2008-12-30
> **retskrad said:**
> Thanks manm Ill stay here,:):popcorn:

Hello again.
I need to go out soonish again unfortunately, will be back late at night.

A few suggestions for now.
Please find out how to put your modem or router into a NAT mode, where it gives you a local ip-address instead of direct connection to the internet.

And try also with the network-cable in your other NIC, now that you've temporarily blacklisted one kernel module for your two NICs.

---

### Post by retskrad on 2008-12-30
> **albinootje said:**
> Hello again.
I need to go out soonish again unfortunately, will be back late at night.

A few suggestions for now.
Please find out how to put your modem or router into a NAT mode, where it gives you a local ip-address instead of direct connection to the internet.

And try also with the network-cable in your other NIC, now that you've temporarily blacklisted one kernel module for your two NICs.

I did a fresh install. I removed Uubntua nfd windows and installed both again. Internet isnt working, still lol. And no, I haven't blacklisted it, I amde a fresh install. Will it make a difference?

---

### Post by albinootje on 2008-12-30
> **retskrad said:**
> I did a fresh install. I removed Uubntua nfd windows and installed both again. Internet isnt working, still lol. And no, I haven't blacklisted it, I amde a fresh install. Will it make a difference?

(I've got a little more time unexpectedly)

Does the onboard network card work in your machine in MS-Windows ?
If so, is it possible for you to take the other network card out of the machine ?

Can you put your modem or router in the simple bridged mode ?
Having it like you have now makes it theoretically more vulnerable to attacks from the outside unless you always run a firewall in Linux and Windows.

Is there anyone else in your area which can help you with the modem/router settings ?
Does your ISP have a support page with instructions ?

---

### Post by kyphi on 2008-12-30
If your internet connection has worked in the past then I would check the cable connection first.  Where the cable is plugged into the back of the computer there should be a small indicator light.  The modem will also show a light for that connection.  If there is no indicator light then the cable has developed a fault and will have to be replaced.
Motherboards come with an ethernet connection that in some cases just does not work and a separate ethernet card is needed to successfully connect to the internet.

Make sure that the cable is plugged into the card and not the motherboard connection.

---

### Post by retskrad on 2008-12-30
> **kyphi said:**
> If your internet connection has worked in the past then I would check the cable connection first.  Where the cable is plugged into the back of the computer there should be a small indicator light.  The modem will also show a light for that connection.  If there is no indicator light then the cable has developed a fault and will have to be replaced.
Motherboards come with an ethernet connection that in some cases just does not work and a separate ethernet card is needed to successfully connect to the internet.

Make sure that the cable is plugged into the card and not the motherboard connection.

When I dualboot Ubuntu internet isntr working. When I dualboot windows ( the same computer), internet works.

Also, a couple of wereks ago internet worked while dualbooting uubntu (same computer).

Its very strange. When I login to ubuntu, only 3 lights are glowing.

---

### Post by retskrad on 2008-12-30
> **albinootje said:**
> (I've got a little more time unexpectedly)

Does the onboard network card work in your machine in MS-Windows ?
If so, is it possible for you to take the other network card out of the machine ?

Can you put your modem or router in the simple bridged mode ?
Having it like you have now makes it theoretically more vulnerable to attacks from the outside unless you always run a firewall in Linux and Windows.

Is there anyone else in your area which can help you with the modem/router settings ?
Does your ISP have a support page with instructions ?

Yes, dualbooting windows, internet works, but not dualbooting uubntu. (same computer).

Whats ISP?

---

### Post by albinootje on 2008-12-30
> **retskrad said:**
> Yes, dualbooting windows, internet works, but not dualbooting uubntu. (same computer).

Sorry to hear that it's still not working :(
> 
Whats ISP?

Internet Service Provider, the company that delivers your internet-connection.

What happens when you plug the network-cable in the other network-card ?
Are the leds on your modem/router showing a connection or not ?

---

### Post by retskrad on 2008-12-30
When you say network cable, you mean the ethernet one? the ethernet cable is a white cable that is connected to the PC, thats the only write from the modem that connects the ocmputer.

Also, thansk for staying around this long time. I really appreciate it,

My ISP is named Comhem. I'll try to look at their homepage.

---

### Post by albinootje on 2008-12-30
> **retskrad said:**
> When you say network cable, you mean the ethernet one? the ethernet cable is a white cable that is connected to the PC, thats the only write from the modem that connects the ocmputer.

With network cable I mean the ethernet cable which goes from your computer to your modem.
Can you put that cable in the other network card slot of your computer and check whether the LEDs on your modem work as it should ?
> 
Also, thansk for staying around this long time. I really appreciate it,

You're welcome.
> 
My ISP is named Comhem. I'll try to look at their homepage.

Good! :)

---

### Post by retskrad on 2008-12-30
> **albinootje said:**
> With network cable I mean the ethernet cable which goes from your computer to your modem.
Can you put that cable in the other network card slot of your computer and check whether the LEDs on your modem work as it should ?

You're welcome.


Good! :)

As far as I know, the etneret cable, the white one, could only fit into the ethernet whole on the abck of the pc, above it is another hole, I believe its from the usb cable, from the modem, but I adont have that usb cable connected , I dont even ahve it...

---

### Post by albinootje on 2008-12-30
> **retskrad said:**
> As far as I know, the etneret cable, the white one, could only fit into the ethernet whole on the abck of the pc, above it is another hole, I believe its from the usb cable, from the modem, but I adont have that usb cable connected , I dont even ahve it...

Okay, can you please post the output of the following :
```

sudo lshw -c network
lspci
ifconfig -a

```
Thanks in advance.

---

### Post by retskrad on 2008-12-30
here it is:

> ubuntu@ubuntu:~$ sudo lshw -c network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: c
bus info: pci@0000:02:0c.0
logical name: eth0
version: 10
serial: 00:11:09:6c:cd:5e
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 4e:c9:60:1a:d5:2d
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by retskrad on 2008-12-30
here it is:

> ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
01:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

---

### Post by albinootje on 2008-12-30
> **retskrad said:**
> here it is:

Okay, thanks! So, you have only one network card in your computer, that should be clear now.

> 
ubuntu@ubuntu:~$ sudo lshw -c network
WARNING: you should run this program as super-user.

(This is quite strange.
If you run "lshw" without sudo, then it should give this error.
But if you run "sudo lshw" then it should *not* give this error.)

Can you download this in your Windows :
("save as")
[http://apt.wicd.net/pool/extras/w/wicd/wicd_1.5.6_all.deb](http://apt.wicd.net/pool/extras/w/wicd/wicd_1.5.6_all.deb)
And then boot Ubuntu again.
Remove Network Manager :
```

sudo apt-get remove --purge network-manager

```
Browse in the Windows-partition.
And install the wicd_1.5.6_all.deb by double-clicking on it.

---

### Post by retskrad on 2008-12-30
Thanks again laddie.

here is another one.

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:09:6c:cd:5e  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13536 (13.5 KB)  TX bytes:13536 (13.5 KB)

pan0      Link encap:Ethernet  HWaddr 6e:6b:38:48:20:b0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ubuntu@ubuntu:~$ 




and here is sudo :

> ubuntu@ubuntu:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 10
       serial: 00:11:09:6c:cd:5e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6e:6b:38:48:20:b0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ubuntu@ubuntu:~$ 



---

### Post by abn91c on 2008-12-30
did you ever try using the usb cable from the modem to the computer to connect that way?

---

### Post by retskrad on 2008-12-30
I don't have that cable. I don't need t connect to the nternet. I can connect to internet when dualbooting windows, but when duabooting ubuntu, it desnt work, so I dont need the usb to connect.

---

### Post by abn91c on 2008-12-30
> **retskrad said:**
> I don't have that cable. I don't need t connect to the nternet. I can connect to internet when dualbooting windows, but when duabooting ubuntu, it desnt work, so I dont need the usb to connect.
do you have other peripherals attached to the PC when booting to ubuntu, like a USB printer, camera, MP3 player? just in case its giving you and IRQ conflict in ubuntu. If so then disconnect them when rebooting, judst leave the essentials like the mouse keyboard and of course cable modem

---

### Post by retskrad on 2008-12-30
I only have a usb and its the mouse that is connected,

---

### Post by albinootje on 2008-12-30
retskrad, you've installed wicd now, can you start it ?

-> Applications -> Internet -> Wicd Network Manager

---

### Post by retskrad on 2008-12-30
Ah now I know what you mean with wicd, wait I'll dualboot uubntu again and see what it is in wicd.

---

### Post by albinootje on 2008-12-30
> 
Also one more thing. A guy at launhpad said:

Quote:

At last we know that there is only one ethernet card: Realtek RTL-8139/8139C/8139C+. The 8139 is indeed the most widely used chip but there are a number of versions.

The most plausible explanation that I can offer is that Windows is set to disable the ethernet connection on shutdown and the Linux kernel cannot turn it back on.

So, try this:
In Windows, right click on My Computer, left click on Manage, left click on Device Manager and locate the entry for Network Adapters. Open the Realtek RTL-8139 entry with a double click and open the Power Management tab. Uncheck "Allow the computer to turn off this device to save power".

Boot back into Ubuntu. 


Very good! 
I've read about this before, and this could be *the* solution to your problem (apart from possible irq-conflicts).

Please try this suggestion.

TTYL.

---

### Post by retskrad on 2008-12-30
I did, and it didint work. Maybe its because of the removal of network manager, and the new network program you sent me, something like wcid? 

I'll try to reinstall windows xp and ubuntu. When I install windows xp, I will chosoe the option homenetwork, not the option connect directly connect to the computer, I'm right, the the new network program you told me to install only reads network internet?

---

### Post by retskrad on 2008-12-30
I will try to install again, man it will take 2 hours!

---

### Post by retskrad on 2008-12-30
bump

---

### Post by kyphi on 2008-12-30
What a pity that my suggestion (on Launchpad) did not work.  I have the same ethernet card and my connection worked immediately without any intervention from me - absolutely nothing to configure.  That was true in both 6.06 and the current installation of 8.04.1.

If you reinstall, the default network manager will be installed which works fine.

I also use a dual boot system with several other operating systems running in VirtualBox - all have internet access (except for Windows where it is turned off).

I hope that re-installation of the two operating systems will solve this issue for you.

---

### Post by retskrad on 2008-12-30
I will now reinstall it.

---

### Post by retskrad on 2008-12-30
But befre, I have tried serveral times to reinstall, still no internet.

---

### Post by retskrad on 2008-12-30
bump

---

### Post by kyphi on 2008-12-30
I just realised that you already had reinstalled so nothing will really be gained by doing it again unless you are going to do things differently.

Why did you choose to use a network for your internet connection?  I use "Direct".

I think that the solution is with either your modem or your connection via a network.

---

### Post by retskrad on 2008-12-30
I will reinstall and choose home network, because this time I coosed direct.. maybe thats the cause? wicd, the new network manager that the guy on this thread told me, looks like only seems a  home network connection. I will reinstall windows and choose home network.. home that makes a difference...

---

### Post by retskrad on 2008-12-30
Also, when installing only ubuntu on my harddrive, no windows, how can you choose from the install, if you want direct or home network, like windows offers that option during install? I can't see one in ubuntu install...

---

### Post by kyphi on 2008-12-30
I have been trawling the net to check on your modem (Webstar EPX-2203).  It is a cable modem from a company that does not support Linux.  I found no solutions for getting this modem to work in Linux.

You might like to consider replacing the modem not only with one that works in Linux but also with a modem/router unit which will work with VoIP, for example.

I use Billion router/modems but there are others.

---

### Post by retskrad on 2008-12-31
> **kyphi said:**
> I have been trawling the net to check on your modem (Webstar EPX-2203).  It is a cable modem from a company that does not support Linux.  I found no solutions for getting this modem to work in Linux.

You might like to consider replacing the modem not only with one that works in Linux but also with a modem/router unit which will work with VoIP, for example.

I use Billion router/modems but there are others.

what are yout talking about? weeks ago, when I installed ubuntu, internet worked. Now suddenly it doesnt...

---

### Post by kyphi on 2008-12-31
It seems that all the efforts I have made to find a solution for you have been to no avail.

Perhaps another will solve this puzzle.

---

### Post by retskrad on 2008-12-31
So you'll just give up? ;)

---

### Post by Sealbhach on 2008-12-31
> A couple of weeks ago internet worked while dual booting ubuntu. Now when i do that, internet doesn't work.

What change, if any, did you make to your system? If it worked then it should work now.:confused: Perhaps it was a kernel update that broke things?


.

---

### Post by retskrad on 2008-12-31
I don't have a clue, I'm not that good with computers network. Although, when I dualboot windows, same computer, same modem, internet works...

---

### Post by albandy on 2008-12-31
Let's try to force a 10 Mbit connection.
On Linux try this:

sudo mii-tool eth0 -F 10BaseT-FD
sudo dhclient eth0

---

### Post by retskrad on 2008-12-31
Should I use the default network maanger or wicd ?

---

### Post by albinootje on 2008-12-31
> **albandy said:**
> Let's try to force a 10 Mbit connection.
On Linux try this:

sudo mii-tool eth0 -F 10BaseT-FD
sudo dhclient eth0

retskrad, can you try it ?

And ethtool which you mentioned, you can find here  :
[http://packages.ubuntu.com/search?keywords=ethtool](http://packages.ubuntu.com/search?keywords=ethtool)

Good luck!

---

### Post by retskrad on 2008-12-31
I'm using 8.10, what is its codename?

---

### Post by retskrad on 2008-12-31
Ok, one more question before I dualboot ubuntu.

1. Write in these commands into the terminal:

> sudo apt-get install ethtool
sudo ethtool -r eth0




2. then write in these:

> 
sudo mii-tool eth0 -F 10BaseT-FD
sudo dhclient eth0

3. then install one of these:

> [http://packages.ubuntu.com/search?keywords=ethtool](http://packages.ubuntu.com/search?keywords=ethtool)

Am i right, in order?

---

### Post by albinootje on 2008-12-31
> **retskrad said:**
> I'm using 8.10, what is its codename?

Intrepid Ibex

---

### Post by retskrad on 2008-12-31
Yeah sorry man, forgot to google ;)

---

### Post by albinootje on 2008-12-31
You probably have the ethtool package on your installation cdrom.
The name is ethtool_6+20080227-1_i386.deb

This is the url you would need in case you want download it to your Windows-partition : [http://nl.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_6+20080227-1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_6+20080227-1_i386.deb)

(You do use the 32 bit Ubuntu installation I assume)

---

### Post by albinootje on 2008-12-31
> **retskrad said:**
> 
Am i right, in order?

The order doesn't matter here.

---

### Post by retskrad on 2008-12-31
Ah ok, thanks, I'll dualboot now.

---

### Post by retskrad on 2008-12-31
Ah ok, thanks, I'll dualboot now.

---

### Post by retskrad on 2008-12-31
Here it si:

> admin2@ubuntu:~$ sudo ethtool -r eth0
Cannot restart autonegotiation: Invalid argument
admin2@ubuntu:~$ sudo mii-tool eth0 -F 10BaseT-FD
admin2@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:09:6c:cd:5e
Sending on   LPF/eth0/00:11:09:6c:cd:5e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
admin2@ubuntu:~$ 



I wrote in these commands in the terminal while having wcid installed instead of the defaul network manager.

---

### Post by albinootje on 2008-12-31
> **retskrad said:**
>  I wrote in these commands in the terminal while having wcid installed instead of the defaul network manager.

Okay, can you post the output of 
```

ifconfig -a

```
to see whether the 10 Mbit change is really active ?

---

### Post by albinootje on 2008-12-31
> **retskrad said:**
> 
admin2@ubuntu:~$ sudo ethtool -r eth0
Cannot restart autonegotiation: Invalid argument

Could be interesting to find out whether this error message is unusual or not for that type of network-card.

---

### Post by retskrad on 2008-12-31
> **albinootje said:**
> Could be interesting to find out whether this error message is unusual or not for that type of network-card.

Is it bad to get that error?

Here it is:

> Ok, here it is:

[QUOTE]admin2@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:09:6c:cd:5e  
          inet6 addr: fe80::211:9ff:fe6c:cd5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

eth0:avahi Link encap:Ethernet  HWaddr 00:11:09:6c:cd:5e  
          inet addr:169.254.6.114  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17776 (17.7 KB)  TX bytes:17776 (17.7 KB)

pan0      Link encap:Ethernet  HWaddr 76:b9:15:1b:d1:76  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

admin2@ubuntu:~$ 

[/QUOTE]

---

### Post by albinootje on 2008-12-31
Okay, please try the following :
```

sudo ethtool -s eth0 autoneg off
sudo ethtool -s eth0 duplex half
sudo ethtool -s eth0 speed 10
sudo dhclient

```

---

### Post by retskrad on 2008-12-31
Aight, thanks you man. it's like only you are loyal to me at this present. Thanks ;).

---

### Post by retskrad on 2008-12-31
Here it is:

> admin2@ubuntu:~$ sudo ethtool -s eth0 autoneg off
[sudo] password for admin2: 
admin2@ubuntu:~$ sudo ethtool -s eth0 duplex half
admin2@ubuntu:~$ sudo ethtool -s eth0 speed 10
admin2@ubuntu:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 5125
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/22:6a:3e:ea:bb:5f
Sending on   LPF/pan0/22:6a:3e:ea:bb:5f
Listening on LPF/eth0/00:11:09:6c:cd:5e
Sending on   LPF/eth0/00:11:09:6c:cd:5e
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
admin2@ubuntu:~$ 



---

### Post by albinootje on 2008-12-31
> **retskrad said:**
> Aight, thanks you man. it's like only you are loyal to me at this present. Thanks ;).

:| Hmmm, well, I'm about to recommend you to run Ubuntu in VirtualBox on MS-Windows on your machine. 
And I already offered you a 3Com network-card via postal mail, that's still an option too, you'll need a free PCI slot in your machine for that.

---

### Post by retskrad on 2008-12-31
here it is:

Here it is:

> admin2@ubuntu:~$ sudo ethtool -s eth0 autoneg off
[sudo] password for admin2: 
admin2@ubuntu:~$ sudo ethtool -s eth0 duplex half
admin2@ubuntu:~$ sudo ethtool -s eth0 speed 10
admin2@ubuntu:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 5125
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/22:6a:3e:ea:bb:5f
Sending on   LPF/pan0/22:6a:3e:ea:bb:5f
Listening on LPF/eth0/00:11:09:6c:cd:5e
Sending on   LPF/eth0/00:11:09:6c:cd:5e
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
admin2@ubuntu:~$ 



how come a couple of weeks ago it worked but now it doesnt?

I can't run it in virtualbox.. I have 760mb RAM, 76gb HDD, ATI Radeon x1650 and intel celeron 2.93ghz..

---

### Post by albinootje on 2008-12-31
> **retskrad said:**
>  how come a couple of weeks ago it worked but now it doesnt?

Good question.
Did you also have 8.10 installed a few weeks ago ?
Or was it 8.04 ?
> 
I can't run it in virtualbox.. I have 760mb RAM, 76gb HDD, ATI Radeon x1650 and intel celeron 2.93ghz..

You should be able to easily run Ubuntu in VirtualBox with that.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by retskrad on 2008-12-31
I haved been running it but its slow. Also, I tried to install both uubntu 8.04 yester day and ubuntu 8.10 (as I have now) still no internet.

did you see the latest output of the commands you told me a couple of minutes agin?

---

### Post by albandy on 2008-12-31
It's a modem problem, I've been searching and I found users with the same problem, they solved it adding this lines to /etc/sysctl.conf
so do:
sudo gedit /etc/sysctl.conf
and add the following lines:

net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
net.ipv4.tcp_no_metrics_save = 1
net.core.net dev_max_backlog = 2500
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_window_scaling = 1

then save and type
sudo sysctl -p

reboot your modem and your computer.

---

### Post by retskrad on 2008-12-31
Will it cause an error if I removed the default network manager than came with uubntu the first install and install wicd, the netwoprk manager? because I have that now...

Also, when you say reboot, you mean reset or hat? Remove the outlet or what? Pleas be specefic.

---

### Post by albandy on 2008-12-31
Simply unpower you modem and power it again
reboot the computer with the reboot command
sudo reboot

---

### Post by albinootje on 2008-12-31
> **albandy said:**
> It's a modem problem, I've been searching and I found users with the same problem, they solved it adding this lines to /etc/sysctl.conf

Interesting, can you give a source where that information came from ?
TIA.

---

### Post by albinootje on 2008-12-31
> **retskrad said:**
> Will it cause an error if I removed the default network manager than came with uubntu the first install and install wicd, the netwoprk manager? because I have that now...


Perhaps you didn't configure wicd yet, but you can try, as always, with :
```

sudo dhclient

```

---

### Post by retskrad on 2008-12-31
Sorry man, if I turn out to be very dumb lol;). But when I write in those commands you said to me, then I unplug this wire:

After the commands, am I suppose to unplug that and plug it in, then restart the computer into ubuntu? Sorry man, there are many power wires...

---

### Post by albinootje on 2008-12-31
> **retskrad said:**
> Sorry man, if I turn out to be very dumb lol;). But when I write in those commands you said to me, then I unplug this wire:

After the commands, am I suppose to unplug that and plug it in, then restart the computer into ubuntu? Sorry man, there are many power wires...

Perhaps it's easier to find the manual for your modem ? :D
That black cable looks like the power cable indeed.
Power-cables are very often at the edge of a device.

---

### Post by albandy on 2008-12-31
> **albinootje said:**
> Interesting, can you give a source where that information came from ?
TIA.

Yes: [http://text.broadbandreports.com/forum/r20097965-help-Linux-DHCP-cant-get-an-IP-with-new-Sci-Atlanta-Cablemo](http://text.broadbandreports.com/forum/r20097965-help-Linux-DHCP-cant-get-an-IP-with-new-Sci-Atlanta-Cablemo)

---

### Post by albandy on 2008-12-31
> **retskrad said:**
> Sorry man, if I turn out to be very dumb lol;). But when I write in those commands you said to me, then I unplug this wire:

After the commands, am I suppose to unplug that and plug it in, then restart the computer into ubuntu? Sorry man, there are many power wires...

The black one.

---

### Post by retskrad on 2008-12-31
I did what you told me, wrote down the lins you told me to do.I rebooted the modem and the computer. And I don't have internet, still. Maybe its the cause of the removal of the defaul network mangaer, I removed it and downloaded wicd..

Although, when I didn't reoobt with "sudo reboot", I just cliked on restart computer.. wil it make a difference?

---

### Post by albandy on 2008-12-31
there's no diference, I'm continuoulsy using the console so is the way I reboot it.

---

### Post by albinootje on 2008-12-31
> **retskrad said:**
> I did what you told me, wrote down the lins you told me to do.

Just to be sure, can you post the output of the following please :
```

cat /etc/sysctl.conf
sudo mii-tool eth0
dmesg|tail -n 30

```

---

### Post by retskrad on 2008-12-31
What is there to do? it didint work.. :(

---

### Post by albinootje on 2008-12-31
> **retskrad said:**
> What is there to do? it didint work.. :(

Please let us try to help you, and post the output of this :
```

cat /etc/sysctl.conf
sudo mii-tool eth0
ifconfig -v
dmesg

```

Thanks in advance.

---

### Post by retskrad on 2008-12-31
Wait, I'll dualboot ubuntu.

---

### Post by retskrad on 2008-12-31
Here it is:

> **admin2@ubuntu:~$ sudo cat /etc/sysctl.conf**
[sudo] password for admin2:
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

################################################## ############3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling ([http://lkml.org/lkml/2008/2/5/167](http://lkml.org/lkml/2008/2/5/167)),
# and is not recommended.
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


################################################## #################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
# The contents of /proc/<pid>/maps and smaps files are only visible to
# readers that are allowed to ptrace() the process
# sys.kernel.maps_protect = 1
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
net.ipv4.tcp_no_metrics_save = 1
net.core.net dev_max_backlog = 2500
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_window_scaling = 1
**admin2@ubuntu:~$ sudo mii-tool eth0**
eth0: link ok
**admin2@ubuntu:~$ dmesg|tail -n 30**
[ 178.817662] type=1503 audit(1230753754.114:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5138 profile="/usr/sbin/cupsd"
[ 189.021610] eth0: no IPv6 routers present
[ 189.873668] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[ 189.873676] eth0: Tx queue start entry 4 dirty entry 0.
[ 189.873681] eth0: Tx descriptor 0 is 000820d3. (queue head)
[ 189.873684] eth0: Tx descriptor 1 is 000820df.
[ 189.873688] eth0: Tx descriptor 2 is 000820a7.
[ 189.873691] eth0: Tx descriptor 3 is 0008205a.
[ 189.873709] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 201.875223] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[ 201.875237] eth0: Tx queue start entry 4 dirty entry 0.
[ 201.875241] eth0: Tx descriptor 0 is 00082058. (queue head)
[ 201.875245] eth0: Tx descriptor 1 is 0008204e.
[ 201.875248] eth0: Tx descriptor 2 is 00082046.
[ 201.875251] eth0: Tx descriptor 3 is 000820c0.
[ 201.875270] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 213.874888] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[ 213.874897] eth0: Tx queue start entry 4 dirty entry 0.
[ 213.874902] eth0: Tx descriptor 0 is 00082069. (queue head)
[ 213.874906] eth0: Tx descriptor 1 is 000820c0.
[ 213.874909] eth0: Tx descriptor 2 is 000820c0.
[ 213.874912] eth0: Tx descriptor 3 is 00082069.
[ 213.874930] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 225.875516] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[ 225.875524] eth0: Tx queue start entry 4 dirty entry 0.
[ 225.875529] eth0: Tx descriptor 0 is 000820b4. (queue head)
[ 225.875533] eth0: Tx descriptor 1 is 000820b4.
[ 225.875536] eth0: Tx descriptor 2 is 00082046.
[ 225.875539] eth0: Tx descriptor 3 is 000820b4.
[ 225.875557] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[    0.030289] ACPI: Unable to load the System Description Tables
[    0.030479] ExtINT not setup in hardware but reported by MP table
[    0.030556] ENABLING IO-APIC IRQs
[    0.030746] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[    0.070453] CPU0: Intel(R) Celeron(R) CPU 2.93GHz stepping 04
[    0.176136] Brought up 1 CPUs
[    0.176141] Total of 1 processors activated (5865.58 BogoMIPS).
[    0.176164] CPU0 attaching sched-domain:
[    0.176168]  domain 0: span 0 level CPU
[    0.176171]   groups: 0
[    0.176580] net_namespace: 840 bytes
[    0.176596] Booting paravirtualized kernel on bare hardware
[    0.176855] Time: 21:08:46  Date: 12/31/08
[    0.176897] NET: Registered protocol family 16
[    0.177551] EISA bus registered
[    0.205339] PCI: PCI BIOS revision 2.10 entry at 0xfbc60, last bus=2
[    0.205344] PCI: Using configuration type 1 for base access
[    0.207179] ACPI: Interpreter disabled.
[    0.207185] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.207262] pnp: PnP ACPI: disabled
[    0.207270] PnPBIOS: Scanning system for PnP BIOS support...
[    0.207302] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc660
[    0.207306] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc690, dseg 0xf0000
[    0.208743] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[    0.209493] PCI: Probing PCI hardware
[    0.209499] PCI: Probing PCI hardware (bus 00)
[    0.209623] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, e3ffffff]
[    0.209769] PCI: 0000:00:1d.0 reg 20 io port: [b800, b81f]
[    0.209824] PCI: 0000:00:1d.1 reg 20 io port: [b000, b01f]
[    0.209878] PCI: 0000:00:1d.2 reg 20 io port: [b400, b41f]
[    0.209937] PCI: 0000:00:1d.7 reg 10 32bit mmio: [e8000000, e80003ff]
[    0.209989] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.209995] pci 0000:00:1d.7: PME# disabled
[    0.210036] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.210037] * this clock source is slow. If you are sure your timer does not have
[    0.210039] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.210082] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.210090] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.210094] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.210115] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.210123] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.210130] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.210138] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.210145] PCI: 0000:00:1f.1 reg 20 io port: [f000, f00f]
[    0.210152] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.210204] PCI: 0000:00:1f.3 reg 20 io port: [500, 51f]
[    0.210249] PCI: 0000:00:1f.5 reg 10 io port: [c000, c0ff]
[    0.210256] PCI: 0000:00:1f.5 reg 14 io port: [c400, c43f]
[    0.210263] PCI: 0000:00:1f.5 reg 18 32bit mmio: [e8001000, e80011ff]
[    0.210270] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [e8002000, e80020ff]
[    0.210299] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.210304] pci 0000:00:1f.5: PME# disabled
[    0.210358] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.210365] PCI: 0000:01:00.0 reg 14 io port: [9000, 90ff]
[    0.210372] PCI: 0000:01:00.0 reg 18 32bit mmio: [e5000000, e500ffff]
[    0.210393] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.210414] pci 0000:01:00.0: supports D1
[    0.210416] pci 0000:01:00.0: supports D2
[    0.210445] PCI: 0000:01:00.1 reg 10 32bit mmio: [e5010000, e501ffff]
[    0.210488] pci 0000:01:00.1: supports D1
[    0.210490] pci 0000:01:00.1: supports D2
[    0.210531] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    0.210535] PCI: bridge 0000:00:01.0 32bit mmio: [e4000000, e5ffffff]
[    0.210540] PCI: bridge 0000:00:01.0 32bit mmio pref: [d0000000, dfffffff]
[    0.210593] PCI: 0000:02:0c.0 reg 10 io port: [a000, a0ff]
[    0.210601] PCI: 0000:02:0c.0 reg 14 32bit mmio: [e7000000, e70000ff]
[    0.210627] PCI: 0000:02:0c.0 reg 30 32bit mmio: [0, ffff]
[    0.210642] pci 0000:02:0c.0: supports D1
[    0.210644] pci 0000:02:0c.0: supports D2
[    0.210646] pci 0000:02:0c.0: PME# supported from D1 D2 D3hot D3cold
[    0.210651] pci 0000:02:0c.0: PME# disabled
[    0.210681] PCI: 0000:02:0d.0 reg 10 32bit mmio: [e7001000, e70017ff]
[    0.210689] PCI: 0000:02:0d.0 reg 14 io port: [a400, a47f]
[    0.210728] pci 0000:02:0d.0: supports D2
[    0.210730] pci 0000:02:0d.0: PME# supported from D2 D3hot D3cold
[    0.210735] pci 0000:02:0d.0: PME# disabled
[    0.210759] pci 0000:00:1e.0: transparent bridge
[    0.210764] PCI: bridge 0000:00:1e.0 io port: [a000, afff]
[    0.210769] PCI: bridge 0000:00:1e.0 32bit mmio: [e6000000, e7ffffff]
[    0.212302] pci 0000:00:1f.0: PIIX/ICH IRQ router [8086/24c0]
[    0.212324] pci 0000:00:1d.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.212330] pci 0000:00:1d.1: PCI->APIC IRQ transform: INT B -> IRQ 19
[    0.212334] pci 0000:00:1d.2: PCI->APIC IRQ transform: INT C -> IRQ 18
[    0.212339] pci 0000:00:1d.7: PCI->APIC IRQ transform: INT D -> IRQ 23
[    0.212347] pci 0000:00:1f.1: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.212352] pci 0000:00:1f.3: PCI->APIC IRQ transform: INT B -> IRQ 17
[    0.212356] pci 0000:00:1f.5: PCI->APIC IRQ transform: INT B -> IRQ 17
[    0.212361] pci 0000:01:00.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.212367] pci 0000:02:0c.0: PCI->APIC IRQ transform: INT A -> IRQ 23
[    0.212372] pci 0000:02:0d.0: PCI->APIC IRQ transform: INT A -> IRQ 23
[    0.212575] NET: Registered protocol family 8
[    0.212575] NET: Registered protocol family 20
[    0.212575] NetLabel: Initializing
[    0.212575] NetLabel:  domain hash size = 128
[    0.212575] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.212575] NetLabel:  unlabeled traffic allowed by default
[    0.212575] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.212575]    actual entries 65620
[    0.212688] AppArmor: AppArmor Filesystem Enabled
[    0.212728] system 00:08: iomem range 0x0-0x9ffff could not be reserved
[    0.212734] system 00:08: iomem range 0xffb00000-0xffb7ffff could not be reserved
[    0.212737] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.212741] system 00:08: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.212744] system 00:08: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.212748] system 00:08: iomem range 0x100000-0xffffff could not be reserved
[    0.212756] system 00:09: iomem range 0xf0000-0xf3fff could not be reserved
[    0.212759] system 00:09: iomem range 0xf4000-0xf7fff could not be reserved
[    0.212762] system 00:09: iomem range 0xf8000-0xfffff could not be reserved
[    0.212765] system 00:09: iomem range 0xd0000-0xd3fff has been reserved
[    0.213872] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.213879] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.213885] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe5ffffff
[    0.213890] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.213898] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.213903] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
[    0.213909] pci 0000:00:1e.0:   MEM window: 0xe6000000-0xe7ffffff
[    0.213914] pci 0000:00:1e.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
[    0.213935] pci 0000:00:1e.0: setting latency timer to 64
[    0.213940] bus: 00 index 0 io port: [0, ffff]
[    0.213942] bus: 00 index 1 mmio: [0, ffffffff]
[    0.213945] bus: 01 index 0 io port: [9000, 9fff]
[    0.213947] bus: 01 index 1 mmio: [e4000000, e5ffffff]
[    0.213950] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.213952] bus: 01 index 3 mmio: [0, 0]
[    0.213955] bus: 02 index 0 io port: [a000, afff]
[    0.213957] bus: 02 index 1 mmio: [e6000000, e7ffffff]
[    0.213960] bus: 02 index 2 mmio: [40000000, 400fffff]
[    0.213962] bus: 02 index 3 io port: [0, ffff]
[    0.213964] bus: 02 index 4 mmio: [0, ffffffff]
[    0.213983] NET: Registered protocol family 2
[    0.214038] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.214038] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.216656] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.217330] TCP: Hash tables configured (established 131072 bind 65536)
[    0.217336] TCP reno registered
[    0.217566] NET: Registered protocol family 1
[    0.217746] checking if image is initramfs... it is
[    0.946432] Freeing initrd memory: 8225k freed
[    0.947803] audit: initializing netlink socket (disabled)
[    0.947825] type=2000 audit(1230757726.944:1): initialized
[    0.953198] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.956883] VFS: Disk quotas dquot_6.5.1
[    0.957047] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.957239] msgmni has been set to 1510
[    0.957472] io scheduler noop registered
[    0.957476] io scheduler anticipatory registered
[    0.957478] io scheduler deadline registered
[    0.957506] io scheduler cfq registered (default)
[    0.957601] pci 0000:01:00.0: Boot video device
[    0.958169] isapnp: Scanning for PnP cards...
[    1.309891] isapnp: No Plug & Play device found
[    1.424348] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.424522] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.426524] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.430150] brd: module loaded
[    1.430275] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.430498] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[    1.430502] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.431192] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.432273] mice: PS/2 mouse device common for all mice
[    1.432665] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.432694] rtc0: alarms up to one day
[    1.432960] EISA: Probing bus 0 at eisa.0
[    1.433000] EISA: Detected 0 cards.
[    1.433005] cpuidle: using governor ladder
[    1.433007] cpuidle: using governor menu
[    1.433694] TCP cubic registered
[    1.433741] Using IPI No-Shortcut mode
[    1.434472] registered taskstats version 1
[    1.434585]   Magic number: 4:660:147
[    1.434642] tty ttyp1: hash matches
[    1.434733] rtc_cmos 00:03: setting system clock to 2008-12-31 21:08:47 UTC (1230757727)
[    1.434737] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.434739] EDD information not available.
[    1.435262] Freeing unused kernel memory: 424k freed
[    1.435330] Write protecting the kernel text: 2576k
[    1.435369] Write protecting the kernel read-only data: 936k
[    1.464387] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.672145] fuse init (API version 7.9)
[    1.909298] thermal: Unknown symbol acpi_processor_set_thermal_limit
[    2.244238] usbcore: registered new interface driver usbfs
[    2.244282] usbcore: registered new interface driver hub
[    2.244355] usbcore: registered new device driver usb
[    2.247359] USB Universal Host Controller Interface driver v3.0
[    2.247432] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.247438] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.247504] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.247537] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000b800
[    2.247798] usb usb1: configuration #1 chosen from 1 choice
[    2.247853] hub 1-0:1.0: USB hub found
[    2.247867] hub 1-0:1.0: 2 ports detected
[    2.348631] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.348638] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.348680] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    2.348713] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b000
[    2.348955] usb usb2: configuration #1 chosen from 1 choice
[    2.348998] hub 2-0:1.0: USB hub found
[    2.349013] hub 2-0:1.0: 2 ports detected
[    2.381973] SCSI subsystem initialized
[    2.386360] 8139too Fast Ethernet driver 0.9.28
[    2.500994] libata version 3.00 loaded.
[    2.556649] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.556656] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.556714] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    2.556749] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
[    2.557016] usb usb3: configuration #1 chosen from 1 choice
[    2.557062] hub 3-0:1.0: USB hub found
[    2.557078] hub 3-0:1.0: 2 ports detected
[    2.668222] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    2.764745] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.764752] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.764810] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    2.768746] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.768762] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe8000000
[    2.796183] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.796466] usb usb4: configuration #1 chosen from 1 choice
[    2.796510] hub 4-0:1.0: USB hub found
[    2.796528] hub 4-0:1.0: 6 ports detected
[    3.007176] eth0: RealTek RTL8139 at 0xa000, 00:11:09:6c:cd:5e, IRQ 23
[    3.007181] eth0:  Identified 8139 chip type 'RTL-8101'
[    3.061622] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[23]  MMIO=[e7001000-e70017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.072064] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.078442] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.083373] ata_piix 0000:00:1f.1: version 2.12
[    3.083442] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.084384] scsi0 : ata_piix
[    3.084559] scsi1 : ata_piix
[    3.084636] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    3.084640] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    3.192205] usb 2-1: device not accepting address 2, error -71
[    3.248594] hub 2-0:1.0: unable to enumerate USB device on port 1
[    3.256517] ata1.00: ATA-7: HDS728080PLAT20, PF2OA28A, max UDMA/100
[    3.256523] ata1.00: 156301488 sectors, multi 16: LBA48 
[    3.280461] ata1.00: configured for UDMA/100
[    3.444796] ata2.00: ATAPI: HL-DT-STDVDRRW GWA-4083B, 1.09, max UDMA/33
[    3.460747] ata2.00: configured for UDMA/33
[    3.460922] scsi 0:0:0:0: Direct-Access     ATA      HDS728080PLAT20  PF2O PQ: 0 ANSI: 5
[    3.462800] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRRW GWA-4083B 1.09 PQ: 0 ANSI: 5
[    3.591955] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    3.592071] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    3.622888] Driver 'sd' needs updating - please use bus_type methods
[    3.623042] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    3.623071] sd 0:0:0:0: [sda] Write Protect is off
[    3.623075] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.623119] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.623232] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    3.625903] sd 0:0:0:0: [sda] Write Protect is off
[    3.625909] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.625997] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.626006]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    3.636379]  sda1
[    3.636557] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.648373] sr0: scsi3-mmc drive: 24x/40x writer cd/rw xa/form2 cdda tray
[    3.648381] Uniform CD-ROM driver Revision: 3.20
[    3.648525] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.864250] usb 2-1: new low speed USB device using uhci_hcd and address 4
[    4.051357] usb 2-1: configuration #1 chosen from 1 choice
[    4.273148] loop: module loaded
[    4.300080] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    4.329790] kjournald starting.  Commit interval 5 seconds
[    4.329817] EXT3-fs: mounted filesystem with ordered data mode.
[    4.344394] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc000062f2e4]
[    4.473721] usb 3-1: configuration #1 chosen from 1 choice
[    4.477002] usbcore: registered new interface driver hiddev
[    4.489812] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
[    4.490162] input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:1d.1-1
[    4.490196] usbcore: registered new interface driver usbhid
[    4.490201] usbhid: v2.6:USB HID core driver
[    9.562638] udevd version 124 started
[   10.240399] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.288439] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.328804] iTCO_vendor_support: vendor-support=0
[   10.366186] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   10.366849] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   10.367085] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.548801] Linux agpgart interface v0.103
[   10.685385] intel_rng: FWH not detected
[   10.712887] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   10.722140] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   11.285484] usbcore: registered new interface driver libusual
[   11.388967] Initializing USB Mass Storage driver...
[   11.396430] scsi2 : SCSI emulation for USB Mass Storage devices
[   11.396765] usbcore: registered new interface driver usb-storage
[   11.396809] USB Mass Storage support registered.
[   11.396817] usb-storage: device found at 2
[   11.396820] usb-storage: waiting for device to settle before scanning
[   11.402243] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   11.708222] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   12.028741] intel8x0_measure_ac97_clock: measured 53615 usecs
[   12.028746] intel8x0: clocking to 48000
[   14.719430] parport_pc 00:0f: reported by Plug and Play BIOS
[   14.719543] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   14.817569] lp0: using parport0 (interrupt-driven).
[   15.695244] EXT3 FS on loop0, internal journal
[   16.398667] usb-storage: device scan complete
[   16.401642] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   16.404637] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   16.407636] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   16.410634] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   16.464794] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   16.465083] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   16.510802] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[   16.511050] sd 2:0:0:1: Attached scsi generic sg3 type 0
[   16.556782] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[   16.557078] sd 2:0:0:2: Attached scsi generic sg4 type 0
[   16.602791] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   16.603049] sd 2:0:0:3: Attached scsi generic sg5 type 0
[   33.421791] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   33.619376] type=1505 audit(1230754160.181:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3832
[   33.832540] type=1505 audit(1230754160.393:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3837
[   33.832940] type=1505 audit(1230754160.393:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3837
[   33.975701] ip_tables: (C) 2000-2006 Netfilter Core Team
[   34.752343] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   34.752496] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   34.753103] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   34.753338] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   35.635519] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   35.699110] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   35.955727] ppdev: user-space parallel port driver
[   38.142468] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   39.043765] Bluetooth: Core ver 2.13
[   39.046316] NET: Registered protocol family 31
[   39.046324] Bluetooth: HCI device and connection manager initialized
[   39.046329] Bluetooth: HCI socket layer initialized
[   39.066575] Bluetooth: L2CAP ver 2.11
[   39.066586] Bluetooth: L2CAP socket layer initialized
[   39.083810] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   39.083820] Bluetooth: BNEP filters: protocol multicast
[   39.140137] Bridge firewalling registered
[   39.142960] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   39.156152] Bluetooth: RFCOMM socket layer initialized
[   39.156503] Bluetooth: RFCOMM TTY layer initialized
[   39.156514] Bluetooth: RFCOMM ver 1.10
[   39.158797] Bluetooth: SCO (Voice Link) ver 0.6
[   39.158806] Bluetooth: SCO socket layer initialized
[   40.422427] [drm] Initialized drm 1.1.0 20060810
[   40.507032] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   40.686403] NET: Registered protocol family 17
[   40.710725] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   41.035582] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   41.035623] agpgart-intel 0000:00:00.0: putting AGP V2 device into 1x mode
[   41.035660] pci 0000:01:00.0: putting AGP V2 device into 1x mode
[   41.098601] [drm] Setting GART location based on new memory map
[   41.098617] [drm] Can't use AGP base @0xe0000000, won't fit
[   41.098624] [drm] Loading R500 Microcode
[   41.098683] [drm] Num pipes: 1
[   41.098692] [drm] writeback test succeeded in 1 usecs
[   88.844908] ------------[ cut here ]------------
[   88.844920] WARNING: at /build/buildd/linux-2.6.27/net/sched/sch_generic.c:219 dev_watchdog+0x21a/0x230()
[   88.844923] NETDEV WATCHDOG: eth0 (8139too): transmit timed out
[   88.844926] Modules linked in: af_packet radeon drm binfmt_misc sco rfcomm bridge stp bnep l2cap bluetooth ppdev apm speedstep_lib cpufreq_conservative cpufreq_ondemand cpufreq_powersave cpufreq_stats freq_table cpufreq_userspace iptable_filter ip_tables x_tables sbp2 parport_pc lp parport snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm evdev pcspkr snd_seq_dummy usb_storage libusual snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device intel_agp snd soundcore snd_page_alloc agpgart iTCO_wdt iTCO_vendor_support shpchp pci_hotplug ext3 jbd mbcache loop usbhid hid sr_mod cdrom sd_mod crc_t10dif sg ata_piix pata_acpi 8139cp ata_generic ohci1394 libata ieee1394 8139too mii scsi_mod dock ehci_hcd uhci_hcd usbcore fbcon tileblit font bitblit softcursor fuse
[   88.845003] Pid: 0, comm: swapper Not tainted 2.6.27-7-generic #1
[   88.845008]  [<c0131d65>] warn_slowpath+0x65/0x90
[   88.845022]  [<f0890fa9>] ? usb_hcd_submit_urb+0x79/0x180 [usbcore]
[   88.845050]  [<f089138f>] ? usb_submit_urb+0xff/0x260 [usbcore]
[   88.845070]  [<f097a682>] ? hid_irq_in+0x72/0x1c0 [usbhid]
[   88.845082]  [<f0891684>] ? usb_unanchor_urb+0x14/0xb0 [usbcore]
[   88.845102]  [<f0891586>] ? usb_free_urb+0x16/0x20 [usbcore]
[   88.845122]  [<f088fe7e>] ? usb_hcd_giveback_urb+0x5e/0xd0 [usbcore]
[   88.845139]  [<c037e61d>] ? _spin_lock+0xd/0x10
[   88.845146]  [<c0154387>] ? timer_stats_update_stats+0x17/0x250
[   88.845152]  [<c0254299>] ? strlen+0x9/0x20
[   88.845158]  [<c025231d>] ? strlcpy+0x1d/0x60
[   88.845162]  [<c02f0967>] ? netdev_drivername+0x37/0x40
[   88.845167]  [<c0305b6a>] dev_watchdog+0x21a/0x230
[   88.845173]  [<c02fb0c0>] ? neigh_table_init_no_netlink+0x150/0x1e0
[   88.845179]  [<c02fa870>] ? neigh_periodic_timer+0x0/0x190
[   88.845184]  [<c013ca1f>] ? mod_timer+0x3f/0x80
[   88.845189]  [<c02fa996>] ? neigh_periodic_timer+0x126/0x190
[   88.845194]  [<c013bf88>] run_timer_softirq+0x138/0x210
[   88.845199]  [<c0305950>] ? dev_watchdog+0x0/0x230
[   88.845204]  [<c0305950>] ? dev_watchdog+0x0/0x230
[   88.845209]  [<c0137682>] __do_softirq+0x92/0x120
[   88.845213]  [<c013776d>] do_softirq+0x5d/0x60
[   88.845217]  [<c01378e5>] irq_exit+0x55/0x90
[   88.845221]  [<c0113f8d>] smp_apic_timer_interrupt+0x5d/0x90
[   88.845228]  [<c01050f8>] apic_timer_interrupt+0x28/0x30
[   88.845233]  [<c010acca>] ? mwait_idle+0x4a/0x50
[   88.845238]  [<c010288d>] cpu_idle+0x7d/0x140
[   88.845242]  [<c036edc3>] rest_init+0x53/0x60
[   88.845248]  =======================
[   88.845251] ---[ end trace 5d409854a38e7c31 ]---
[   91.845077] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   91.845086] eth0: Tx queue start entry 4  dirty entry 0.
[   91.845091] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   91.845095] eth0:  Tx descriptor 1 is 00082156.
[   91.845098] eth0:  Tx descriptor 2 is 00082156.
[   91.845101] eth0:  Tx descriptor 3 is 00082156.
[   91.845119] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  115.846391] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  115.846400] eth0: Tx queue start entry 4  dirty entry 0.
[  115.846404] eth0:  Tx descriptor 0 is 00082156. (queue head)
[  115.846408] eth0:  Tx descriptor 1 is 0008203c.
[  115.846411] eth0:  Tx descriptor 2 is 0008203c.
[  115.846415] eth0:  Tx descriptor 3 is 0008203c.
[  115.846432] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  127.847051] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  127.847060] eth0: Tx queue start entry 4  dirty entry 0.
[  127.847064] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[  127.847068] eth0:  Tx descriptor 1 is 0008203c.
[  127.847071] eth0:  Tx descriptor 2 is 000820f1.
[  127.847075] eth0:  Tx descriptor 3 is 0008209b.
[  127.847092] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  139.847712] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  139.847721] eth0: Tx queue start entry 4  dirty entry 0.
[  139.847725] eth0:  Tx descriptor 0 is 000820f1. (queue head)
[  139.847729] eth0:  Tx descriptor 1 is 000820f1.
[  139.847732] eth0:  Tx descriptor 2 is 000820df.
[  139.847735] eth0:  Tx descriptor 3 is 0008209b.
[  139.847753] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  149.900572] ppdev0: registered pardevice
[  149.948694] ppdev0: unregistered pardevice
[  150.000406] ppdev0: registered pardevice
[  150.048273] ppdev0: unregistered pardevice
[  151.559005] ppdev0: registered pardevice
[  151.608672] ppdev0: unregistered pardevice
[  151.872694] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  151.872705] eth0: Tx queue start entry 4  dirty entry 0.
[  151.872710] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[  151.872714] eth0:  Tx descriptor 1 is 0008203c.
[  151.872717] eth0:  Tx descriptor 2 is 000820df.
[  151.872720] eth0:  Tx descriptor 3 is 000820d3.
[  151.872738] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  152.006989] type=1503 audit(1230754278.567:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5154/net/" pid=5154 profile="/usr/sbin/cupsd"
[  153.101915] type=1503 audit(1230754279.663:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5173/net/" pid=5173 profile="/usr/sbin/cupsd"
[  153.240774] NET: Registered protocol family 10
[  153.242328] lo: Disabled Privacy Extensions
[  153.244935] type=1503 audit(1230754279.807:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5173 profile="/usr/sbin/cupsd"
[  153.244951] type=1503 audit(1230754279.807:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5173 profile="/usr/sbin/cupsd"
[  153.244959] type=1503 audit(1230754279.807:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5173 profile="/usr/sbin/cupsd"
[  153.244967] type=1503 audit(1230754279.807:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5173 profile="/usr/sbin/cupsd"
[  153.244974] type=1503 audit(1230754279.807:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5173 profile="/usr/sbin/cupsd"
[  153.244982] type=1503 audit(1230754279.807:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5173 profile="/usr/sbin/cupsd"
[  153.244989] type=1503 audit(1230754279.807:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5173 profile="/usr/sbin/cupsd"
[  153.244997] type=1503 audit(1230754279.807:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5173 profile="/usr/sbin/cupsd"
[  163.609003] eth0: no IPv6 routers present
[  163.873034] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  163.873043] eth0: Tx queue start entry 4  dirty entry 0.
[  163.873047] eth0:  Tx descriptor 0 is 000820df. (queue head)
[  163.873051] eth0:  Tx descriptor 1 is 000820a7.
[  163.873054] eth0:  Tx descriptor 2 is 0008205a.
[  163.873057] eth0:  Tx descriptor 3 is 00082058.
[  163.873075] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  175.874563] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  175.874577] eth0: Tx queue start entry 4  dirty entry 0.
[  175.874582] eth0:  Tx descriptor 0 is 0008204e. (queue head)
[  175.874585] eth0:  Tx descriptor 1 is 00082046.
[  175.874589] eth0:  Tx descriptor 2 is 000820c0.
[  175.874592] eth0:  Tx descriptor 3 is 00082069.
[  175.874609] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
admin2@ubuntu:~$ 



---

### Post by albinootje on 2008-12-31
> **retskrad said:**
> Here it is:
```

[ 88.845238] [<c010288d>] cpu_idle+0x7d/0x140
[ 88.845242] [<c036edc3>] rest_init+0x53/0x60
[ 88.845248] =======================
[ 88.845251] ---[ end trace 5d409854a38e7c31 ]---
[ 91.845077] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[ 91.845086] eth0: Tx queue start entry 4 dirty entry 0.
[ 91.845091] eth0: Tx descriptor 0 is 00082156. (queue head)
[ 91.845095] eth0: Tx descriptor 1 is 00082156.
[ 91.845098] eth0: Tx descriptor 2 is 00082156.
[ 91.845101] eth0: Tx descriptor 3 is 00082156.
[ 91.845119] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 115.846391] eth0: Transmit timeout, status 0d 0000 c07f media 10.

```


Thank you very much!
This is very useful information to know.

Can you post this output (the long dmesg output in your last comment) as attachment in your answers.launchpad.net thread too ?

Will be back in a while.

---

### Post by retskrad on 2008-12-31
Done. ;)

---

### Post by albinootje on 2008-12-31
> **retskrad said:**
> Done. ;)

Thanks.

I just found this :

[http://forums.fedoraforum.org/showthread.php?p=872197](http://forums.fedoraforum.org/showthread.php?p=872197)

comment #8 
> 
After booting Knoppix, Ubuntu and Mandriva live CDs and noticing that none of them seemed to be able to wake up and use the Realtek interface (although they all detected it and reported it as present and working), I decided that Windows must have caused the problem! I went back to Hardware manager in Windows and rolled back the Realtek driver from the latest update to the previous one circa 2003. Bingo, when I restarted the computer with Linux the eth0 was back and working. Watching the network LAN lights on my router I can see that the new Windows driver turns off the data stream (lights go out), while the old one does NOT. Linux drivers do not seem to able to wake up the slumbering NIC from its Windows induced coma, while XP has no problems.


---

### Post by albinootje on 2008-12-31
Here's another posting with a similar problem : 

[http://ubuntuforums.org/archive/index.php/t-925252.html](http://ubuntuforums.org/archive/index.php/t-925252.html)

> 
Solved! Adding "irqpoll" to the boot options, as was suggested in kern.log got it working properly. I don't know what irqpoll does but eh, it works!


---

### Post by albinootje on 2008-12-31
And here's another similar problem, with a different solution :

[http://howtoxyz.blogspot.com/2008/07/netdev-watchdog-eth0-transmit-timed-out.html](http://howtoxyz.blogspot.com/2008/07/netdev-watchdog-eth0-transmit-timed-out.html)

> 
This was due to the interrupt conflict that occured between the acpi and network modules.
I turned off acpi while booting by adding following words at the end of the boot option.


acpi=off as kernel boot parameter

---

### Post by retskrad on 2008-12-31
Thanks for finding them... don't know what I should do right now, :(

---

### Post by albinootje on 2008-12-31
[http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue](http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue)

---

### Post by retskrad on 2008-12-31
Done! I changeed it to enable.

So now, I'm suppose to fully shut the computer down?

---

### Post by albinootje on 2008-12-31
> **retskrad said:**
> Done! I changeed it to enable.

Excellent!
> 
So now, I'm suppose to fully shut the computer down?

Yes, please, pull the power cord completely from the back of the computer.

---

### Post by retskrad on 2008-12-31
I will not shut down.

---

### Post by albinootje on 2008-12-31
> **albinootje said:**
> [http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue](http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue)
> 
 In Windows XP (example)
 Right click my computer
 --> Hardware tab
   --> Device Manager
     --> Network Adapters
       --> "double click" Realtek ...
         --> Advanced tab
           --> Wake-On-Lan After Shutdown
             --> Enable.


Glad that the problem is finally solved now!

Happy GNU year! :)

---

### Post by dnoyeb on 2009-01-08
So did that fix it?  It really didnt seem sleep since the logs were showing the 100mb link up.

If not the next thing I would try is to assign the Ip address manually.

---

### Post by albinootje on 2009-01-08
> **dnoyeb said:**
> So did that fix it?  It really didnt seem sleep since the logs were showing the 100mb link up.

If not the next thing I would try is to assign the Ip address manually.

It did fix it for the OP. 
The OP did send me a personal message about it.

---

