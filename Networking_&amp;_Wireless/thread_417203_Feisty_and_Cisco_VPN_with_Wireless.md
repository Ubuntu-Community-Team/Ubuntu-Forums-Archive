---
title: "Feisty and Cisco VPN with Wireless"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by tak1150 on 2007-04-21
I had problems installing Cisco VPN and then I got it to install using the patch found [here]("http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/").

But, I cannot connect to VPN at all and get this message (while connected to internet via wireless at home);
```
Initializing the VPN connection.
Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.

```

However, VPN does work if I am on ethernet (wired) network at home. Please help! Thanks.

---

### Post by melcloud on 2007-04-23
I had the same problem before.

I found a solution:

type ifdown eth0 (assume you wire connection is eth0) before you use vpnclient

This will fix the problem.

---

### Post by der_vegi on 2007-04-23
Thanks!

Had the same problem and now it works.

---

### Post by ZERO_SHIFT on 2007-04-23
Thanks that fixed it :-)

---

### Post by jester805 on 2007-04-24
I'm new to this, but I downloaded the Linux VPN client from Cisco's site.  I tried to run the installer (with the default options) and it errored out on me twice.

> Making module
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/dnolan/Desktop/new/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/dnolan/Desktop/new/vpnclient/linuxcniapi.o
/home/dnolan/Desktop/new/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/dnolan/Desktop/new/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/dnolan/Desktop/new/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Any help would be greatly appreciated!
Thanks!

---

### Post by dudestir on 2007-05-22
This link worked for me

[http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/]("http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/")

The key was 

2. Download the patch
# wget -q [http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.19.diff](http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.19.diff)

3. Change to the vpnclient diretory
# cd vpnclient

4. Apply the patch
# patch <../vpnclient-linux-2.6.19.diff

---

### Post by dans on 2007-05-24
I am successfully running Cisco VPN Client v4.8 with Feisty and wireless on Network Manager.

However, sometimes I get the results you posted, and they are unexplained.

What is working for me right now is to load the module -- cd ~ then type  "sudo /etc/init.d/vpnclient_init start" -- then start vpn -- cd to /bin then type "sudo vpnclient connect <profile> user <username> eraseuserpwd".  The param eraseuserpwd forces you to type your password each time you log in, but it seems to make everything more reliable.  Then every time I disconnect -- cd /bin type "sudo vpnclient disconnect" --, then I also unload the module right away -- cd ~ type "sudo /etc/init.d/vpnclient_init stop".

Cisco FAQ says that once you have the connection up you can type Ctrl+Z, then "bg", to put the vpn connection in the background and keep using the terminal window.

If anyone knows how to set up routing with Cisco I'd love to hear.  The preconfigured pcf files from my client take over all traffic, breaking my email and IM connections which is annoying.  I'd like to limit the cisco vpn to one series of IP addresses and one set of domains.

---

### Post by yevad76 on 2007-06-05
> **jester805 said:**
> I'm new to this, but I downloaded the Linux VPN client from Cisco's site.  I tried to run the installer (with the default options) and it errored out on me twice.
Making module
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/dnolan/Desktop/new/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
CC [M] /home/dnolan/Desktop/new/vpnclient/linuxcniapi.o
/home/dnolan/Desktop/new/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/dnolan/Desktop/new/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/dnolan/Desktop/new/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


Any help would be greatly appreciated!
Thanks!

I am having this same problem.  anyone find a solution to this?  any help is great appreciated.

---

### Post by ZERO_SHIFT on 2007-06-06
Did you try to patch with the method mentioned in one of the previous posts?

---

### Post by gatdammit on 2007-06-07
I tried this patch.. but it doesn't patch it just hangs...

---

### Post by WhimpyPeon on 2007-06-07
If you are using a passphrase and nothing fancy you might want to look into vpnc.  I have found it is much easier to use.

sudo apt-get install vpnc

edit
/etc/vpnc/vpnc.conf

should be something like:
IPSec gateway your_cisco_ip_address
IPSec ID your_vpn_group
IPSec secret your_vpn_group_password
Xauth username your_Xauth_username

Then:
sudo vpnc-connect

You will be prompted for your Xauth password.  Bingo you are in!

To disconnect:
sudo vpnc-disconnect

Granted, this is assuming that your setup is similar to this.  I really haven't tried anything complicated like certificates though.  I have used it on PIX and ASA devices without any problems.

---

### Post by cipher99 on 2007-06-13
> **dudestir said:**
> This link worked for me

[http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/]("http://www.tuxx-home.at/archives/2006/12/07/T09_36_48/")

The key was 

2. Download the patch
# wget -q [http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.19.diff](http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.19.diff)

3. Change to the vpnclient diretory
# cd vpnclient

4. Apply the patch
# patch <../vpnclient-linux-2.6.19.diff


I have tried both the patch for 2.6.19 and for 2.6.22 and neither works with my 2.6.20
Has anyone found a patch for 2.6.20, or any other way to get Cisco VPN installed with this kernel?

---

### Post by WhimpyPeon on 2007-06-15
Are you using anything more than preshared keys?

Really this kernel "mucking around" is why I abandoned the Cisco clients.  Every new kernel you would have to rebuild the Cisco client, trouble with patches...

If it is just PSK auth I HIGHLY recommend vpnc, it works great.

---

### Post by prkfriryce on 2007-07-18
> **melcloud said:**
> I had the same problem before.

I found a solution:

type ifdown eth0 (assume you wire connection is eth0) before you use vpnclient

This will fix the problem.

ahhh.. even if you are physically connected via eth1, vpnclient by default automatically checks eth0. So, after I unplumbed eth0, I was able to connect via eth1.

```
eth0      Link encap:Ethernet  HWaddr 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:505 dropped:0 overruns:0 carrier:1010
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:806 (806.0 b)
          Interrupt:21 Base address:0xc800 

eth1      Link encap:Ethernet  HWaddr   
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
```

:guitar:

---

