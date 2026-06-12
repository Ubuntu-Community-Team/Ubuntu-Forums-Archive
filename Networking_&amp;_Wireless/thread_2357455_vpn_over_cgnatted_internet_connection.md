---
title: "vpn over cgnatted internet connection?"
date: 2017-04-02
forum: Networking &amp; Wireless
---

### Post by nginmu on 2017-04-02
My setup is:

Huawei B593 mobile 4g router with uk EE PAYG SIM card giving me 20-odd ms ping figures & 15 Meg up & down speed, 
connected via it's 1st wired LAN port to eth0 on a laptop running Lubuntu

All works fine. All set up on a 12V battery connected to a solar panel in a field on my farm.

I am having trouble remotely accessing the IP cameras I've connected round the farm though, from a remote location.

I can't dial into the router's IP address from a computer out on the Internet to access the video stream from the cameras, because EE use something called carrier-grade NAT (CGNAT). This seems to mean that whilst I do have something claiming to be my Internet IP, that the router is happily showing me, that EE have assigned to my net connection, it is only valid as far as handshaking direct with EE. Once EE have done dealing with my traffic, it ends up being presented by them to the public Internet under a completely different (and unknown to me) genuine IP address.

Apparrently this is getting to be the norm these days with a lot of providers, as IPv4 address space becomes squeezed.

I also tried as an experiment, setting up an FTP server on the farm's laptop, with port forwarding appropriately set up on the farm's simcard router to the Lubuntu laptop running the server.

Remote tests revealed that whilst the target IP address I had noted down from the router was basically 'up', it was not responding to any pings or port probes. As noted above, whatever was actually on that IP probably wasn't my machine anyway.

I've heard of an animal known as a VPN, and I read you can set one up on linux quite easily. What I'm wondering is, would a VPN be able to overcome CGNAT and allow me to remotely gain access to the farm network, and thereby be able to view the farm LAN's camera feeds?

Or does CGNAT just kill everything dead with no hope.

Thanks for any info..

