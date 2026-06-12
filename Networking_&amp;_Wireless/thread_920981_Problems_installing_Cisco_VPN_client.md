---
title: "Problems installing Cisco VPN client"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by tuffguy45 on 2008-09-15
My school uses a VPN connection and I have the linux files but the people in tech services told me they had no idea how to use them.

these are the files they gave me

[PHP]sam@sam-laptop:~/Desktop/VPN Client linux/vpnclient$ dir
cisco_cert_mgr	 IPSecDrvOSFunctions.h	linuxcniapi.c	  vpnapi.h
Cniapi.h	 IPSecDrvOS_linux.c	linuxcniapi.h	  vpnclient
config.h	 IPSecDrvOS_linux.h	linuxkernelapi.c  vpnclient.ini
cvpnd		 ipseclog		linux_os.h	  vpnclient_init
driver_build.sh  libdriver64.so		Makefile	  vpn_install
frag.c		 libdriver.so		mtu.h		  vpn_ioctl_linux.h
frag.h		 libvpnapi.so		sample.pcf	  vpn_uninstall
GenDefs.h	 license.rtf		unixcniapi.h
interceptor.c	 license.txt		unixkernelapi.h[/PHP]

Whenever I try to use the make commands this is what I get

> sam@sam-laptop:~/Desktop/VPN Client linux/vpnclient$ make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/sam/Desktop/VPN Client linux/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `Client'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2

---

### Post by casevh on 2008-09-15
The installer is run by:

sudo sh ./vpn_install

This may or may not succeed. The latest version of the client works fine on a 32-bit system but requires a couple of patches for a 64-bit platform.

Here is a link describing the process for a 64-bit platform:

[http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/](http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/)

A Google search for "ubuntu 8.04 cisco vpn client" will provide several more useful links.

Did they give the configuration files (.pcf)? If not, you can usually copy them from a Windows box.

casevh

---

### Post by tuffguy45 on 2008-09-15
Well I'm running it on a 32 bit system so that shouldn't be a problem and, no I didn't get a .pcf file. I'm guessing its neccessary to run it but there are plenty of windows boxes to pull it off. It really kills me that they give out linux distrubutions and no one in the entire technical services department knows how to put it on a system. Yay for the ubuntu forums...

---

### Post by Crafty Kisses on 2008-09-15
Try the following:

Download vpnclient-linux-4.8.00.0490-k9.tar.gz, which you can download that VPN client right [**here**]("http://www.longren.org/files/vpnclient-linux-4.8.00.0490-k9.tar.gz"). You need to save that to your home directory.

Open a Terminal window and untar the vpnclient with the following command:
```
sudo tar xzf vpnclient-linux-4.8.00.0490-k9.tar.gz
```
This will create a new folder called vpnclient in your home directory. Leave the terminal window open, you&#8217;ll need it later. You need to download the patch, to patch your VPN client.

Once you've downloaded the patch, you need to go back to your Terminal and move the VPN client:
```
sudo cd vpnclient/
```
Once you've done that, you need to patch the VPN client, try this:
```
patch < vpnclient-linux-2.6.22.diff
```
After that we will need to compile the actual VPN client.
```
sudo ./vpn_install
```
Mark OK for everything, unless you have reason not to. The VPN Client is installed now, and you can start it by doing the following:
```
sudo /etc/init.d/vpnclient_init start
```
Also you need to place your .**pcf config files** somewhere, here's just an example:
```
/etc/opt/cisco-vpnclient/Profiles/
```
If your .pcf file is called myVPN.pcf, you&#8217;ll connect to the VPN with the following command:
```
sudo vpnclient connect myVPN
```
Then you should be ready to go, and enjoy your VPN client.

---

### Post by tuffguy45 on 2008-09-16
Well its further than I was before but I still have another error.

<code>sam@sam-laptop:~/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-19-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-19-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-19-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/sam/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/sam/vpnclient/linuxcniapi.o
In file included from /home/sam/vpnclient/Cniapi.h:15,
                 from /home/sam/vpnclient/linuxcniapi.c:30:
/home/sam/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/sam/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/sam/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
</code>

---

### Post by tuffguy45 on 2008-09-17
Bump

---

### Post by Crafty Kisses on 2008-09-18
Change the following line in Makefile:
```
CFLAGS += -mcmodel=kernel -mno-red-zone
```
To the following:
```
EXTRA_CFLAGS += -mcmodel=kernel -mno-red-zone
```
Then after that you need to apply 2 patches:
```
vpnclient_folder$ wget lamnk.com/vpnclient-linux-2.6.24-final.diff
vpnclient_folder$ wget lamnk.com/cisco_skbuff_offset.patch
vpnclient_folder$ patch < ./vpnclient-linux-2.6.24-final.diff
vpnclient_folder$ patch < ./cisco_skbuff_offset.patch
vpnclient_folder$ ./vpn_install

