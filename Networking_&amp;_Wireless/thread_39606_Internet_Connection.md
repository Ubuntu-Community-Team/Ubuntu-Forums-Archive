---
title: "Internet Connection"
date: 2005-06-05
forum: Networking &amp; Wireless
---

### Post by chris2re on 2005-06-05
Hi!
i have adsl internet (pppoe), and a modem connected to the network card in my computer.
My problem is that the internet connection closes after about 20-30 minutes.
To fix this I have to open preferences for network, and change the dns servers.
it changes for 130.67.60.68 and 130.67.15.198 to 10.0.0.1, and then I hva to change it back.
Why? Is there a way to fix this?

Sorry if my english is bad...(Norwegian) :P

---

### Post by Mez on 2005-06-05
sounds liek your adsl modem si trying to get a newr IPS address when it shouldnt be, and then assigning a false IP to your computer

---

### Post by chris2re on 2005-06-06
Well...what do I do then?

---

### Post by grakhul on 2005-06-07
This was happening to me.  It turned out to be my ISP's slow dns servers and the fact that there was a script in Ubuntu rewriting the resolv.conf based on the IP information sent by the ISP. (this is normal)  I found out which one of my ISP's dns servers were the fastest and plugged this into the network config settings.

The I did what you see below.  Be sure to make a back up of the files you will alter just in case it doesn't work and you want to revert to your old config and continue troubleshooting with other methods

[b]
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


That should have you sorted sunshine![/b]

By the way the file you see above is the file that is rewritting your resolv.conf file which are your dns settings.

---

### Post by chris2re on 2005-06-09
Theese are the ip`s that I have in my dns-thingie..:
130.67.60.68 and 130.67.15.198.
Does that make a difference?

---

### Post by voidlogic on 2005-06-11
On a side note, Have any of you guys seen this modem issue? 

[http://www.ubuntuforums.org/showthread.php?p=202288#post202288](http://www.ubuntuforums.org/showthread.php?p=202288#post202288)

I'm really stuck.  :( and forced to use windows, untill I move back to where I go to college and have broadband again.

 ](*,)  ](*,)  ](*,)

---

### Post by niels2005 on 2005-07-02
hi, I followed your steps (see below) but my question is, if I use WLAN at home with DHCP and LAN at work (static IP), can I take 192.168.1.0 out of resolv.conf and second question, booting up seems to run 0dns-down, which apparently cancels all my dns settings done in the network-manager (gnome),
thanks for any help
niels

Ubuntu Hoary 5.04
Dell 510m

> **grakhul]This was happening to me.  It turned out to be my ISP's slow dns servers and the fact that there was a script in Ubuntu rewriting the resolv.conf based on the IP information sent by the ISP. (this is normal)  I found out which one of my ISP's dns servers were the fastest and plugged this into the network config settings.

The I did what you see below.  Be sure to make a back up of the files you will alter just in case it doesn't work and you want to revert to your old config and continue troubleshooting with other methods

[b]
 Go to COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (you will need to be superuser (root))

Then go to the DNS tab (probably 192.168.blah.blah as entry)

Find out your ISPs DNS nameservers, for example, Tiscali is 212.74.112.66 and 212.74.112.67.

Enter those bad boys in. Take 192.168.blah.blah OUT!



Then go to /etc/resolv.conf
Make sure that these two entries are there:

nameserver 212.74.112.66
nameserver 212.74.112.67

Your ISPs nameservers replacing mine  said:**
> ; then
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


That should have you sorted sunshine![/b]

By the way the file you see above is the file that is rewritting your resolv.conf file which are your dns settings.

---

