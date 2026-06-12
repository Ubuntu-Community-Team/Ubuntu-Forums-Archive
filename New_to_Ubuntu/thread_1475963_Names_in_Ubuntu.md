---
title: "Names in Ubuntu"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by zcacogp on 2010-05-07
Chaps, 

OK. Putting my 'Beginner' credentials well and truly on public display here, I have always failed to understand computer names in Ubuntu. 

I have three machines. All running 10.4 Lucid. They are all given names, and the name appears at the command prompt whenever I open a terminal. 
They also are all given IP addresses when I log onto my local network. These names and IP addresses are as follows: 

desktop - 192.168.10.2
ogp-x31 - 192.168.10.23 (when on wireless)
x61s - 192.168.10.21 (when on wireless)

(These are set in my router.) 

The question is, is it possible to connect to the various machines across the network by using the name of the machine instead of the IP address? (When I say "connect to", I mean when using remote desktop or an NFS connection, for example.) This is asked partially because it is easier to remember a name than an IP address, and partially because the IP address of the latter two machines (both laptops) changes depending upon whether they are hooked up wirelessly or using a cable (hence the "when on wireless" comment above.) 

Can I connect to these machines using the names above (that appear in the terminal), or do I give them other names as well? If so, how do I do it? Do I set the name of the machine at the machine in question (i.e. tell the 'desktop' machine that it is called 'Desktop' and should therefore identify itself as that on the network), or do I tell all the other machines that the machine at 192.168.10.2 is called "Desktop"? (Did this make sense?) 

All assistance welcomed - thanks!


Oli.

---

### Post by jbrown96 on 2010-05-07
The easiest way is to setup /etc/hosts. Open it with a text editor like nano or vi ```
sudo vi /etc/hosts
``` ```
sudo nano /etc/hosts
``` Then add the IP address, tab, and hostname.

---

### Post by r-senior on 2010-05-07
Potential problem there is that wireless clients are probably allocated addresses using DHCP from the router and may not always get the same IP address, unless there is a way of making the addresses "sticky" in the router setup.

If you want slightly more functionality (esp DNS caching), have a look at dnsmasq. It can do DHCP too and will register the names of DHCP clients in your local DNS. You'd install dnsmasq on one machine (probably the fixed IP desktop machine) and it would use the /etc/hosts file as the source of name/address translation.

---

### Post by zcacogp on 2010-05-07
jbrown, 

Thanks. On any one machine, am I setting up the name of that machine, or the names of all the other machines on the network? 

My /etc/hosts file on this machine (desktop) looks like this: 