```
If your system is 32 bit then you only need to patch the vpnclient-linux-2.6.24-final.diff file.

Hope this helps. :)

---

### Post by tuxp3 on 2008-09-18
Actually there is a newer client from cisco which works out of the box with Ubuntu... (4.8.02) {PM me for a link}

Either way its the same basic install without the patching..

On a side note: My school (University at Buffalo) recently had massive budget cuts and as a result linux support has been reduced, but it does still exist. (my former student job was a linux support assistant) One of the things that continues to be supported is the VPN client (cisco vpn) I can hopefully help with any issues the VPN has.

-Andrew

---

### Post by tuffguy45 on 2008-09-18
I'm still getting the same thing :(

sam@sam-laptop:~/Desktop/VPN Client linux/vpnclient$ sudo ./vpn_install
[sudo] password for sam: 
Cisco Systems VPN Client Version 4.8.02 (0030) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-19-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-19-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-19-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/sam/Desktop/VPN Client linux/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `Client'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

---

### Post by Crafty Kisses on 2008-09-18
Make sure you have this package installed:
```
sudo apt-get install build-essential
```
Then you need to use Synaptic to search and install the correct kernel-headers, **not source**. You also have to make sure you open your VPN client with:
```
sudo /etc/init.d/vpnclient_init start
```
So basically install those packages I mentioned, and try what I've stated, if you still have issues please post back.

---

### Post by tuffguy45 on 2008-09-18
I got the build essentials but, I'm not familiar with Synaptic, can I get a quick primer on what I need to do or a link to read?

---

### Post by tuffguy45 on 2008-09-18
Erm sorry, I didn't realize that Synaptic was the gui front end for apt-get, but, what are the names of ther kernel headers I'm supposed to get?

---

### Post by tuffguy45 on 2008-09-18
I've installed the ones for my version and it still doesn't work...

---

### Post by Crafty Kisses on 2008-09-18
This might be the package you want to get:
```
sudo apt-get install kernel-headers-2.6.23.1-42.fc8
```

---

### Post by tuffguy45 on 2008-09-19
sam@sam-laptop:~$ sudo apt-get install kernel-headers-2.6.23.1-42.fc8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-headers-2.6.23.1-42.fc8

---

### Post by Crafty Kisses on 2008-09-20
I'm sorry, you need to install these kernel-headers:
```
sudo apt-get install linux-headers-2.6.24-19-generic
```
Once you've done that, you need to patch the client, I think that's where your going wrong at. You need to download the patch, and you can do the following: ```
# wget -q http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff
```
Once you've downloaded the patch, you must apply it, this is the part where I think you're doing it wrong, once you've ran this command:
```
patch <../vpnclient-linux-2.6.22.diff
``` It should look something like this:
```
patching file frag.c
patching file interceptor.c
patching file IPSecDrvOS_linux.c
patching file linuxcniapi.c
patching file linux_os.h
```
Once you've installed the patches, you can now actually install and compile the Cisco VPN client, run the following:
```
#./vpn_install
```
Not sure if you knew this either, there is a newer version of the Cisco VPN client I'm actually running it right now, that does not require the patches. You can download that version right [**here**]("http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz"). If you still want to use the VPN client that requires the patch, the latest patch is right [**here**]("http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.19+-rev1.diff").

