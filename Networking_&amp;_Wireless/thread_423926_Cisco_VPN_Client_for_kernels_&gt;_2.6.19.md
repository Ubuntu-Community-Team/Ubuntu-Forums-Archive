---
title: "Cisco VPN Client for kernels &gt; 2.6.19"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by etola on 2007-04-26
Hello everyone, 

With the changes in the kernel headers, VPN Client does not compile as it is. I searched around a bit and managed to get it working, Here is the changes you have to do:

in interceptor.c

  - replace

```
     #include <linux/config.h> 
```
    with
```
    
     #if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,19)
     #include <linux/autoconf.h>
     #define CHECKSUM_HW CHECKSUM_COMPLETE
     #define skb_checksum_help(a,b) skb_checksum_help((a))
     #else
     #include <linux/config.h>
     #define skb_checksum_help(a,b) skb_checksum_help((a),(b))
     #endif

```

 - and at every other place where you have 
```

#include <linux/config.h>

```   

 replace it with

 ```
    
     #if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,19)
     #include <linux/autoconf.h>
     #else
     #include <linux/config.h>
     #endif

```


the error messages before these changes were: 

```

interceptor.c:11:26: error: linux/config.h: No such file or directory

In function ‘recv_ip_packet_handler’:
..vpnclient/interceptor.c:555: error: ‘CHECKSUM_HW’ undeclared (first use in this function)

in function ‘recv_ip_packet_handler’:
../vpnclient/interceptor.c:561: error: too many arguments to function ‘skb_checksum_help’

```

---

### Post by silverbullet007 on 2007-04-26
I just downloaded the 4.8 client from Cisco yesterday.  It actually compiled/installed perfectly for me.  And I'm using a fiesty upgrade on kernel 2.6.20-15-generic.  But now even after trying the "Magic Bit" fix, I still get

>  vpnclient connect work
             privsep: unable to drop privileges: group set failed

To which I havent yet found a solution.



Sorry didnt mean to hijak there, what ver of the client are you wanting to use?

---

### Post by etola on 2007-04-26
> **silverbullet007 said:**
> 
Sorry didnt mean to hijak there, what ver of the client are you wanting to use?

My school distributes a pre-configured client and  it is of version 4.6. 

That's why I'm doing all these hoop-jumpings. Maybe I should download the latest one and configure it myself ;)

---

### Post by Zeffel on 2007-04-30
I did the changes you suggested, but got error messages like "LINUX_VERSION_CODE not defined" and "KERNEL_VERSION not defined".
So I removed the if-conditions, so for example interceptor.c starts like this:
```

//#include <linux/config.h>
#include <linux/autoconf.h>
#define CHECKSUM_HW CHECKSUM_COMPLETE
#define skb_checksum_help(a,b) skb_checksum_help((a))

```

But I got more error messages:

```

Shutting down /opt/cisco-vpnclient/bin/vpnclient: module cisco_ipsec is not running.
Stopped: /etc/init.d/vpnclient_init (VPN init script)
Making module
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/tim/vpnclient modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/tim/vpnclient/interceptor.o
In file included from /home/tim/vpnclient/interceptor.c:19:
include/linux/netdevice.h:988:49: error: macro "skb_checksum_help" requires 2 arguments, but only 1 given
/home/tim/vpnclient/interceptor.c: In Funktion »handle_vpnup«:
/home/tim/vpnclient/interceptor.c:313: Warnung: Zuweisung von inkompatiblem Zeigertyp
/home/tim/vpnclient/interceptor.c:337: Warnung: Zuweisung von inkompatiblem Zeigertyp
/home/tim/vpnclient/interceptor.c:338: Warnung: Zuweisung von inkompatiblem Zeigertyp
/home/tim/vpnclient/interceptor.c: In Funktion »do_cleanup«:
/home/tim/vpnclient/interceptor.c:381: Warnung: Zuweisung von inkompatiblem Zeigertyp
/home/tim/vpnclient/interceptor.c: In Funktion »recv_ip_packet_handler«:
/home/tim/vpnclient/interceptor.c:560: Fehler: gerufenes Objekt »skb_checksum_help« ist keine Funktion
/home/tim/vpnclient/interceptor.c: In Funktion »do_cni_send«:
/home/tim/vpnclient/interceptor.c:686: Fehler: gerufenes Objekt »skb_checksum_help« ist keine Funktion
make[2]: *** [/home/tim/vpnclient/interceptor.o] Fehler 1
make[1]: *** [_module_/home/tim/vpnclient] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Fehler 2
Failed to make module "cisco_ipsec.ko".

```

Removing the "#define skb_checksum_help(a,b) skb_checksum_help((a))" produces other errors.

Does anyone know how to fix this?

---