```
127.0.0.1	localhost
127.0.1.1	desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

I think this is pretty much as it came out of the box (I don't think I have changed it.) Why is it listing 127.0.1.1 as being the local machine? 

Thanks again for your help. 


Oli.

---

### Post by zcacogp on 2010-05-07
> **r-senior said:**
> Potential problem there is that wireless clients are probably allocated addresses using DHCP from the router and may not always get the same IP address, unless there is a way of making the addresses "sticky" in the router setup.

If you want slightly more functionality (esp DNS caching), have a look at dnsmasq. It can do DHCP too and will register the names of DHCP clients in your local DNS. You'd install dnsmasq on one machine (probably the fixed IP desktop machine) and it would use the /etc/hosts file as the source of name/address translation.
Thanks. Those IP addresses are sticky - I have set the router such that they are assigned by the router, and always the same (with the wireless/not wireless proviso.) 

Sorry to be thick, but DNS and DHCP are two terms I don't understand. Is there a good manual I can read up, or some helpful web pages? (I would ask you to explain, but it may involve a fair chunk of typing!)


Oli.

---

### Post by r-senior on 2010-05-07
Not too much typing I hope ... ;)

[DNS](http://en.wikipedia.org/wiki/Domain_Name_System) is Domain Name Service, which translates domain names, e.g. [www.ubuntu.com](www.ubuntu.com) to IP addresses, e.g. 91.189.90.40.

[DHCP](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CCAQFjAA&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FDynamic_Host_Configuration_Protocol&ei=OD7kS9PEHY_u0wSvkIW1AQ&usg=AFQjCNF1ddj1C67TIrMvwagdAd-OoGczUQ&sig2=0CzsyjmQcaEdOkumJB-OHQ) is Dynamic Host Configuration Protocol which allocates IP addresses from a pool of addresses as clients request them. That's what's happening in your router (although you;ve configured them as sticky).

127.0.0.1 is a special IP address (aka the [loopback address](http://en.wikipedia.org/wiki/Loopback_address)) which refers to the machine you are on. The entry in your hosts file is associating the domain name "localhost" with that loopback address, which is the usual convention.

The entry in /etc/hosts for "desktop" should be set to 192.168.10.2 (the IP address of the desktop machine).

You can check what's going on using ping ...

$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.093 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.083 ms

$ ping desktop
PING desktop (192.168.10.2) 56(84) bytes of data.
64 bytes from desktop (192.168.10.2): icmp_seq=1 ttl=64 time=0.093 ms
64 bytes from desktop (192.168.10.2): icmp_seq=2 ttl=64 time=0.083 ms

---

### Post by srs5694 on 2010-05-07
FWIW, many routers today are actually highly specialized Linux systems that run, among other things, the dnsmasq server referred to by r-senior. Some of those that aren't Linux-based include similar functionality via other software. It's therefore conceivable that you'll be able to do the job just by setting names in the router, without adjusting /etc/hosts or any other file on your local computer.

You can check on one important detail by typing "cat /etc/resolv.conf". This file contains one or more nameserver lines, each of which points to a DNS server by IP address. If you've got a nameserver line that points to your router's IP address, then chances are it's running a DNS server. That DNS server might do nothing more than forward DNS queries to your ISP's DNS server, or it might be configurable to handle local name resolution. You'll have to check your router's documentation to learn what it can do. If you find that confusing, try posting the name and model number of your router, or see if the manufacturer has a forum where you can ask questions. If your /etc/resolv.conf file doesn't refer to your router, but includes entries pointing to a DNS server run by your ISP, then either your router doesn't have DNS capabilities or you've configured it to tell your network's computers to use your ISP's DNS server directly rather than use the router for this.

If the router doesn't have sufficient DNS capabilities, then the simplest course is to adjust /etc/hosts, as r-senior suggests. Since you've apparently configured your router to assign fixed IP addresses to your network's computers, this should work fine. The main drawback is that you must adjust all your /etc/hosts files whenever you make a change -- say, if you add a new computer to your network. With only three systems, this probably isn't a big deal, though. (If your router has DNS capabilities, then you can just adjust its configuration and all your systems will see those changes automatically.)

---

### Post by jbrown96 on 2010-05-07
I wouldn't bother with DNS. It's a decent amount of work to setup for just a few machines. I forgot to post my hosts file earlier ```
127.0.0.1	localhost
127.0.1.1	hyperion
10.0.0.3	main
10.0.0.5	phoenix
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

``` You can see that I've added two entries for main and phoenix.

---

### Post by zcacogp on 2010-05-07
Chaps, 

Thanks for the answers. I think I am following it, correct me if I am wrong; a DNS is a central list of all the machines which are available, and the IP addresses that they take. Which clearly needs to be a part of the system that is handing out IP addresses, so that if IP address *n* is given to machine *x*, it knows that machine *x *can be found at address *n*. If machine *x* disconnects and later reconnects, and is given address *m* then the DNS then knows that machine *x *can be found at *m*. 

... and the /etc/hosts file is a small-scale substitute for a DNS - non? So you'd need to have the name and corresponding IP address of all the machines in the network in the /etc/hosts file on each machine? 

If this is the case then I still have an outstanding question (which may yet have to be answered by experimentation.) Of my three machines I have two laptops; 'ogp-x31' and 'x61s'. These each have two network connections - a wireless one and an ethernet one. Depending upon the means by which the machine is connected to the internet (wirelss or ethernet), they will take a different IP address. So ogp-x31s could be 192.168.10.23 if hooked up wirelessly, or 192.168.10.24 if plugged in via an ethernet cable. Can I have two entries in the /etc/hosts file for one machine? i.e. Can my /etc/hosts file look like this: 

```

192.168.10.21      x61s
192.168.10.22      x61s
192.168.10.23      ogp-x31s
192.168.10.24      ogp-x31s

