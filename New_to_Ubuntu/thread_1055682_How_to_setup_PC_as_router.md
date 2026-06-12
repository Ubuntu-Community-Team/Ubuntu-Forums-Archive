---
title: "How to setup PC as router?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by deadguysleeps on 2009-01-31
I'm really new to linux (I'm a long time Windows user), so far, i've figured out how to install ubuntu 8.10 on several laptops, setup the ip address and using Samba to share files over a network. And I do this without any command line at all, which I'm impressed. (i thought linux will be terrifying after i heard stories that a user need to use the command line a lot)

Right now, my lecturer asked my group to do this:
---------------------------------------------------------------
Instructions and Tasks :

1. Design and implement a simple network
   consist of minimum 3 PCs; One PC will be the router, one PC
   will be the server and another PC will be the client.

2. Install and configure Proxy Server.
3. Install and configure a Web Server.
4. Install and configure DNS servers.

• Your network must have Internet access.
----------------------------------------------------------------

1)So... what is the concept behind these configurations? I don't get it.
  Is this topology correct?

  university's internet ---> Pc as router ---> Server ---> Client

2) What kind of software should I use for the server?

3)I tried googling "pc as router" but I found that I have to install 2 network cards, which is impossible, as we only have laptops.


Can you help me?

---

### Post by Synt4xError on 2009-01-31
The only thing I can answer is, YES you do need 2 nic cards on one machine as far as I know. You need a NIC dedicated for the net, and another to distribute.

My friend is using his laptop as a router. He has a Hand held PDA that acts as a modem. Then he bought a plug-n-play nic card with a rj45 port and configured it with in windows and hooked it up to a hub.

Thats the best I can answer!

---

### Post by TCSnyder on 2009-01-31
well if you only have laptops, then they do have usb network cards.

---

### Post by deadguysleeps on 2009-01-31
usb network cards, huh? I think I can buy those.

But I still don't get the concept behind "PC as router". I thought router is like Belkin, D-Link, Aztech, Linksys, etc...

How do I set up the PC as the router?

---

### Post by Abu_Dayya on 2009-01-31
Actually, routers are nothing more that a machine that has two network cards, and one network card can farward packets to the other card. One card will be for your external IP (to connect to the internet) and the other will be connected to your LAN.

---

### Post by GammaRay256 on 2009-01-31
In response to question #2, what kind of software should you use:

Web server - Apache (apt-get install apache2)
Proxy Server - Squid Proxy Server

You said "install and configure DNS server_**s**_"
If you need to run a DNS server, use:
BIND ([http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093))
Or, if you just need DNS servers, use opendns.com

---

### Post by deadguysleeps on 2009-01-31
> **Abu_Dayya said:**
> Actually, routers are nothing more that a machine that has two network cards, and one network card can farward packets to the other card. One card will be for your external IP (to connect to the internet) and the other will be connected to your LAN.

I see...

> 
by GammaRay256:

[I]In response to question #2, what kind of software should you use:

Web server - Apache (apt-get install apache2)
Proxy Server - Squid Proxy Server

You said "install and configure DNS servers"
If you need to run a DNS server, use:
BIND ([http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093))
Or, if you just need DNS servers, use opendns.com[/I] 

Um, what's the difference between dns server and server**s**?

Ok, thanks, I'll try it in a few days after I gather my group.

---

### Post by GammaRay256 on 2009-02-01
> **deadguysleeps said:**
> I see...



Um, what's the difference between dns server and server**s**?

Ok, thanks, I'll try it in a few days after I gather my group.

Well, when you configure your local connection on each machine, you can specify DNS servers that your computer will use to lookup IP addresses when given a domain name.  (eg. if you enter "google.com" into Firefox, your computer checks whatever DNS servers are set (usually the ISPs, or OpenDNS) and figures out what IP address that domain has)...  These servers are usually automatically set with DHCP.

If you just need to configure the DNS servers for each computer, it's probably easiest to just set them to the two OpenDNS IPs (208.67.222.222 and 208.67.220.220).  Or set your DHCP server to use those addresses.

