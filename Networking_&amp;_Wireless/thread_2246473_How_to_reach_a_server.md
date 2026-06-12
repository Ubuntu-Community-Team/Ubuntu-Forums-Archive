---
title: "How to reach a server?"
date: 2014-10-01
forum: Networking &amp; Wireless
---

### Post by ELMIT on 2014-10-01
I got a special challenge:

I have setup an Ubuntu Server locally. This server (no graphic) will be moved to another place. How can I reach that server?
I do not know the IP address of that new place. And the people there are farmers and now exactly that much about computers!

I am looking for a more or less plug and play solution.

Teamviewer could work, but I have no graphic, or does Teamviewer also work without graphic?

I could use a dyndns service. Which one would you recommend and how to setup this on the server?
Here I still face the challenge, that the router must forward the port 22 to the machine.

---

### Post by TheFu on 2014-10-01
I've never done it, but look into ssh reverse connections. That might work.  Without the ability to open a port on the router, you are fighting an uphill battle. If you are providing the router too, then you could pre-configure that stuff and just need a ping-tool to know which IP it ends up at.

Also - load fail2ban, don't listen on port 22, and only use key-based ssh authentication. [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

---

### Post by Lars Noodén on 2014-10-01
> **TheFu said:**
> I've never done it, but look into ssh reverse connections. That might work.  Without the ability to open a port on the router, you are fighting an uphill battle. If you are providing the router too, then you could pre-configure that stuff and just need a ping-tool to know which IP it ends up at.

Also - load fail2ban, don't listen on port 22, and only use key-based ssh authentication.

For reverse connections you do need a second server or other machine with a stable address, either hostname or ip address.  The hostname can be dynamic, that doesn't matter, just as long as the farmers' machine can reach it.  I've used reverse  connections, they are not hard.   But if you use them, you will either need an automated connection so that the connection comes up when the machine boots or else something for the farmers to run or click on that can be done by following instructions on a paper or something.  

It is less complex to just use a dynamic DNS hosting service and then just log into their machine as needed.  DynDNS is gone, as a free service, but thete are others:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

There is a script you can install and configure to keep the machine's address up to date.  It is called ddclient and is in the repository.  Though with some services you should be able to get away with plain wget.  Here is an example (don't mind the other text)

