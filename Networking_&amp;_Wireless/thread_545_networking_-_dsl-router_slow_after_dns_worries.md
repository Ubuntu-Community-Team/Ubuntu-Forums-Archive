---
title: "networking - dsl-router slow after dns worries"
date: 2004-10-14
forum: Networking &amp; Wireless
---

### Post by arctic on 2004-10-14
hi :)
my problem is the following: i have a d-link router. works perfect with the windows boxes but didn't resolve the dns in linux. i changed the dns-server to another value and now i do get access to my ubuntu box but still not on the mandrake boxes (the /etc/resolv.conf is still causing trouble, being constantly rewritten with bad values). 

the problem with ubuntu is that the web-access is now very slow. pages need up to ten seconds to respond. i never had this problem before and as said: works perfect on my windows-boxes. any idea how i can speed the website-loading?

hardware: realtek 10/100 ethernet cards, d-link dsl-546t router, 4-comp lan (one mandrake10.1/ubuntu4.10, one mandrake10, two win me).

thank you in advance for any ideas.

---

### Post by FLeiXiuS on 2004-10-14
Try giving turning off ipv6 off in your

/etc/modutils/alias 

un comment #alias ipv6

that might do it for you..

---

### Post by arctic on 2004-10-14
funny...  but these lines aren't in my files. :D
i got around this problem on another partition by simply reinstalling the system. weird thing that changing the router and lan causes this much trouble with the dns resolving.
btw: the dns problem could not be fixed on any mandrake box. the resolv.conf was repeatedly overwritten by the system...   :shock:

---

### Post by python on 2005-01-17
[QUOTE=arctic]funny...  but these lines aren't in my files. :D
i got around this problem on another partition by simply reinstalling the system. weird thing that changing the router and lan causes this much trouble with the dns resolving.
btw: the dns problem could not be fixed on any mandrake box. the resolv.conf was repeatedly overwritten by the system...   :shock:[/QUOTE]
 Go to COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (you will need to be superuser (root))

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

---

### Post by wklenk on 2005-10-05
[QUOTE=arctic]hi :)
my problem is the following: i have a d-link router. works perfect with the windows boxes but didn't resolve the dns in linux. i changed the dns-server to another value and now i do get access to my ubuntu box but still not on the mandrake boxes (the /etc/resolv.conf is still causing trouble, being constantly rewritten with bad values). 
the problem with ubuntu is that the web-access is now very slow. pages need up to ten seconds to respond. i never had this problem before and as said: works perfect on my windows-boxes. any idea how i can speed the website-loading?
hardware: realtek 10/100 ethernet cards, d-link dsl-546t router, 4-comp lan (one mandrake10.1/ubuntu4.10, one mandrake10, two win me).
thank you in advance for any ideas.[/QUOTE]
Same problem with me: Looking up the names of webservers (name resolution) is very slow, Firefox even sometimes reports it cannot lookup the name. I'm using router Netgear WGR614, Internet Provider is Kabel-BW in Germany.
Pragmatical solution:
- When configuring the network interfaces, do NOT use DHCP, instead use a static IP address (e.g. 192.168.0.10).  Gateway IP address should be set to the IP address of the router (e.g. 192.168.0.1).
- Find out which DNS Server your router is using. Use the router's web interface to do this.
- In the "DNS" Tab of the "Network Settings", remove any existing DNS servers and add the IP addresses for the DNS servers you found in the web interface of the router.
If all operations went well successfully, the file /etc/resolv.conf should also reflect the changes of the DNS servers.

---

### Post by Dafydd on 2006-04-07
[QUOTE=python]... Then go to /etc/resolv.con  ... Finally, go to /etc/dhcp3/dhclient-script and comment out this: ... That should have you sorted sunshine!  ... [/QUOTE]

Thanks. This works wonderfully on my machine. Now dillo, gaim, ipodder etc all work whereas before i could only use certain internet programs...

However, what do i do when i change wireless networks? I usually use about three networks. I don't know the dns name servers of the other networks. I even asked once, and the technician said: 'You don't need to know'.

i'll try again today, but I think my internet won't work on another network without more fiddling.

Dafydd

---

