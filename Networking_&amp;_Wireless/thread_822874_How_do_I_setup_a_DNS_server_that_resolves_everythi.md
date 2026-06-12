---
title: "How do I setup a DNS server that resolves everything to one IP address?"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by blastus on 2008-06-08
How do I setup a DNS server that resolves all requests to a single non-routeable IP address? I want to setup a private network that isn't connected to the Internet and allow public wireless access to it. But I want it so that whoever connects to it and types in an address in their browser gets "redirected" to a computer on the network running a web server.

---

### Post by jetsam on 2008-06-08
You may have to mess with this a bit to get it working, but this can get you started.

Install dnsmasq with:
```
sudo apt-get install dnsmasq
```

You can start, stop and restart the server with:
[B]sudo /etc/init.d/dnsmasq stop
sudo /etc/init.d/dnsmasq start[/B]
or
**sudo /etc/init.d/dnsmasq restart**

Make a backup of the dnsmasq config file.  It's full of useful comments for tweaking its settings:
```
sudo cp /etc/dnsmasq.conf /etc/dnsmasq.conf.orig
```

Stick this in the top of your /etc/dnsmasq.conf file:
```
#--ADD YOUR WIRELESS INTERFACE NAME--
interface=eth0,lo
listen-address=127.0.0.1
#--SET RANGE OF DHCP ADDRESSES HERE--
dhcp-range=192.168.15.50,192.168.15.99,72h

# --ALL THE REDIRECTION HAPPENS IN THIS LINE--
# --CHANGE THE IP TO YOUR WEBSERVER ADDRESS--
address=/#/192.168.15.1

# Never forward plain names (without a dot or domain part)
domain-needed
# Never forward addresses in the non-routed address spaces.
bogus-priv

# If you don't want dnsmasq to read /etc/resolv.conf or any other
# file, getting its servers from this file instead (see below), then
# uncomment this.
no-resolv

# If you don't want dnsmasq to poll /etc/resolv.conf or other resolv
# files for changes and re-read them then uncomment this.
no-poll

# If you don't want dnsmasq to read /etc/hosts, uncomment the
# following line.
# --TELLS DNSMASQ NOT TO READ THE SERVER'S /ETC/HOSTS FILE.--
no-hosts
# or if you want it to read another file, as well as /etc/hosts, use
# this.
# --YOU CAN PUT EXTRA HOSTS IN THIS FILE INSTEAD.--
addn-hosts=/etc/dnsmasq_hosts

# Add other name servers here, with domain specs if they are for
# non-public domains.
# --COMMENTED BELOW SO YOU WON'T FORWARD OR LOOK UP ANYTHING--
#server=192.168.0.1
```

That should set it up as a dhcp server and dns server for the 192.168.15.x subnet.  It will answer all dns lookups with 192.168.15.1, although it will actually resolve hostnames of the dhcp clients as well.  My comments are in ALL CAPS.  The lower case ones are copied from the original.  

You'll need to give the server a static ip on the same subnet: 192.168.15.1 in the config above.  If you set the server's own dns address to 127.0.0.1 it will use itself as a dns server.  Useful for testing.  

More info from **man dnsmasq** and the dnsmasq homepage: [http://www.thekelleys.org.uk/dnsmasq/doc.html]("http://www.thekelleys.org.uk/dnsmasq/doc.html")

Hope it works...  

Should I ask why you want to do this?

---

