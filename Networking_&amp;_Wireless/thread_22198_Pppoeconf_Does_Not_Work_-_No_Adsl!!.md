---
title: "Pppoeconf Does Not Work - No Adsl!!"
date: 2005-03-26
forum: Networking &amp; Wireless
---

### Post by chis on 2005-03-26
Hi all,

I have been using MandrakeLinux 10 with ADSL access (using their adsl-start suite...).

Recently I have been trying Ubuntu Live CD and am very impressed. However I have failed to connect to the internet.

I tried "sudo pppoeconf". Setup has no errors. "pon dsl-provider" seems to be normal as well. But I can't access any web sites afterwards!!! (I tried to ping websites as well with no luck).

To confirm, I tried pppoeconf with Knoppix (and Ubuntu Live CD) on two different computers and I cannot connect to the internet in all occasions (setup is fine)!!!

Would anyone mind telling me what the problem is and how I can overcome it? Can I use something like adsl-start in Ubuntu?

I am using a adsl-modem-router (NetComm).

Thx heaps!!

chis

---

### Post by arctic on 2005-03-26
hello and welcome aboard :)

if you are connected to the net, using a router, you do not need to do a lot (you might not need pppoeconf at all). start the network-tool from your system-menu and set up a lan eth0 connection. it could well be that your blocked webaccess is caused by the infamous ipv6 problem. in order to find out if this is the case, after activating your network card with the network tool, open a terminal and try to ping e.g. [www.google.com](www.google.com). if that works, open your browser and try to access e.g. google.com. if this fails, you are suffering from ipv6 problems. but those can be solved.
in firefox, type "about:config" in the adressbar. in the new searchbar, type ipv6 and you will see two entries. change the disable-ipv6 from false to true by double clicking on "false".
now you should be able to access all webpages. evolution won't work though. in order to achieve that, you need to do one of the following three things:

1. change the /etc/modprobe.d/aliases file. it should contain the following entries:
alias net-pf-10 off
alias ipv6 off

then change the /etc/sysctl.conf. it should contain the following line:
net.ipv4.tcp_window_scaling=0

2. install the following packages via apt-get (you might need to ping the server from your terminal at the same time, otherwise you might get a timeout):
pump
dnsmasq
resolvconf

3. in case your base system is formatted with ext3, you can set up valid dns-servers in your /etc/resolv.conf and lock it afterwards with "chattr +i /etc/resolv.conf". if you do this, your system might hang while booting somewhere at the activation of your eth0 card. if this is the case, y simple "ctrl+c" will continue the booting. the network should work nontheless.

good luck. :D

---