[http://wiki.ubuntu-fi.org/Dynaaminen_DNS](http://wiki.ubuntu-fi.org/Dynaaminen_DNS)

And +1 for keys and such.  The service will be found and probed regardless of port, but the logs will be quieter.

---

### Post by Hugo_Serrano on 2014-10-01
Hi!

You have here an example of the reverse ssh tunnel.
[http://www.alexonlinux.com/reverse-ssh-tunnel-or-connecting-to-computer-behind-nat-router](http://www.alexonlinux.com/reverse-ssh-tunnel-or-connecting-to-computer-behind-nat-router)

If you don't have a server with static IP, you can do this with dynamic DNS on both sides and a cronjob running on the machine @farm every 30 min or so. You can do a script to check if there's a connections, and if not, create one and run it every 30 min or so.

Just and idea!

Cheers,
Hugo.

---

### Post by SeijiSensei on 2014-10-01
I solved this problem with OpenVPN using a shared private key.  The remote machine was configured as an OpenVPN client that started at boot.  When the machine came up, it connected to my public server in the cloud.  Then I had a full-time tunnel to the remote machine.

SSH tunneling is an alternative, but I like having a full connection to the remote machine rather than just a few forwarded ports.

---

### Post by TheFu on 2014-10-01
I'm loving all this help!  

All these solutions mandate 1 side of the connection having a static IP.  The "server" must have a static IP on the LAN, regardless.

OpenVPN may be more complex than wanted, but in a simple configuration, it is relatively easy. The farmers would be the client and you would run the server. Wish my openvpn setup were just simple (not multi-user, multi-access restricted) one. Alas, there are different classes of users who need access to different internal subnets which mucks up the configuration.

My intent with the reverse ssh connection was just for the initial install - I'd use that to setup normal ssh server, dynamic-DNS and open the firewall/router port from the inside. Then it would be a normal ssh connection going forward.  There are many interesting ssh settings that are helpful for this stuff. [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh) - like changing the timeout or auto-reconnect.

When I needed to do this with "Mom's" system, I just lived without remote access for the month before I could get there and set things up. There was a Windows-nerd onsite, but he wasn't ready to handle editing network files or forwarding router ports. It was best that everything waited until I could get there.

BTW - DNS services are about $20/yr, so not completely unreasonable if a paid version is needed.  I've seen VPS servers for $14/yr, if the reverse ssh as a proxy needs a server on the internet to connect.

---

### Post by Lars Noodén on 2014-10-01
> **TheFu said:**
> All these solutions mandate 1 side of the connection having a static IP.  The "server" must have a static IP on the LAN, regardless.

Yes, the server should have a static ip or hostname, I guess that's part of the usual definition of a server, but even if it doesn't the OpenVPN and reverse SSH options can get by with ELMIT's having even a dynamic DNS address.

---

### Post by TheFu on 2014-10-01
> **Lars Noodén said:**
> Yes, the server should have a static ip or hostname, I guess that's part of the usual definition of a server, but even if it doesn't the OpenVPN and reverse SSH options can get by with ELMIT's having even a dynamic DNS address.

Correct as usual, Lars.  

I don't assume people have just 1 or 2 devices on a network. 

All my machines/VMs get static IPs on their home network. If they need DHCP (laptops and other portable devices or where the setting page sucks to use (roku, entertainment devices, etc), then DHCP reservations are setup on the router.  Only guest devices or freshly installed VMs use floating DHCP addresses on our network. It makes all sorts of things easier - mainly DevOps stuff like centralized patching, but NFS, CIFS, remote desktops, the list can go on and on and on.

---

### Post by sandyd on 2014-10-01
> **SeijiSensei said:**
> I solved this problem with OpenVPN using a shared private key.  The remote machine was configured as an OpenVPN client that started at boot.  When the machine came up, it connected to my public server in the cloud.  Then I had a full-time tunnel to the remote machine.

SSH tunneling is an alternative, but I like having a full connection to the remote machine rather than just a few forwarded ports.

+1 for OpenVPN

If you dont have another server with OpenVPN, you can just rent a VPS for around $3-4/mo.

---

### Post by ELMIT on 2014-10-20
> **SeijiSensei said:**
> I solved this problem with OpenVPN using a shared private key.  The remote machine was configured as an OpenVPN client that started at boot.  When the machine came up, it connected to my public server in the cloud.  Then I had a full-time tunnel to the remote machine.

SSH tunneling is an alternative, but I like having a full connection to the remote machine rather than just a few forwarded ports.

Can you guide me how to setup OpenVPN for that?

I have to connect to multiple such remote machines.
What do I need to install on the remote machine, what on the remote server and what on my machine, which wants to reach the remote machines?

A        B        C        (Remote machines)
 \        |       /
    \     |     /
       \  |  /
    Remoter server with fix IP
          |
          |
          |
        Nat   (with fixed public IP)
          |
  My home computer

Which ports do I need to open and where?

---

### Post by TheFu on 2014-10-20
Oops - didn't re-read the 2week old issue before posting this morning. Removed bad assumptions below:

You'll need to ensure the private LAN address for A, B, C are not on the same subnet as your home computer ... so the routing tables can be worked out with the VPN. I've moved my entire home subnet to the 172.22.x.x to avoid VPN conflicts like this - most business will use 10.x.x.x or 192.168.x.x addresses.

---

### Post by ELMIT on 2014-10-20
Now, I am totally lost!!!

Do you mean A, B, C, .... must have also internal LAN different IPs?
Or do you mean:

A:   192.168.1.10   router: 192.168.1.1
B:   192.168.2.10   router: 192.168.2.1
...
Server:   A.B.C.D
Home: 192.168.178.100  router: 192.168.178.1

I am planning to follow this guide: [https://help.ubuntu.com/14.04/serverguide/openvpn.html](https://help.ubuntu.com/14.04/serverguide/openvpn.html)
What do I need to change ?
I assume my targets are clients and me also a client, while the public IP address server is the server.

---

### Post by TheFu on 2014-10-20
"My home computer" needs to have a different NAT/private IP subnet than the other computers (remote server, A, B, C) so the routing can be worked out. I've setup ovpn where the server had a different subnet than the target machines ... but that isn't what you are trying to do here (you're going exactly backwards) ... so I don't think the A, B, C even need to know about ovpn at all beyond using "remote server" as their gateway / dhcp / device.  

If the remote server is only for this sort of access, I'd deploy pfSense (which is NOT linux) on it. A $100 box can do this stuff.

To avoid confusion going forward, please update the diagram and label EVERY COMPUTER and networking device (routers/switches) on it clearly with a unique name, expected IPs + subnet netmask and any other information you think is relevant.  I'm partial to C.xx for ovpn clients where the .xx is the last part of the IP and S.xx for the ovpn server and r/s.xx for the routers and managed switches (unmanaged switches don't have any IPs/subnets) on both sides of the device.  Of course, do what makes sense to you and we can adjust.

Basically, you want to setup a site-to-site VPN that the desktops know nothing about. Very doable. [http://www.youtube.com/watch?v=OeYtoM2VSzI](http://www.youtube.com/watch?v=OeYtoM2VSzI) is for pfSense and show all the needed steps to setup the site-to-site ovpn with a static server and remote client. Of course, it doesn't show how to install/configure pfSense, but that is relatively simple.
Other home-type routers capable of running after-market firmware can do this too ... like  dd-wrt - [http://www.dd-wrt.com/phpBB2/viewtopic.php?p=748720](http://www.dd-wrt.com/phpBB2/viewtopic.php?p=748720)  It keeps the client PCs out of the VPN business.  Of course, using Ubuntu for this is also possible, but it is usually easier in the long term to have the router do the ovpn stuff when multiple client machines are involved too.  Just my opinion.

Of course, the issue with site-to-site is that not only can you see their network, but they can see yours, so definitely setup any firewall rules to protect your network from them as you see fit.

---

### Post by ELMIT on 2014-10-20
Only my home computer and server exists. Others we can chose:

A is connected to a router with DHCP, and from there to the Internet. Any further computer set B, C, D ... will do the same:

/----------\
| Internet | Ubuntu 14.04 server edition
\----------/
. . . |
. . . |
. . . |   dynamic IP
/----------\
| . router .|
\----------/  DHCP
. . . |
. . . |
. . . |   192.168.x.10
/----------\
| . . A . . .|
\----------/




/----------\
| Internet |
\----------/
. . . |
. . . |
. . . |   Fix IP address  a.b.c.d
/----------\
| . server .|
\----------/



/----------\
| Internet |
\----------/
. . . |
. . . |
. . . |   fix IP
/----------\
| . router .|
\----------/  DHCP
. . . | |----------- other computers (dynamic IP), VoIP phones, wireless devices, ...
. . . |
. . . |   192.168.172.100
/----------\
| . home . |
|computer | Ubuntu 14.04 Desktop edition
\----------/


They don't want to use pfSense.

Nobody is working on the remote PCs.
Preferable run from a USB thumb drive, that I can send them.
Preferable remote logging to my home computer.

I wish they would send me the PCs, but that is not an option, so I have to run that system 12,000 km away with people (literally farmers) who know Linux from the news paper, ...

---

### Post by SeijiSensei on 2014-10-21
Let me describe my arrangement as a starting point.

I maintain cloud-based servers at Linode.  One of them works as my VPN hub.  It runs OpenVPN with a .conf file for each of the tunnels it maintains with other machines.  On this "server" machine, the configuration files look like this:
```

dev tun
ifconfig 10.0.0.1 10.0.0.10
secret /etc/openvpn/keys/my.key
port 12345
user nobody
group nogroup
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key

```
There is one file like this for each tunnel, with a common source IP (10.0.0.1) and different target IPs for each remote machine.  Each tunnel also uses a different port.  I created a private key with "sudo openvpn --genkey --secret /etc/openvpn/keys/my.key".  (I created the "keys" subdirectory; it's not part of a vanilla installation.)

I then copied the key to the same directory on each remote, and copied the configuration file as well.  I make two changes to the file on the remote.  One is to add 
```
remote ip.of.my.server
```
which tells the remote to connect to the server at boot.  The second change reverses the order of the IP addresses in the "ifconfig" statement.

The server's firewall must permit UDP traffic on each port you use.  If the remote machines have static IP addresses, you can configure iptables to only allow those machines to connect to the server. 

If, as it appears, your local connection has a fixed address, you can use your local machine instead of a cloud server like I have. Configure your local router to allow inbound UDP traffic on the appropriate ports, then configure "port forwarding" on the router to send the traffic back to your server.

If the remotes you need to configure are already in the field, installing all this may be a pretty complex task.  You could write a little bash script like this:
```

#!/bin/bash

apt-get install -y openvpn
mkdir /etc/openvpn/keys
cp mykey.key /etc/openvpn/keys
cp myconf.conf /etc/openvpn
reboot

```
and store the script, key, and configuration file on a USB key.  You'll still have to walk someone through the process of plugging in the USB device, finding its mount point, and running "sudo /path/to/mount/point/install.sh" or whatever you named the installation script.

---

### Post by ELMIT on 2014-11-05
I try to follow this tutorial to setup openvpn: [https://help.ubuntu.com/14.04/serverguide/openvpn.html](https://help.ubuntu.com/14.04/serverguide/openvpn.html)

sudo apt-get install openvpn easy-rsa

mkdir /etc/openvpn/easy-rsa/
sudo cp -r /usr/share/easy-rsa/* /etc/openvpn/easy-rsa/

sudo gedit /etc/openvpn/easy-rsa/vars
export KEY_COUNTRY="TW"
export KEY_PROVINCE="TW"
export KEY_CITY="Taipei"
export KEY_ORG="Elmit"
export KEY_EMAIL="ronald@me.com"
export KEY_OU="MyRemoteServersUnit"
# If you'd like to sign all keys with the same Common Name, uncomment the KEY_CN export below
# You will also need to make sure your OpenVPN server config has the duplicate-cn option set
export KEY_CN="MyRemoteServersUnit"


cd /etc/openvpn/easy-rsa/
source ./vars
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/keys

sudo ./clean-all
sudo ./build-ca
  Please edit the vars script to reflect your configuration,
  then source it with "source ./vars".
  Next, to start with a fresh PKI configuration and to delete any
  previous certificates and keys, run "./clean-all".
  Finally, you can run this tool (pkitool) to build certificates/keys.


Whatever I try I come always to this output.

---

### Post by ELMIT on 2014-12-07
Thank you very much! It works!
They did not turn on the server so I could not verify it earlier.

I got an additional challenge to it:
I can make a simple web site with status of the server on that server. However, only I can reach it. My first thought was to use iframe, but iframe with an web address 10.8.x.x would not be reachable again.
How can I get this done?

---

