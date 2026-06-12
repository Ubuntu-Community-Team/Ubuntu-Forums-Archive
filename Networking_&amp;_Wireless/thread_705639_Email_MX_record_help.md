---
title: "Email MX record help"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by flyinggreg on 2008-02-23
Hi

I'm a newb regarding web admin.  I have setup a web site and use eDNS for my name server & dynamic DNS.  Everything regarding the web site works with exception of email.  Since I am new at this I think my MX record isn't setup correct.  I could use some help here to rule the MX out as a problem and move onto to fixing Postfix (if need be).

Here's the the setup I currently have:

[HTML]DYNAMIC DOMAIN:  wingandrotors.com
HOST                      TYPE        VALUE                      MX
wingandrotors.com         A           xxx.xxx.xxx.xxx            -
wingandrotors.com         MX          mail.wingandrotors.com     0
www.wingandrotors.com     CNAME       wingandrotors.com          -

DYNAMIC DOMAIN:  mail.wingandrotors.com
HOST                        TYPE      VALUE                      MX
mail.wingandrotors.com      A         xxx.xxx.xxx.xxx            -

Results from mxtoolbox.com:
wingandrotors.com = 
PREFERENCE               HOST NAME                  IP                  TTL
0                        mail.wingandrotors.com     xxx.xxx.xxx.xxx     300
DNS HOST: unknown
EMAIL HOST: <blank>

SMTP EMAIL SERVER TEST: 
MAIL SERVER: mail.wingandrotors.com
BANNER: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond[/HTML]

xxx.xxx.xxx.xxx = dynamic IP, but is the same IP between records (ex. currently all are pointing to 68.250.187.17)

Sorry about using the HTML quotes - need to somewhat organize the information as I see it!
Thanks for the help!

---

### Post by Eiríkr on 2008-02-23
> **flyinggreg said:**
> Here's the the setup I currently have:

[HTML]DYNAMIC DOMAIN:  wingandrotors.com
HOST                      TYPE        VALUE                      MX
wingandrotors.com         A           xxx.xxx.xxx.xxx            -
wingandrotors.com         MX          mail.wingandrotors.com     0
www.wingandrotors.com     CNAME       wingandrotors.com          -

