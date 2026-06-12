---
title: "[SOLVED] Hostname Problems on LAN"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by GenuineXP on 2008-03-12
So I'm having a bunch of problems resolving hostnames on my LAN. I have two Ubuntu machines and one Windows XP machine on the LAN. I've installed winbind on both Ubuntu machines and added the wins feature to hosts in the nsswitch.conf files.

The Windows machine can ping both Ubuntu boxes using their respective hostnames, but the Ubuntu boxes are dumb as rocks when it comes to using the hostnames of anything connected to the LAN. I'm using one Ubuntu machine as a server of sorts, and it's annoying having to ssh and ftp into the machine by IP address, especially when I'm accessing it via the LAN and not the Internet where I would need DNS services.

Why does the Windows machine have no problem with the hostnames but the Ubuntu machines do? Any ideas? I don't want to setup DNS right now as I attempted to follow a few guides and it seems very complex and hard to maintain; I won't be staying on this particular LAN for long.

Any help is appreciated. Thanks!

---

### Post by dmizer on 2008-03-13
are you using opendns for your domain name servers?

can you post the contents of your /etc/nsswitch.conf

on your ubuntu machines, have you installed and configured a samba server?

---

### Post by Eiríkr on 2008-03-13
Also, and possibly more simply for small and relatively static home networks, have you included the hostnames and respective IP addresses in the /etc/hosts files of each Ubuntu machine?  (This same old-fashioned approach can work for Windows, too -- the hosts file on XP is located in the [font=courier]C:\WINDOWS\system32\drivers\etc[/font] folder.)

---

### Post by GenuineXP on 2008-03-13
I'm not using any DNS server (that I know of); I tried to accomplish this via WINS and the winbind package to no avail for the Ubuntu machines. Here's one of the nsswitch.conf files, though I'm quite sure they are exactly the same on both machines.

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

You can see where I added "wins".

I've read about adding the hosts manually to the hosts file, but I don't like this approach since it's so static; the IP of at least one of the Ubuntu machines is dynamically assigned by DHCP. Only the server box uses a static address. Once I take these machines off this network and onto mine, the IPs may change, and I may reassign the server's as well, so I'd have to edit the hosts file again. There's another Ubuntu machine and a Windows machine on my network that both use dynamic addresses as well, so that would become quite annoying.

Thanks for the help.

---

### Post by Eiríkr on 2008-03-13
Don't know if it's relevant, but [thread=182824]this old thread[/thread] seems to suggest that you might also need to install Samba as well for this approach to work.  I've never tried using windbind myself and don't have the time right now to experiment, but a quick [font=courier]sudo apt-get install samba[/font] might be a relatively easy way to get your name resolution up and running.  

Cheers,

Eiríkr

---

### Post by GenuineXP on 2008-03-13
Samba is installed and running on both Ubuntu machines.

When I try to ping by hostname, it pings a very strange address and I have no idea where it comes from.

Thanks for the help, btw.

---

### Post by dmizer on 2008-03-13
in your /etc/nsswitch.conf file, change the hosts line to this:
```
hosts:          files [COLOR="Red"]wins[/COLOR] mdns4_minimal [NOTFOUND=return] dns mdns4
```
restart networking:
```
sudo /etc/init.d/networking restart
```
then try pinging your ubuntu machines from eachother.

edit:
btw ... opendns servers are open to any network.  so if you use opendns static dns servers, it doesn't matter what network your computer is connected to, you still get dns resolution.

---

### Post by GenuineXP on 2008-03-13
That seems to work! Thanks!

I'm surprised that the order matters here. I'll look into using DNS when I get back on my network. From what I've read, it's a pain to deal with.

Thanks again!

---

### Post by Eiríkr on 2008-03-13
Unless OpenDNS also offers some kind of dynamic DNS service package, the OpenDNS servers are only useful for internet-wide name resolution, and *will not* help you for LAN name resolution.  However, setting up your own LAN DNS needn't be terribly complicated.  One decent online HOWTO I've used successfully is [this one](http://www.langfeldt.net/DNS-HOWTO/BIND-9/DNS-HOWTO.html).  Have a look at [Chapter 5](http://www.langfeldt.net/DNS-HOWTO/BIND-9/DNS-HOWTO-5.html) in particular.  

Cheers,

Eiríkr

---

### Post by GenuineXP on 2008-03-13
Thanks for the link. I'll check it out. :-)

I'd like to note that while WINS works from a terminal (that is, I can use ssh and ftp to access the machine by hostname from a terminal), it does not work elsewhere. Using the hostname in Firefox or Nautilus fails, while using the hostname in Firefox on the Windows machine works like a charm. I'm not sure why.

---

### Post by GenuineXP on 2008-03-13
I'm having a lot of trouble with the posted DNS tutorial. It doesn't seem to work for me, and many of my files and directories are different from the tutorial's. (I'm running Ubuntu Gutsy and the bind9 package.)