---

### Post by tuffguy45 on 2008-09-21
This is weird, I was able to patch it on the other version

sam@sam-laptop:~/Desktop/VPN Client linux/vpnclient$ patch <vpnclient-linux-2.6.22.diff
patching file frag.c
Hunk #1 FAILED at 1.
Hunk #2 FAILED at 51.
Hunk #3 FAILED at 72.
Hunk #4 FAILED at 130.
Hunk #5 FAILED at 140.
Hunk #6 FAILED at 207.
6 out of 6 hunks FAILED -- saving rejects to file frag.c.rej
patching file interceptor.c
Hunk #1 FAILED at 5.
Hunk #2 FAILED at 342.
Hunk #3 FAILED at 558.
Hunk #4 FAILED at 577.
Hunk #5 FAILED at 597.
Hunk #6 FAILED at 686.
Hunk #7 FAILED at 701.
7 out of 7 hunks FAILED -- saving rejects to file interceptor.c.rej
patching file IPSecDrvOS_linux.c
Hunk #1 FAILED at 11.
1 out of 1 hunk FAILED -- saving rejects to file IPSecDrvOS_linux.c.rej
patching file linuxcniapi.c
Hunk #1 FAILED at 5.
Hunk #2 FAILED at 295.
Hunk #3 FAILED at 341.
Hunk #4 FAILED at 459.
Hunk #5 FAILED at 479.
5 out of 5 hunks FAILED -- saving rejects to file linuxcniapi.c.rej
patching file linux_os.h

---

