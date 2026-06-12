---
title: "Network Gateway Server setup problems..."
date: 2011-05-13
forum: New to Ubuntu
---

### Post by cgrossmann on 2011-05-13
Hi All, 

I have followed this great example on how to setup a network Gateway server, but somewhere I still do something wrong...please advice.

====================================================================================
Ubuntu Router Network Gateway
October 27, 2009


In this article you will learn how to setup your very own Ubuntu router internet gateway. The Ubuntu router / gateway will act exactly like any other router that you can purchase at the store, except your linux box will have more functionality and extra security.Â  What you will need to build your Ubuntu router:

    Extra computer
    (2) Ethernet cards
    Switch
    Ubuntu 10.04 LTS Server Edition
    Putty

This article will explain how to setup a fresh install of Ubuntu 10.04 server edition, configuring a dhcp server for a local network, while a including a firewall from the nasty internet. The first thing that you are going to do is a fresh install of the Ubuntu server edition, but selecting only Open SSH server during the software installation section of the Ubuntu install. After the installation completes and your pc reboots, you are then going to want to set a root password (su).

sudo passwd root

After you have a set a root password, login into root by typing the following command:

su

After you are in super user mode (root) we are then going to want to update our Ubuntu distro. Type the following commands to update the os and other programs.

apt-get update

apt-get upgrade

After your computer updates, restart it.

reboot

Setup Network Cards

vi /etc/network/interfaces

In the example below my eth0 represents the network interface that connects to the internet and the eth1 interface connects to switch. The switch then connects to all of your other networked devices, such as your gaming system and other networked devices. I added the following code into the /etc/network/interfaces file:

auto eth1

iface eth1 inet static

address 192.168.10.1

netmask 255.255.255.0

network 192.168.10.0

broadcast 192.168.10.255

1 300x187 Ubuntu Router Network Gateway

/etc/init.d/networking restart

The next following step is not required, but I like to set a hostname for my Ubuntu router, all you have to do is install apache and you could have your own personal intranet or web server.

vi /etc/hosts

2 300x187 Ubuntu Router Network Gateway

echo homeserver.gateway.2wire.net > /etc/hostname

/etc/init.d/hostname.sh start

hostname

hostname -f

3 300x187 Ubuntu Router Network Gateway

Once you have completed the following above, you can use putty to access your linux machine from your windows based pc. This will allow you to copy and paste the following code, to speed up the process of creating your linux gateway. The first thing that you must do to use putty to configure your Ubuntu router, is set a static ip on your windows machine, since we don’t have a dhcp server installed yet. Set a static ip address for Microsoft Vista. If you don’t want to use putty you can just type out the rest of the code, putty just makes it easier. Once you have chosen your terminal program that you are going to use, again login under root. It is now time to install some software that we will need to setup the gateway.

apt-get install dhcp3-server bind9 vim perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

Enable packet forwarding

vi /etc/sysctl.conf

# Uncomment the next line to enable packet forwarding for IPv4

net.ipv4.ip_forward=1

echo 1 > /proc/sys/net/ipv4/ip_forward

Install Webmin

Webmin is another good program to use to configure you Ubuntu gateway and other server programs that you might use. If you use webmin, you will be able to easily configure you server, using any web browser you choose.

cd /opt

mkdir webmin

cd /opt/webmin

wget [http://prdownloads.sourceforge.net/webadmin/webmin-1.430.tar.gz](http://prdownloads.sourceforge.net/webadmin/webmin-1.430.tar.gz)

tar xzvf webmin-1.430.tar.gz

cd webmin-1.430/

./setup.sh

During installation you will be asked a few questions, just press enter a few times. The only thing that you want to change is the port number, user name and password and also say yes to SSL.

4 300x234 Ubuntu Router Network Gateway

Configure dhcp

    Network address – 192.168.10.0
    Netmask – 255.255.255.0
    Address ranges -192.168.10.100 – 192.168.10.200

After you have entered the above click on the create button. You should now see an icon that reads 192.168.10.0, click on this new icon and then click on the Edit Client Options button.

    Subnet mask – 255.255.255.0
    Default routers – 192.168.10.1
    Broadcast address – 192.168.10.255
    DNS servers – 192.168.10.1

After you have the above into the client options windows click the save button twice, which should return you to the main Dhcp server window. Inside the dhcp server screen, you see a button called Edit Network Interface, click this button and select eth1 then click save. Now click on the Start Sever button to start you dhcp server, if you see no errors, you are good.

Configure firewall

Once you have setup you dhcp server, click on the Networking tab,Â then click on the Linux Firewall link.Â  You will now need to select “Do network address translation on external interface:” on eth0, then click on Setup Firewall.Â  Once you are inside the firewall program, change the drop down list from Network Address Translation (NAT) to Packet filtering (filter).Â  You will now need to add the following rules to your firewall.

Input:

    Accept if input interface is lo
    Accept if input interface is eth0 and state of connection is ESTABLISHED, RELATED
    Accept if input interface is eth1
    Click on Apply Configurations.
====================================================================================

I have a computer connected onto the second NIC and configured the IP address range as requested, but somehow I still cannot connect through the gateway Server onto the Internet. I can however reach the server but not beyond it.

In front of the Server there is a D-Link Router which is connected directly onto the Internet. 

Please advice further.

Thanks in advance.
C
:popcorn:

---