### Post by Zeffel on 2007-04-30
I forgot:
```
home/tim/vpnclient/interceptor.c:560: Fehler: gerufenes Objekt »skb_checksum_help« ist keine Funktion
```
means
```
home/tim/vpnclient/interceptor.c:560: error: called object »skb_checksum_help« is not a function
```
(I've installed the German version of Ubuntu ;) )

---

### Post by etola on 2007-04-30
You should also add 

```
 #define skb_checksum_help(a,b) skb_checksum_help((a))
```

part. The error is related to this one. 

They changed the interface in the kernel headers. so ... try it with this.

---

### Post by etola on 2007-04-30
as for the missing LINUX_VERSION_CODE part. I have no idea why you haven't got them.

---

### Post by BrowneR on 2007-04-30
i get the following errors when trying to compile the kernel module.

looks like a different issue but wondered if you could help me out with it:

```

root@chris-laptop:~/cisco vpnclient# ./driver_build.sh /usr/src/linux/
make -C /usr/src/linux/ SUBDIRS=/home/chris/cisco vpnclient modules
make[1]: Entering directory `/usr/src/linux-2.6.20.6'
make[1]: *** No rule to make target `vpnclient'. Stop.
make[1]: Leaving directory `/usr/src/linux-2.6.20.6'
make: *** [default] Error 2

```

cheers

---

### Post by BrowneR on 2007-04-30
ok so that issue was related to having a space in the current directory's name. fixed that and now i'm getting errors similar to Zeffel.

```

make -C /lib/modules/2.6.20.6/build SUBDIRS=/home/chris/cisco modules
make[1]: Entering directory `/usr/src/linux-2.6.20.6'
  CC [M]  /home/chris/cisco/interceptor.o
In file included from /home/chris/cisco/interceptor.c:25:
include/linux/netdevice.h:987:49: error: macro "skb_checksum_help" requires 2 arguments, but only 1 given
/home/chris/cisco/interceptor.c: In function &#8216;handle_vpnup&#8217;:
/home/chris/cisco/interceptor.c:318: warning: assignment from incompatible pointer type
/home/chris/cisco/interceptor.c:342: warning: assignment from incompatible pointer type
/home/chris/cisco/interceptor.c:343: warning: assignment from incompatible pointer type
/home/chris/cisco/interceptor.c: In function &#8216;do_cleanup&#8217;:
/home/chris/cisco/interceptor.c:386: warning: assignment from incompatible pointer type
/home/chris/cisco/interceptor.c: In function &#8216;recv_ip_packet_handler&#8217;:
/home/chris/cisco/interceptor.c:565: error: called object &#8216;skb_checksum_help&#8217; is not a function
/home/chris/cisco/interceptor.c: In function &#8216;do_cni_send&#8217;:
/home/chris/cisco/interceptor.c:691: error: called object &#8216;skb_checksum_help&#8217; is not a function
make[2]: *** [/home/chris/cisco/interceptor.o] Error 1
make[1]: *** [_module_/home/chris/cisco] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.20.6'
make: *** [default] Error 2

```

i have added ```
#define skb_checksum_help(a,b) skb_checksum_help((a))
``` to interceptor.c as you suggest but the problem remains.
do i only need to add that line to interceptor.c?

---

### Post by BrowneR on 2007-04-30
ok got it sorted!

let me refer you to [this]("http://tuxx-home.at/archives/2007/04/10/T15_55_43/") guide. I also found a copy of vpnclient 4.8 [here]("http://www.uni-konstanz.de/RZ/wlan/ipsec/software/cisco-vpnclient-4.8/")

after applying the patch provided everything works fine.

---

### Post by etola on 2007-04-30
I'm glad that you solved your problem.


from the error message it looks like you've also had the older version of this macro in netdevice.h file. This file should have been updated for kernels bigger than 2.6.19. I don't know why you have the old version though. Just to make the matter clear, what is your kernel version ?

---

### Post by BrowneR on 2007-04-30
i'm running 2.6.20.6 vanilla

---

### Post by Zeffel on 2007-05-02
Well, I'm using vpnc now instead of the cisco client. With its GUI KVpnc it's even more comfortable than the Cisco client.
Vpnc and KVpnc are included in the Ubuntu repositories!

---

### Post by myrandomstuff on 2007-05-04
Hello to all, I ran the patch and all, but still no joy. 

Any help would be appreciated, Thanks in advance


Here is what I have for this:

root@unbunny7:/home/david/Documents/web cisco vpn 4.8/vpnclient-FILES/vpnclient# ls
cisco_cert_mgr   GenDefs.h              libvpnapi.so      Makefile         vpnclient.ini
Cniapi.h         interceptor.c          license.rtf       mtu.h            vpnclient_init
config.h         IPSecDrvOSFunctions.h  license.txt       sample.pcf       vpn_install
cvpnd            IPSecDrvOS_linux.c     linuxcniapi.c     unixcniapi.h     vpn_ioctl_linux.h
driver_build.sh  IPSecDrvOS_linux.h     linuxcniapi.h     unixkernelapi.h  vpn_uninstall
frag.c           ipseclog               linuxkernelapi.c  vpnapi.h
frag.h           libdriver.so           linux_os.h        vpnclient
root@unbunny7:/home/david/Documents/web cisco vpn 4.8/vpnclient-FILES/vpnclient# ls
cisco_cert_mgr   IPSecDrvOSFunctions.h  linuxcniapi.h     vpnclient
Cniapi.h         IPSecDrvOS_linux.c     linuxkernelapi.c  vpnclient.ini
config.h         IPSecDrvOS_linux.h     linux_os.h        vpnclient_init
cvpnd            ipseclog               Makefile          vpnclient-linux-2.6.19+-rev1.diff
driver_build.sh  libdriver.so           mtu.h             vpn_install
frag.c           libvpnapi.so           sample.pcf        vpn_ioctl_linux.h
frag.h           license.rtf            unixcniapi.h      vpn_uninstall
GenDefs.h        license.txt            unixkernelapi.h
interceptor.c    linuxcniapi.c          vpnapi.h
root@unbunny7:/home/david/Documents/web cisco vpn 4.8/vpnclient-FILES/vpnclient# patch <../vpnclient-linux-2.6.19+-rev1.diff
bash: ../vpnclient-linux-2.6.19+-rev1.diff: No such file or directory
root@unbunny7:/home/david/Documents/web cisco vpn 4.8/vpnclient-FILES/vpnclient# patch <../vpnclient-linux-2.6.19+-rev1.diff
patching file IPSecDrvOS_linux.c
patching file frag.c
patching file interceptor.c
patching file linuxcniapi.c
root@unbunny7:/home/david/Documents/web cisco vpn 4.8/vpnclient-FILES/vpnclient# su
root@unbunny7:/home/david/Documents/web cisco vpn 4.8/vpnclient-FILES/vpnclient# ./vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.20-15-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.20-15-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.20-15-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/david/Documents/web cisco vpn 4.8/vpnclient-FILES/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** No rule to make target `cisco'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
root@unbunny7:/home/david/Documents/web cisco vpn 4.8/vpnclient-FILES/vpnclient#

---

### Post by etola on 2007-05-04
of the top of my head, do not use spaces in folder names and try again

---

### Post by nick1 on 2007-05-08
Cisco REALLY needs to fix the code in their VPN client so that users don't have to apply patches or edit configuration files just to establish a VPN connection.  ggrrr
I'm not sure if one already exists, but I would like to see a GUI for the Cisco VPN client, such as the Windows GUI version.
Also, I think Ubuntu should start including a default VPN client.

Well I finally got my Cisco VPN client working on Ubuntu 7.04 Feisty Fawn.  It took me waaay too much time to get it working but I did document the process I used and would like to share it with everyone.

These instructions describe how to install the Cisco VPN Linux client version vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz on Ubuntu 7.04 Feisty Fawn.

1.) Untar the VPN Client
	```
tar xzf vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz
```

