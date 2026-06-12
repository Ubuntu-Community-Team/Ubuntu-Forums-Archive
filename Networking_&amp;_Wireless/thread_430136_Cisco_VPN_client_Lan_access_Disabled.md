---
title: "Cisco VPN client: Lan access Disabled"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by exidez on 2007-05-01
Hi
I am having problem with the VPN client. I have managed to install it all correctly and connect to the VPN but i cannot access the lan.
There is a message that says LAN access Disabled.

How do i enable it?
I beleive the problem is on my side

---

### Post by strongmantim on 2007-05-04
That's impressive. How'd you get it installed?? I'm running Ubuntu 7.04 but only have Cisco VPN Client 4.6.00.0045-k9.

---

### Post by exidez on 2007-05-06
my origional post here will help you
[http://ubuntuforums.org/showthread.php?t=428263](http://ubuntuforums.org/showthread.php?t=428263)

---

### Post by aranoyas on 2007-12-10
you will not become access to local lan if an administrator of cisco box you connecting to has disabled tunnel splitting (client settings of  EnableLocalLAN does not matter) :mad:

after short inspection of vpnclient-4.8.00.0490-k9 i wrote a simple patch that overrides settigs of cisco box giving you the local lan back:

[FONT="Courier New"]--------------------------------------------------------------------------------------------------------
--- vpnclient-4.8.00.0490-k9.orig/interceptor.c 2007-12-11 03:22:01.000000000 +0100
+++ vpnclient-4.8.00.0490-k9/interceptor.c      2007-12-11 03:26:44.000000000 +0100
@@ -644,8 +644,12 @@
 
         break;
     case CNI_DISCARD:
+       /* override local lan access */
+        rc2 = original_ip_handler.orig_handler_func(skb, dev, type);
+       /*
         dev_kfree_skb(skb);
         rx_dropped++;
+        */
         break;
     default:
         printk(KERN_DEBUG "RECV: Unhandled case in %s rc was %x\n",
@@ -757,8 +761,12 @@
         /* packet dropped */
         else
         {
+           /* override local lan access */
+            rc2 = pBinding->InjectSend(skb, dev);
+            /*
             dev_kfree_skb(skb);
             tx_dropped++;
+           */
         }
         break;
     case CNI_CHAIN:
--------------------------------------------------------------------------------------------------------
[/FONT]

do not forget to restore a routing table and resolv.conf after connecting to vpn box:

[FONT="Courier New"]root@localhost:/usr/src> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

root@localhost:~> vpnclient connect xxx
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.23.9 #2 SMP PREEMPT Fri Dec 7 21:55:21 CET 2007 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Enter Certificate password: 
Initializing the VPN connection.
Contacting the gateway at xxx.xxx.xxx.xxx
User Authentication for xxx

Enter Username and Password.

Username [xxxx]: 
Password []: 
Authenticating user.
Negotiating security policies.
Securing communication channel.

Welcome to bla bla bla

Your VPN connection is secure.

VPN tunnel information.
Client address: xxx.xxx.xxx.xxx
Server address: xxx.xxx.xxx.xxx
Encryption: 168-bit 3-DES
Authentication: HMAC-SHA
IP Compression: None
NAT passthrough is active on port UDP 4500
Local LAN Access is disabled

root@localhost:/usr/src> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
cisco.box.remote.ip    192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
vpn.net.addr.0        0.0.0.0         255.0.0.0       U     0      0        0 cipsec0
0.0.0.0         your.client.vpn.ip   0.0.0.0         UG    0      0        0 cipsec0

root@localhost:/usr/src> route del -net 0.0.0.0 dev cipsec0
root@localhost:/usr/src> route add -host 192.168.1.1 dev wlan0
root@localhost:/usr/src> route add default gw 192.168.1.1
root@localhost:/usr/src> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 wlan0
cisco.box.remote.ip    192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
vpn.net.addr.0        0.0.0.0         255.0.0.0       U     0      0        0 cipsec0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0[/FONT]

assuming 192.168.1.1 is an address of you gateway and wlan0 is a primary network interface

enjoy
:guitar:

---

### Post by Vekin on 2007-12-11
I have the same problem.  How do you even use that patch?  I'm really new to this.

---

### Post by aranoyas on 2007-12-11
I assume you are familiar with installation of cisco vpn client software on linux.
All you need to do is simple additional step during the installation.
You will need an original client distribution. It can be taken here: [http://tuxx-home.at/vpn/Linux/vpncli...0490-k9.tar.gz](http://tuxx-home.at/vpn/Linux/vpncli...0490-k9.tar.gz)
You should also apply a patch for newest kernels:
[http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff](http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff)
My patch is attached to this post.

1. Download the client
# wget [http://tuxx-home.at/vpn/Linux/vpncli...0490-k9.tar.gz](http://tuxx-home.at/vpn/Linux/vpncli...0490-k9.tar.gz)

2. Untar the VPN Client
# tar xzf vpnclient-linux-4.8.00.0490-k9.tar.gz

3. Change to the vpnclient directory
# cd vpnclient

4. Download the kernel fix patch
# wget -q [http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff](http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff)

5. Apply the kernel fix patch
# patch < vpnclient-linux-2.6.22.diff
patching file frag.c
patching file interceptor.c
patching file IPSecDrvOS_linux.c
patching file linuxcniapi.c
patching file linux_os.h

5. Download the override-local-lan-access.diff.gz into current directory

6. Unpack it
# gunzip override-local-lan-access.diff.gz

7. Apply it
# patch < override-local-lan-access.diff
patching file interceptor.c

Now the patches has been applied and you can safely install the client
#./vpn_install

---

### Post by jflaker on 2007-12-13
> **exidez said:**
> Hi
I am having problem with the VPN client. I have managed to install it all correctly and connect to the VPN but i cannot access the lan.
There is a message that says LAN access Disabled.

How do i enable it?
I beleive the problem is on my side

Although you have set your options to allow access to your LAN....The LAN Security setup on the remote side has policies which are applied to your client based on your user's ID AND/OR group.  The policies from the remote side will always supersede your settings regardless of what you do.

You would need to have the settings changed from the remote side.  The recommended settings for the remote is to disable LAN access to prevent infection from jumping from another computer on the LAN over into the remote LAN.

I hope this answers the question.

(user of Cisco VPN client)

---

### Post by aranoyas on 2007-12-14
> **jflaker said:**
> Although you have set your options to allow access to your LAN....The LAN Security setup on the remote side has policies which are applied to your client based on your user's ID AND/OR group.  The policies from the remote side will always supersede your settings regardless of what you do.

You would need to have the settings changed from the remote side.  The recommended settings for the remote is to disable LAN access to prevent infection from jumping from another computer on the LAN over into the remote LAN.

I hope this answers the question.

(user of Cisco VPN client)

Oh!!!, a cisco man :)

There is an excellent firewall in linux kernel to prevent evil "infection from jumping from another computer on the LAN over into the remote LAN". It is not a business of some client software, i use just to connect to somewhere, to prevent me to use my network printer, access my nas drive or listen to my preferred internet radiostation.

I`m sorry, if you are not a "cisco man". 
Look, how about just to try the patch and see if it works, instead of saying something like  "you have no choice if big and wise cisco has decide you cannot access you lan".
I think it is simple enough to use, even for linux newbies.

(user of linux)

---

### Post by sansadk on 2008-01-06
> **jflaker said:**
> Although you have set your options to allow access to your LAN....The LAN Security setup on the remote side has policies which are applied to your client based on your user's ID AND/OR group.  The policies from the remote side will always supersede your settings regardless of what you do.

You would need to have the settings changed from the remote side.  The recommended settings for the remote is to disable LAN access to prevent infection from jumping from another computer on the LAN over into the remote LAN.

I hope this answers the question.

(user of Cisco VPN client)

Hi There,

I am using the same profile under ubuntu that I use under Windows. The profile under windows works and it provides me LAN access (I can access any computer in my office network without any problem). However, the same profile doesnt seem to work under ubuntu. It gives me "LAN access disabled" message.

So, if you say that the settings needs to be changed on the remote side, then I should have seen a similar behavior under windows, right?

Attached is my profile. Im using client version 4.8.01 (I did not apply any patches):

[main]

Description=

Host=xxx.xxx.xxx.xxx

AuthType=1

GroupName=remote

GroupPwd=

enc_GroupPwd=8CB7329BA2C97D444A40D4
D17B0AE6A912D4B0A8BC4FAC494BB42014D2E54FB199AD38E06855D4A537FC61485F83FA6C36D5A5AA8BDEC6

EnableISPConnect=0

ISPConnectType=0

ISPConnect=

ISPPhonebook=

ISPCommand=

Username=xxxx

SaveUserPassword=0

UserPassword=

enc_UserPassword=

NTDomain=

EnableBackup=0

BackupServer=

EnableMSLogon=1

MSLogonType=0

EnableNat=1

TunnelingMode=0

TcpTunnelingPort=10000

CertStore=0

CertName=

CertPath=

CertSubjectName=

CertSerialHash=00000000000000000000000000000000

SendCertChain=0

PeerTimeout=480

EnableLocalLAN=1

---

### Post by LoneSt4r on 2008-01-08
> **aranoyas said:**
> I assume you are familiar with installation of cisco vpn client software on linux.
All you need to do is simple additional step during the installation.
You will need an original client distribution. It can be taken here: [http://tuxx-home.at/vpn/Linux/vpncli...0490-k9.tar.gz](http://tuxx-home.at/vpn/Linux/vpncli...0490-k9.tar.gz)
You should also apply a patch for newest kernels:
[http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff](http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff)
My patch is attached to this post.

1. Download the client
# wget [http://tuxx-home.at/vpn/Linux/vpncli...0490-k9.tar.gz](http://tuxx-home.at/vpn/Linux/vpncli...0490-k9.tar.gz)

2. Untar the VPN Client
# tar xzf vpnclient-linux-4.8.00.0490-k9.tar.gz

3. Change to the vpnclient directory
# cd vpnclient

4. Download the kernel fix patch
# wget -q [http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff](http://tuxx-home.at/projects/cisco-vpnclient/vpnclient-linux-2.6.22.diff)

5. Apply the kernel fix patch
# patch < vpnclient-linux-2.6.22.diff
patching file frag.c
patching file interceptor.c
patching file IPSecDrvOS_linux.c
patching file linuxcniapi.c
patching file linux_os.h

5. Download the override-local-lan-access.diff.gz into current directory

6. Unpack it
# gunzip override-local-lan-access.diff.gz

7. Apply it
# patch < override-local-lan-access.diff
patching file interceptor.c

Now the patches has been applied and you can safely install the client
#./vpn_install

I just tried it and it did miracles in my case!  I have access to all I need.

Just don't forget to update the routing table and the /etc/resolv.conf file.  I had to use the remote nameserver FIRST and my local nameserver SECOND for the setup to work.

I just love Ubuntu...  It makes our lives so easy.

LoneSt4r

---

### Post by L8erG8er on 2008-02-25
> **jflaker said:**
> Although you have set your options to allow access to your LAN....The LAN Security setup on the remote side has policies which are applied to your client based on your user's ID AND/OR group.  The policies from the remote side will always supersede your settings regardless of what you do.

You would need to have the settings changed from the remote side.  The recommended settings for the remote is to disable LAN access to prevent infection from jumping from another computer on the LAN over into the remote LAN.

I hope this answers the question.

(user of Cisco VPN client)

This is an old thread, and I don't know if anyone will read it, but jflaker makes a valid point.  The script above may indeed override the LAN access disable, but if you're connecting to your company's network, be careful!!  They disabled the LAN access for a reason on their end, and for me personally, I would rather have my job than bypass their security.

You can always VPN into your company's network, then change your browser's network settings to use their proxy and have internet through them.

---

### Post by serrs on 2008-04-08
It'd be awesome if someone could make a patch for the vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz version.  

I attempted and it removed all networking just by loading the kernel module.  ;)

---

