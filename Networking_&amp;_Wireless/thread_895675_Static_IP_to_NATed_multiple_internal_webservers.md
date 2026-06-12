---
title: "Static IP to NATed multiple internal webservers"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by jsandreas on 2008-08-20
Hello forum,

Here is what I want to do. I have 1 static IP I want to have apache web servers on the LAN side of the networks. I want the public to be able to access those servers. 

I've gone throught the newsgroups and forums and all state that I need to forward to a port. I don't disagree with that how ever there is a way to do this with NAT, BIND, and Proxy servers.

I've done this with FreeBSD in the past with help from this website, [http://ezine.daemonnews.org/200202/multiweb.html](http://ezine.daemonnews.org/200202/multiweb.html).


 1. Overview

This article discusses a network setup where multiple webservers reside behind one IP address. Such a situation may arise when you need a specific webserver for one task and a different webserver for another task, running different operating systems or webserver software. With only one IP address available from the Internet, you could simply use Network Address Translation (NAT) with port forwarding. However, this forces you to give each webserver an ugly URL with a non-standard port number. Luckily, there is a better way. In the setup described in this article, each webserver can be reached via its own fully qualified domainname on the standard HTTP port (80).

All machines discussed in this article are running FreeBSD 4.4. The NAT machine has two interfaces, one connected to the Cable or xDSL modem, and one to the hub of the LAN. The nameserver, proxyserver and webserver machines all have one interface, which is connected to the hub. The webserver machines will not be discussed any further in this article, because they might be running different operating systems and webserver software. That was the whole point, wasn't it?

2. Theory

Let's start with some theory about URLs and the HTTP protocol.

2.1 URLs and HTTP

A URL consists of four parts:

# The protocol, in our case HTTP
# The hostname, e.g. [www.example.com](www.example.com)
# The port number, mostly omitted, default 80 for HTTP
# The file location, e.g. /directory/file.html

A number of steps are performed when somebody asks for a certain URL in a web browser. First, the web browser does a DNS lookup to find the IP address associated with the hostname. The web browser then sends a HTTP request to this IP address. In HTTP 1.0, the web browser just sent the file location part of the URL in the request. This resulted in a one-to-one link between domain names and IP addresses, making it impossible to serve more than one domain on one IP address. In HTTP 1.1, the web browser also sends the hostname part of the URL, which removes this limitation. The webserver can now serve multiple domains with just one IP address.

2.2 Our setup

Let's use the following data for our setup. We have a webserver called webserver1 in our domain example.com with IP address 10.0.0.4. The public IP address of our NAT machine is 216.136.204.21. Now, somebody wants to view a webpage located on this webserver from the Internet.

The web browser first performs a DNS lookup to find the IP address of the webserver. Because the web browser is not located on the LAN, but somewhere on the Internet, we want this to be the public IP address of our NAT machine. The web browser then sends a request to this IP address on the standard HTTP port (80). We now have to decide which server on the LAN to forward this request to. The NAT machine has no knowledge about the HTTP protocol, so it can't forward the request to a webserver based on the HTTP request the web browser made. Therefore, it has to forward all HTTP requests to a specific server. This can't be a webserver, because it would limit our number of webservers to one!

To solve this problem, we shouldn't have the NAT machine forward HTTP requests to a specific webserver, but to a proxyserver. This proxyserver does have knowledge about the HTTP protocol, so it can fetch webpages for the web browser based on the hostname present in the request. There is one problem however, the proxyserver must not fetch the webpage from the NAT machine (216.136.204.21), but from the webserver (10.0.0.4). So, the proxyserver should get another result (10.0.0.4) then the web browser (216.136.204.21) when looking up the IP address of webserver1.example.com.

