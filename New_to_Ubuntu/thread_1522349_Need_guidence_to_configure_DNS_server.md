---
title: "Need guidence to configure DNS server"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by honey_bee on 2010-07-02
Hi,
           I am using Linux .I want to configure DNS server on my Linux machine.Any tutorial/Belog from where I can Learn it ?
 
honey

---

### Post by Sanjeevtrip on 2010-07-02
Hi,

you can checkout this

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch18_:_Configuring_DNS](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch18_:_Configuring_DNS)

---

### Post by honey_bee on 2010-07-02
well any more site ...I am new in Linux and want to configure DNS or you say BIND

---

### Post by surfer on 2010-07-02
i use dnsmasq. very easy: it reads your [FONT="Courier New"]/etc/hosts[/FONT] file and spits out what it finds in there.

dnsmasq can also be used as DHCP and/or TFTP server. the example configurations in [FONT="Courier New"]/etc/dnsmasq.conf[/FONT] sould be easy to understand.

so, basically:
```

$ sudo apt-get install dnsmasq

```
edit [FONT="Courier New"]/etc/hosts[/FONT] (and- but probably not necessary - [FONT="Courier New"]/etc/dnsmasq.conf[/FONT])
```

$ sudo service dnsmasq restart

```
...and that should be it.

---

### Post by kimikrishna on 2010-07-02
If you mean "i want to add dns servers" 

(for example Opendns, google dns, norton dns) .

Right click on the networking icon on the panel >  edit connections > choose the one > under ipv4 tab > DNS SERVERS > add the two separated by a comma.

---

### Post by honey_bee on 2010-07-02
there is a file  "  /etc/hosts  " and  "/etc/resolv.conf  "
 
what is the purpose of these files For configuring a new DNS server which file should I edit ?

---

### Post by surfer on 2010-07-02
once again: do you want to configure your computer to send its dns requests to a special dns server or do you want to setup a custom dns server for your own network?

in [FONT="Courier New"]/etc/resolv.conf[/FONT] the dns servers your computer connects to are listed. normally you do not have to edit this file by hand; the network manager will do it for you.

there is usually not much in [FONT="Courier New"]/etc/hosts[/FONT]. a minimal configuration is:
```
127.0.0.1	localhost

```
but as i use dnsmasq, i have entries for my squeezeboxes in my local network:
```
192.168.0.11  	squeezebox-livingroom 	suqeezebox-livingroom.metaweb
192.168.0.12	squeezebox-office	squeezebox-office.metaweb
192.168.0.13	suqeezecontroller	suqeezecontroller.metaweb

```

---

### Post by Jakiejake on 2010-07-02
> **kimikrishna said:**
> If you mean "i want to add dns servers" 

(for example Opendns, google dns, norton dns) .

Right click on the networking icon on the panel >  edit connections > choose the one > under ipv4 tab > DNS SERVERS > add the two separated by a comma.

If I want to do DNS thats what I do!

---

### Post by Jakiejake on 2010-07-02
Try This it will tell you how to easily set up DNS on Ubuntu
[https://store.opendns.com/setup/device/ubuntu/print](https://store.opendns.com/setup/device/ubuntu/print)

---

### Post by honey_bee on 2010-07-02
well thanks "[surfer]("http://ubuntuforums.org/member.php?u=1345")" for your kind reply. Previously I was using windows server 2000 for my internal DNS server. I give the IP address of my DNS server in the client machines.

Now I switch to Linux operating system and now I want to use Linux as a DNS server for my small office. So in this case what can I do ?

---

### Post by bodhi.zazen on 2010-07-02
> **honey_bee said:**
> well thanks "[surfer]("http://ubuntuforums.org/member.php?u=1345")" for your kind reply. Previously I was using windows server 2000 for my internal DNS server. I give the IP address of my DNS server in the client machines.

Now I switch to Linux operating system and now I want to use Linux as a DNS server for my small office. So in this case what can I do ?

You have two options for setting up a DNS server.

1. bind

2. dnsmasq

For s SBHO dnsmask is trivial to set up.

For BIND see:

[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

dnsmask is easier to set up, it uses /etc/hosts on the server, and it will do DHCP as well.

See:

[http://wiki.debian.org/HowTo/dnsmasq](http://wiki.debian.org/HowTo/dnsmasq)

[http://www.thekelleys.org.uk/dnsmasq/docs/setup.html](http://www.thekelleys.org.uk/dnsmasq/docs/setup.html)

So it depends on which you prefer, there are probably additional options as well. Although it may seem complex, I had dnsmask set up in less then 5 minutes (it is trivial), bind will take more time.

Once you have dnsmasq or bind configured, you give the ip address to your clients exactly the same way you did before, nothing different client side.

---

### Post by surfer on 2010-07-02
i'd suggest you install dnsmasq [as described before]("http://ubuntuforums.org/showpost.php?p=9537136&postcount=4") and [edit your hosts file accorgingly]("http://ubuntuforums.org/showpost.php?p=9537750&postcount=7"). dont forget to restart the server afterwards.

---

