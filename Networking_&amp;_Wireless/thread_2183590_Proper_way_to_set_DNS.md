---
title: "Proper way to set DNS?"
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by arnold_layne2 on 2013-10-25
I have a DNS server running on my computer, and I want Ubuntu to use it to resolve addresses. I've setup mydomain.com as a custom domain


I went into Network settings, switched to manual in 'Wired', entered my IP, Gateway, Mask. And then I entered my IP in the DNS field.


How do I cause this to take effect? `dig @myiphere mydomain.com` works, but `dig mydomain.com` doesn't return any address.


If I edit `/etc/resolv.conf` by hand and change the first line from `127.0.1.1` to `myiphere`, then everything starts to work.


But this doesn't seem to be the right way to do things as `resolv.conf` warns against manual changes by hand.


So how do I PROPERLY and reliably change DNS?

---

### Post by Mautobu on 2013-10-25
In Terminal:
```
sudo echo dns-nameservers 8.8.8.8 >> /etc/networking/interfaces
```

---

### Post by bab1 on 2013-10-25
> **Mautobu said:**
> In Terminal:
```
sudo echo dns-nameservers 8.8.8.8 >> /etc/networking/interfaces
```

So what you are really saying is: 

Add ***dns-nameservers <your dns servers ip address>*** to the bottom of the /etc/network/interfaces file.  The file needs to be edited by root so you need to use sudo with your editor to open the file.

---

### Post by arnold_layne2 on 2013-10-25
Nope, it doesn't work. dig mydomain.com still returns no address. Also to be noted is that this response is coming from ";; SERVER: 127.0.1.1#53(127.0.1.1)", which is the first server in resolv.conf!

I'm frankly quite surprised how tough simply changing DNS is turning out to be.

---

### Post by bab1 on 2013-10-25
> **arnold_layne2 said:**
> Nope, it doesn't work. dig mydomain.com still returns no address. Also to be noted is that this response is coming from ";; SERVER: 127.0.1.1#53(127.0.1.1)", which is the first server in resolv.conf!

I'm frankly quite surprised how tough simply changing DNS is turning out to be.
If you are looking up the IP address at the correct DNS server (127.0.1.1)  and you get an unexpected response, you problem might be with the DNS servers configuration.  

The setting the *default DNS server * is a fairly trivial configuration.  It's time to diagnose rather than guess.

Post the output of ```
cat /etc/network/interfaces
```...along with the output of ```
cat /etc/resolv.conf
```...and ```
cat /etc/hosts
```

---

### Post by papibe on 2013-10-25
> **arnold_layne2 said:**
> So how do I PROPERLY and reliably change DNS?
The way you described is the proper way (without changing /etc/resolv.conf).

However, in my experience, network-manager not always reset itself after a change as it should be.

To be 100% sure, after making the changes, open a terminal and run:
```
 sudo service network-manager restart
```
Regards.

Note1: to get the current settings of NetworkManager, you can use this:
```
nm-tool
```
Note2: In 12.04 and above, /etc/resolv.conf is a symlink to /run/resolvconf/resolv.conf . You can recreate the link manually or run this to recreate it:
```
sudo dpkg-reconfigure resolvconf
```

---

### Post by bab1 on 2013-10-25
> **papibe said:**
> The way you described is the proper way (without changing /etc/resolv.conf).

However, in my experience, network-manager not always reset itself after a change as it should be.

To be 100% sure, after making the changes, open a terminal and run:
```
 sudo service network-manager restart
```
Regards.

Note1: to get the current settings of NetworkManager, you can use this:
```
nm-tool
```
Note2: In 12.04 and above, /etc/resolv.conf is a symlink to /run/resolvconf/resolv.conf . You can recreate the link manually or run this to recreate it:
```
sudo dpkg-reconfigure resolvconf
```

My guess is the OP is not so much interested in setting the DNS forwarder as he/she is interested in resolving local LAN DNS using a local DNS server.  None of that has anything to do with NM except to stop NM from managing the wired connection.

We shall see when there is a response from the OP.

---

### Post by alivema4ever on 2013-10-26
> **arnold_layne2 said:**
> I have a DNS server running on my computer, and I want Ubuntu to use it to resolve addresses. I've setup mydomain.com as a custom domain


