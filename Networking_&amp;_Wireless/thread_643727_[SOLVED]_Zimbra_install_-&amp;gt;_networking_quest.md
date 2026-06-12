---
title: "[SOLVED] Zimbra install -&amp;gt; networking questions"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by purdticker on 2007-12-18
I need some help installing Zimbra.  I'm following this tutorial: [http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

Unfortunately, I'm having some issues with hostname and MX setup.

I'm using dyndns.org:  purd.getmyip.com

What should my /etc/hosts and /etc/hostname files look like?

---

### Post by purdticker on 2007-12-18
This is the error I get when installing zimbra:

DNS ERROR - none of the MX records for mail.purd.getmyip.com resolve to this host.
Change domain name? [Yes]

---

### Post by purdticker on 2007-12-19
I followed this tutorial: [http://wiki.zimbra.com/index.php?title=Beginner%27s_Guide_to_installing_Zimbra_on_Ubuntu_6.06_Server](http://wiki.zimbra.com/index.php?title=Beginner%27s_Guide_to_installing_Zimbra_on_Ubuntu_6.06_Server)

Here is the process I followed to successfully install Zimbra:

Downloaded and install Ubuntu 6.06 LTS (this version is important, Zimbra will not work on later versions).

> 1) The installation wants to configure your LAN via DHCP. Cancel it before it gets that far, and manually configure it with a static IP address, netmask, and gateway. Don't put in a public DNS for your nameserver configuration; instead put in the same IP address that you just gave the machine for its own static IP (this won't let you resolve names on the internet until we do some more configuration below, but it saves headaches later).
I used the internal ip 192.168.0.100

> 2) When the installation asks for a hostname, give it only a one-word hostname (e.g. "mail" or "myserver") NOT the fully-qualified domain name (mail.mydomain.com).

I chose "mail" as my hostname.

> 
sudo su -

apt-get update

apt-get install bind9

edit "/etc/bind/named.conf.options" to look like the following
> 
options {
        directory "/var/cache/bind";

        query-source address * port 53;

        forwarders {
               ** xxx.xxx.xxx.xxx; xxx.xxx.xxx.xxx;**
        };

        auth-nxdomain no;    # conform to RFC1035
};

For the IP's, I used my ISP's DNS IP's.  If you do not know these, you can find them on the Status tab of your router.

Verify "/etc/resolv.conf" looks like the following:
> 
nameserver 192.168.0.100


Run the following command:
> 
/etc/init.d/bind9 restart


Append the following lines to "/etc/bind/named.conf.local".  I'm using purd.getmyip.com from dyndns.org.
> 
zone "mydomain.com"  {
   type master;
   file "/etc/bind/db.purd.getmyip.com";
};


Create the file: /etc/bind/db.purd.getmyip.com
> 
;
; BIND data file for purd.getmyip.com
;
$TTL    604800
@       IN      SOA     mail.purd.getmyip.com. admin.purd.getmyip.com. (
                         070725         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      mail
        IN      MX      10 mail
        IN      A       192.168.0.100
mail    IN      A       192.168.0.100


Run the following command:
> 
nslookup purd.getmyip.com


This should return internal IP address (192.168.0.100).

Edit your "/etc/hosts" file.
> 
127.0.0.1       localhost.localdomain   localhost
**192.168.0.100      mail.purd.getmyip.com  mail**

It seemed to work with my internal IP here, however the tutorial shows an external ip.

Run the following command:
> 
apt-get install curl fetchmail libpcre3 libgmp3c2 libexpat1 libxml2 libtie-ixhash-perl libstdc++6 libstdc++5


Then I installed Zimbra.  The install asks you to change the hostname, I changed mine to purd.getmyip.com.  The install successfully continued after that.  After the install, I ran this command:
> 
crontab -u zimbra -l


I restarted the machine here for good measure, although it's may not be necessary.

The Zimbra install sucks, apparently if you mess up ANY of these steps in ANY way and you try to install Zimbra, it completely screws up.  Now you will have to completely reformat your computer and start from scratch.  You're supposed to be able to run /opt/zimbra/libexec/zmsetup.pl to finish the setup, but I've never been able to resume an install successfully.

Can someone run through my instructions and correct me where I am wrong?

---

### Post by Charles-2007 on 2007-12-21
I hope that you will post some follow-up on how well Zimbra works for you.

---

### Post by purdticker on 2007-12-21
I definitely will, so far I'm still doing testing.

Zimbra is definitely awesome!  My only complaint is that configuration AFTER you install zimbra really sucks.  It's resulted in me reformatting like 10 times so far.

---

### Post by purdticker on 2007-12-21
Well, Zimbra is working great now.  One extra thing I had to do was to make sure mail.purd.getmyip.com pointed to same ip as purd.getmyip.com.  I did this through dyndns.org.

---

