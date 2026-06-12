---
title: "DHCP with 2 nics and a AP"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by jphillip on 2007-04-01
Hello,

I have a Ubuntu computer with two nics running DHCP and is working.

/etc/dhcpd.conf
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;
option domain-name-servers 192.168.1.1;
option domain-name "Ourhouse";
                
subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.100;
range 192.168.1.150 192.168.1.200;
}

I hard code the Internet nic 192.168.1.5 and have a linksys router connected to it / the internet (192.168.1.1) 
No DHCP. And can surf the web using the ISP DNS and my DHCP server hands out ip's to any computer that is connected to the Linksys router

I hard coded my second nic at 10.10.10.1 (which isn't working)
I want to connect a wireless router (AP) to my second nic card on the different 10.10.10.1 network and have dhcp hand out ip addresses to wireless clients with a 10.10.10.X. But I am not sure how to do this.

I think I need to do something with DHCP conf file and create a 2nd subnet?
I also think I need to, on the wireless Access Point give it a 10.10.10.2 address? 

But I have reached the limited of my home network knowledge and google power searching for the right question / tutorial.

My whole goal is to fiqured this out and then create a NocatAuth system for a wireless hotspot.

Thanks in advance.

---

### Post by jorno on 2007-04-02
Hello.

It's been some time since I did such a setup myself, but I strongly believe you need to run two instances of DHCPd, with different configs. The first dhcpd you need to bind to the first network interface, with the current dhcpd-config. The second dhcpd you need to bind to the second network interface, with a new dhcpd-config. (Look at the manpages of your dhcpd to find the right switches for this).

You'd probably also want to make yourself a new copy of the init-script for the dhcpd, so you don't have to manually start the second dhcpd after each reboot).


Please ask if I need to explain some of this further - and everyone else; Feel free to correct me if I've said anything wrong/misleading.


:-)

---

### Post by jphillip on 2007-04-02
I think I went the wrong direction with my dhcp. I think I need to set it up to hand out 10.10.10.x (which I don;t understand) at the wireless side of things and create /bind the two nics so that 10.10.10.x nic can forward out to the 192.168.1.5 nic and can hit the internet where my gateway of 192.168.1.1 is at. (if that make any sense)


Just some notes when I am on the computer with dhcp and the two nics I can hit the 10.10.10.2  Belkin web config router  I can also hit the [http://192.168.1.1](http://192.168.1.1) Linksys web config page. So I am making progress. 

I read some where about IPTABLES -t FORWARD something ->eth0  or eth1 MASQUARDE but it didn't make any sense at the time.  I am wonder if this might be the missing link..

Anyway any more info you might can come up with would be great. 
I plan on writing a tutorial when I am all done and I understand this better. I think there are a lot of people out there who might like to try this for home network. At least I do.

---

### Post by jorno on 2007-04-03
You're right about the "IPTABLES -t FORWARD something ->eth0 or eth1 MASQUARDE"-thing.

Would be GREAT if you could write some sort of wiki-guide/howto about this topic, for other Ubuntu-users to enjoy, if you get this going. I've read about many who's wondering about this exact same thing in the forums.

You could read some more about Router-setups here: [http://www.gentoo.org/doc/en/home-router-howto.xml](http://www.gentoo.org/doc/en/home-router-howto.xml)
This is Gentoo-documentation, but mostly all of it should apply to any Linux-distro, with the exception of package installation. As your in Ubuntu, you could also skip the whole "kernel re-configuration" step.

It could also be worth taking a look at the following documentation (it's from Gentoo, as I've found Gentoo to have an incredibel amount of documentation out there):
[http://gentoo-wiki.com/HOWTO_Iptables_for_newbies](http://gentoo-wiki.com/HOWTO_Iptables_for_newbies)
[http://gentoo-wiki.com/HOWTO_Chillispot_with_FreeRadius_and_MySQL](http://gentoo-wiki.com/HOWTO_Chillispot_with_FreeRadius_and_MySQL)
[http://forums.gentoo.org/viewtopic-t-450339-highlight-nics+running+dhcp.html](http://forums.gentoo.org/viewtopic-t-450339-highlight-nics+running+dhcp.html)
[http://forums.gentoo.org/viewtopic-t-178160-highlight-nics+running+dhcp.html](http://forums.gentoo.org/viewtopic-t-178160-highlight-nics+running+dhcp.html)


I'm sorry I can't give you my own iptables-setup right now, as I'm on work, and my work-network doesn't allow outgoing SSH (yet). ;-)

---

### Post by jphillip on 2007-04-03
Thanks for the list I will keep reading.

JP

---