I went into Network settings, switched to manual in 'Wired', entered my IP, Gateway, Mask. And then I entered my IP in the DNS field.


How do I cause this to take effect? `dig @myiphere mydomain.com` works, but `dig mydomain.com` doesn't return any address.


If I edit `/etc/resolv.conf` by hand and change the first line from `127.0.1.1` to `myiphere`, then everything starts to work.


But this doesn't seem to be the right way to do things as `resolv.conf` warns against manual changes by hand.


So how do I PROPERLY and reliably change DNS?

Ubuntu is including dnsmasq as default on new release. It can act as dns server for localhost or an internal network. It also provides dhcp functionality.
To configure dns nameserver on dnsmasq, just create a file /etc/dnsmasq.conf with the following options
```

# pointing to a folder containing dnsmasq rules
conf-dir=/etc/dnsmasq.d
# nameserver to forward dns request
server=208.67.222.222
server=208.67.220.220
server=add_your_nameserver_here
```
If you want custom addresses such as myip.com on 127.0.0.1, just add the following line on /etc/dnsmasq.conf
```
address=/myip.com/127.0.0.1
```
To verify your configuration, stop all dnsmasq instances
```
sudo killall dnsmasq
```
Test your dnsmasq configuration
```
sudo dnsmasq --test
```
if you get response "dnsmasq: syntax check OK", you're good to go. Start dns server
```
sudo dnsmasq
```
Try to dig for some host to verify that dns is working as expected.

---

### Post by arnold_layne2 on 2013-10-26
> **bab1 said:**
> If you are looking up the IP address at the correct DNS server (127.0.1.1)  and you get an unexpected response, you problem might be with the DNS servers configuration.  

The setting the *default DNS server * is a fairly trivial configuration.  It's time to diagnose rather than guess.

Post the output of ```
cat /etc/network/interfaces
```...along with the output of ```
cat /etc/resolv.conf
```...and ```
cat /etc/hosts
```

/etc/network/interfaces
```

# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback


# iface eth0 inet static
#                address 10.3.3.68
#                netmask 255.255.255.0
#                gateway 10.3.3.1
#                dns-nameservers 10.3.3.68 10.1.1.61
```

I had  earlier manually hashed put the values inside 'iface eth0' just to test. Then I commented the whole thing out since it didn't make any difference. 
Remember my configuration is manual, using 'Network Settings'. I'm able to access the internet just fine right now.


/etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


# OpenDNS Fallback (configured by Linux Mint in /etc/resolvconf/resolv.conf.d/tail).
nameserver 208.67.222.222
nameserver 208.67.220.220



```


/etc/hosts
```
ankit@HAL9000 ~ $ cat /etc/hosts127.0.0.1       localhost
127.0.1.1       MYCOMPNAME


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters



```

dig mydomain.com
```
; <<>> DiG 9.9.2-P1 <<>> mydomain.com;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64816
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 3


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;mydomain.com.                 IN      A


;; ANSWER SECTION:
mydomain.com.          38400   IN      A       10.3.3.68


;; AUTHORITY SECTION:
mydomain.com.          38400   IN      NS      ns2.mydomain.com.
mydomain.com.          38400   IN      NS      ns1.mydomain.com.


;; ADDITIONAL SECTION:
ns1.mydomain.com.      38400   IN      A       10.3.3.68
ns2.mydomain.com.      38400   IN      A       10.3.3.68


;; Query time: 1 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Sun Oct 27 08:30:54 2013
;; MSG SIZE  rcvd: 126



```

So dig is able to resolve the domain. I can open my website in Midori. A strange thing is that here the 'Server' is '127.0.1.1' whereas I supposed that the reply would come from '10.3.3.68'. 

I installed a Chrome extension to check the IP of whatever page I open. And it shows some strange IP: 67.215.65.132.


My mind is boggled.

---

### Post by bab1 on 2013-10-27
> **arnold_layne2 said:**
> /etc/network/interfaces
```

# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback


