---
title: "home web server can't be visited from outside my local network"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by flyingdragon on 2008-02-11
Hi,

I am setting up a home webserver with ubuntu server 6.06 lts. I followed the 'the perfect set up' guide to page three(setting up network) and also installed apach2. I am able access it from within my local network but not able to visit it from outside my local network. 

here are my settings. I'm using AT&T, so I have a modem, a linksys wrt54G router, one laptop, and a desktop. The desktop is installed with ubuntu 6.08 lts.

The modem:
Modem IP Address	192.168.0.1
IP Address	68.122.50.xxx
IP Gateway	68.122.51.254
DNS Servers	68.94.156.1  dnsr1.sbcglobal.net
68.94.157.1  dnsr2.sbcglobal.net

The router:
IP Address:  	68.122.50.xxx  
Local IP Address: 192.168.1.1	   	 
Subnet Mask: 	255.255.255.0 	  	
Default Gateway: 	68.122.50.250 	  	
DNS 1: 	192.168.0.1

The server: network/interface
iface eth0 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        #network 192.168.1.0
        #broadcast 192.168.1.255
        gateway 192.168.1.1

resolve.conf
        nameserver 192.168.1.1

I did port forwarding and opened two ports for 192.168.1.101 in the router setting.
port 22 for ssh
port 80 for webserver 

Now from my laptop, I can ssh 192.168.1.101 , I can also visit 192.168.1.101 to reach the apache2 default page. But I can't ssh 68.122.50.xxx  or visit 68.122.50.xxx  with browser to reach the apache2 default page.

any help?

---

### Post by jetsam on 2008-02-12
Just a possibility:  On your router admin page, make sure security-->firewall-->"Filter Internet Nat Redirection" is unchecked.  Otherwise, you can't test your servers using your external ip address from inside your network.

---

### Post by flyingdragon on 2008-02-13
It is unchecked. the weird thing is that the connection is very unstable. most of the time I can't ssh my external ip address, but sometime I can. Most of the time I can't visit my external IP with a browser, very few times I can.

what the heck is the problem?

---

### Post by jetsam on 2008-02-13
Is it maybe that AT&T is blocking the ports?  Google shows a lot of web pages that say they do block ports.  

If you want to try a different port for ssh:
You can change the port ssh is listening on by editing /etc/ssh/sshd.config
and changing the port line:
```
# What ports, IPs and protocols we listen for
Port 2223

```

and then restarting ssh with 
```
sudo /etc/init.d/ssh restart
```

You'll have to change your router port forwarding as well.  To connect to the new port use:
```
ssh -p 2223 <user>@<ipaddress>
```

---