[edit] - link to background info: [https://community.ee.co.uk/t5/4G-and-mobile-data/Incoming-Connections-4G-PAYG/m-p/549836#M113929](https://community.ee.co.uk/t5/4G-and-mobile-data/Incoming-Connections-4G-PAYG/m-p/549836#M113929)

---

### Post by SeijiSensei on 2017-04-02
What is your local IP address?  If it begins with 10, or 172.16-31, or 192.168, those are [RFC1918 private address ranges]("https://tools.ietf.org/html/rfc1918") so the carrier has be providing NAT services upstream from you.

I just helped a friend install a [Reolink]("https://reolink.com/") camera.  I was surprised that we can view it over the Internet since it is behind his router provided by Verizon.  I guess it must use uPNP to create a tunnel.  The software is pretty good, too, including a client for smartphones.  I wonder if that would work with your setup.

---

### Post by nginmu on 2017-04-02
31.96.xxx.xxx, according to EE that's me on tinternet

Reolink - many thanks for the suggestion. Will look into it.

---

### Post by nginmu on 2017-04-03
I tried setting up openvpn so I could try it out. Ran into a couple of problems - Wondered if anyone could suggest remedies and help me work through it & understand what's what? In the listing below I've marked the points where I got stuck, with # symbols.. any assistance appreciated. Thanks.

Last edited 2131 GMT 3 April

```

01. sudo apt-get update           <-------- yep managed that fine;
02. sudo apt-get install openvpn    <-------- yep managed that fine;
03. sudo apt-get install bridge-utils   <-------- yep managed that fine;

04. configure the bridge:

    /etc/network/interfaces:

### wasn't sure what to use here.
### my router reports 31.96.xxx.xxx as my WAN IP
### router itself is 192.168.1.1
### I have one single laptop on LAN, 192.168.1.4
### laptop is locked to 192.168.1.4 via MAC address


    # This file describes the network interfaces available on your system
    # and how to activate them.


auto lo
iface lo inet loopback
    # The loopback network interface
    # The next two lines are the original lines of the file, leave them in here.

    #These next lines will create a the bridge for OpenVPN

auto br0
iface br0 inet static

address 192.168.1.4
    # The IP Address above needs to be the IP address of your server.
    # Be  sure that this IP address is the Internal IP Address of the
    # Server, not the public IP. It should look similair to the IP
    # Address above.

network (should I use 192.168.1.0?)
    # Not sure what the line above does or how it should be configured

netmask 255.255.255.0
    # The netmask will probably not need to be changed.

broadcast (should I use 192.168.1.255?)
    # Not sure what the line above does or how it should be configured

gateway (should I use 192.168.1.1?)
    # The gateway column refers to the default gateaway of your router.
    # This address will probably be the same as the address used to
    # port forward.

bridge_ports eth0
    # This command bridges your ethernet connection for OpenVPN

bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
    # Not sure what the 4 lines above do or how they should be configured

iface eth0 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down

    # Don't know what these last set of lines do or how they should be 
    # configured, but they apparently still need to be here.





05. sudo /etc/init.d/networking restart  <-------- ### succeeded, but I lost all connectivity
                                                                    ### probably used wrong settings above!

Now create certificates:

06. sudo mkdir /etc/openvpn/easy-rsa/    <-------- yep managed that fine;
07. sudo cp -r /usr/share/doc/openvpn/examples/easy-rsa/2.0/* /etc/openvpn/easy-rsa/  ### failed; no source /easy-rsa/ directory
                                                                                                                          ### at this point I tried sudo apt-get install easy-rsa
                                                                                                                           ### which succeeded, but still no /usr/share/doc/openvpn/examples/easy-rsa/
### this is as far as I got ####



08. sudo chown -R $USER /etc/openvpn/easy-rsa/

09. Now edit /etc/openvpn/easy-rsa/vars:

export KEY_COUNTRY="US"
export KEY_PROVINCE="KY"
export KEY_CITY="Louisville"                         ### suggestions as to appropriate selections for UK sought ###
export KEY_ORG="Monkeypantz"
export KEY_EMAIL="
 This e-mail address is being protected from spambots. You need JavaScript enabled to view it
 "

10. Create the certificates:

cd /etc/openvpn/easy-rsa/
source vars
./clean-all
./build-dh                                   ### tried none of this yet ###
./pkitool --initca
./pkitool --server server
cd keys
sudo openvpn --genkey --secret ta.key
sudo cp server.crt server.key ca.crt dh1024.pem ta.key /etc/openvpn/

11. Create client certificates:

cd /etc/openvpn/easy-rsa/
source vars
./pkitool hostname (actual hostname of client machine that wants to connect)

for each client, copy to the /etc/openvpn directory:

/etc/openvpn/ca.crt
/etc/openvpn/ta.key
/etc/openvpn/easy-rsa/keys/hostname.crt
/etc/openvpn/easy-rsa/keys/hostname.key

12. Configure the server:

sudo cp /usr/share/doc/openvpn/examples/sample-config-files/server.conf.gz /etc/openvpn/
sudo gzip -d /etc/openvpn/server.conf.gz

- edit example server.conf -

local  (should I use 192.168.1.4?)
(IP address of the bridged interface)   ### what would be appropriate here? ###

dev tap0

up "/etc/openvpn/up.sh br0"

down "/etc/openvpn/down.sh br0"

# wild guess at what I should use...
server-bridge 192.168.1.101 255.255.255.0 192.168.1.105 192.168.1.200
# (server will push out the IP address range of 192.168.1.105-200 to clients) - ?
# (the vpn will appear as 192.168.1.101 on the remote client machines) - ?

# Do these lines look valid and workable?
# I have no idea what they do..
push "route 192.168.1.1 255.255.255.0"
push "dhcp-option DNS 192.168.1.201"
# This next line in particular, should I configure this otherwise somehow?
push "dhcp-option DOMAIN example.com"

tls-auth ta.key 0 # This file is secret
user nobody
group nogroup


13. create scripts to start and stop:
----------------------
#!/bin/sh
#This is /etc/openvpn/up.sh

BR=$1
DEV=$2
MTU=$3
/sbin/ifconfig $DEV mtu $MTU promisc up
/usr/sbin/brctl addif $BR $DEV
----------------------
#!/bin/sh
#This is/etc/openvpn/down.sh


BR=$1
DEV=$2


/usr/sbin/brctl delif $BR $DEV
/sbin/ifconfig $DEV down
-----------------------

sudo chmod 755 /etc/openvpn/down.sh
sudo chmod 755 /etc/openvpn/up.sh

14. start the server

sudo /etc/init.d/openvpn restart

```

---

### Post by nginmu on 2017-04-04
Checked my IP today:

From router admin panel, my Internet connection is 10.101.xxx.xxx - as you noted SeijiSensei, that's a private address.

The Internet thinks I am 213.205.xxx.xxx as reported by whatsmyip.com

Why I was on 31.96.xxx.xxx with EE the other day I don't know.

[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=698195")

---

