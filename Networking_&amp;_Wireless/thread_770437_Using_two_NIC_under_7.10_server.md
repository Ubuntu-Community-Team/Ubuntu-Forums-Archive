---
title: "Using two NIC under 7.10 server"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by mathieublais on 2008-04-27
I'm currently having problem trying to setup a second NIC in 7.10 ubuntu server.  I tried to modify /etc/network/interfaces so it activates both NIC at start but soon both are on server doesn't respond anymore, unable to ping anything.  It seems to get confused when both cards are on.

We had to get a second inet line in because we needed more bandwidth.So the main goal is to have the server in two seperate network. The services activated on server are Apache, FTP, POP and SMTP.  

On one NIC, external clients needs to be able to access FTP, HTTP and POP.  On the other NIC, local users would need to be able to send email thru the local SMTP. 

Any help will be really appreciated

---

### Post by Iowan on 2008-04-27
Might have better response on the **Server Platforms** forum - although it IS a networking issue...
Post the **/etc/network/interfaces** file.

---

### Post by mathieublais on 2008-04-28
Here's my file
# The loopback network interface
auto lo eth0 eth2
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 192.168.1.8
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        # dns-nameservers 198.235.216.131

iface eth2 inet static
        address 10.0.0.8
        netmask 255.255.255.0
        broadcast 10.0.0.255
        network 10.0.0.0

---

### Post by petergg on 2008-04-29
Hi,

I'm having the *same* problem with 2 nics.  I can ping either one or the other, but not both at the same time.  My interfaces file just about mirrors yours.  I have found many posts, but no solutions to this problem.  Right now, it is holding up activation of our first Ubuntu Server ( 7.10 ).  We are trying to find an alternative to windoz, which easily works with this kind of configuration.

It almost seems that Ubuntu does not know what gateway to use and is confused by having the potential of having 2 available gateways to send data.  We have spent hours in trying to configure this correctly.  Does anyone have a setup actually working with 2 nics, in my case, both are public and with seperate network addresses?  Can you post a interface file or any additional options we need to configure?

Thanks, -Pete

---

### Post by marcelokoehler on 2008-04-30
Hello everyone

I have a 7.10 Server which work as firewall/proxy/router, and it is using two NICs.

First, at /etc/network/interfaces, it has the gateway for each NIC defined.

Then the default gateway is set by the command

route add default gateway .... that you can put in post-up command at /etc/network/interfaces, for example.

---

### Post by petergg on 2008-05-01
Hi,

Could you post a copy of your interface file ?  It would be very helpful.

Thanks, -Pete

---

