---
title: "installation  cisco  vpnclient"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by balki2005 on 2006-08-25
Hello,

I try  to  install   cisco vpnclient  but  I  recieve this  error:
balki@thunderbird:~/Programs/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.6.02 (0030) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.15-26-686/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-26-686/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.15-26-686/build" will be used to build th e module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.15-26-686/build SUBDIRS=/home/balki/Programs/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-686'
  CC [M]  /home/balki/Programs/vpnclient/linuxcniapi.o
/home/balki/Programs/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/balki/Programs/vpnclient/linuxcniapi.c:312: error: ‘struct sk_buff’ has no  member named ‘stamp’
/home/balki/Programs/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/balki/Programs/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no  member named ‘stamp’
make[2]: *** [/home/balki/Programs/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/balki/Programs/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-686'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


do  somebody known what's going wrong  ?

thanks  in advance,

balki2005

---

### Post by apjone on 2006-08-25
hey dude, where did you get the client from ? I having been lookin for a vpn client for ages

---

### Post by sinuhe14 on 2006-08-27
Hi,

I'm receiving the same error and would also appreciate help on this. Also running Ubunt Dapper. This is wehere I downloaded my client: [http://www.tilburguniversity.nl/services/its/software/downloads/cisco-vpn-clients.html](http://www.tilburguniversity.nl/services/its/software/downloads/cisco-vpn-clients.html)

Cheers,

Sinuhe

---

### Post by f00buntu on 2006-08-27
Hi,

Make sure you got build essential:

sudo apt-get install build-essential

...and your kernel headers:

sudo apt-get install linux-headers-`uname -r`

then try to build the cisco vpnclient again.

Good luck,

f00

---

### Post by Ivhassel on 2006-08-27
Why don't you install vpnc from the dapper universe ?
There's even a nice GUI : kvpnc ( Qt based ).

The good news, it's perfectly compatible with the cisco program, doesn't have to be compiled, and it's free.

[I]Description: Cisco-compatible VPN client
 vpnc is a VPN client compatible with cisco3000 VPN Concentrator (also
 known as Cisco's EasyVPN equipment). vpnc runs entirely in userspace
 and does not require kernel modules except of the tun driver to
 communicate with the network layer.
 .
 It supports most of the features needed to establish connection to the
 VPN concentrator: MD5 and SHA1 hashes, 3DES and AES ciphers, PFS and
 various IKE DH group settings.[/I]

---

### Post by sinuhe14 on 2006-08-28
> **f00buntu said:**
> Hi,

Make sure you got build essential:

sudo apt-get install build-essential

f00

Thanks,

I didn't think of doning that, but when I ran apt-get I was notified that both are installed already. I also made the vpn_setup point to the kernel header location and again it gives me the same error msg.

Sinuhe

---

### Post by sinuhe14 on 2006-08-28
> **Ivhassel said:**
> Why don't you install vpnc from the dapper universe ?
There's even a nice GUI : kvpnc ( Qt based ).
[/I]

eh... good question :-)

I've just installed it... but now as soon as I want  to connect to a vpn gateway I get the following error msg:

error: Tunnel device is missing, loading module "tun" has failed: stop.

I did some googling and all I can find are pages that tell me to get myself a new kernel.... that's a bit out of my league as a noob..
Is there an easier way maybe?

Thanks,

S.

---

### Post by 2shanfernando on 2006-09-03
I've got the same issue anyone know a fix?

From what i've researched it should be apart of the kernel.

---

### Post by Psykotik on 2006-09-03
Try

sudo modprobe tun

If it works, add a line with "tun" to your /etc/modules

---

### Post by joris1977 on 2006-09-04
Hé there,

I had exactly the same problem and terminal turnout as balki2005 when i was trying to install the vpn client that was offered on the website of my university, the Uva in Amsterdam. I wanted to install this vpnclient to have acces to the online library, see also my earlier post : [http://www.ubuntuforums.org/showthread.php?t=21054&page=7](http://www.ubuntuforums.org/showthread.php?t=21054&page=7)

I had no succes with vpnc but finally solved the issue. The Cisco-vpnclient the university is offering and you are trying to install is outdated (Version 4.6.02) and will not work in dapper. You need Version 4.8. You can download it from the university of Gent. Follow this link: [http://helpdesk.ugent.be/ugentnet/en/vpnakkoord.php](http://helpdesk.ugent.be/ugentnet/en/vpnakkoord.php)  

Then follow Hemps step by step guide on installing a cisco vpn client  

For All you Cisco Client Users out there, here is a Step by Step guide on how to install it on Ubuntu 5.04 (works for dapper) 


1. Mine was a fersh install
2. Place your latest Cisco Client in your home directory.
3. Do a
Code:

sudo apt-get install build-essential


4. Do a
Code:

sudo apt-get install gcc


5. Do a uname -r to find the correct kernel-headers for your build.
6. Use synaptic to search and install the correct kernel-HEADERS, not source.
7. Untar your Cisco Client, go to the vpnclient folder and do a
Code:

sudo sh vpn_install


8. Answer all questions, the defaults worked for me.
9. make sure you start the vpn sub-system with
Code:

sudo /etc/init.d/vpnclient_init start


10. Copy your .pcf profile to the
Code:

sudo cp <your .pcf> /etc/opt/cisco-vpnclient/Profiles

.
11. Do a vpnclient connect <your profile> (without the .pcf extention)
12. Hope this helps.

Hemps 

To be found on this link: [http://www.ubuntuforums.org/showthread.php?t=21054&page=3](http://www.ubuntuforums.org/showthread.php?t=21054&page=3)

Hope it will work out

grts

Joris

---

### Post by Blues- on 2006-09-04
> **apjone said:**
> hey dude, where did you get the client from ? I having been lookin for a vpn client for ages

I got mine from here real.com :) => [http://realvpn.real.com/]("http://realvpn.real.com/")

Cheers,
Blues-

---

### Post by Shakaboom on 2008-06-06
I've succeeded to install Uva VPN on Hardy Heron. It turns out to be the easiest thing in the world.

here's a small how to for the complete noob (i am quite noob myself in linux)

go to System>Administration>Synaptic.

Search vpnc

Tick boxes "network-manager-vpnc" and "vpnc" (KDE tool is optional)

Click on network icon in panel>vpn connections>configure vpn

Click Add

Fill in (tab "Required):
Connection name = uva vpn (i think you can name it whatever you want)
Gateway = vpn.uva.nl
Group Name is ipsec

Fill in (tab "Optional")
Tick box "override user name
Set user name to your student ID

Apply!

Click on network icon>vpn connections>uva vpn

password is your normal login password for uva network
group password is ipsec

Enjoy!!

---

