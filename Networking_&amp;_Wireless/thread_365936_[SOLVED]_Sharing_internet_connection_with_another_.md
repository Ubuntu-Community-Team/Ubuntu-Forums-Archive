---
title: "[SOLVED] Sharing internet connection with another PC (help?!)"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by blueturtl on 2007-02-20
I have two computers:
my main system running Ubuntu 6.06 LTS with wireless web access
my legacy system with Windows 95 without wireless interface

Since the two systems are within a reasonable distance of each other I have them hooked together via a twisted pair cable and 10 mbit ethernet cards. I want to be able to access the web from my legacy system (and thus my main system has to share the connection).

The first thing I tried was Firestarter
1. "sudo apt-get install firestarter"
2. I then proceeded to run the wizard. I selected my internet device wlan0 as the device to use for internet access and my second wired ethernet (eth1) as the device to share the connection to.
3. eth1 was configured to a static ip of 192.168.0.1
4. The Windows machine was configured to a static ip of 192.168.0.5 and the DNS and gateway were configured to 192.168.0.1
5. Systems rebooted

No go, the machines can ping each other but the legacy PC cannot access the web.

So I purge Firestarter and follow the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=91370&highlight=howto+share+internet+connection").

After applying the instructions in the first post I reboot and cannot access the web on *either* of the machines!
I play with iptables for a while but I cannot make my main system stay online. There is an odd moment when both machines temporarily access the web and then after rebooting it's a no go for both AGAIN. I end up removing ipmasq and dnsmasq and after that everything returns to normal meaning that my main system can access the web.

I then follow the [instructions in the community wiki]("https://help.ubuntu.com/community/InternetConnectionSharing").
While this doesn't break anything I still don't get any further than I got with Firestarter, meaning that while both machines see each other and respond to ping I cannot access the web on the legacy PC.

This is all that matters:
wlan0 connects the Ubuntu machine to the web, it gets an IP through DHCP in our wlan-router.
eth1 is the wired interface that connects my Ubuntu-machine to the legacy PC.
I would appreciate static IPs on both machines, but if it cannot be done DHCP is fine.
Can someone please point me in the right way?

---

### Post by apjone on 2007-02-20
It may be best setting up your ubuntu machine as a proxy server.

---

### Post by blueturtl on 2007-02-20
I got it to work!

This is what I did.

I configured the Windows PC like so:
Static IP 192.168.0.5
Sub 255.255.255.0
DNS 192.168.0.1
Gateway 192.168.0.1

On the Ubuntu machine I configured eth1 like so:
Static IP 192.168.0.1
Sub 255.255.255.0

I then did this:
$sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
$sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
$sudo apt-get install dnsmasq
$sudo gedit /etc/dnsmasq.conf

I then proceeded to edit the following lines:

# If you want dnsmasq to listen for DHCP and DNS requests only on
# specified interfaces (and the loopback) give the name of the
# interface (eg eth0) here.
# Repeat the line for more than one interface.
interface=eth1
# Or you can specify which interface _not_ to listen on
#except-interface=
# Or which to listen on by address (remember to include 127.0.0.1 if
# you use this.)
#listen-address=
# If you want dnsmasq to provide only DNS service on an interface,
# configure it as shown above, and then use the following line to
# disable DHCP on it.
no-dhcp-interface=1

Now save the file and

$sudo dpkg-reconfigure dnsmasq

After I booted the Windows machine I can now access the internet on both machines!
I'm not sure if the changes are permanent, I suspect I will have to enter these commands every time I start the Ubuntu machine to make the connection sharing work:

$sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
$sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

Hope this helps someone.

---

### Post by koenn on 2007-02-20
> I suspect I will have to enter these commands every time I start the Ubuntu machine to make the connection sharing work:
you can enter those commands (without sudo) in a startup script - see post #2 of [http://ubuntuforums.org/showthread.php?t=358169](http://ubuntuforums.org/showthread.php?t=358169)
(bur use those 2 commands that worked for you in it)
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

---

