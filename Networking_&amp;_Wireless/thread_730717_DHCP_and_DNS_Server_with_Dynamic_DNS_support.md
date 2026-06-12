---
title: "DHCP and DNS Server with Dynamic DNS support"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by rocsak on 2008-03-21
This a guide inspired by [rickyjones]("http://ubuntuforums.org/member.php?u=61841")  guide [Ubuntu Server 7.10: OpenLDAP + SAMBA Domain Controller]("http://ubuntuforums.org/showthread.php?t=640760") and the effort to build a "Ubuntu Small Business Server Guide". I hope it helps. The main resources for writing this guide are those links: (and the man pages....)

[http://sipx-wiki.calivia.com/index.php/HowTo_Configure_DHCP_and_DNS_Servers](http://sipx-wiki.calivia.com/index.php/HowTo_Configure_DHCP_and_DNS_Servers)
[http://ubuntuforums.org/showthread.php?t=267974](http://ubuntuforums.org/showthread.php?t=267974)
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Many thanks to the guys that wrote the above articles for sharing with us all the great information and tips.
This guide is for use only in a LAN environment, with DNS servers not open to Internet access directly. Securing the server is not a priority of this guide at this moment. There are numerous of security options that you can implement both to DHCP and DNS servers that are not mentioned in this guide.

For a more easy way to configure all this you can use [Webmin.]("http://www.webmin.com") It's a great tool and can make your life easier if you are just starting to experiment with Ubuntu Server (like me). But we still need to know what is going on behind the curtains. Or we can go back to Windows!!! (no way) 

The guide has two parts. Part 1 describes the steps to configure a simple DNS and DHCP installation and part 2 how to extend this installation in order to have Dynamic Dns support. (that means that when DHCP serves a client with an ip address, that ip address is dynamically registered in the DNS record files along with the FQDN of the client)

The server is an Ubuntu 7.10 server with xubuntu desktop installed. The configuration is tested with windows client running Windows Server 2003 SP2 and Linux clients running both Ubuntu 7.10 and Ubuntu 7.04.

The mousepad text editor (found in xubuntu) is used to edit files. You can replace it with your own favorite text editor.

**[SIZE=4]1. Simple DNS & DHCP Installation (without dynamic DNS)[/SIZE]**

[B][SIZE=3]1.1 Installing the DNS Server[/SIZE]
[/B]
[ install BIND DNS]("apt:bind9") in ubuntu:

```
sudo apt-get install bind9 dnsutils

```By default the installation in Ubuntu creates and uses three configuration files: 

/etc/bind/named.conf           ---- is the main configuration file
/etc/bind/named.conf.options   ---- is the configuration file for extra options
/etc/bind/named.conf.local     ---- is the configuration file for the local zones


Assumptions:

[B]* DNS and DHCP server run on the same machine with ip address 192.168.0.1
* your subnet is 192.168.0.0/24
* your domain name is example.com
[/B]

[B][SIZE=2]1.1.1 Edit /etc/bind/named.conf
[/SIZE][/B]
 ```
sudo mousepad /etc/bind/named.conf

``````
 include "/etc/bind/named.conf.options";
  
 // prime the server with knowledge of the root servers
 zone "." {
         type hint;
         file "/etc/bind/db.root";
 };
 
 // be authoritative for the localhost forward and reverse zones, and for
 // broadcast zones as per RFC 1912
 
 zone "localhost" {
         type master;
         file "/etc/bind/db.local";
 };
 
 zone "127.in-addr.arpa" {
         type master;
         file "/etc/bind/db.127";
 };
 
 zone "0.in-addr.arpa" {
         type master;
         file "/etc/bind/db.0";
 };
 
 zone "255.in-addr.arpa" {
         type master;
         file "/etc/bind/db.255";
 };
 
 include "/etc/bind/named.conf.local";
 
 logging {
          category queries {
                 default_syslog;
                 };
         };

```**[SIZE=2]1.1.2 Edit /etc/bind/named.conf.options[/SIZE]**

```
 sudo mousepad /etc/bind/named.conf.options
```If your ISP provided one or more IP addresses for stable nameservers, you probably want to use them as forwarders. Insert the addresses replacing x1.y1.z1.w1 and x2.y2.z2.w2, or comment out the block 'forwarders...' if you don't need it.

 ```
options {
        directory "/var/cache/bind";
        dump-file "/var/cache/bind/cache_dump.db";
        statistics-file "/var/cache/bind/named_stats.txt";
     
        forwarders {
                x1.y1.z1.w1;
                x2.y2.z2.w2;
                };
 
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};


```[B][SIZE=2]1.1.3 Edit /etc/bind/named.conf.local
[/SIZE][/B]
 
```
sudo mousepad /etc/bind/named.conf.local
``` ```
//create the forward master zone
 zone "example.com" IN {
        type master;
        file "/etc/bind/example.com.hosts";
        };
 //create the reverse master zone
 zone "0.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/192.168.0.rev";
        };


```[B][SIZE=2]1.1.4 Edit(create)  /etc/bind/example.com.hosts (zone file for the forward master zone)
[/SIZE][/B]

[B]Assumptions:

* your FQDN for your DNS server machine is ns.example.com
* the email address for the admin of the zone is [EMAIL="admin@example.com"]admin@example.com[/EMAIL]
[/B]

Notes:

* Be aware of the dots in the end of the domain names, they are very important! In a lookup, if a name (hostname or domainname) is followed by a period "." nothing is appended. If there is no period, the domain name of the current context is automatically appended.
* In the following file, [EMAIL="admin@example.com"]admin@example.com[/EMAIL] translates to admin.example.com.
* the '1' in the second row of the file is very important. It's called the **serial number** of the zone. Every time that you manually edit the zone (that is after the first time) you ''must'' increase it. (if you use Webmin it does it for you automatically) Be aware that the serial number is a 32-bit integer with values between 0 and 4,294,967,295. You can use a more meaningful number like '2008032102', in the  YYYYMMDDnn format, which would mean the second revision (02) of the file on March 21, 2008, in order to track changes of the zone file. But, in the case that you enable Dynamic DNS updates, every time that a client is joining the network, his ip address and FQDN are registered in the zone file and the serial number of the zone is automatically increased. In large networks with more than 100 updates per day that kind of format would be useless.
So, choose the serial number depending on your needs. (1 is nice number to start with...)

 ```
sudo mousepad /etc/bind/example.com.hosts
``````
 
$ttl 38400
example.com.         IN      SOA     ns.example.com. admin.example.com. (
                                 1          ; **serial number **
                                 10800      ; refresh (3 hours)
                                 3600       ; retry (1 hour)
                                 604800     ; expire (1 week)
                                 38400      ; minimum (10 hours 40 minutes)
                                )
example.com.         IN      NS    ns.example.com.
ns.example.com.    IN      A    192.168.0.1


```[B][SIZE=2]
1.1.5 Edit(create) /etc/bind/192.168.0.rev [/SIZE][/B]**[SIZE=2](zone file for the reverse master zone)[/SIZE]**


```
 sudo mousepad /etc/bind/192.168.0.rev
``````
 
$TTL 38400    
0.168.192.in-addr.arpa        IN    SOA    ns.example.com. admin.example.com. (
                                1           ; **serial number **
                                10800      ; refresh (3 hours)
                                3600       ; retry (1 hour)
                                604800     ; expire (1 week)
                                38400      ; minimum (10 hours 40 minutes)
                                )
0.168.192.in-addr.arpa        IN    NS    ns.example.com.
1.0.168.192.in-addr.arpa.    IN    PTR    ns.example.com.



```restart the server:

```
 sudo /etc/init.d/bind9 restart
```[B][SIZE=2]1.1.6 Final steps
[/SIZE][/B]


You have to do the following steps to the server machine:

Open the /etc/resolv.conf file for editing

```
sudo mousepad /etc/resolv.conf

```Edit the file so that the only lines in the file are the following

```
 search example.com
 nameserver 192.168.0.1

```We need to change the server hostname to be a fully qualified domain name (FQDN).

so first 
 
```
 sudo mousepad /etc/hosts

```and make the necessary changes so the contents of the file is like that:  

 ```
127.0.0.1       localhost
 127.0.1.1       ns ns.example.com
 
 # The following lines are desirable for IPv6 capable hosts
 ::1     ip6-localhost ip6-loopback
 fe00::0 ip6-localnet
 ff00::0 ip6-mcastprefix
 ff02::1 ip6-allnodes
 ff02::2 ip6-allrouters
 ff02::3 ip6-allhosts
```and then 
 ```
sudo mousepad /etc/hostname

```and again make the necessary changes so the contents of the file is like that:  


 ```
ns.example.com

```and now is the time to do a reboot just to be safe.

[B][SIZE=3]1.2 Installing the DHCP Server[/SIZE]
[/B]

Install in ubuntu:
 ```
sudo apt-get install dhcp3-server
```Assumptions:
[B]* your subnet is 192.168.0.1-192.168.0.254
* your network interface is called eth0
* the range of addresses that you want your server to distribute is 192.168.0.2->192.168.0.254
* your server has a static ip address of 192.168.0.1 and acts as a DNS server, DHCP server, router and WINS server
[/B]
edit the file /etc/dhcp3/dhcpd.conf
 
```
 sudo mousepad /etc/dhcp3/dhcpd.conf
```and add this code (remember to put your settings where is needed)

 ```
authoritative;                                 # that means your server is authoritative for the subnet
 ddns-update-style none;                        # disable dynamic dns updates
 
 subnet 192.168.0.0 netmask 255.255.255.0 {     # declare the subnet to use
     interface eth0;                            # the network interface to serve addresses
     range 192.168.0.2 192.168.0.254;           # range of addresses to use
     default-lease-time 86400;                  
     max-lease-time 86400;
     option subnet-mask 255.255.255.0;
     option broadcast-address 192.168.0.255;
     option routers 192.168.0.1;                # the default gateway of the network
     option domain-name-servers 192.168.0.1;    # the DNS server of the network
     option netbios-name-servers 192.168.0.1;  # the WINS server of the network
        }
 
 host clientpc {                                # here we declare a reservation address for the client 'clientpc'
   hardware ethernet 0C:0C:6E:D2:DA:0C;         # as an alternative of setting a static ip address on the client
   fixed-address 192.168.0.2;                   # you can delete this part if you don't need it 
   default-lease-time 86400;
   max-lease-time 86400;
       }

```restart the process 
```
 sudo /etc/init.d/dhcp3-server restart
```The file with the leases to the clients is in:
```
 /var/lib/dhcp3/dhcpd.leases

```[SIZE=4][B]

2. Configure DNS and DHCP Servers for Dynamic DNS updates[/B]
[/SIZE]

[B][SIZE=3]2.1 Configure the DNS Server for Dynamic DNS updates[/SIZE]
[/B]

**This is something very important when configuring ddns updates. **
When dynamic update is enabled for a zone, the zone can no longer be manually edited as normal, and this applies both to the forward and to reverse zone. When using BIND 9.3, in order not to stop the name server while editing the zone files, you can use the following procedure: 

freeze the zone for editing 
```
 sudo rndc freeze example.com

```Manually edit the zone file (don't forget to increment the serial number in the zone file) 

unfreeze the zone for normal operation 
```
 sudo rndc unfreeze example.com

```[B][SIZE=2]2.1.1 Generate a key required to exchange updates between DHCP and DNS
[/SIZE][/B]

First we have to generate a key required to exchange updates between DHCP and DNS. We do that by running the following command: 
```
 sudo rndc-confgen -a -k rndc-key
```where rndc-key is the name of the key generated. You can put anything you like there. The command creates the following file: 
```
 /etc/bind/rndc.key
```and if you open the file for editing you will see something like this: 
```
 key "rndc-key" {
        algorithm hmac-md5;
        secret "2kBEZW7WqtBhrDe2AoDTlQ==";
};
```  [SIZE=2]**2.1.2 Edit /etc/bind/named.conf**
[/SIZE]
 
```
sudo mousepad /etc/bind/named.conf
```go to the end of the file and paste this code: (change the 'rndc-key' if you used something else when generating the key) 
```
 include "/etc/bind/rndc.key";
controls {
        inet 127.0.0.1 port 953 allow { 127.0.0.1; } keys { rndc-key; };
        };

```[SIZE=2]**2.1.3 Edit /etc/bind/named.conf.local**
[/SIZE]
 
```
sudo mousepad /etc/bind/named.conf.local
```and add this lines both in the forward and the reverse zone: (change the 'rndc-key' if you used something else when generating the key) 
```
allow-update { key rndc-key; };
notify yes;

```your /etc/bind/named.conf.local file should look like this after editing: 

```
 //create the forward master zone
zone "example.com" IN {
      type master;
      file "/etc/bind/example.com.hosts";
      allow-update { key rndc-key; };
      notify yes;
      };
//create the reverse master zone
zone "0.168.192.in-addr.arpa" {
      type master;
      file "/etc/bind/192.168.0.rev";
      allow-update { key rndc-key; };
      notify yes;
      };
```restart the server 

```
 sudo /etc/init.d/bind9 restart
```[B][SIZE=3]2.2 Configure the DHCP Server for Dynamic DNS updates[/SIZE]
[/B]

Open /etc/bind/rndc.key and copy the contents of the file. (without the ';' and the end of it)

edit the configuration file  (change the 'rndc-key' if you used something else when generating the key)  
 ```
sudo mousepad /etc/dhcp3/dhcpd.conf

```change the line that says  
 ```
ddns-update-style none; 
```to 
 ```
ddns-update-style interim;
```and then add the following code after that 

```
 ignore client-updates;      
ddns-domainname "example.com.";
ddns-rev-domainname "in-addr.arpa.";

#################################################
#                                               #
# paste the contents of /etc/bind/rndc.key file #
#                   here                        #
#                                               #
#################################################

zone example.com. {
       primary 127.0.0.1;
       key rndc-key;
       }

zone 0.168.192.in-addr.arpa. {
       primary 127.0.0.1;
       key rndc-key;
       }

```your /etc/dhcp3/dhcpd.conf file should look like this now: 


```
 authoritative;                                 # that means your server is authoritative for the subnet
ignore client-updates;      
ddns-domainname "example.com.";
ddns-rev-domainname "in-addr.arpa.";

key "rndc-key" {
        algorithm hmac-md5;
        secret "2kBEZW7WqtBhrDe2AoDTlQ==";
}

zone example.com. {
       primary 127.0.0.1;
       key rndc-key;
       }

zone 0.168.192.in-addr.arpa. {
       primary 127.0.0.1;
       key rndc-key;
       }

subnet 192.168.0.0 netmask 255.255.255.0 {     # declare the subnet to use
    interface eth0;                            # the network interface to serve addresses
    range 192.168.0.2 192.168.0.254;           # range of addresses to use
    default-lease-time 86400;                  
    max-lease-time 86400;
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;                # the default gateway of the network
    option domain-name-servers 192.168.0.1;    # the DNS server of the network
    option netbios-name-servers 192.168.0.1;  # the WINS server of the network
       }

host clientpc {                                # here we declare a reservation address for the client 'clientpc'
  hardware ethernet 0C:0C:6E:D2:DA:0C;         # as an alternative of setting a static ip address on the client
  fixed-address 192.168.0.2;                   # you can delete this part if you don't need it 
  default-lease-time 86400;
  max-lease-time 86400;
      }
```restart the process  

```
 sudo /etc/init.d/dhcp3-server restart
```and hopefully everything works!! 

You can check the /etc/bind/example.com.hosts and /etc/bind/192.168.0.rev files to see if clients are registering correctly. (But be aware that it takes a long time for changes to be written in those files. But you can also check /var/lib/dhcp3/dhcpd.leases file to see if everything is ok.)

Also you can use the host command to perform forward and reverse lookup against a known DHCP client to ensure a successful lookup.

```
 host clientpc.example.com
```should give something like this:

```
 clientpc.example.com has address 192.168.0.2
```and 

```
 host 192.168.0.2
```should give something like this:

```
 2.0.168.192.in-addr.arpa domain name pointer clientpc.example.com.
```

---