### Post by Crafty Kisses on 2008-09-21
Just remove everything you have from the previous installation and start fresh with the latest version of the Cisco VPN client. Try downloading the latest version of the client, it does not require the patch, you can download it right [**here.**]("http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz")  Remember you need to install this package:```
sudo apt-get install linux-headers-2.6.24-19-generic
```Once you've downloaded the latest version, do the following:```
#./vpn_install
```Like I've stated before after you've ran that command you should be able to install and compile it.

---

### Post by tuxp3 on 2008-09-21
> **Codename said:**
> Just remove everything you have from the previous installation and start fresh with the latest version of the Cisco VPN client. Try downloading the latest version of the client, it does not require the patch, you can download it right [**here.**]("http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz")  Remember you need to install this package:```
sudo apt-get install linux-headers-2.6.24-19-generic
```Once you've downloaded the latest version, do the following:```
#./vpn_install
```Like I've stated before after you've ran that command you should be able to install and compile it.

Actually that link is outdated.. the Current version of the VPN is 4.8.02
You DO need your kernel-headers (kernel-sources shouldn't be required) you can use synaptic to get the ones that match the kernel that you are running (which can be found by running `uname -a` in a terminal)

After installing kernel-headers, then in a terminal # sudo ./vpn_install and verify that the cisco installation script detects the correct kernel version folder (it should, but verify it).. 

Good Luck!

---

### Post by tuffguy45 on 2008-09-22
sam@sam-laptop:~/Desktop/vpnclient$ sudo ./vpn_uninstall
[sudo] password for sam: 
./vpn_uninstall: line 48: chkconfig: command not found
Cisco Systems VPN Client Version BUILDVER_STRING Linux UnInstaller
Copyright (C) 1998-2001 Cisco Systems, Inc. All Rights Reserved.

Are you sure that you wish to uninstall the VPN Client?  [no] 
Uninstall Aborted
sam@sam-laptop:~/Desktop/vpnclient$ sudo ./vpn_uninstall
./vpn_uninstall: line 48: chkconfig: command not found
Cisco Systems VPN Client Version BUILDVER_STRING Linux UnInstaller
Copyright (C) 1998-2001 Cisco Systems, Inc. All Rights Reserved.

Are you sure that you wish to uninstall the VPN Client?  [no] yes

Do you wish to remove all existing profiles and certificates?  [no] yes
 - Existing Profiles and Certificates will be removed

Directory where binaries were installed [/usr/local/bin] 
 - Binary uninstall directory set to /usr/local/bin

Cleaning up installed files and directory....
Done.
sam@sam-laptop:~/Desktop/vpnclient$ uname -a
Linux sam-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
sam@sam-laptop:~/Desktop/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-19-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-19-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-19-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/sam/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/sam/Desktop/vpnclient/linuxcniapi.o
In file included from /home/sam/Desktop/vpnclient/Cniapi.h:15,
                 from /home/sam/Desktop/vpnclient/linuxcniapi.c:31:
/home/sam/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
make[2]: *** [/home/sam/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/sam/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

---

### Post by Crafty Kisses on 2008-09-23
I'm thinking your kernel source in ```
/usr/src/linux
``` Is probably not set up correctly. Check that ```
/usr/include/linux
``` Is set up correctly, and make sure that you've configured your kernel source to (at least roughly) match your running system. I've heard scrollback can be a factor of this error, so open up that file, and add this line to it:
```
2>&1 | less
```
If that doesn't do it, try the following, install the following package:
```
sudo apt-get install gcc
```
You then need to run this command:
```
uname -r
```
To find the correct kernel-headers for your build. Use Synaptic to find the correct build, once you've done that, unzip your Cisco VPN client and run the following:
```
sudo sh vpn_install
```
Make sure you start the vpn sub-system with:
```
sudo /etc/init.d/vpnclient_init start
```
Copy your .pcf profile to the following directory:
```
sudo cp <your .pcf> /etc/opt/cisco-vpnclient/Profiles
```
Once it's copied you need to run this command:
```
sudo chmod 744 <your>.pcf
```
Then after you've ran that command, do the following:
```
vpnclient connect <your profile>
```
Make sure it's **without the .pcf extension**. Please post back if it doesn't work and I'll continue to help you.

---

### Post by Crafty Kisses on 2008-09-23
One more thing I forgot to add, you need to remove EVERYTHING related to the Cisco VPN client and start fresh, then follow my instructions.

---

### Post by nineowls on 2008-09-23
of the many many tries these last three hours
this is the least errors I have received so far
Making module
make -C /usr/src/linux SUBDIRS=/home/j/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/j/vpnclient/linuxcniapi.o
/home/j/vpnclient/linuxcniapi.c:1: error: code model ‘kernel’ not supported in the 32 bit mode
make[2]: *** [/home/j/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/j/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

---

### Post by tuffguy45 on 2008-09-24
Sorry maybe, I didn't understand you. What file am I editing? You gave me a directory with A LOT of files in it.

---

### Post by tuffguy45 on 2008-09-26
Bump

---

### Post by obi1kenobi on 2008-09-29
Hi there,

Had the same problem:
```

[...]
Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/obi1kenobi/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: [COLOR="Red"]***** No rule to make target `VPN'.Stop.**[/COLOR]
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
[...]

```   

My VPN client was untar-ed on my home directory and I remembered that up until now I have always unzipped it on /tmp directory and worked flawessly.

So what I've done was to move the whole "vpnclient" directory to /tmp and launched it form there:

```

mv /home/obi1kenobi/vpnclient /tmp/
cd /tmp/vpnclient
sudo ./vpn_install

```

AND HAPPY DAYS !!!! **[COLOR="Blue"]IT WORKED[/COLOR]** !!!!  :guitar:

BTW: I am using KUbuntu 8.0.4 KDE 4.1.1, 32 bit and Cisco VPN Client 8.0.4.2 (the latest one) and NO patching.


Hope this helps.

-Obi1

---