Anyone know any other guides I could try? Thanks.

---

### Post by Eiríkr on 2008-03-13
I've got Gutsy, and one caveat I recall running into with the HOWTO is that for some reason relative paths in the [font=courier]named.conf[font] file don't seem to work -- only absolute paths don't generate errors.  

Here's a sample setup (based on my own LAN).

**_named.conf_**

Basically just the default.
```
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};
```

**_named.conf.options_**
```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        // query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.  ## NB -- you could also use the OpenDNS IPs here.

        forwarders {
                68.94.156.1;
                68.94.157.1;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };

        allow-query { localnets; };

        allow-recursion { localnets; };
};
```

**_named.conf.local_**
```
zone "homelan.org" {
        type master;
        notify no;
        file "/etc/bind/homelan.org.hosts";
        allow-transfer { localnets; };
};

zone "168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/192.168.hosts";
        allow-transfer { localnets; };
};
```

**_homelan.org.hosts_**

Main hosts file for hostname lookups.
```
;
; Zone file for home network homelan.org
;
$ttl 38400
@       IN      SOA     Ubuntu.homelan.org. grandpoobah.homelan.org. (
                        1203324117      ; serial #
                        10800           ; refresh in seconds
                        3600            ; retry in seconds
                        604800          ; expire in seconds
                        38400 )         ; min in seconds
;
                NS      Ubuntu        ; name server
                ; MX    10 mail.homelan.org ; Mail server, as yet unimplemented (2008-02-18)
;

localhost       A       127.0.0.1

Ubuntu        A       192.168.10.10
                TXT     "Better a long wind... than a broken one."
;www            CNAME   Ubuntu

Modem           A       192.168.0.1
                TXT     "The DSL modem."

Router          A       192.168.10.1
                TXT     "The router."

ibook        A       192.168.10.13
                TXT     "The Mac iBook."

printer           A       192.168.10.20
                TXT     "The printer."
```


**_192.168.hosts_**

For reverse lookups of IP addresses.
```
$TTL 3D
@       IN      SOA     Ubuntu.homelan.org. admin.homelan.org. (
                        1203324121      ; serial #
                        10800           ; refresh in seconds
                        3600            ; retry in seconds
                        604800          ; expire in seconds
                        38400 )         ; min in seconds
;
                NS      Ubuntu.homelan.org.       ; name server

1.0             PTR     Modem.homelan.org.
1.10            PTR     Router.homelan.org.
10.10           PTR     Ubuntu.homelan.org.
13.10           PTR     ibook.homelan.org.
20.10           PTR     printer.homelan.org.
```

Note that all files are in the /etc/bind/ directory.

I've read somewhere that there's supposed to be a way to wed DHCP and DNS functionality so DHCP clients will automatically have their hostnames added to the DNS hosts files, but I haven't had the time yet to really look into that.  Plus, I think in such a setup the DHCP and DNS servers need to be on the same machine, so I'm saving up a bit to get an OpenWRT-compatible router to try it out there.  Anyway, hope the above helps.  

Cheers,

Eiríkr

---

### Post by GenuineXP on 2008-03-13
Hm, I think I may be confused as to how this actually works. I'm getting the same results as before, and using dig on either machine (the server or a dynamically addressed machine) yields nothing. On the other hand, both are using the DNS provided by my router (and ultimately my ISP). Would I have to disable this or something? That doesn't seem like a good idea, but...

Anyway, ultimately what I want is to be able to use my laptop to access the server using a domain name rather than an IP. At the moment, I'm trying to use fefnir.arcardia, but to no avail. dig still gets no results and attempts to ssh to that name result in "Name or service not known" errors.

This DNS stuff is tough.

---