I suppose there are reasons to run your own DNS server, but I don't know enough about DNS to tell you whether you should have on or not.

---

### Post by sandyd on 2009-02-01
inteligent thought..

i saw someone asking about sharing their internet over wifi....

why don't you create a wifi network. that would work (i'm guessing that your laptops have wifi)

try THAT!!

---

### Post by deadguysleeps on 2009-02-12
> **carlee said:**
> inteligent thought..

i saw someone asking about sharing their internet over wifi....

why don't you create a wifi network. that would work (i'm guessing that your laptops have wifi)

try THAT!!

my university's wifi is bad, but i have bought the usb to lan device.

one more thing, i found this on linuxquestions.org :
> Ok, from what you have said you have/want something like this:

```

Internet Router (10.0.0.1)
      |
     eth0 (10.0.0.2)
   Linux Box 
     eth1 (192.168.0.1)
      |
  Lan Switch
Other Computers

```
So what you want to do is Proxy the html on the linux box (squid is as good as any) and Nat the other computers.

So lets start with the lan stuff.
The quickest way to do this is staticly map the other computers to the 192.168.0 network and set their default route to the eth1 ipaddress on the linux box. This means that if you PC tries to connect to an IP not on your network it sends it to the default route address (your Linux Box).
You can install a DHCP server on the linux box to make things easier in the long run (look up dhcp server at you distros web site and look for a FAQ or Howto on it).

Now we have the off net packets going to the right place you need to install and configure a firewall gui (if not already installed) for ease, you could do it by hand if you like but if I was you I wouldn't to start with. There are a few out there, firestarter was prity cool at one point but they don't seem to be fixing it mutch now days. Use your choice of software to setup your iptables and it should also sort out the forwarding for you. This now means you have internet access from behind you linux box, but DNS probably won't work.

DNS, two ways to do this, the first is to use your internet router as you dns server, the second is to install a DNS server on your linux Box and set it up as you see fit (probably just a DNS Caching server) FAQ's and Howto's are out there, have a read and they should sort you out.

The last thing to do is check that squid is running on your Linux Box then point your web browsers proxy settings at port 3128 (default for squid) on the linux box. You can also do enforced proxy by adding a rule to your iptables, the instructions are some place in the Documents at squid.

i don't understand the iptables thing. I have searched the internet, but I don't know about:

1) where should I input the iptables code? in the terminal?
   what is the ip addresses should i use?

2) which computer should I input the iptables? The "pc as router" or the computer that wanted to become "proxy server, web server & dns server" ? (when i googled "configure transparent squid", the tutor always setup iptables after configuring squid, but they don't make it easier for a newbie to understand what are they talking about)

Again, i try to draw my topology over here:

```

     
     |
     |    (eth1: 10.5.18.x, gateway: 10.5.18.254)   
  pc as router
     |    (eth0: 192.168.0.1)
     |
     |
   switch
     |
 -----------------------------
 |                           |          
client                 (proxy/web/dns server)
                    (eth0: 192.168.0.77 , gateway: 192.168.0.1)

```

is my topology correct?

---

### Post by kavon89 on 2009-02-12
You've got to assign each network card to a seperate subnet (I think that is the term). Ex: 192.168.1.x and 192.168.0.x

Then you pretty much set up your iptables, squid, and cups to accept connections from the local subnet, and properly route/forward connections from the local subnet to the public one.

I have my network set up with static ips, one could set up some DHCP server or somthing to assign ips automatically. I also just assigned my DSL modem as the DNS.

---

### Post by deadguysleeps on 2009-02-14
> **kavon89 said:**
> You've got to assign each network card to a seperate subnet (I think that is the term). Ex: 192.168.1.x and 192.168.0.x

Then you pretty much set up your iptables, squid, and cups to accept connections from the local subnet, and properly route/forward connections from the local subnet to the public one.

I have my network set up with static ips, one could set up some DHCP server or somthing to assign ips automatically. I also just assigned my DSL modem as the DNS.


```

     
     |
     |    (eth1: 10.5.18.x, gateway: 10.5.18.254)   
  pc as router
     |    (eth0: 192.168.0.1)
     |
     |
   switch
     |
 -----------------------------
 |                           |          
client                 (proxy/web/dns server)
                    (eth0: 192.168.1.77 , gateway: 192.168.0.1)

```

1) Can you tell me first is this topology correct, or if it is wrong, should I install proxy server and dns server in the "pc as router"?

