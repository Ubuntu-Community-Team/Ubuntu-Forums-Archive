---
title: "Installing VPN client in Gutsy"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by frenchcr on 2007-10-19
In feisty (7.04) I always had to patch my vpn software to get it to install, I was using version 4.8.0.xxxx

If you use the following version....

[COLOR="Black"][COLOR="Red"]Cisco VPN client for Linux-x86 ver. 4.8.01.0640[/COLOR][/COLOR]

[http://linux-support.hiwi.rz.uni-konstanz.de/downloads/Cisco-VPN-Client-Linux-x86-4.8.01.0640.tar.bz2]("http://linux-support.hiwi.rz.uni-konstanz.de/downloads/Cisco-VPN-Client-Linux-x86-4.8.01.0640.tar.bz2")

with the new gutsy kernel 2.6.22-14-generic it should install no prob (no patch required), just ./vpn_install and you should get the following...


```
root@frenchcr03-lap:/usr/src/vpnclient# ./vpn_install 
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer 
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved. 

By installing this product you agree that you have read the 
license.txt file (The VPN Client license) and will comply with 
its terms. 


Directory where binaries will be installed [/usr/local/bin] 

Automatically start the VPN service at boot time [yes]yes 

In order to build the VPN kernel module, you must have the 
kernel headers for the version of the kernel you are running. 


Directory containing linux kernel source code [/lib/modules/2.6.22-14-generic/build] 

* Binaries will be installed in "/usr/local/bin". 
* Modules will be installed in "/lib/modules/2.6.22-14-generic/CiscoVPN". 
* The VPN service will be started AUTOMATICALLY at boot time. 
* Kernel source from "/lib/modules/2.6.22-14-generic/build" will be used to build the module. 

Is the above correct [y]y 

Making module 
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/usr/src/vpnclient modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic' 
  CC [M]  /usr/src/vpnclient/linuxcniapi.o 
  CC [M]  /usr/src/vpnclient/frag.o 
  CC [M]  /usr/src/vpnclient/IPSecDrvOS_linux.o 
  CC [M]  /usr/src/vpnclient/interceptor.o 
  CC [M]  /usr/src/vpnclient/linuxkernelapi.o 
  LD [M]  /usr/src/vpnclient/cisco_ipsec.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
WARNING: could not find /usr/src/vpnclient/.libdriver.so.cmd for /usr/src/vpnclient/libdriver.so 
  CC      /usr/src/vpnclient/cisco_ipsec.mod.o 
  LD [M]  /usr/src/vpnclient/cisco_ipsec.ko 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic' 
Create module directory "/lib/modules/2.6.22-14-generic/CiscoVPN". 
Copying module to directory "/lib/modules/2.6.22-14-generic/CiscoVPN". 
Already have group 'bin' 

Creating start/stop script "/etc/init.d/vpnclient_init". 
    /etc/init.d/vpnclient_init 
Enabling start/stop script for run level 3,4 and 5. 
Creating global config /etc/opt/cisco-vpnclient 

Installing license.txt (VPN Client license) in "/opt/cisco-vpnclient/": 
    /opt/cisco-vpnclient/license.txt 

Installing bundled user profiles in "/etc/opt/cisco-vpnclient/Profiles/": 
* New Profiles     : sample 

Copying binaries to directory "/opt/cisco-vpnclient/bin". 
Adding symlinks to "/usr/local/bin". 
    /opt/cisco-vpnclient/bin/vpnclient 
    /opt/cisco-vpnclient/bin/cisco_cert_mgr 
    /opt/cisco-vpnclient/bin/ipseclog 
Copying setuid binaries to directory "/opt/cisco-vpnclient/bin". 
    /opt/cisco-vpnclient/bin/cvpnd 
Copying libraries to directory "/opt/cisco-vpnclient/lib". 
    /opt/cisco-vpnclient/lib/libvpnapi.so 
Copying header files to directory "/opt/cisco-vpnclient/include". 
    /opt/cisco-vpnclient/include/vpnapi.h 

Setting permissions. 
    /opt/cisco-vpnclient/bin/cvpnd (setuid root) 
    /opt/cisco-vpnclient (group bin readable) 
    /etc/opt/cisco-vpnclient (group bin readable) 
    /etc/opt/cisco-vpnclient/Profiles (group bin readable) 
    /etc/opt/cisco-vpnclient/Certificates (group bin readable) 
* You may wish to change these permissions to restrict access to root. 
* You must run "/etc/init.d/vpnclient_init start" before using the client. 
* This script will be run AUTOMATICALLY every time you reboot your computer. 
root@frenchcr03-lap:/usr/src/vpnclient# 
```

Result!!!

---

### Post by lynxus on 2007-10-19
Cisco vpn client can be a pain in the tits.


If you rightclick the network manager icon you should be able to configure cisco vpns from that.

Or 

sudo apt-get install vpnc 

Hope this helps

---

### Post by luvdemheels on 2007-10-19
I have vpnc installed but everytime I try to goto the /etc/vpnc directory to setup my tunnel it says I do not have permission. What can I do now???

---

### Post by frenchcr on 2007-10-20
This thread is just meant as a guide to help others. We use cisco vpn client at our uni so im stuck with that unfortunately. Not familiar with vpnc...will check it out thanks.

---

### Post by ncubede on 2007-10-22
Vpnc is great for short distances and can easily connect to a nearby Cisco VPN appliance, where normally the cisco VPN client is used.  It is bound to use UDP for the tunneling, so long-distance does not work right.  Also, about once a day it dies, but a simple restart revives things, I guess this is rekeying which is problematic.

Vpnc can not do TCP, though, so its use is pretty much impossible to use over a longer distance.  In my case I VPN into a server across the Atlantic, and this requires TCP-tunneling, so I am stuck with Cisco vpnclient.  Should vpnc ever implement the TCP tunnel, I'll be happy to switch back.

---

### Post by uroc on 2007-10-22
I'm not having any luck getting the cisco vpn to run under Gutsy on an AMD64.  I fixed a compile error when building the driver.  Now when trying to run vpnclient connect, I keep getting an error "No such file or directory".  I've verified the permissions have execute.  Has anyone seen this?

---

### Post by soce_32 on 2007-10-22
Our university is distributing 4.8.00, which won't compile on gutsy.  I downloaded the package linked in frenchcr's op, copied in the profiles from the 4.8.00 tar ball I got from my uni download site and it works like a charm.  Thanks!

---

### Post by cybertrekman on 2007-10-23
OK, I want to be a ubuntu convert and this is a very useful thread to install Cisco VPN, but as a totally new ubuntu user (as of three days ago) I have no idea what to do to configure it and I need it to access my office files at ad-hoc times - wondering if I should have stayed with Vista on my new Lenovo T60 laptop - Cisco VPN seems to have loaded OK, but from what I have found on the web so far I cannot figure out what the next steps are to configure it as nothings working (maybe they were specif to those sites). Is there something specific to configure Cisco VPN in Gutsy? 

Can anyone help with a dummies guide to what do you do to configure Cisco VPN and enable launch/shutdown from a desktop icon(s):confused::confused:

---

### Post by CypherBit on 2007-10-23
I have the same issue. It seemed to install just fine, although I did get this:

```
Setting permissions.
    /opt/cisco-vpnclient/bin/cvpnd (setuid root)
    /opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient/Profiles (group bin readable)
    /etc/opt/cisco-vpnclient/Certificates (group bin readable)
* You may wish to change these permissions to restrict access to root.
* You must run "/etc/init.d/vpnclient_init start" before using the client.
* This script will be run AUTOMATICALLY every time you reboot your computer.

```

I don't know how to run "/etc/init.d/vpnclient_init start" and I have no idea how to connect with the client after install. I do have the .pcf (and all the information) just don't know how to use it.

Any help is greatly appreciated.

---

### Post by dgavenda on 2007-10-24
frenchcr,

Thanks!!  Worked like a charm one I switched to 2.6.22-14-generic.

That was the easiest time I have had getting the cisco vpn client working.

Thx again,
Dan

---

### Post by CypherBit on 2007-10-24
dgavenda, would you be so kind to write up how you managed to install and then use it?

---

### Post by soce_32 on 2007-10-24
CypherBit,

The install message states that it will start each time you reboot, so as long as you've rebooted, the vpn modules will be loaded.  You can issue sudo /etc/init.d/vpn_client {start|stop|restart} from the command line to manually control the service.

In order to use the client, copy your pcf file to /etc/CiscoSystemsVPNClient/Profiles, you can then issue this command:

sudo vpnclient connect <yourprofile>

where <yourprofile> is the name of the pcf file you copied without the .pcf extention.

You should then get prompted for your username and password.

---

### Post by luvdemheels on 2007-10-24
What if you do not have a pcf file?? Is there a gui for this??

---

### Post by MusashiX2 on 2007-10-24
i tried the directions in frenchcr's first post, and the VPN Client did not install.  it said that it could not open the "driver_build.sh" file.  it asked all these questions about where to install stuff and i just kept hitting enter.  any idea what the problem may be?

---

### Post by Virtual_Ron on 2007-10-25
When I try to install the cisco-vpn generic, I get the following errors during compile.
Can someone point out what I'm missing???
Thanks



ronb@vulcan:~/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.22-14-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.22-14-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.22-14-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/ronb/Programs/Cisco- VPN-Client-Linux-x86-4.8.01.0640 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/linuxcniapi.o
In file included from /home/ronb/Programs/Cisco- VPN-Client-Linux-x86-4.8.01.0640/Cniapi.h:15,
                 from /home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/linuxcniapi.c:31:
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/GenDefs.h:110:2: warning: #warning 64 bit
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/linuxcniapi.c: In function 'CniInjectReceive':
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/linuxcniapi.c:341: warning: cast from pointer to integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/linuxcniapi.c:342: warning: cast from pointer to integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/linuxcniapi.c: In function 'CniInjectSend':
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/linuxcniapi.c:481: warning: cast from pointer to integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/linuxcniapi.c:482: warning: cast from pointer to integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/linuxcniapi.c:491: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/linuxcniapi.c:491: warning: cast from pointer to integer of different size
  CC [M]  /home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.o
In file included from /home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/Cniapi.h:15,
                 from /home/ronb/Programs/Cisco- VPN-Client-Linux-x86-4.8.01.0640/frag.c:20:
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/GenDefs.h:110:2: warning: #warning 64 bit
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c: In function 'queue_fragment':
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:50: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:50: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:50: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:50: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:52: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:52: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:52: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:52: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:70: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:70: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:70: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:70: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:73: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:73: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:73: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:73: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c: In function 'have_all_fragments':
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:126: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:126: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:126: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:126: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:134: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:134: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:134: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:134: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:141: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:141: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:141: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:141: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:142: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:146: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:146: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:146: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:146: warning: cast to pointer from integer of different size
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c: In function 'need_reorder_frag':
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/frag.c:198: warning: cast to pointer from integer of different size
  CC [M]  /home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/IPSecDrvOS_linux.o
In file included from /home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/IPSecDrvOS_linux.c:24:
/home/ronb/Programs/Cisco- VPN-Client-Linux-x86-4.8.01.0640/GenDefs.h:110:2: warning: #warning 64 bit
  CC [M]  /home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/interceptor.o
In file included from /home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640 /Cniapi.h:15,
                 from /home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/interceptor.c:34:
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/GenDefs.h:110:2: warning: #warning 64 bit
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/interceptor.c: In function 'recv_ip_packet_handler':
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/interceptor.c:639: warning: assignment makes integer from pointer without a cast
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/interceptor.c:660: warning: passing argument 2 of 'CniNewFragment' makes pointer from integer without a cast
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640 /interceptor.c: In function 'do_cni_send':
/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640/interceptor.c:778: error: invalid operands to binary -
make[2]: *** [/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640 /interceptor.o] Error 1
make[1]: *** [_module_/home/ronb/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
ronb@vulcan:~/Programs/Cisco-VPN-Client-Linux-x86-4.8.01.0640$

---

### Post by lamnk on 2007-10-25
Hi Ron, i've the exact problem like you. Not only on Ubuntu but also on openSUSE 10.3. Both distros are 64 bit version. Guess it's a bug from Cisco because they claimed support for biarch x86_64 with this newest version 4.8.01.0640.

The only solution now is to use vpnc while waiting for a 5.0 release. Open Source is really the way to go \o/ :p

---

### Post by Virtual_Ron on 2007-10-25
> **lamnk said:**
> Hi Ron, i've the exact problem like you. Not only on Ubuntu but also on openSUSE 10.3. Both distros are 64 bit version. Guess it's a bug from Cisco because they claimed support for biarch x86_64 with this newest version 4.8.01.0640.

The only solution now is to use vpnc while waiting for a 5.0 release. Open Source is really the way to go \o/ :p

I totally agree...  but I've been having a 8itch of a time getting the vpnc to work.  I've posted my woes here:   [http://ubuntuforums.org/showpost.php?p=3629190&postcount=19](http://ubuntuforums.org/showpost.php?p=3629190&postcount=19)

Thanks!
Ron

---

### Post by CypherBit on 2007-10-25
Thank you soce_32, it seems I am getting a bit closer, but still not where I'd want to be.
Having a working VPN client is an absolute must for me, it's just one of those apps that I use numerous times a day.

I rebooted copied the .pcf where you said and ran sudo vpnclient connect <yourprofile>. Everything looked ok so I entered my username, then my SecurID passcode and get

```
Authenticating user.
Negotiating security policies.
Securing communication channel.
Contacting the gateway at secondary_IP_here
User Authentication for profile...

Enter Username and Password.

Username [username_here]: 

```

*secondary_IP_here* is actually our backup, which never works,  The main IP (as it should be) is listed before I get prompted for my password/passcode just before the suplied code.

I tried using different variations of my username domain\user, [email]user@domain.com[/email] and plain user. I get the same result, which is, I get prompted for the username, password (not passcode).
I've never connected under Linux, but have run v4.6, 4.8 and 5.0 from this same machine (just not a VM - VirtualBox) and can connect under Windows just fine.

How should the process look like. Get prompted for username, passcode, I supply those, then what? How do you guys connect to your VPN using SecurID?

Any assistance, perhaps just pointers are more then welcome.

---

### Post by dgavenda on 2007-10-25
CypherBit,

I followed frenchcr's directions to a T AFTER I switched to the generic kernel.

To switch, I did an apt-get for the generic kernel then modified my /boot/grub/menu.lst file to make it load the generic kernel by default.  Then frenchcr's directions.

It truly was that easy.

Type: uname -r  
This will display your kernel revision.    

Hope this helps.  

Dan

---

### Post by peteguhl on 2007-10-26
Those having problems with x86_64 go here:
[http://ubuntuforums.org/showthread.php?p=3637667#post3637667](http://ubuntuforums.org/showthread.php?p=3637667#post3637667)

---

### Post by CypherBit on 2007-10-27
dgavenda I don't think there were any errors during my install. The client seems to be working, it's just that I can't (or don't know how to) connect.

The kernel I have is 2.6.22-14-generic.

---

### Post by dgavenda on 2007-10-27
CypherBit,

Once you have everything installed and ready, you need to do this:

sudo /etc/init.d/vpnclient_init start
sudo /opt/vpnclient/vpnclient connect 

Of course, you need to have a pcf (profile) for your vpn.  I received it from our it admin at work but it's nothing special.  

Hope this helps,
Dan

---

### Post by Tlon on 2007-10-27
> **ncubede said:**
> Vpnc is great for short distances and can easily connect to a nearby Cisco VPN appliance, where normally the cisco VPN client is used.  It is bound to use UDP for the tunneling, so long-distance does not work right.  Also, about once a day it dies, but a simple restart revives things, I guess this is rekeying which is problematic.

Vpnc can not do TCP, though, so its use is pretty much impossible to use over a longer distance.  In my case I VPN into a server across the Atlantic, and this requires TCP-tunneling, so I am stuck with Cisco vpnclient.  Should vpnc ever implement the TCP tunnel, I'll be happy to switch back.

Wow, thank you for this information.  I've been trying to figure out why I couldn't get this stupid thing to work right for ages.  I guess that's my answer.  Cheers.

---

### Post by otakuj462 on 2007-12-13
Works like a charm for me on Kubuntu 7.10 :)

---

### Post by phissure on 2007-12-28
For some reason the download link didn't work for me...  It might just be too busy.
Anyway, I found an alternate download location:
[http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz](http://tuxx-home.at/vpn/Linux/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz)

---