This leads us to setting up two nameservers. The first one listens to DNS requests on the standard DNS port (53) on the LAN, giving IP addresses in the 10.0.0.0/24 range. The second one listens to DNS requests on a non-standard port (let's use 1053), always giving the IP address 216.136.204.21. The NAT machine should then forward DNS requests on its port 53 to port 1053 on the nameserver machine.

2.3 Summary

To summarize, here are the steps performed when somebody requests the URL [http://webserver1.example.com/directory/file.html](http://webserver1.example.com/directory/file.html) from a web browser on the Internet. We assume that 216.136.204.21 has been made authorative nameserver for the domain example.com:

   1. The web browser sends a DNS request to 216.136.204.21 on port 53 for the IP address of webserver1.example.com.
   2. The NAT machine forwards this DNS request to port 1053 on the nameserver.
   3. The nameserver replies with 216.136.204.21.
   4. The NAT machine sends this reply to the webbrowser.
   5. The web browser sends a HTTP request to 216.136.204.21 on port 80 for the hostname and the file location.
   6. The NAT machine forwards this HTTP request to the proxyserver on port 1080.
   7. The proxyserver sends a DNS request to port 53 on the nameserver.
   8. The nameserver replies with 10.0.0.4.
   9. The proxyserver sends the HTTP request to 10.0.0.4.
  10. The webserver replies with the right web page.
  11. The proxyserver replies with this web page.
  12. The NAT machine sends this reply to the web browser. 

If we want to fetch the same file from webserver2 instead of webserver1, the main differences will be in steps 8 and 9. The nameserver will reply with 10.0.0.5 instead of 10.0.0.4 in step 8. In step 9, the proxyserver will fetch the URL from 10.0.0.5.

3. Implementation

Now that we've seen the theory, let's shift our attention to the implementation.

3.1 Network Address Translator (NAT)


Kernel

We want to be able to divert and filter IP packets. The FreeBSD generic kernel doesn't allow this, so we have to make our own kernel. We do this by making a copy of the generic kernel:

   cd /usr/src/sys/i386/conf
   cp GENERIC NAT

Then we add the following lines to the NAT file:

   options IPDIVERT
   options IPFIREWALL

Now we can compile our new kernel and install it:

   config NAT
   cd ../../compile/NAT
   make depend
   make
   make install


Configuration

We should now edit some configuration files to really enable the capabilities just added to the kernel. The first file is /etc/rc.conf which contains the network interface configuration as well as the services configuration:

   # Host- and domainname
   hostname="nat.example.com"

   # Network interface connected to the Cable or xDSL modem
   ifconfig_xl0="inet 216.136.204.21 netmask 255.255.248.0"

   # Network interface connected to the hub of the LAN
   ifconfig_rl0="inet 10.0.0.1 netmask 255.255.255.0"

   # Default router on network interface xl0
   defaultrouter="216.136.204.1"

   # Enable firewall capabilities
   firewall_enable="YES"

   # Enable gateway capabilities
   gateway_enable="YES"

   # Enable network address translation
   natd_enable="YES"
   natd_interface="xl0"
   natd_flags="-f /etc/natd.conf"

The second file is /etc/natd.conf which contains the rules for the NAT daemon:

   # Redirect DNS packets to the nameserver
   redirect_port udp 10.0.0.2:1053 53

   # Redirect HTTP packets to the proxyserver
   redirect_port tcp 10.0.0.3:1080 80

The third file is /etc/rc.firewall which contains the rules for the packet filter. In our case we first divert all IP packets to the NAT daemon. After that, we make sure that IP packets can only go where they are supposed to go.

   # Flush all previous firewall rules
   /sbin/ipfw -f flush

   # Divert all IP packets to the NAT daemon
   /sbin/ipfw add divert natd ip from any to any via xl0

   # Allow all IP packets through the loopback interface by the localhost
   /sbin/ipfw add allow ip from 127.0.0.1 to 127.0.0.1 via lo0

   # Allow DNS and HTTP packets through the public interface to LAN machines
   /sbin/ipfw add allow udp from any to 10.0.0.2 1053 in recv xl0
   /sbin/ipfw add allow tcp from any to 10.0.0.3 1080 in recv xl0

   # Allow all IP packets through the public interface from this machine
   /sbin/ipfw add allow ip from 216.136.204.21 to any out xmit xl0

   # Allow all IP packets through the private interface from and to LAN machines
   /sbin/ipfw add allow ip from 10.0.0.1/24 to any in recv rl0
   /sbin/ipfw add allow ip from any to 10.0.0.1/24 out xmit rl0

   # Deny all IP packets not allowed until this point
   /sbin/ipfw add deny ip from any to any


3.2 Nameserver


Configuration

For our nameserver machine we will use BIND 8.2.4. This software is pre-installed on FreeBSD, so we just have to configure it. As mentioned earlier, we have to set up and run two seperate instances of BIND. Let's start with the one that serves our LAN. The first file to edit is /etc/namedb/named-lan.conf which contains the general configuration of BIND. To avoid very long listings, just the additions to the original file are shown:

   zone "example.com" {
      type master;
      file "db-lan.example.com";
   };

   zone "0.0.10.in-addr.arpa" {
      type master;
      file "rev.0.0.10";
   };

The second file is /etc/namedb/db-lan.example.com which contains the mapping from names in the example.com domain to IP addresses:

   $TTL 86400

   @  IN  SOA  nameserver.example.com.  hostmaster.example.com. (
      2002011501 ; Serial (yyyymmddxx)
      86400      ; Refresh (1 day)
      7200       ; Retry (2 hours)
      604800     ; Expire (7 days)
      86400 )    ; Minimum (1 day)

   @             IN   NS  nameserver.example.com.

   nat           IN   A   10.0.0.1
   nameserver    IN   A   10.0.0.2
   proxyserver   IN   A   10.0.0.3
   webserver1    IN   A   10.0.0.4
   webserver2    IN   A   10.0.0.5
   webserver3    IN   A   10.0.0.6

The third file is /etc/namedb/rev.0.0.10 which contains the reverse mapping, from IP addresses to names in the example.com domain:

   $TTL 86400

   @  IN  SOA  nameserver.example.com.  hostmaster.example.com. (
      2002011501 ; Serial (yyyymmddxx)
      86400      ; Refresh (1 day)
      7200       ; Retry (2 hours)
      604800     ; Expire (7 days)
      86400 )    ; Minimum (1 day)

   @   IN   NS    nameserver.example.com.

   1   IN   PTR   nat.example.com.
   2   IN   PTR   nameserver.example.com.
   3   IN   PTR   proxyserver.example.com.
   4   IN   PTR   webserver1.example.com.
   5   IN   PTR   webserver2.example.com.
   6   IN   PTR   webserver3.example.com.

Let's continue with the BIND that serves the Internet. The fourth file to edit is /etc/namedb/named-internet.conf. Just the changes and additions to the original file are shown:

   options {
      directory "/etc/namedb";
      listen-on port 1053 { 10.0.0.2; };
   };

   zone "example.com" {
      type master;
      file "db-internet.example.com";
   };

Note that we tell this BIND to listen to a non-standard port number, 1053 in our case. The fifth file is /etc/namedb/db-internet.example.com which contains the mapping from names in the example.com domain to the public IP address of our NAT machine. Just the changes to the LAN file are shown:

   webserver1   IN   A   216.136.204.21
   webserver2   IN   A   216.136.204.21
   webserver3   IN   A   216.136.204.21

The entries for nat.example.com, nameserver.example.com and proxyserver.example.com are left out, because they won't be serving web pages. We have left out the file that contains the reverse mapping, because the reverse mapping for the public IP address is usually done by the ISP. Finally, we will start the two BIND instances:

   /usr/sbin/named -u bind -g bind -c /etc/namedb/named-lan.conf
   /usr/sbin/named -u bind -g bind -c /etc/namedb/named-internet.conf


3.3 Proxyserver


Installation

For our proxyserver machine we will use Squid 2.4.6. This comes as a port on FreeBSD, so we have to install it first:

   cd /usr/ports/www/squid24
   make
   make install


Configuration

In its normal function, Squid is a real proxyserver. This means that web browsers have to be told to access certain (or all) webservers via this proxyserver. Because we want this setup to work without modifications to the web browser, we need to change Squids default behaviour. If we want Squid to act as a transparent proxyserver, we have to set it to accelerator mode. The only file to edit here is /usr/local/etc/squid.conf which contains all configuration options for Squid. To avoid very long listings, just the changes and additions to the original file are shown:

   # Port Squid listens on
   http_port 1080

   # Allow all clients access
   http_access allow all

   # Proxy for several virtual hosts, each on port 80
   httpd_accel_host virtual
   httpd_accel_port 80

   # Use host header in requests
   httpd_accel_uses_host_header on

To start Squid, we will use the startup script that came along when we performed the installation:

   /usr/local/etc/rc.d/squid.sh start


4. Testing

We will test our setup from within our LAN (internal) and from the Internet (external).

Internal

From a client connected to the LAN we will start the test of our configuration. Let's try to fetch a HTML page from one of the webservers:

   [http://webserver1.example.com/directory/file.html](http://webserver1.example.com/directory/file.html)

If the webserver doesn't use virtual hosts, we would get the same result if we asked for this URL:

   [http://10.0.0.4/directory/file.html](http://10.0.0.4/directory/file.html)


External

Now try the same thing from a client on the Internet:

   [http://webserver1.example.com/directory/file.html](http://webserver1.example.com/directory/file.html)

The following test will (and should) fail hopelessly, because the proxyserver can't fetch the HTML page from itself:

   [http://216.136.204.21/directory/file.html](http://216.136.204.21/directory/file.html)



It explains exactly how to do such a setup. My question is with ubuntu server 8.04 how do I do this? Some of the areas are a little foggy.

Thanks

---

### Post by jsandreas on 2008-08-20
I should reiterate, that the only problem I have with the ubuntu server setup is with the nat and firewall settings. If someone can help me with that portion I should be able to get the rest of it configured. 

Once this is done I would create a nice HOWTO for the ubuntu group.

Thanks

---