```

(If the answer is 'go and try it', that's fine!) 

Thanks for your help - everyone. I still don't quite follow the localhost thing, but will read the wiki article again and see if I make some progress. 


Oli.

---

### Post by zcacogp on 2010-05-07
> **srs5694 said:**
> 
You can check on one important detail by typing "cat /etc/resolv.conf". This file contains one or more nameserver lines, each of which points to a DNS server by IP address. If you've got a nameserver line that points to your router's IP address, then chances are it's running a DNS server. That DNS server might do nothing more than forward DNS queries to your ISP's DNS server, or it might be configurable to handle local name resolution. You'll have to check your router's documentation to learn what it can do. If you find that confusing, try posting the name and model number of your router, or see if the manufacturer has a forum where you can ask questions. If your /etc/resolv.conf file doesn't refer to your router, but includes entries pointing to a DNS server run by your ISP, then either your router doesn't have DNS capabilities or you've configured it to tell your network's computers to use your ISP's DNS server directly rather than use the router for this.

srs5694, 

Thanks for this. For what it's worth, if I do as you suggested I get this: 

```
ogp@desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.10.1
```

And the router is a Netgear dg834gt wireless router. 


Oli.

---

### Post by jbrown96 on 2010-05-07
> **zcacogp said:**
> Chaps, 

Thanks for the answers. I think I am following it, correct me if I am wrong; a DNS is a central list of all the machines which are available, and the IP addresses that they take. Which clearly needs to be a part of the system that is handing out IP addresses, so that if IP address *n* is given to machine *x*, it knows that machine *x *can be found at address *n*. If machine *x* disconnects and later reconnects, and is given address *m* then the DNS then knows that machine *x *can be found at *m*. 

... and the /etc/hosts file is a small-scale substitute for a DNS - non? So you'd need to have the name and corresponding IP address of all the machines in the network in the /etc/hosts file on each machine? 

If this is the case then I still have an outstanding question (which may yet have to be answered by experimentation.) Of my three machines I have two laptops; 'ogp-x31' and 'x61s'. These each have two network connections - a wireless one and an ethernet one. Depending upon the means by which the machine is connected to the internet (wirelss or ethernet), they will take a different IP address. So ogp-x31s could be 192.168.10.23 if hooked up wirelessly, or 192.168.10.24 if plugged in via an ethernet cable. Can I have two entries in the /etc/hosts file for one machine? i.e. Can my /etc/hosts file look like this: 

```

192.168.10.21      x61s
192.168.10.22      x61s
192.168.10.23      ogp-x31s
192.168.10.24      ogp-x31s

```

(If the answer is 'go and try it', that's fine!) 

Thanks for your help - everyone. I still don't quite follow the localhost thing, but will read the wiki article again and see if I make some progress. 


Oli.
You can't have two entries with the same name. Your system will find the first (192.168.10.23) and stop searching, even if 192.168.10.23 isn't active. It will never get to the .24 entry.

You should actually create different entries for each interface. I have three machines A, B, and C. A and B only have a wired interface and always get the same address. C could have two addresses. The actual name for an address in /etc/hosts doesn't matter. It's like in Algebra; you can call a variable x or y as long as you are consistent. 
In this case one machine A, I would do > 
10.0.0.2 B
10.0.0.3 C-wired
10.0.0.4 C-wireless Then if you want to ssh into C, you just do ```
ssh C-wired
``` or ```
ssh C-wireless
```
You can change the names to whatever you want; I could even change A's entry to X, although it would be confusing to the user. Any time your system expects a internet address and gets a name instead, it goes to /etc/hosts and looks for a matching entry. 
Just make sure not to create any entries for A in A's /etc/hosts and same for the other machines.
The problem with running your own DNS server is that it's designed to have a hostname on the internet (like google.com). 

A DNS server is slightly different from how you are explaining it. The way you said it is both DNS+DHCP. Think of it like physical addresses. The city planer or someone decides what your actual street address is; you have no say over this. This is DHCP. DNS is like the telephone book. It takes a of addresses, which are probably provided by the city, and then matches people's names (and phone numbers) to those pre-assigned addresses.

---

### Post by zcacogp on 2010-05-09
Sorry for the slight delay in replying. 

jbrown - thanks. Very helpful. I've done as you suggested, and it works fine. Yes, I had to name the two laptops twice (x31s and x31s - cable, for instance), but this was no great shakes. 

Your analogy of a town planner was helpful too. I think I'd like to play with the DNS and DHCP settings in the router to see whether I can come up with a more elegant solution, but that's another job for another time. And I get the impression that it is more of a router-based issue than an Ubuntu-based issue, so there isn't much point in asking on here (I'd do better to ask on a forum specifically for Netgear routers.) 

Thanks again for your help. 


Oli.

---