2) My project says that i have to install dns server, so I cannot just insert the opendns ip address in the "pc as router" ?

3) i don't want to install dhcp server, because i want to learn without using dhcp (for now)

4) sorry.... but i am real noob, and i don't understand your sentence:
> Then you pretty much set up your iptables, squid, and cups to accept connections from the local subnet, and properly route/forward connections from the local subnet to the public one.

---

### Post by linux_tech on 2009-02-14
You can edit the iptables through the terminal

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by rogasgr on 2009-02-14
hello. this is my first post, hehe! :popcorn:

your exercise is not really diff but it needs certain knowledge. 
let's start:
topology is not a problem, you can have any topology u like since traffic doesn't know topologies, meaning you can throw 3 pc's on a switch and u have the wright topology as soon as you have the correct configs.
pc config:
  ip                   192.168.1.3
  subnet               255.255.255.0
  deflt gateway        192.168.1.2   (server)
  dns server primary   192.168.1.2
             secondary 192.168.1.2
  domainName           pc1.lan

router config:
ip                     192.168.1.2
subnet                 255.255.255.0
def gteway             192.168.1.1  (he has gateway the router, that means that every traffic destinated outside the servers lan will be directed to the router)
dns server             he will be dns server (dont know how :guitar:)
              but e will also have dns server the router for domains asked outside the lan

domainName              server.lan


router config:         192.168.1.1
subnet                 255.255.255.0
def gatewwy            wan port e.g. pppoe_1
dns                    brought by isp automatically
domain name           FOR ethernet use only    router.lan




download apache as above said a friend... get a .html saying this is the webserver of .lan domain. get a dns running, screw the proxy (i dont know ****) and get a good grade :P 

i hope i helped:guitar:

---

### Post by blueridgedog on 2009-02-14
> **deadguysleeps said:**
> ```

     
     |
     |    (eth1: 10.5.18.x, gateway: 10.5.18.254)   
  pc as router
     |    (eth0: 192.168.0.1)
     |
     |
   switch
     |
 -----------------------------
 |                           |          
client                 (proxy/web/dns server)
                    (eth0: 192.168.1.77 , gateway: 192.168.0.1)

```

1) Can you tell me first is this topology correct, or if it is wrong, should I install proxy server and dns server in the "pc as router"?

2) My project says that i have to install dns server, so I cannot just insert the opendns ip address in the "pc as router" ?

3) i don't want to install dhcp server, because i want to learn without using dhcp (for now)



If your routing PC has in internal network of 192.168.0.1 and it is configured as a class C address block with a mask of 255.255.255.0, then your server is not on the same network with an ip of 192.168.1.77.  A better IP would be any one from 192.168.0.2 to 192.168.0.254 (the last is used for the "network" and you have used the first for the router already).

You can install some of the services on the router, DNS is especially suited to running on a routing device.  

I too recommend against DHCP in this environment.

One thing to clarify from your instructor is if network address translation is required on the router or if simply routing is required.

---

### Post by deadguysleeps on 2009-02-15
> **linux_tech said:**
> You can edit the iptables through the terminal

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

i think that page teach how to setup iptables as firewall, not routing, and i don't really understand that tutorial. Sorry for being a noob...

