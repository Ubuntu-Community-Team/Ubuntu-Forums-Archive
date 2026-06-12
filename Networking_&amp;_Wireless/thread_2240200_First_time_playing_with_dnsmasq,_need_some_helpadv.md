---
title: "First time playing with dnsmasq, need some help/advice."
date: 2014-08-18
forum: Networking &amp; Wireless
---

### Post by Ackis on 2014-08-18
Hello everyone, I've set up dnsmasq on my headless server to act as a DHCP server for my network and an internal DNS which forwards as needed.  However I'm having some problems and I think it stems from my ignorance overall.

The intent of my setup is to manage IP's on my local network from a central source, and to provide access to various shared services via name resolution like service.home.lan.  Eventually I would like to get a wireless access point setup on wlan1.

So some specific things that I've noticed with my current configuration that don't work:

[LIST=1]
[*]If I go to foo.home.lan and it doesn't exist I'm always redirected to intranet.home.lan.  Is this a DNS issue or related to my apache configuration?
[*]If for some reason my server is down, I'd like the clients to use a secondary DNS server (e.g. 8.8.8.8).  Is there a way I can configure that in dnsmasq?
[*]I have no idea what to do with IPv6.  I've read through various documents on it, but one thing that's remained unclear is what private range of IP's am I allowed to use?
[/LIST]


This is my current dnsmasq configuration:

```
# Configuration file for dnsmasq.#
# Format is one option per line, legal options are the same
# as the long options legal on the command line. See
# "/usr/sbin/dnsmasq --help" or "man 8 dnsmasq" for details.


domain-needed
bogus-priv


server=/home.lan/192.168.0.199
server=//192.168.0.199
server=8.8.8.8
server=8.8.4.4


local=/home.lan/


interface=eth0
#interface=wlan1
listen-address=127.0.0.1
listen-address=192.168.0.199


no-hosts
no-resolv
addn-hosts=/etc/dnsmasq.hosts # http://winhelp2002.mvps.org/hosts.htm 


domain=home.lan
dhcp-range=192.168.0.10,192.168.0.254,12h


#dhcp-option=3,1.2.3.4
dhcp-option=option:router,192.168.0.1
dhcp-option=option:dns-server,0.0.0.0
#dhcp-option=option:ntp-server,3.ca.pool.ntp.org # This doesn't work.. why?


# Windows/Samba suggestions from default configuration
dhcp-option=option:ip-forward-enable,0
dhcp-option=option:netbios-ns,0.0.0.0
dhcp-option=option:netbios-dd,0.0.0.0
dhcp-option=option:netbios-nodetype,8


#dhcp-option=19,0           # option ip-forwarding off
#dhcp-option=44,0.0.0.0     # set netbios-over-TCP/IP nameserver(s) aka WINS server(s)
#dhcp-option=45,0.0.0.0     # netbios datagram distribution server
#dhcp-option=46,8           # netbios node type


dhcp-leasefile=/var/lib/misc/dnsmasq.leases
bogus-nxdomain=64.94.110.11
dhcp-authoritative


mx-host=home.lan,mail.home.lan,30
txt-record=home.lan,"v=spf1 mx -all"


# For debugging purposes, log each DNS query as it passes through
# dnsmasq.
#log-queries


# Log lots of extra information about DHCP transactions.
#log-dhcp


# Include another lot of configuration options.
#conf-file=/etc/dnsmasq.more.conf
conf-dir=/etc/dnsmasq.d




# Blocked Addresses
# Todo:
#	Script to import from some safe hosts file


address=/addthis.com/127.0.0.1
address=/ligatus.com/127.0.0.1
address=/conduit.com/127.0.0.1
address=/snapdo.com/127.0.0.1




# DHCP Address Reservations
# Todo:
#	Deal with chantelle/chantelle2


# PC Address Range: 10 - 40
dhcp-host=E0:CB:4E:97:70:CE,john,192.168.0.10
dhcp-host=00:22:15:9C:8E:46,chantelle,192.168.0.11
dhcp-host=00:22:15:9C:A2:34,chantelle2,192.168.0.12
# Laptop wired


# Wireless Range: 41-70
dhcp-host=80:3f:5d:22:38:e9,ubuntuwifi,192.168.0.41
dhcp-host=80:1f:02:9b:de:66,johnwifi,192.168.0.42
dhcp-host=00:9A:90:00:2F:20,chantellewifi,192.168.0.43
# Laptop wireless




# Game Consoles
dhcp-host=28:18:78:89:EC:11,xboxone,192.168.0.75
# X360
# PS3
# Wii U
# Vita
# 3DS1
# 3DS2


# Mobile Devices
# Johns Phone - Nexus
# Chantelles Phone - Galaxy S2
# Tablet - Galaxy Tab 2 10.1
# Tablet - iPad


# Network Devices


# Routers
dhcp-host=84:1B:5E:3A:DB:77,router,192.168.0.1
dhcp-host=00:21:29:9B:74:C6,wrt-160n,192.168.0.200
dhcp-host=00:16:B6:36:0F:25,wrt-54g,192.168.0.201


# Printers
dhcp-host=DC:85:DE:6D:0D:BF,mf4890,192.168.0.101
dhcp-host=80:3F:5D:08:E0:2A,usbprint,192.168.0.104
dhcp-host=00:00:85:E8:72:37,mp620,192.168.0.106


# Media Devices


dhcp-host=00:18:DD:03:B4:82,hdhr3,192.168.0.103
dhcp-host=9C:AD:EF:60:06:C5,obi200,192.168.0.105
dhcp-host=D0:E7:82:B9:B5:CF,chromecast,192.168.0.110
dhcp-host=00:1B:C7:FF:D2:79,monocamwifi,192.168.0.150
dhcp-host=00:1B:C7:02:1B:4F,monocam,192.168.0.151


# Servers
dhcp-host=80:3f:5d:22:38:cf,ubuntuap,192.168.0.198
dhcp-host=E0:3F:49:7F:AC:80,ubuntu,192.168.0.199


# All files in this directory will be read by dnsmasq as 
# configuration files, except if their names end in 
# ".dpkg-dist",".dpkg-old" or ".dpkg-new"
#
# This can be changed by editing /etc/default/dnsmasq




# LAN Name Resolution


# Web servers
address=/internet.home.lan/192.168.0.199
address=/intranet.home.lan/192.168.0.199
address=/home.lan/192.168.0.199
address=/www.home.lan/192.168.0.199


# System Admin Servers
address=/webmin.home.lan/192.168.0.199


# LAN Servers
address=/mail.home.lan/192.168.0.199


# Media Services
address=/bubble.home.lan/192.168.0.199
address=/calibre.home.lan/192.168.0.199
address=/plex.home.lan/192.168.0.199
address=/plexwatch.home.lan/192.168.0.199


address=/znc.home.lan/192.168.0.199


# Routers
address=/wrt-160n.home.lan/192.168.0.200
address=/router.home.lan/192.168.0.1



```

