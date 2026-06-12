---
title: "Network only available in LiveCD mode"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by philipf on 2006-09-13
Im at a loss trying to get my network to work in Dapper.

(I have tried a couple of settings mentioned in this forum, such as blacklist ipv6 and static IP addresses but it doesn't seem to work for me)

I am able to ping another host for short while (30 seconds or so) after a restart or pulling and putting my network cable back.

After a while I am getting: Destination host unreachable
Calling ifdown eth0 and ifup eth0 doesn't have the same effect as pulling the cable...

Possible points of interest:
**1. Networking works perfectly in LiveCD mode, only stops to work after installing Dapper from the LiveCD**
2. Network settings used to work in Breezy.
3. Using out of the box network settings (DHCP)

Can I perhaps copy config files from the LiveCD to my installed version to sort this problem or is there another solution?  (Which config files would these be....)

Regards,
Philip Fourie

---

### Post by tbonius on 2006-09-13
Wow.. that is strange.  Are you doing updates after you install Dapper?  What driver module does your card use?  Are there any kernel messages realted to your network connectivity? (dmesg).  What happens if you unload the driver module.. reload it.. and run dhclient on eth0?  What (who) is your DHCP server?  You shouldnt need statics.

T

---

### Post by philipf on 2006-09-13
>  Are you doing updates after you install Dapper?
Couldn't get that far, before being able to update the network dies.


> What driver module does your card use? What happens if you unload the driver module.. reload it.. and run dhclient on eth0?
You lost me. :) I am a newbie. How do I determine that and how do I unload it?


> Are there any kernel messages realted to your network connectivity? (dmesg).

Output from dmesg: (Is the problem the IPv6 router issue?)
dmesg | grep eth0
[4294692.915000] eth0: Davicom DM9102/DM9102A rev 49 at 0001e800, 00:80:AD:7A:60:BB, IRQ 193.
[4294696.666000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[4294721.568000] eth0: no IPv6 routers present


> What (who) is your DHCP server?
The DHCP server is an old Linux Fedora 2 installation which I am trying to replace with Ubuntu.  This Fedora machine currently serves as DHCP server for a small Windows network.

Thanks so far,
Philip

---

### Post by tbonius on 2006-09-13
You lost me.. youre replacing your Fedora machine with Ubuntu and also using it as a DHCP server.. as well as it needs a DHCP address? Or the DHCP server is a seperate system?

Run lsmod.. what modules are loaded.

Post your /etc/network/interfaces file.

Post your dhcpd.conf file

T

---

### Post by philipf on 2006-09-14
Sorry for the confusion.  Lets keep the setup simple.  I have a seperate Fedora 2 DHCP server and this new Ubuntu DHCP client.  With LiveCD the Ubuntu client obtained its IP from the Fedora server but that this no longer wants to work after installing Ubuntu on the client. (I haven't made any changes to the Fedora DHCP server either). 

For step 1, I don't want to install DHCP server on the Ubuntu client.

It is using **tulip **as the network driver

Here is my **interfaces **file
-----------------------------------------------
[FONT="Courier New"]cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
sent[/FONT]
-----------------------------------------------

Here is the Fedora server's dhcpd.config
----------------------------------------->>
[FONT="Courier New"]ddns-updates on;
use-host-decl-names on;
option time-servers 192.168.0.20;
option ntp-servers 192.168.0.20;
option routers 192.168.0.20;

option domain-name "mydomain.com";
option domain-name-servers 192.168.0.20;
ddns-update-style ad-hoc;

# xxx Network
subnet 192.168.0.0 netmask 255.255.255.0 {
        ddns-rev-domainname "mydomain.com";
        ddns-updates on;
        range dynamic-bootp 192.168.0.2 192.168.0.19;
        }
authoritative;
# yyyyy
host yyyyy{
        fixed-address 192.168.0.18;
        }
# Print
host NPI997C89 {
        fixed-address 192.168.0.13;
        }
--------------------------------------------------<<[/FONT]

Is it possible my default gateway is a problem, my DHCP server is 192.168.0.20?

[FONT="Courier New"]------------------------------------------------>>
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.20    0.0.0.0         UG        0 0          0 eth0
-------------------------------------------------<<[/FONT]



Thanks again,
Philip

---

### Post by satano on 2006-09-14
Hello

I have the same problem.

I have a 3Com900 Combo ethernet card, and D-com aDSL Router v3. Router is connected to the card and it's IP is 192.168.1.1. Router also acts as a DHCP server, which assignes IP to my computer.

When I used Ubuntu 5.10, started LiveCD and in Administration->Networking set up gateway to 192.168.1.1 (eth0 was set to DHCP), internet worked OK. I did not set up anything else, just installed Ubuntu. After installation, the network settings was set up as I set it in live mode - eth0 to DHCP and gateway to 192.168.1.1, but the internet did not work.

I downloaded Ubuntu 6.06 and hoped the things will be ok, but it's worse. Now my internet connection is not working in both, the live CD and the installed system. :(

A friend of mine has this problem on his notebook and as he says, it helped him to add **noapic** and **nolapic** to boot parameters. This did not make any change to me.

Does anybody know what's going on?

Thanks, Stano

---

### Post by tbonius on 2006-09-14
The default gateway should not make a difference as long as .20 actually functions as a gateway.  Are you able to assign a static at all and get any sort of connectivity.. can you ping your gateway?

T

---

### Post by satano on 2006-09-14
Hi.

No, I cannot get any connectivity even if I assign a static IP. I also cannot ping my router.

---

### Post by tbonius on 2006-09-14
And you are sure your card uses the tulip module?  Is this an older DEC chipset?  What about using the forcedeth module?  What exact chipset is this network card?

T

---

### Post by satano on 2006-09-14
Unfortunately, I cannot answer all your questions. I don't know the chipset. I's not in the manual and I was not able to find it on the internet.

I loaded the tulip module and after forcedeth module, but still nothing.

S.

---

### Post by tbonius on 2006-09-14
It would help to know more infor about the ethernet card.  It might help to disable IPv6.  Theres a thread going around about this:

[http://ubuntuforums.org/showthread.php?t=254625](http://ubuntuforums.org/showthread.php?t=254625)

What kind of motherboard is this?  Is the ethernet controller integrated?  Can you look it up online?  Can you pull the cover off and look?

T

---

### Post by philipf on 2006-09-15
Hi Tbonius,

Thank you for your effort and help!

I managed to get my setup to work by replacing the ethernet card with another.

Looking at the old card, which was removed from a Dell Dimension 8200, it seems to be a Davicom/Cnet chipset 100Mb card. I guess Ubuntu didn't like that card for some reason...

Much appreciated,
Philip

---

### Post by bhdenterprises on 2006-09-15
i know this seems to late, but i believe there is already a fix with the Davicom chips not working with Ubuntu. If your network card manufacturer uses Davicom chips in their NICs, most likely it will not work in an Ubuntu installation as it seems that Davicom still uses 'dmfe' drivers instead of tulip. 

please try this link: [ How to fix problem with Davicom ethernet adapter]("http://ubuntuforums.org/showthread.php?t=186430") and post here the results.. It works for me all the time... I used three Cnet 200Pro Fast Ethernet PCI adapter on my box.

Although you have resolved the problem, if this works with you, you could still use the Cnet card and return the card you replace it with to its old box. :D 

cheers!

---

