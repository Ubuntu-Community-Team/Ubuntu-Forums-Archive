---
title: "Your DNS issues / problems here"
date: 2005-05-12
forum: Networking &amp; Wireless
---

### Post by grakhul on 2005-05-12
My internet connection works fine after resolving the domain name.  Only thing is.  It takes about 10 to 45 seconds to resolve a domain name.  This is what I have tried yet the issue of domain name resolution still persist.

1.  I have commented out a script that rewrites the DNS setttings in resolv.conf
2.  I have entered the DNS servers of my ISP and from various DNS servers on the net.
3.  When I use IP addresses to bring up the website everything works fine. (connection works great, no lag or delay with the connection)

My Ubuntu box still takes 10 to 45 seconds to resolve domain names.

Any help would be appreciated.

*I have a **Westel DSL modem/router** that is configured in bridge mode(this mode bascally keeps the westel ON, without it actually doing anything.  I need to do this, as the Westell has a RJ 11 phone jack on one end, which is where the DSL is being served from) and it has an RJ45 port on the other. 

*I have a **Motorola Router** connected to the RJ45 port on the westell,  which establishes the connection with the ISP using it's own PPPoE system.  It is also the DHCP client and seems to be the DNS server.  Even though I added my own DNS servers to the laptop.  The router has retrieved the DNS servers it will use, from the ISP.  Once while troubleshotting the connection and doing a "DIG" I noticed that the DNS replies were coming from the router on port 53.

My laptop is connected wirelessly to the motorola.

To sum up:

Westel DSL modem/router<-------->Motorola Router<--------->Laptop (wireless)

---

### Post by grakhul on 2005-05-15
I am beginning to think that this has NOTHING to do with UBUNTU.  I rather think that my ISP's DNS servers are extremely slow.  I haven't had the chance to connect to my router and change DNS servers yet, but when I get the chance I will let you know.

---

### Post by alastair on 2005-05-15
If you are "benchmarking" resolution via a web browser, a delay might be caused by doing an IPv6 lookup first.

Disable this in Firefox via :

about:config

search for : network.dns.disableIPv6

and make it "true" (double-click).

See if that helps.

---

### Post by john.mccarty on 2005-05-17
Grakhul,

In your initial post, you said that you had "commented out a script that rewrites the DNS settings in resolv.conf"... Could you give me some details about that, as I think that might solve my DNS problems.

My cable modem connects to my Blitzz BWA711 wireless router, which functions as my DHCP server for my machines.  I have a WinXP box and an Ubuntu box.

After installing Ubuntu 5.x, the network works, however, I have some DNS problems.
Most sites will not be found.  nslookup [www.google.com](www.google.com) shows the routers IP as the nameserver and the IP returned for Google is 0.0.0.10.

After I open Ubuntu's Networking GUI app and change the DNS server from the routers IP to 4.2.2.2....  everything is fine.  Sites are found, nslookup will return a correct result, etc.
The problem is that this change never "sticks".  After a while it seems to revert back to using the routers IP for DNS.

I've edited /etc/resolv.conf and manually added the nameservers that I want to use there... but they are not being used (or so it seems). 
Perhaps the script you noted is rewritting my DNS nameservers against my will?

thanks,
john

---

### Post by WildTangent on 2005-05-17
im having trouble connecting my friend to the internet. i finally convinced him tp try ubuntu, and now were having trouble getting onto the internet. his network card works, because we were able to connect to his router and check the settings. hes connected to Bell Sympatico DSL through a Dlink DI-604 Router. i remember when i initially setup windows we had similar problems, and had to edit his DNS settings IIRC. i believe the protocol his DSL uses is PPPoE. i dont know how to fix this, because i have a static IP with my cable.

-Wild

---

### Post by grakhul on 2005-06-06
>  Go to COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (you will need to be superuser (root))

Then go to the DNS tab (probably 192.168.blah.blah as entry)

Find out your ISPs DNS nameservers, for example, Tiscali is 212.74.112.66 and 212.74.112.67.

Enter those bad boys in. Take 192.168.blah.blah OUT!



Then go to /etc/resolv.conf
Make sure that these two entries are there:

nameserver 212.74.112.66
nameserver 212.74.112.67

Your ISPs nameservers replacing mine ;-P
Nameserver 192.168.blah.blah should either be commented out (preceded with a #) or not be there at all.



Finally, go to /etc/dhcp3/dhclient-script and comment out this:

# Modified for Debian. Matt Zimmerman and Eloy Paris, December 2003

# The alias handling in here probably still sucks. -mdz

#make_resolv_conf() {
# if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
# local new_resolv_conf=/etc/resolv.conf.dhclient-new
# rm -f $new_resolv_conf
#
# if [ -n "$new_domain_name" ]; then
# echo search $new_domain_name >> $new_resolv_conf
# else # keep 'old' search/domain scope
# egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# if [ -n "$new_domain_name_servers" ]; then
# for nameserver in $new_domain_name_servers; do
# echo nameserver $nameserver >>$new_resolv_conf
# done
# else # keep 'old' nameservers
# egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# chown --reference=/etc/resolv.conf $new_resolv_conf
# chmod --reference=/etc/resolv.conf $new_resolv_conf
# mv $new_resolv_conf /etc/resolv.conf
# fi
#}


That should have you sorted sunshine! 

Sorry it took so long, been very busy.

---

### Post by grakhul on 2005-06-06
> im having trouble connecting my friend to the internet. i finally convinced him tp try ubuntu, and now were having trouble getting onto the internet. his network card works, because we were able to connect to his router and check the settings. hes connected to Bell Sympatico DSL through a Dlink DI-604 Router. i remember when i initially setup windows we had similar problems, and had to edit his DNS settings IIRC. i believe the protocol his DSL uses is PPPoE. i dont know how to fix this, because i have a static IP with my cable. 
Still having this problem **tangent**?

---