# iface eth0 inet static
#                address 10.3.3.68
#                netmask 255.255.255.0
#                gateway 10.3.3.1
#                dns-nameservers 10.3.3.68 10.1.1.61
```

I had  earlier manually hashed put the values inside 'iface eth0' just to test. Then I commented the whole thing out since it didn't make any difference. 
Remember my configuration is manual, using 'Network Settings'. I'm able to access the internet just fine right now.

So this is irrelevant right now.  The current settings can be seen with```
ifconfig -a
```...and what ever you have set in NM. 
> 


/etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


# OpenDNS Fallback (configured by Linux Mint in /etc/resolvconf/resolv.conf.d/tail).
nameserver 208.67.222.222
nameserver 208.67.220.220



```


/etc/hosts
```
ankit@HAL9000 ~ $ cat /etc/hosts127.0.0.1       localhost
127.0.1.1       MYCOMPNAME


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters



```

dig mydomain.com
```
; <<>> DiG 9.9.2-P1 <<>> mydomain.com;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64816
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 3


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;mydomain.com.                 IN      A


;; ANSWER SECTION:
mydomain.com.          38400   IN      A       10.3.3.68


;; AUTHORITY SECTION:
mydomain.com.          38400   IN      NS      ns2.mydomain.com.
mydomain.com.          38400   IN      NS      ns1.mydomain.com.


;; ADDITIONAL SECTION:
ns1.mydomain.com.      38400   IN      A       10.3.3.68
ns2.mydomain.com.      38400   IN      A       10.3.3.68


;; Query time: 1 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)  [COLOR="#FF0000"]<-- Resolved by this DNS server[/COLOR]
;; WHEN: Sun Oct 27 08:30:54 2013
;; MSG SIZE  rcvd: 126



```

So dig is able to resolve the domain. I can open my website in Midori. A strange thing is that here the 'Server' is '127.0.1.1' whereas I supposed that the reply would come from '10.3.3.68'. 


I installed a Chrome extension to check the IP of whatever page I open. And it shows some strange IP: 67.215.65.132.


My mind is boggled.
Here is what I see using the information you have supplied.  The dig command is being resolved by 127.0.1.1 (see the red annotation above) as it is configured in the /etc/resolv.conf file.  When using dig or nslookup you bypass the OS's normal methods of name resolution.  In normal operation the name resolution uses the /etc/hosts file first (dig doesn't).  This order is set by the /etc/nsswitch.conf file.  See ```
man nsswitch.conf
```...the term *files *refers to the /etc/hosts file.  Don't mess with this file.

In addition you have another problem.  By default the DNS server at 127.0.1.1 is configured as a caching only dns server in later versions of Ubuntu .  This is not a complete install of DNSmasq.  It is a striped down version that Ubuntu uses.  See [here]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-dns-resolving") for the details.  For a good explanation of the changes you can read [this]("https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/").  Can the default DNSmasq updated to provide full services?  I really don't know.  That's something that you will have to try to see if it works.

I use the Ubuntu 12.04.3 server edition so I manually configure the networking information in the /etc/networking and /etc/resolv.conf files.   My opinion also is that you should not be using 127.0.1.1 as the IP address of a web server of DNS server, even if you are only using that host only.  The proper way is to use the IP address of a NIC.  The loopback address is for internal testing only.  If you have other hosts in the network they will never see that DNS server as each one has a 127.0.1.1 loopback address of their own. My development web server is available to all with the FQDN or the hostname and is resolved to the IP address of the NIC at eht0.  The DNS sever resides on another host.

You have options here.  Use the /etc/hosts file for resolution or create a different DNS server or see if you can configure DNSmasq for your needs.

---

### Post by papibe on 2013-10-27
> **arnold_layne2 said:**
> A strange thing is that here the 'Server' is '127.0.1.1' whereas I supposed that the reply would come from '10.3.3.68'.
+1 to what  bab1 said.

In other words, Network Manager is using the DNSMasq plugin. To see what is the actual DNS being used run this:
```
nm-tool
```
> **arnold_layne2 said:**
> I installed a Chrome extension to check the IP of whatever page I open. And it shows some strange IP: 67.215.65.132.
That is your current public IP. In understand that your are configuring a local DNS (with forwarding I presume), so it will only resolve LAN address.

What software are you using for you DNS? Bind? DNSMasq?

Regards.

---