Anyway, i found this from [http://kuscsik.blogspot.com/2008/01/transparent-proxy-with-squid-3-on.html]("http://kuscsik.blogspot.com/2008/01/transparent-proxy-with-squid-3-on.html")

> Last but not the least we need to redirect the HTTP traffic to your new shiny proxy

iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.0.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128

where eth1, eth0 are the LAN, WAN devices and 192.168.0.1 is the IP address of your LAN device.

how do I fit in the iptables (from above) for my configuration? Should i change the 
```
iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.0.1:3128
```

to this?
```
iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.1.1:3128
```

This is my new proposed configuration with my current understanding (i don't really understand much, actually), based on everyone's advices:
```
     
     |
     |
     |    (eth1:    10.5.18.100/24 (taken from comp.lab's ip address)
     |     gateway: 10.5.18.254 (the university's default route)
     |     dns:     10.0.8.19   (the university's dns server)
     |     domain:  router.lan) 
     |
  "pc as router"(with proxy & dns server)
     |
     |    (eth0:    192.168.1.1/24)
     |     gateway: 10.5.18.100
     |     dns:     10.5.18.100
     |     domain:  server.lan) 
     |
     |
   switch
     |
 -----------------------------
 |                           |          
client                  (web server)
                    (eth0:    192.168.1.77/24
                     gateway: 192.168.1.1)
                     dns:     192.168.1.1
                     domain:  pc1.lan )

```

Next, I want to install the proxy and dns server on the "pc as router" because I want the "pc as router" to cache the web and collect dns thingy from... i don't know... rootserver of the world? Then, route the external lan to internal lan using iptables.

My last question: Is my "current understanding of this configuration" correct or not? Again, sorry for being noobish...

---

### Post by blueridgedog on 2009-02-15
> **deadguysleeps said:**
> 
to this?
```
iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.1.1:3128
```

This is my new proposed configuration with my current understanding (i don't really understand much, actually), based on everyone's advices:
```
     
     |
     |
     |    (eth1:    10.5.18.100/24 (taken from comp.lab's ip address)
     |     gateway: 10.5.18.254 (the university's default route)
     |     dns:     10.0.8.19   (the university's dns server)
     |     domain:  router.lan) 
     |
  "pc as router"(with proxy & dns server)
     |
     |    (eth0:    192.168.1.1/24)
     |     gateway: 10.5.18.100
     |     dns:     10.5.18.100
     |     domain:  server.lan) 
     |
     |
   switch
     |
 -----------------------------
 |                           |          
client                  (web server)
                    (eth0:    192.168.1.77/24
                     gateway: 192.168.1.1)
                     dns:     192.168.1.1
                     domain:  pc1.lan )

```

My last question: Is my "current understanding of this configuration" correct or not? Again, sorry for being noobish...

Well, if you want to push port 80 traffic from the outside, hitting the outside interface of your router, to your inside web server, residing at 192.168.1.77, you would use:
```

iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.1.77:80
```

That assumes your inside web server is running on port 80, if it is using another port, they change the 192.168.1.77:80 as needed.

Looking at your setup, you will not need to state a gateway for the eth0 of the router as the router has a gateway already (10.5.18.254), nor will you need to explicitly state a DNS server for eth0, as DNS is relative to the OS as a whole and not each interface.  I would list your external eth1 as the DNS for all systems as you will in the long run make it a stand alone fully functional DNS server.  I am not certain what you mean by domain.

You are doing great!  Do you have the gear to mock up this?

---

### Post by deadguysleeps on 2009-02-15
in the past few hours, i tried to  configure squid, using tutorial from this site: [http://kuscsik.blogspot.com/2008/01/transparent-proxy-with-squid-3-on.html]("http://kuscsik.blogspot.com/2008/01/transparent-proxy-with-squid-3-on.html")

and this is what he said about editing the config file:
> and set the transparency and the allowed hosts

http_port 3128 transparent
acl our_networks src 192.168.0.0/24
acl localnet src 127.0.0.1/255.255.255.255
http_access allow our_networks
http_access allow localnet

I don't understand what it means, so i'm guessing:
```
acl our_networks src 192.168.0.0/24
```
is to set the an access list for the network 192.168.0.0/24

and
```
acl localnet src 127.0.0.1/255.255.255.255
```
is to set the an access list for 127.0.0.1/255.255.255.255 ?

Am I correct?

After configuring squid & restarting it, I access the log file (using tail -f) & nothing showed up. So i go to System > Preferences > Network Proxy & configure it manually, set the HTTP proxy to 127.0.0.1 port 3128. And then, poof! The log file start filling in. Err... what just happened?

But, a problem showed up... I can't access the my html file (from the browser: [http://localhost/wolfmechanic/](http://localhost/wolfmechanic/)) that i put in my xampp folder (/opt/lampp/htdocs/wolfmechanic). It says:
```
You don't have permission to access /wolfmechanic/ on this server.
Apache/2.2.11 (Unix) DAV/2 mod_ssl/2.2.11 OpenSSL/0.9.8i PHP/5.2.8 mod_apreq2-20051231/2.6.0 mod_perl/2.0.4 Perl/v5.10.0 Server at localhost Port 80
```

Before this, my website on the localhost showed up perfectly in the browser, I wonder what happen? I've tried googling the 
```
You don't have permission to access /wolfmechanic/ on this server.
Apache/2.2.11 (Unix) DAV/2 mod_ssl/2.2.11 OpenSSL/0.9.8i PHP/5.2.8 mod_apreq2-20051231/2.6.0 mod_perl/2.0.4 Perl/v5.10.0 Server at localhost Port 80
```

but i don't get any answer... any help please? I never set any security permission on xampp. The xampp homepage ([http://localhost/](http://localhost/)) showed up but not my webpage.

---

### Post by rogasgr on 2009-02-15
> 
```
     
     |
     |
     |    (eth1:    10.5.18.100/24 (taken from comp.lab's ip address)
     |     gateway: 10.5.18.254 (the university's default route)
     |     dns:     10.0.8.19   (the university's dns server)
     |     domain:  router.lan) 
     |
  "pc as router"(with proxy & dns server)
     |
     |    (eth0:    192.168.1.1/24)
     |     gateway: 10.5.18.100
     |     dns:     10.5.18.100
     |     domain:  server.lan) 
     |
     |
   switch
     |
 -----------------------------
 |                           |          
client                  (web server)
                    (eth0:    192.168.1.77/24
                     gateway: 192.168.1.1)
                     dns:     192.168.1.1
                     domain:  pc1.lan )

```




I think you should do this...

```
     
     |
     |
     |    (eth1:    10.5.18.100/24 (taken from comp.lab's ip address)
     |     gateway: 10.5.18.254 (the university's default route)
     |     dns:     10.0.8.19   (the university's dns server)
     |     domain:  router.lan)   <-no need cause dns is only for the        private network, you dont care all the uni to know the .lan network
     |
  "pc as router"(with proxy & dns server)
     |
     |    (eth0:    192.168.1.1/24)
     |     gateway: 10.5.18.100
     |     dns:     10.5.18.100
     |     domain: router.lan) 
     |
     |
   switch
     |
 -----------------------------------
 |                                 |          
client                      (web server)
domain:  pc1.lan )      (eth0:    192.168.1.77/24
                        gateway: 192.168.1.1)
                        dns:     192.168.1.1
                        domain:  server.lan) 

```

---

### Post by deadguysleeps on 2009-02-15
i have installed bind9 on the "pc as router", right now i tried to configure bind, so i went to:
[https://help.ubuntu.com/8.10/serverguide/C/dns-configuration.html]("https://help.ubuntu.com/8.10/serverguide/C/dns-configuration.html")

but now, i'm stuck at:
> **Caching Nameserver**

The default configuration is setup to act as a caching server. All that is required is simply adding the IP Addresses of your ISP's DNS servers. Simply uncomment and edit the following in /etc/bind/named.conf.options:

forwarders {
                1.2.3.4;
                5.6.7.8;
           };

Replace 1.2.3.4 and 5.6.7.8 with the IP Adresses of actual nameservers. 

So, what ip address should i use? Is it: 10.0.8.19 (based on the university's dns server) ?

---