2.) Download the patch.  Place the patch into the vpnclient directory.
	```
wget -q http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.19+-rev1.diff
```

3.) Change to the vpnclient directory.
	```
cd vpnclient
```

4.) Apply the patch.
	```
patch < vpnclient-linux-2.6.19+-rev1.diff
```

	the following will be outputted:
		patching file IPSecDrvOS_linux.c
		patching file frag.c
		patching file interceptor.c
		patching file linuxcniapi.c

	4.1) Now the patch has been applied and you can safely install the client
		```
./vpn_install
```

	4.2) When the installation asks for the location of the Kernel source, type:
		```
/usr/src/linux-headers-<results of uname &#8211;r command>
```
		Replace <results of uname &#8211;r command> with the results returned by issuing the following command in a different console window:
```
uname &#8211;r
```
		The result of uname &#8211;r will look something like 2.6.20-15-generic

	4.3) After the installation is complete, read what the three *&#8217;s say at the end of the installation
 Before you can start the vpnclient you need to issue:
		```
Sudo /etc/init.d/vpnclient_init start
```
	The system will probably complain that it could not find the working directory but after 	you enter your password the command will find the correct directory and successfully 	execute the command.

5.) Place your profile files (.pcf) into:
	/etc/opt/cisco-vpnclient/Profiles

6.) To start a VPN session:
	```
cd /opt/cisco-vpnclient/bin
```
	```
sudo vpnclient connect name_of_profile
```

Replace name_of_profile with the name of the profile you want to use for this session.
Do NOT include the file extension, for example:  name_of_profile.pcf.
Just use the name of the profile, for example: myprofile

7.) To disconnect a VPN session:
	```
cd /opt/cisco-vpnclient/bin
```
	```
sudo vpnclient disconnect
```

Additional Resources:
[http://tuxx-home.at/archives/2007/04/10/T15_55_43/](http://tuxx-home.at/archives/2007/04/10/T15_55_43/)

---

### Post by David Valentine on 2007-05-24
Thank you for your guide--I wish I'd found your post a couple of days ago!  You might consider putting this on the wiki?  Again, thanks!:KS

---

### Post by v3nd3tta7 on 2007-11-21
Thanks heaps Nick1! With Gutsy I used the updated patch 2.6.22 and it worked like a charm ;)

---