### Post by JTSoftware on 2008-09-30
The key here (for Ubuntu 8.04, kernel 2.6.24-19) seems to be in getting the Cisco VPN Client 8.0.4.2, as 8.0.4.01 is definitely out of date with respect to the kernel headers.

Would some kind soul either post it somewhere or tell us where we can find it?

In trying to fix the errors, I get as far as for_each_netdev taking two args instead of one, and I'm stuck.

Thanks.

-John

---

### Post by JTSoftware on 2008-10-01
I did some more Googling and found it:  [http://www.gegereka.com/?bank=0&query=vpnclient-linux-x86_64-4.8.02.0030-k9](http://www.gegereka.com/?bank=0&query=vpnclient-linux-x86_64-4.8.02.0030-k9)

It built perfectly, and with help from the prior posts, I'm in!

THANKS!!!!

-John

---

### Post by Oskarius on 2008-11-20
I had exactly the same problem with the same vpn-client from cisco and solved it by forgetting all about it and in stead use two apps that come with Ubuntu.

Applications - Add/Remove
Show: All available applications
Search for vpnc 
Check vpnc and Kvpnc
Apply Changes

After installation you have to configure
Applications - Internet - KVpnc
Click New Profile
After the usual welcome screen you get to choose VPN type
Choose Cisco (free)
If you have a pcf-file import it. Otherwise configure as needed.
:)

---

### Post by citybird on 2008-11-25
I get the following when I try to run the build on the latest version of the Cisco VPN Client: "vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz"

I go into Makefile and change it to EXTRA_CFLAGS and then run ./vpn_install

```

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-21-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-21-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-21-generic/build SUBDIRS=/usr/src/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /usr/src/vpnclient/linuxcniapi.o
/usr/src/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/usr/src/vpnclient/linuxcniapi.c:341: warning: cast from pointer to integer of different size
/usr/src/vpnclient/linuxcniapi.c:342: warning: cast from pointer to integer of different size
/usr/src/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/usr/src/vpnclient/linuxcniapi.c:481: warning: cast from pointer to integer of different size
/usr/src/vpnclient/linuxcniapi.c:482: warning: cast from pointer to integer of different size
/usr/src/vpnclient/linuxcniapi.c:491: warning: cast to pointer from integer of different size
/usr/src/vpnclient/linuxcniapi.c:491: warning: cast from pointer to integer of different size
  CC [M]  /usr/src/vpnclient/frag.o
/usr/src/vpnclient/frag.c: In function ‘queue_fragment’:
/usr/src/vpnclient/frag.c:50: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:50: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:50: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:50: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:52: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:52: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:52: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:52: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:70: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:70: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:70: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:70: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:73: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:73: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:73: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:73: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c: In function ‘have_all_fragments’:
/usr/src/vpnclient/frag.c:126: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:126: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:126: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:126: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:134: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:134: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:134: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:134: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:141: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:141: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:141: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:141: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:142: warning: cast to pointer from integer of different size

/usr/src/vpnclient/frag.c:146: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:146: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:146: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c:146: warning: cast to pointer from integer of different size
/usr/src/vpnclient/frag.c: In function ‘need_reorder_frag’:
/usr/src/vpnclient/frag.c:198: warning: cast to pointer from integer of different size
  CC [M]  /usr/src/vpnclient/IPSecDrvOS_linux.o
  CC [M]  /usr/src/vpnclient/interceptor.o
/usr/src/vpnclient/interceptor.c: In function ‘recv_ip_packet_handler’:
/usr/src/vpnclient/interceptor.c:646: warning: assignment makes integer from pointer without a cast
/usr/src/vpnclient/interceptor.c:667: warning: passing argument 2 of ‘CniNewFragment’ makes pointer from integer without a cast
/usr/src/vpnclient/interceptor.c: In function ‘do_cni_send’:
/usr/src/vpnclient/interceptor.c:785: error: invalid operands to binary -
make[2]: *** [/usr/src/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/usr/src/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```

---

### Post by LPGDEV on 2009-01-24
> **obi1kenobi said:**
> Hi there,

