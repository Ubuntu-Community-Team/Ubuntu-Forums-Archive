---
title: "Configuring Network Interfaces not working on boot"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by gwilson on 2005-11-02
Hi. I've seen several problems similar to this (I think) but just let me run this past you.

During the bootup sequence (very pretty now in Breezy), I see the ALSA configurations come up and pass, but when the line says Configuring Network Interfaces, the system hangs up for about a minute while it goes out an tries to set up the network. I can see lights blinking on both my Belkin router and my DSL modem while this is taking place. Eventually, this passes and the boot sequence moves ahead. I believe it is sometimes successful before it moves on and sometimes just times out. When the system is fully up and I run Firefox or Evolution, sometimes the network is letting me out to the internet and sometimes it is not. If the network isn't working, I can get it up by going to Systems>Administrations>Networking.  Ethernet eth0 is always shown as active, but I must deactivate it and reactivate it again to gain access to the internet. My default gateway should be eth0, but I'm not sure it always comes up when I first boot up.

I added two DNS addresses in dhclient.conf , but I wonder if the DHCP system is searching for too many factors under the "request" line.

Any help would be appreciated. This all worked fine prior to Breezy. Now it's intermittent.  Thanks.
 
My dhclient.conf look like this:

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 209.137.171.10, 209.137.171.20;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

---

### Post by bcavagnolo on 2005-11-02
I have this same problem.  Every time I boot I end up running

dhclient eth0

at a prompt and that brings everything up.  I dug around and I'm having trouble figuring out what's going on.  In my /etc/networking/interfaces eth0 is mapped to "hotplug" for reasons described in /usr/share/doc/hotplug/README.Debian, so it should be brought up by /etc/init.d/hotplug at boot time.  /etc/init.d/hotplug calls /etc/hotplug/net.rc, which calls /etc/hotplug/net.agent which calls /etc/hotplug/net.ifup.  I see that the net.ifup script is called as a daemon.  I imagine that this is so that other init tasks can go on while the possibly time-consuming task of bringing up the network interfaces  happens.

Indeed when I manually trace the script, it looks like all of the right stuff should be happening.  Also, when I set DEBUG to yes in the environment and run the script, /var/log/user.log has all of the expected output.  The log even reports "Invoking ifup eth0=hotplug" from the net.ifup script, and if I type that in manually at the prompt everything comes up as expected.  However, when I run the script, the interface comes up but doesn't get a an address.

Help!

---

### Post by bcavagnolo on 2005-11-03
I think I figured out what was happening on my system.  I had installed the network-manager hoping that it would enhance the functionality of my wireless facilities.  I uninstalled it and everything seems to be back to normal.  I don't really understand what was broken, but it works now.  Perhaps this helps you.

Ciao,
Brian

---

### Post by PaganHippie on 2005-11-03
I had a similar issue, solved it by disabling DHCP, using a static IP address & manually entering DNS, gateway, &c.

---

