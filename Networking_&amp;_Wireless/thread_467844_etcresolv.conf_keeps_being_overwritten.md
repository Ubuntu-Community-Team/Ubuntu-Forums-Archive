---
title: "/etc/resolv.conf keeps being overwritten"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by minj on 2007-06-08
Hello. As far as I know, this file is used to save DNS server ips, right? It worked fine in dapper when I added 
```

nameserver x.x.x.x
nameserver y.y.y.y

```
to it, x.x.x.x & y.y.y.y coresponding to my ISP's DNS servers. This was useful because otherwise I had to manually enter those addresses to network-admin everytime I booted. By default DNS is 192.168.1.1 coresponding to my router. Now when I switched to feisty the file seems to be overwritten with defaults (that is 192.168.1.1) everytime I boot. I even tried to disable write access to the file but that didn't help either :) Then I tried to create a new location in network-admin but everytime I boot I have to switch it on manually. So my question is: how to make /etc/resolv.conf stay there or how to make the newly created location loaded by default?

---

### Post by bapoumba on 2007-06-08
Hi,
not sure I can help you all the way through, others will. But what kind of router do you have? Do you use DHCP or static IP? What does return:
```
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig
```

---

### Post by minj on 2007-06-08
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

nameserver x.x.x.x
nameserver y.y.y.y
eth0      Link encap:Ethernet  HWaddr 00:20:ED:74:FA:A7  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:edff:fe74:faa7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:259489 errors:0 dropped:0 overruns:0 frame:0
          TX packets:313750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:148558953 (141.6 MiB)  TX bytes:144424729 (137.7 MiB)
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6847 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:243411 (237.7 KiB)  TX bytes:243411 (237.7 KiB)

```

Yes I use DHCP. Everyhting is ok with my internet (otherwise I wouldn't be able to post here :)), it's just that I have to set these settings explicitly everytime I boot which is rather annoying. My only question is: how to make them "stick"?

---

### Post by nixfaced on 2007-06-08
Does DNS not work when using the router's IP as a nameserver?  Most home routers these days act as DNS forwarders that send your queries on to the ISP's nameservers.  In theory, things should work fine with that setup.

If you really just want to use the ISP's nameservers directly, you should be able to do so by sudo editing /etc/dhcp3/dhclient.conf to include the line 

supersede domain-name-servers server-ip1 server-ip2 

and then sudo invoke-rc.d networking restart.

---

### Post by minj on 2007-06-08
My router's DNS seems to be incomplete or slow, ISP's DNS works much better. Anyway, your suggestion worked, so thank you.

---

### Post by fakie_flip on 2007-06-08
Here is part of the Help Documentation that is included with Ubuntu Feisty. To get to it, click on System>Help and Support>Advanced Topics>Installing Server Applications>Networking>Network Configuration```
In this case, you will need to specify your DNS servers manually in
		/etc/resolv.conf, which should look something like this:
		

search mydomain.example
nameserver 192.168.0.1
nameserver 4.2.2.2


		The search directive will append mydomain.example
		to hostname queries in an attempt to resolve names to your network.  For example,
		if your network's domain is mydomain.example and you try to ping the host
		&#8220;mybox&#8221;, the DNS query will be modified to &#8220;mybox.mydomain.example&#8221;
		for resolution.  The nameserver directives
		specifiy DNS servers to be used to resolve hostnames to IP addresses.  If you use
		your own nameserver, enter it here.  Otherwise, ask your Internet Service Provider
		for the primary and secondary DNS servers to use, and enter them into
		/etc/resolv.conf as shown above.

Many more configurations are possible, including dialup PPP interfaces, IPv6
		networking, VPN devices, etc.  Refer to man 5 interfaces
		for more information and supported options.  Remember that
		/etc/network/interfaces is used by the 
		ifup/ifdown scripts as a
		higher level configuration scheme than may be used in some other Linux distributions,
		and that the traditional, lower level utilities such as ifconfig,
		route, and dhclient are still
		available to you for ad hoc configurations.
		
2.1.2.&#8195;Managing DNS Entries

This section explains how to configure which nameserver
            to use when resolving IP addresses to hostnames and vice
            versa. It does not explain how to configure the system as a name
            server.
            


            To manage DNS entries, you can add, edit, or remove DNS names
            from the /etc/resolv.conf file. A sample file is given below:
            

search com
nameserver 204.11.126.131
nameserver 64.125.134.133
nameserver 64.125.134.132
nameserver 208.185.179.218


             The search key specifies the string
             which will be appended to an incomplete hostname. Here, we
             have configured it to com. So, when we
             run: ping ubuntu it would be interpreted
             as ping ubuntu.com.
            


            The nameserver key specifies the
            nameserver IP address. It will be used to resolve a given
            IP address or hostname. This file can have multiple nameserver
            entries. The nameservers will be used by the network query
            in the same order.
            

            


[COLOR="Red"]            If the DNS server names are retrieved dynamically from DHCP
            or PPPoE (retrieved from your ISP), do not add nameserver
            entries in this file. It will be overwritten.[/COLOR]
           

            

            


            The changes you make in /etc/resolv.conf
            will be erased when you reboot your machine. If you want to
            make this change permanent, you should install
            resolvconf package from the Universe repository and 
	    update the DNS information in the
            /etc/resolvconf/resolv.conf.d/base
            file provided by that package.
           

            
2.1.3.&#8195;Managing Hosts


            To manage hosts, you can add, edit, or remove hosts from
            /etc/hosts file. The file contains IP
            addresses and their corresponding hostnames.  When your
            system tries to resolve a hostname to an IP address or
            determine the hostname for an IP address, it refers to the
            /etc/hosts file before using the name
            servers.  If the IP address is listed in the
            /etc/hosts file, the name servers are
            not used.  This behavior can be modified by editing 
			/etc/nsswitch.conf at your peril.
            


            If your network contains computers whose IP
            addresses are not listed in DNS, it is recommended that you
            add them to the /etc/hosts file.
```

---

