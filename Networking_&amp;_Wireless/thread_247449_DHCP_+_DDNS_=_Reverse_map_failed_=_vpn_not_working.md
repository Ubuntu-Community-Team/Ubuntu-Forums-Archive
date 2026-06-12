---
title: "DHCP + DDNS = Reverse map failed = vpn not working"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by twiggy on 2006-08-30
Hi guys,

So i have been fighting with getting a dhcp server up and getting it to dynamically update my dns (bind) records.  Finally got it to work, well almost completely. 

Couple of things:

1) i kept getting permission failers when trying to create the journal files and the only way i seemed to be able to fix it was to give 775 permissions to the bind folder (chmod -R 775 /etc/bind).  I have a bad feeling this is very dangerous and leave me open to lots of nasty things i dont know about.  I am a bit of a noob when it comes to linux.  I am learning as i go and find the whole permission thing a little confusing at times.  any thoughts, suggestions.  the bind permissions are as follows:
[PHP]
-rwxrwxr-x 1 bind bind  237 2006-08-30 19:21 db.0
-rwxrwxr-x 1 bind bind  368 2006-08-30 19:21 db.10.168.162
-rwxrwxr-x 1 bind bind  271 2006-08-30 19:21 db.127
-rwxrwxr-x 1 bind bind  237 2006-08-30 19:21 db.255
-rwxrwxr-x 1 bind bind  353 2006-08-30 19:21 db.empty
-rwxrwxr-x 1 bind bind  256 2006-08-30 19:21 db.local
-rwxrwxr-x 1 bind bind  279 2006-08-30 19:21 db.plonk
-rwxrwxr-x 1 bind bind 3360 2006-08-30 21:29 db.plonk.jnl
-rwxrwxr-x 1 bind bind 1507 2006-08-30 19:21 db.root
-rwxrwxr-x 1 bind bind  388 2006-08-30 19:21 logging.conf
-rwxrwxr-x 1 bind bind 2383 2006-08-30 20:13 named.conf
-rwxrwxr-x 1 bind bind  412 2006-08-30 20:11 named.conf.local
-rwxrwxr-x 1 bind bind  685 2006-08-30 19:21 named.conf.options
-rwxrwxr-x 1 bind bind   77 2006-08-30 19:21 rndc.key
-rwxrwxr-x 1 bind bind 1317 2006-08-30 19:21 zones.rfc1918[/PHP]

2) well the above got ride of the permissions error and it actually ran but in syslog i got the following error:

[PHP]
Added new forward map from dale.plonk.com. to 162.168.10.197
Aug 30 21:29:24 localhost dhcpd: unable to add reverse map from 197.10.168.162.in-addr.arp. to dale.plonk.com.: timed out
[/PHP]

I can do all my internal pining now but vpn'ing in or out seems to have gone up the swanny.  can anyone help me please?

Thx guys

Twiggy

---

### Post by twiggy on 2006-08-30
Just thought you might want to see the dhcpd.conf file:

[PHP]
authoritative;

ddns-updates on;
ddns-domainname "plonk.com.";
ddns-rev-domainname "in-addr.arp.";
ddns-update-style interim;
allow client-updates;

max-lease-time 172800;
default-lease-time 43200;

subnet 162.168.10.0 netmask 255.255.255.0 {
option subnet-mask 255.255.255.0;
option broadcast-address 162.168.10.255;

option domain-name "plonk.com";
option domain-name-servers 162.168.10.1;
option routers 162.168.10.1;

range 162.168.10.101 162.168.10.200;
}

key "rndc-key" {
        algorithm hmac-md5;
        secret "BLEH";
};

zone ponywars.com. {
        primary 127.0.0.1;
        key rndc-key;
}

zone 10.168.162.in-addr.arpa. {
        primary 127.0.0.1;
        key rndc-key;
}
[/PHP]

if you need to see anything else just shout...

thx again :)

---

### Post by twiggy on 2006-08-31
Hi all,

fixed my problem.  it was a typo really:

[PHP]ddns-rev-domainname "in-addr.arp.";[/PHP]

should have had an "a" at the end of it so it knew what zone to add it to.

but anyway. it all seems to be working.  vpns in and out are working and pinging internal comps from the vpn resolves fine as well.

my only thought and worry is this permissions thing i did.  any advice on this would be MOST wonderful

thx

Twiggy

---

