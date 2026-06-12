---
title: "vpnclient installation problems"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by YQ002lc2 on 2009-08-27
Hi Friends,

               I ran the following commands:

cd /home/jpinson/Desktop
ls
tar xzvf vpnclient-linux-4.6.00.0045-k9.tar.gz
cd vpnclient
sudo ./vpn_install

               This is what I got:

Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.28-15-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.28-15-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.28-15-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/jpinson/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/jpinson/Desktop/vpnclient/linuxcniapi.o
/home/jpinson/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
In file included from /home/jpinson/Desktop/vpnclient/Cniapi.h:15,
                 from /home/jpinson/Desktop/vpnclient/linuxcniapi.c:34:
/home/jpinson/Desktop/vpnclient/GenDefs.h:114: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
/home/jpinson/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/jpinson/Desktop/vpnclient/linuxcniapi.c:315: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/jpinson/Desktop/vpnclient/linuxcniapi.c:347: error: ‘struct sk_buff’ has no member named ‘nh’
/home/jpinson/Desktop/vpnclient/linuxcniapi.c:348: error: ‘struct sk_buff’ has no member named ‘mac’
/home/jpinson/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/jpinson/Desktop/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/jpinson/Desktop/vpnclient/linuxcniapi.c:456: error: ‘struct sk_buff’ has no member named ‘mac’
/home/jpinson/Desktop/vpnclient/linuxcniapi.c:457: error: ‘struct sk_buff’ has no member named ‘nh’
/home/jpinson/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘h’
/home/jpinson/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/jpinson/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/jpinson/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".



Please help!  Thanks, jpinson

---

### Post by Partyboi2 on 2009-08-28
Hi, open a terminal and install the linux headers, if you have not already got them installed.[FONT=monospace]
[/FONT]```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by YQ002lc2 on 2009-08-28
Thank you Partyboi2, but when I run that code, nothing changes. It says 0 upgraded. 

This is exactly what it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.28-15-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  python-alsaaudio libconvert-binhex-perl libtext-bidi-perl krita-data
  libsoap-lite-perl kword-data libemail-find-perl koshell kivio-data
  libclass-methodmaker-perl libxml-perl python-pygame libhtml-fromtext-perl
  python-kaa-base libhttp-response-encoding-perl libregexp-common-perl
  kthesaurus kpresenter krita libexporter-lite-perl koffice-data
  libarchive-zip-perl libossp-uuid-perl libmime-tools-perl kugar
  libxml-libxslt-perl xmltv-util libossp-uuid15 libnet-domain-tld-perl
  python-beautifulsoup xulrunner-1.9-dom-inspector libxml-dom-perl
  python-kaa-metadata ruby libmikmod2 liblog-tracemessages-perl
  libio-stringy-perl libhtml-tableextract-perl python-xml lsdvd libnet-ip-perl
  libhttp-server-simple-perl libnet-dns-perl kword libdate-manip-perl
  libhttp-cache-transparent-perl libwww-mechanize-perl python-sqlite
  libfile-slurp-perl liblingua-preferred-perl libsdl-mixer1.2 kchart karbon
  libfcgi-perl libunicode-string-perl libxml-writer-perl libemail-address-perl
  kspread libpoppler-qt2 python-kaa-imlib2 kplato libxml-regexp-perl
  libdigest-hmac-perl libemail-valid-perl kivio koffice-libs libwv2-1c2 kexi
  libxmltv-perl libpqxx-2.6.9ldbl libterm-progressbar-perl kpresenter-data
  xpdf-common libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks,

jpinson

---

### Post by Partyboi2 on 2009-08-28
You may need to apply a patch see [[COLOR=Blue]here[/COLOR]]("http://geeksdatabase.blogspot.com/2008/08/installing-cisco-vpn-client-on-ubuntu.html").
You can also install the one in the Ubuntu repos, which is a lot easier to install with
```
sudo apt-get install vpnc
```

---

### Post by YQ002lc2 on 2009-08-28
By the way, I ran the: 

sudo apt-get autoremove

I'm attaching my bash history in case it helps. 
I'm particularly concerned about the following command I ran:

sudo ln -s 2.6.28-15-generic linux

Thanks for anyone's help!

jpinson

---

### Post by YQ002lc2 on 2009-08-28
Thank you again partyboi2,

I following the instructions on the link you gave me with the patch and everything. 

I still get the following error after sudo ./vpn_install:

Making module
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/jpinson/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/jpinson/Desktop/vpnclient/linuxcniapi.o
In file included from /home/jpinson/Desktop/vpnclient/Cniapi.h:15,
                 from /home/jpinson/Desktop/vpnclient/linuxcniapi.c:31:
/home/jpinson/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/jpinson/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/jpinson/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

---

### Post by forgewire on 2009-08-29
> **Partyboi2 said:**
> You may need to apply a patch see [[COLOR=Blue]here[/COLOR]]("http://geeksdatabase.blogspot.com/2008/08/installing-cisco-vpn-client-on-ubuntu.html").
You can also install the one in the Ubuntu repos, which is a lot easier to install with
```
sudo apt-get install vpnc
```

The one in Ubuntu repos (vpnc) is VPN client compatible with cisco3000 VPN Concentrator. Its not the original one from cisco.
The one I want to install is cisco vpn client 4.8.01.0640.

And when I try I've got:
Making module
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/demon/Downloads/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/demon/Downloads/vpnclient/linuxcniapi.o
In file included from /home/demon/Downloads/vpnclient/Cniapi.h:15,
                 from /home/demon/Downloads/vpnclient/linuxcniapi.c:31:
/home/demon/Downloads/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/demon/Downloads/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/demon/Downloads/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

I tried [http://tuxx-home.at/archives/2007/05/29/T16_34_26/](http://tuxx-home.at/archives/2007/05/29/T16_34_26/)
and [http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/)
but never manage to instal it on Ubuntu 2.6.28-15

---

### Post by Partyboi2 on 2009-08-29
Try using a later version and seeing if that works.
[http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.02/](http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.02/)

---

### Post by YQ002lc2 on 2009-08-31
I've given up on trying to install this way. 
I ended up installing KVpnc from the synaptic package manager and used my school's instructions to get the actual VPN information. 

I am still interested if anyone can solve this problem though. 

Thanks,

jpinson

---