Had the same problem:
```

[...]
Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/obi1kenobi/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: [COLOR="Red"]***** No rule to make target `VPN'.Stop.**[/COLOR]
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
[...]

```   

My VPN client was untar-ed on my home directory and I remembered that up until now I have always unzipped it on /tmp directory and worked flawessly.

So what I've done was to move the whole "vpnclient" directory to /tmp and launched it form there:

```

mv /home/obi1kenobi/vpnclient /tmp/
cd /tmp/vpnclient
sudo ./vpn_install

```

AND HAPPY DAYS !!!! **[COLOR="Blue"]IT WORKED[/COLOR]** !!!!  :guitar:

BTW: I am using KUbuntu 8.0.4 KDE 4.1.1, 32 bit and Cisco VPN Client 8.0.4.2 (the latest one) and NO patching.


Hope this helps.

-Obi1

I spent hours trying to figure out what was happening and moving the vpnclient directory to /tmp/ solved it!!

Thanks! :D

---

### Post by jchedstrom on 2009-06-29
After spending about 4 hours on this problem I finally have the newest Cisco VPN Client installed, 4.8.02.0030, on Ubuntu Jaunty 9.04 kernel 2.6.28-13.

1) the more obvious parts to the solutions if you RTFM (this installs the prerequisite files for the build):
```

sudo apt-get build-essential
sudo apt-get linux-headers-generic

```2) If you fixed the problem by moving the ***/vpnclient/ directory to /tmp/vpnclient, what you've likely done is avoided a common bug in scripts where they don't surround directory variables in quotes. This mistake mangles directory names with spaces in them. Easiest solution: move vpnclient anywhere without a space in the full name, ie ~/VPN Client/vpnclient will give you problems, ~/vpnclient or /tmp/vpnclient will be fine.

3) If you recieve the error about CFLAGS, change CFLAGS to EXTRA_CFLAGS inside of "Makefile".

4) Fixing the scary compiling error:
```

/tmp/vpnclient/interceptor.c:785: error: invalid operands to binary - (have ‘sk_buff_data_t’ and ‘unsigned char *’)
make[2]: *** [/tmp/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/tmp/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [default] Error 2

```My understanding is that the compiler just wants the variables to be casted properly. So, after poking around in the code I discovered that you need to change line 785 in 'interceptor.c' 
**from:**
```

hard_header_len = skb->network_header - skb->data;

```
**to:**
```

hard_header_len = skb->network_header - (sk_buff_data_t) skb->data;

```Hopefully this helps a few people from bashing their heads against their screens (man I hate Cisco today...).

(yea! my first post ever!)

---

### Post by loadedmind on 2009-07-14
Ok all, this has me inspired so it drove me to attempt the whole VPN thing again.  Normally, I use the Cisco VPN client for OS X.  I hit the Connect button and it prompts me to enter a pin+RSA 6-digit number for authentication.  At the behest of another person who has posted previously, I installed the vpnc and Kvpn gui frontend.  I noticed how the profile .pcf file was imported, but I'm a bit confused as to the group password/password prompts.  Are either of these the pin+SecurID combination?  How do I know what information belongs in which fields?  If it helps, I can post some screenshots of this process.  Also, not sure whether to use the free version or proprietary version of the Cisco profile within Kvpn.

Thanks,
Loadedmind

---

### Post by sof1a on 2011-08-02
Im trying to install the Cisco VPN client aswell...
Followed the suggestions in thead and added the patches, change CFLAG options and checked linux-headers. When I run 
>sudo /etc/init.d/vpnclient_init start
the module cisco_ipsec starts to run.
My problems comes when I try to incorporate the certificates.

>cisco_cert_mgr -R -op import -f /usr/local/src/vpn/cert/root.cer
bash: /usr/local/bin/cisco_cert_mgr: No such file or directory

Looking in  /usr/local/bin/ I can find the cisco_cert_mgr. 
Does someone have the suggestion how to solve this?

---

