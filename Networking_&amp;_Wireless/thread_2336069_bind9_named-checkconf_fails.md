---
title: "bind9 named-checkconf fails"
date: 2016-09-04
forum: Networking &amp; Wireless
---

### Post by bobwdn on 2016-09-04
I have created a U16.04LTS virtualbox testing environment of two U16.04LTS dns servers running bind9. I mention this but what to focus on the primary "dc1" machine first. If I can figure out what is wrong this it then I think I can correct the dc2 as both are having the same test issues:

I found and followed this tutorial (if this matters):[HTML]http://www.ostechnix.com/install-and-configure-dns-server-ubuntu-16-04-lts/[/HTML] and have substituted by data in the appropriate locations.

Here is my /etc/bind/named.conf on DC1:```
root@dc1:~# cat /etc/bind/named.conf
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
```

Here is named-chceckconf output:```
root@dc1:~# named-checkconf /etc/bind/named.conf
/etc/bind/named.conf.local:10: unknown option '*******'
/etc/bind/named.conf.local:11: unknown option '*******'
/etc/bind/named.conf.local:12: unknown option '*******'
/etc/bind/named.conf.local:13: unknown option '*******'
/etc/bind/named.conf.local:14: unknown option '*'
/etc/bind/named.conf.local:14: unexpected token near '}'
```

What has me most puzzled is the open ". . . [COLOR="#FF0000"]unknown option**'      '** "[/COLOR] and the references to (what I believe are line references anyway) ". . . . [COLOR="#FF0000"]nd/named.conf.local:**14**[/COLOR]: unknown option ' ' " when there is no line 14 in /etc/bind/named.conf.

So, I must be wrong these are not line references?

Here is:```
root@dc1:~# named-checkconf /etc/bind/named.conf.options
root@dc1:~# named-checkconf /etc/bind/named.conf.local
/etc/bind/named.conf.local:10: unknown option '*******'
/etc/bind/named.conf.local:11: unknown option '*******'
/etc/bind/named.conf.local:12: unknown option '*******'
/etc/bind/named.conf.local:13: unknown option '*******'
/etc/bind/named.conf.local:14: unknown option '*'
/etc/bind/named.conf.local:14: unexpected token near '}'
root@dc1:~# named-checkconf /etc/bind/named.conf.default-zones
```

As /etc/bind/named.conf.local does NOT named-checkconf here is it:```
cat: /etc/bind/named.ocnf.local: No such file or directory
root@dc1:~# cat /etc/bind/named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
// include "/etc/bind/zones.rfc1918";

zone "bwtest.bw" {
******* type master;
******* file "/etc/bind/for.bwtest.bw";
******* allow-transfer { 192.168.24.52; };
******* also-notify { 192.168.24.52; };
*};
zone "24.168.192.in-addr.arpa" {
******* type master;
******* file "/etc/bind/rev.bwtest.bw";
******* allow-transfer { 192.168.24.52; };
******* also-notify { 192.168.24.52; };
*};
```

I have checked and rechecked all the "{" and "}" brackets to insure beginnings and endings.

Suggestions on what to look at or adjust next would be greatly appreciated?

---

### Post by bobwdn on 2016-09-05
Okay, so, let's try only my first question.

"What has me most puzzled is the open ". . . unknown option' ' " and the references to (what I believe are line references anyway) ". . . . nd/named.conf.local:14: unknown option ' ' " when there is no line 14 in /etc/bind/named.conf." 

Is the **[COLOR="#FF0000"]" . . . :14: unknown option"[/COLOR]** referring to line 14 of the /etc/bind/named.conf file?

Anybody?

---

### Post by SeijiSensei on 2016-09-05
All those "***" entries are the problem just like the report says.  The entries should read
```

zone "bwtest.bw" {
     type master;
     file "/etc/bind/for.bwtest.bw";
     allow-transfer { 192.168.24.52; };
     also-notify { 192.168.24.52; };
};

```
(I indented for readability; it's not required.) If you thought those stars were commenting out the lines, they're not.  The only valid comment prefix in a BIND configuration file is //.  You can also embed comments between /* and */ pairs.

---

### Post by bobwdn on 2016-09-10
Thanks for clearing that up. It seems that when I "cut and paste" your code, the editor (vi in my case) created the blank spaces that caused problems. Removing the spaces and saving allowed bind9 to function properly.

Perhaps you should correct your document so does not happen to someone else in the future? Other than that, is is a great article. Thanks for your work.

---