[Here's a great online HOWTO for a simple DNS server config](http://www.langfeldt.net/DNS-HOWTO/BIND-9/DNS-HOWTO-5.html).  I'd highly recommend you read through it and go from there; I got my own DNS server set up properly after doing the same.  Just on the basis of that HOWTO, it looks like your MX records are funny (assuming the above is your zone file).  A sample zone file looks like this:
```
;
; Zone file for linux.bogus
;
; The full zone file
;
$TTL 3D
@       IN      SOA     ns.linux.bogus. hostmaster.linux.bogus. (
                        199802151       ; serial, todays date + todays serial #
                        8H              ; refresh, seconds
                        2H              ; retry, seconds
                        4W              ; expire, seconds
                        1D )            ; minimum, seconds
;
                NS      ns              ; Inet Address of name server
                MX      10 mail.linux.bogus     ; Primary Mail Exchanger
                MX      20 mail.friend.bogus.   ; Secondary Mail Exchanger
;
localhost       A       127.0.0.1
ns              A       192.168.196.2
mail            A       192.168.196.4
```

A great diagnostic tool when setting up your DNS server is the [font=courier]dig[/font] command.  The HOWTO linked to above shows numerous instances of how to use the command and what its output looks like.

HTH,

Eiríkr

---

### Post by flyinggreg on 2008-02-23
I can't seem to find the /etc/bind/named.conf file.  In Webmin, I can set the BIND server configuration, so BIND is installed.  But under the files system, I have no /etc/bind directory.  I do have a /var/cache/bind/ directory, but nothing is in it.  Also, my webserver works fine, just no external email - I am not sure about internal email.

---

### Post by Eiríkr on 2008-02-23
> **flyinggreg said:**
> I can't seem to find the /etc/bind/named.conf file.  In Webmin, I can set the BIND server configuration, so BIND is installed.  But under the files system, I have no /etc/bind directory.  I do have a /var/cache/bind/ directory, but nothing is in it.  Also, my webserver works fine, just no external email - I am not sure about internal email.

What version of Ubuntu are you running?  In Webmin, what Bind version does it show at the top of the Bind DNS Server config page?  In Webmin, what do you see when you hit the "Edit Config File" icon?  The top of your named.conf.options file should look like this:
```
options {
	directory "/var/cache/bind";
```
At the bare minimum, this should give you a hint as to where to look.  

If these all come up with naught, fire up Synaptic, hit "Search" and look for "bind" to see what package you have installed.  Look at the package properties to find out specifically which files are installed (and where they are).

HTH,

Eiríkr

---

### Post by flyinggreg on 2008-02-24
> **Eiríkr said:**
> What version of Ubuntu are you running?  In Webmin, what Bind version does it show at the top of the Bind DNS Server config page?  In Webmin, what do you see when you hit the "Edit Config File" icon?  The top of your named.conf.options file should look like this:
```
options {
	directory "/var/cache/bind";
```
At the bare minimum, this should give you a hint as to where to look.  

If these all come up with naught, fire up Synaptic, hit "Search" and look for "bind" to see what package you have installed.  Look at the package properties to find out specifically which files are installed (and where they are).

HTH,

Eiríkr

I'm running Ubuntu Server 6.06 and BIND is version 9.3.2.  Yes, directory pointed to is /var/cache/bind.  So that is where I need to place the named.conf file?

I started following the HOWTO and for some reason I can't telnet 127.0.0.1 on webmin.  So...there's a problem with with one of the other config files (nsswitch.conf, resolv.conf, or hosts)?   I don't understand why I can connect to my website, but not telnet my server.

---

### Post by flyinggreg on 2008-02-24
Ok, I changed my MX record on everydns.net and checked it with
```
> dig wingandrotors.com

; <<>> DiG 9.3.2 <<>> wingandrotors.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52891
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 4

;; QUESTION SECTION:
;wingandrotors.com.		IN	A

;; ANSWER SECTION:
wingandrotors.com.	300	IN	A	68.250.187.17

;; AUTHORITY SECTION:
wingandrotors.com.	256171	IN	NS	ns2.everydns.net.
wingandrotors.com.	256171	IN	NS	ns3.everydns.net.
wingandrotors.com.	256171	IN	NS	ns4.everydns.net.
wingandrotors.com.	256171	IN	NS	ns1.everydns.net.

;; ADDITIONAL SECTION:
ns1.everydns.net.	169771	IN	A	209.131.97.99
ns2.everydns.net.	169771	IN	A	204.152.184.150
ns3.everydns.net.	169771	IN	A	208.96.6.134
ns4.everydns.net.	169771	IN	A	64.158.219.3

;; Query time: 87 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Feb 24 04:10:19 2008
;; MSG SIZE  rcvd: 199

```
As you can see, there is no MX entry.  I am trying to follow the HOWTO, but I don't have NAMED anywhere.  I am guessing that is why I can't resolve the MX record?

I am still trying to figure out WebMin - how do I setup a proper zone file for my website?  Like I said, the website is running ok (a little slow to connect) but the email is zilch.  I don't want to mess around too much and screw up the apache2 connections - been there, done that, didn't like fixing....

---

### Post by Eiríkr on 2008-02-24
> **flyinggreg said:**
> I'm running Ubuntu Server 6.06 and BIND is version 9.3.2.  Yes, directory pointed to is /var/cache/bind.  So that is where I need to place the named.conf file?

I started following the HOWTO and for some reason I can't telnet 127.0.0.1 on webmin.  So...there's a problem with with one of the other config files (nsswitch.conf, resolv.conf, or hosts)?   I don't understand why I can connect to my website, but not telnet my server.

About telnet, I'm not sure if you're aware, but Webmin runs on port 10000.  I can telnet to my localhost provided I specify this port: [font=courier]telnet localhost 10000[/font].  Does that work for you?

About the bind config files, I was misremembering something when last I posted -- the bind files should not be placed in the /var/cache/bind directory.  If you go back into Webmin and click the "Edit Config Files" button again, look at the dropdown at the top -- it should have the following three files listed:
[list][*]/etc/bind/named.conf.options
[*]/etc/bind/named.conf
[*]/etc/bind/named.conf.local[/list]
If these show up, they *should* ostensibly be in your /etc/bind directory.  If they're not there, try finding them by typing [font=courier]locate named.conf[/font] etc.  (You might need to first run [font=courier]sudo updatedb[/font] beforehand to update the locate database.)  If that *still* draws a blank, it sounds like your config files were deleted somehow.  At this point, I'd recommend opening Synaptic, *fully* removing the Bind9 package, and then reinstalling it.  This should get you at least a sample set of config files in the /etc/bind directory, which you can then customize as needed.  

Incidentally, what do you find in /etc/resolv.conf?  

Cheers,

Eiríkr

---

### Post by Eiríkr on 2008-02-24
> **flyinggreg said:**
> Ok, I changed my MX record on **everydns.net** and checked it with
```
> dig wingandrotors.com

; <<>> DiG 9.3.2 <<>> wingandrotors.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52891
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 4

<snip>
```

As you can see, there is no MX entry.  I am trying to follow the HOWTO, but I don't have NAMED anywhere.  I am guessing that is why I can't resolve the MX record?

Aha -- you had me confused there -- you're ***not*** using Bind at all!  :)  Doh!  So of *course* you're not going to have anything in /etc/bind!  Please disregard my previous posting about the DNS HOWTO (unless you plan on setting up your own DNS server on one of your own machines).  

Okay, I'm not familiar with EveryDNS, but over at DynDNS.com, once you log in and get to your personal zone settings, you can click a link marked "Add New MX", after which you simply plug in the hostname of your mail exchanger.  Presumably EveryDNS has something similar.  

Sorry for the confusion.  Good luck with EveryDNS!

Cheers,

Eiríkr

---

### Post by snowmann on 2008-06-22
@flyinggreg

You chan check your MX by "dig -t MX wingandrotors.com"
```
; <<>> DiG 9.4.2 <<>> -t MX wingandrotors.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24293
;; flags: qr rd ra; QUERY: 1, ANSWER: 7, AUTHORITY: 4, ADDITIONAL: 11

;; QUESTION SECTION:
;wingandrotors.com.             IN      MX

;; ANSWER SECTION:
wingandrotors.com.      300     IN      MX      10 ASPMX3.GOOGLEMAIL.com.
wingandrotors.com.      300     IN      MX      10 ASPMX4.GOOGLEMAIL.com.
wingandrotors.com.      300     IN      MX      10 ASPMX5.GOOGLEMAIL.com.
wingandrotors.com.      300     IN      MX      1 ASPMX.L.GOOGLE.com.
wingandrotors.com.      300     IN      MX      5 ALT1.ASPMX.L.GOOGLE.com.
wingandrotors.com.      300     IN      MX      5 ALT2.ASPMX.L.GOOGLE.com.
wingandrotors.com.      300     IN      MX      10 ASPMX2.GOOGLEMAIL.com.

;; AUTHORITY SECTION:
wingandrotors.com.      259200  IN      NS      ns2.everydns.net.
wingandrotors.com.      259200  IN      NS      ns4.everydns.net.
wingandrotors.com.      259200  IN      NS      ns1.everydns.net.
wingandrotors.com.      259200  IN      NS      ns3.everydns.net.

;; ADDITIONAL SECTION:
ASPMX.L.GOOGLE.com.     166     IN      A       66.249.91.27
ALT1.ASPMX.L.GOOGLE.com. 111    IN      A       209.85.201.27
ALT1.ASPMX.L.GOOGLE.com. 111    IN      A       209.85.201.114
ALT2.ASPMX.L.GOOGLE.com. 110    IN      A       72.14.247.27
ASPMX2.GOOGLEMAIL.com.  542     IN      A       209.85.135.27
ASPMX3.GOOGLEMAIL.com.  2624    IN      A       64.233.167.27
ASPMX4.GOOGLEMAIL.com.  3291    IN      A       66.249.93.27
ASPMX5.GOOGLEMAIL.com.  1465    IN      A       66.249.83.27
ns2.everydns.net.       55      IN      A       204.152.184.150
ns3.everydns.net.       43063   IN      A       208.96.6.134
ns4.everydns.net.       2773    IN      A       64.158.219.3

;; Query time: 219 msec
;; SERVER: 192.168.1.5#53(192.168.1.5)
;; WHEN: Sun Jun 22 08:39:05 2008
;; MSG SIZE  rcvd: 471
```

I have the same problem... Can you give me en example of the MX settings from everydns.com?

Add a record:
- Fully Qualified Domain Name: 	
- Record Type: 	
- Record Value: 	
- If MX Record, MX Value:

Sorry i see you use google.com
Thats not what I need ;)

Thanks
SnowMann

---