### Post by Eiríkr on 2008-03-13
The biggest bugaboo I ran into was how easy it is for an extremely hard-to-see typo to completely throw things off, given how a period in the wrong place changes the whole thing.  It took me a while to work things through, each time incrementally changing something and restarting to see if it worked.  

What dig results are you getting?  And is there anything of note from named in the syslog?  If any of your hosts or conf files have errors in them, named should report on them there on bind9 startup or reload.  

And by "both are using the DNS provided by my router", what do you mean by this?  Maybe you mean your /etc/resolv.conf files?  Make sure these look something like this:
```
search fefnir.arcadia
nameserver 127.0.0.1
```
Replace the IP address here with the IP address of your LAN's DNS server.  (Or leave as-is for the resolv.conf file on the DNS server itself.)  I'm not sure, but "fefnir.arcadia" might need a ".org" or ".com" or something on the end.  And is "fefnir" the hostname, or part of you domain name?  Whatever the case, replace the "fefnir.arcadia" here with the proper name of your domain.  In my previous example, this would be **_homelan.org_**.  

Cheers,

Eiríkr

---

### Post by GenuineXP on 2008-03-13
I've seemed to have gotten it working. I only changed a few small things, but the solution seems very similar to the setup you posted. Thanks again for that. :-)

Anyway, I had to change my resolve.conf files to point to my server box rather than my router and that did the trick. I added my router as the forwarder on my server so that clients can still see Internet domains (very important!).

fefnir is both the hostname and the domain name. Since I have it working here, I'm not too sure that's a problem. What I'd like to know now is how I'll keep this working since the network manager wipes and rewrites resolve.conf often. I'm thinking my router may have a setting to specify a different DNS, but I haven't seen anything yet.

Also, I don't have that search directive in resolve.conf. Is that a problem?

The server box I'm using is running *all* of my services, so I've set up the DNs dn.fefnir.arcadia, web.fefnir.arcadia, and [www.fefnir.arcadia](www.fefnir.arcadia) (via CNAME) to all point to 192.168.1.9.

Another offshoot question, but is there an Apache 2 environment variable to get/set the domain name? I'm using redirection but it currently puts a hard coded IP address in. I'd like to replace this with the web domain name ([www.fefnir.arcadia](www.fefnir.arcadia)).

Thanks for all the help. I really appreciate it. :-)

---

### Post by Eiríkr on 2008-03-14
Glad to hear you're up and running!  Now comes the fun part of working out the various wrinkles particular to your individual LAN setup.  :D

> What I'd like to know now is how I'll keep this working since the network manager wipes and rewrites resolve.conf often. I'm thinking my router may have a setting to specify a different DNS, but I haven't seen anything yet.

Ah yes, Network Manager -- I found in my case that this worked best when using a static IP setup in Network Manager, so NM won't rewrite all the time on the basis of the DHCP lease results.  Another option is to set up your router to grant fixed leases assigned to each machine on the basis of their MAC addresses (something most, but perhaps not all, consumer routers can do), and assign your local DNS server as the DNS server the router should refer to -- that way any machines negotiating a DHCP lease from your router will automatically point to your local DNS server.  

> Also, I don't have that search directive in resolve.conf. Is that a problem?

I understand that the search directive is what defines how non-fully-qualified domain names are handled.  So if I type in [font=courier]http://rutabaga/[/font] in my browser, the domain name after "search" in the resolv.conf file is what gets automatically added onto the end.  

> The server box I'm using is running all of my services, so I've set up the DNs dn.fefnir.arcadia, web.fefnir.arcadia, and [www.fefnir.arcadia](www.fefnir.arcadia) (via CNAME) to all point to 192.168.1.9.

Sounds fine.  I've read somewhere that certain services might require a proper A record instead of a CNAME, but then I've also read that it's possible to have multiple A records pointing to the same IP.  

> Another offshoot question, but is there an Apache 2 environment variable to get/set the domain name? I'm using redirection but it currently puts a hard coded IP address in. I'd like to replace this with the web domain name ([www.fefnir.arcadia](www.fefnir.arcadia)).

No idea, I'm afraid -- I'm perfectly ignernt when it comes to Apache.  :-|

Glad to help, and good luck with the rest of your configuration!  :)

Cheers,

Eiríkr

**PS --**

If this resolves your hostname difficulties and brings this thread to a close, please remember to mark it as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

---