This is my apache config, figured I'd add it just for completeness:

```



#NameVirtualHost *:80


<VirtualHost intranet.home.lan:80>
        ServerAdmin webmaster@home.lan
        ServerName intranet.home.lan
        DocumentRoot /var/www/intranet
        Redirect permanent / https://intranet.home.lan
</VirtualHost>


<VirtualHost internet.home.lan:80>
        ServerName internet.home.lan
        ServerAlias www.home.lan
        DocumentRoot /var/www/internet
        #Redirect permanent / https://internet.home.lan/
</VirtualHost>


<IfModule mod_ssl.c>
        <VirtualHost intranet.home.lan:443>
                ServerAdmin webmaster@home.lan
                ServerName intranet.home.lan:443


                DocumentRoot /var/www/intranet


                #Include conf-available/serve-cgi-bin.conf


                SSLEngine on


                SSLCertificateFile      /opt/sslkey/apache2.crt
                SSLCertificateKeyFile   /opt/sslkey/apache2.key


                <FilesMatch "\.(cgi|shtml|phtml|php)$">
                        SSLOptions +StdEnvVars
                </FilesMatch>
                <Directory /usr/lib/cgi-bin>
                        SSLOptions +StdEnvVars
                </Directory>


                BrowserMatch "MSIE [2-6]" \
                        nokeepalive ssl-unclean-shutdown \
                        downgrade-1.0 force-response-1.0
                BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown
        </VirtualHost>
        <VirtualHost znc.home.lan:443>
                ServerAdmin webmaster@home.lan
                ServerName znc.home.lan
                #RedirectPermanent / https://192.168.0.199:63000
                #ProxyPass https://znc.home.lan http://192.168.0.199:63000/
                #ProxyPassReverse https://znc.home.lan http://192.168.0.199:63000/
        </VirtualHost>


</IfModule>
<VirtualHost znc.home.lan:80>
        ServerAdmin webmaster@home.lan
        ServerName znc.home.lan
        #RedirectPermanent / https://192.168.0.199:63000
        RedirectPermanent / https://znc.home.lan
        #ProxyPass https://znc.home.lan http://192.168.0.199:63000/
        #ProxyPassReverse https://znc.home.lan http://192.168.0.199:63000/
</VirtualHost>

```

---

