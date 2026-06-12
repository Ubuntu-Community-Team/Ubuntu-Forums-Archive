---
title: "Attempt to install Cisco Linux VPN Client resulted in no wifi."
date: 2011-02-20
forum: New to Ubuntu
---

### Post by lornag on 2011-02-20
Hi,
I've just put Ubuntu 10.10 on my laptop along side windows with a view to eventually completely moving over to Ubuntu. Just in case it's relevant my laptop is an Eee PC 1000H.

 I attempted to install cisco linux vpn client using the instructions on my universities website. It didn't work and now I can't access the internet via wireless (tho' wireless still works in windows). I think some file was missing, the instructions said:
In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running. 
For RedHat 6.x users these files are installed in /usr/src/linux by default
For RedHat 7.x users these files are installed in /usr/src/linux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux-2.4.10.SuSE by default

I didn't really understand this so (stupidly) just carried on an hoped for the best.

**First question:** What is a kernel header? (I've googled it but it still doesn't make sense)

The terminal ended with this:

p, li { white-space: pre-wrap; } Making module
 make -C /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/lorna/Desktop/vpnclient modules
 /usr/src/linux-headers-2.6.35-25-generic/scripts/gcc-version.sh: line 25: gcc: command not found
 /usr/src/linux-headers-2.6.35-25-generic/scripts/gcc-version.sh: line 26: gcc: command not found
 make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
 /usr/src/linux-headers-2.6.35-25-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
 make[1]: gcc: Command not found
   CC [M]  /home/lorna/Desktop/vpnclient/linuxcniapi.o
 /bin/sh: gcc: not found
 make[2]: *** [/home/lorna/Desktop/vpnclient/linuxcniapi.o] Error 127
 make[1]: *** [_module_/home/lorna/Desktop/vpnclient] Error 2
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
 make: *** [default] Error 2
 Failed to make module "cisco_ipsec.ko".
 root@slug-1000H:/home/lorna/Desktop/vpnclient# 
 

**Second question: **Any idea what went wrong, how I can fix the wifi and how I might install VPN?

I am happy to reinstall Ubuntu and start again but I'd rather fix it.  Any help or explanations would be much appreciated.
Lorna

---

### Post by yeats on 2011-02-20
Without digging in to your specific issues with this installation, why don't you try installing VPNC:

```
sudo apt-get install vpnc
```

Then clicking on the Network Manager applet at the upper right and select VPN Connections -> Configure VPN.  Click Add, "select Cisco Compatible VPN (vpnc)", and enter your credentials.

If your system is really borked from trying the other installation, you might want to reinstall before trying ;-).

Good luck

---

### Post by lornag on 2011-02-20
Thanks. I'll try to fiddle about trying to make the wifi work (after all I can't make it any worse!) but if it doesn't I'll reinstall ubuntu and then try vpnc.

---

### Post by lornag on 2011-02-22
I reinstalled ubuntu which meant the wifi worked again. Unfortunately it looks like I'm going to have to install the Cisco Linux VPN client. (I've just made a second attempt which seemed not to work for the same reasons but I can't check whether wifi works as I have a wired connection at the moment).

Anyway it looks like I'll be reinstalling Ubuntu again, which is fine.

I have installed  "build essential" as apparently the installation needs this. This doesn't seem to help.

At some point the installation asks me: 
Directory containing linux kernel source code [/lib/module/2.6.35-25-generic/build] ? 

I've looked in this directory and I don't have a folder called module, so I think I need to manually enter where the linux kernel source code is. I've had a bit of a hunt around and I think it might be  /usr/src/linux-headers-2.6.35-25-generic. Could someone confirm or deny this?

---

### Post by yeats on 2011-02-22
> **lornag said:**
> I reinstalled ubuntu which meant the wifi worked again. Unfortunately it looks like I'm going to have to install the Cisco Linux VPN client. (I've just made a second attempt which seemed not to work for the same reasons but I can't check whether wifi works as I have a wired connection at the moment).

So installing VPNC did not work?  You can also use it via the command line.  You could do:

```
sudo gedit /etc/vpnc/example.conf
```

Which looks like this:
```
#IPSec gateway <gateway>
#IPSec ID <group-id>
#IPSec secret <group-psk>
#IKE Authmode hybrid
#Xauth username <username>
#Xauth password <password>

```

If you remove the #s from the lines you need and substitute the values in the < >s (without using the < >s) for what your connection needs, and save it as university.conf, you could do

```
sudo vpnc-connect university.conf
```

to connect.

> I have installed  "build essential" as apparently the installation needs this. This doesn't seem to help.

Yes, build-essential pulls in most, if not all, of the tools you'll need to compile software from source.

> At some point the installation asks me: 
Directory containing linux kernel source code [/lib/module/2.6.35-25-generic/build] ? 

You will need to install the linux-source package to have this directory.  That will add this directory:

```
/lib/modules/2.6.35-27-generic/build/
```

(using 10.10 with all updates applied)

---

### Post by lornag on 2011-02-24
Thank you so much for you help and thank you for persuading me to figure out how to use vpnc.

Just in case anyone (with a similar lack of knowledge) has a problem figuring out how to use vpnc, here is some information:
If you need to get your connection information from a pcf file you can find websites on the internet that will decrypt the enc_GroupPwd. 
The Host is your IPSec gateway.
The group name is your IPSec ID.
The Username is your Xauth username.
The UserPassword is your Xauth password.

Apparently there is a program called pcf2conf which will take a pcf file and create a conf file. This didn't work for me but it might for others.

---

### Post by yeats on 2011-02-25
> **lornag said:**
> Thank you so much for you help and thank you for persuading me to figure out how to use vpnc.

Sure!  Glad you could get it working.  Best of luck with Ubuntu!

---

### Post by Piro-san on 2011-03-10
Hello,
I have more or less the same  basic problem as lornag, which is, I couldn't find the cisco vpn client, so installed it using 

```
sudo apt-get install vpnc
```And it seemed like it worked, and followed the following directions:

> Network Manager applet at the upper right and select VPN Connections -> Configure VPNBut I could not see the Cisco Compatible VPN (vpnc) selection, I only see Point-to-point Tunneling Protocol(PPTP). I tried to see if the package from the vpnc was installed and I received the following message from my terminal:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vpnc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgrade
```So it looks like it installed it, but I cannot see it on the Configure VPN-> Add section...
I was wondering if I had to install something else or if there was a way to get it to work on the network connections without  going through all the changes Yeats went through at the end.


PS: I am using Ubuntu 10.04 LTS, along side windows on a toshiba A300.

I get the impression that when I install things with :

```
sudo apt-get  
```The things install but I can't get to them ( installed postgresql and psycopg2 last week installed them correctly and the system tells me I have them but for some reason I can't use them, but this is a matter for another thread :)

-- Piro --

---

### Post by Piro-san on 2011-03-10
I figured out the problem :), after typing:

```
sudo apt-get install vpnc
```

I had to type:

```
sudo apt-get install network-manager-vpnc
```

to see it pop-up in the network connections.

Now I only have to try it out, and see if it works at uni, hopefully I won't have any problems :)

---

