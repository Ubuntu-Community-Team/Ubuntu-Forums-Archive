---
title: "Ubuntu 18.04 / DNS Issue"
date: 2019-07-12
forum: Networking &amp; Wireless
---

### Post by banaanas on 2019-07-12
**Hello guys,**

First of all, I'd like to thank everyone for your awesome job. Also, I would like to apologize for my mediocre english, but I'm French.

Anyway! I wanted to use Opendns DNS so I've changed the setting on my network managers for those : 

[LIST]
[*][B][I] 208.67.222.222;
[/I][/B]
[*]***208.67.220.220.***
[/LIST]

Then, because I wanted the Opendns filter to be on all my Wifi network, I changed my routeur's DNS and used those. But it did not work, so I reset my routeurs parameters (network), then and deleted also the Opendns' dns on my network manager (desktop).
But still, I'm stuck with : ***208.67.222.222, 208.67.220.220***I've been searching and trying a lot.

My resolv.conf gives this output --> 
[LIST]
[*]***nameserver 127.0.0.53***
[*]***options edns0***
[/LIST]

Everything is fine on Windows so I guess it's a Ubuntu issue. I've been flushing my DNS using the comand line. But still nothing.

I let you some pictures to ilustrate my issue. Hope you can help me.
Thank you very much.

[ATTACH=CONFIG]283611[/ATTACH][ATTACH=CONFIG]283612[/ATTACH]

---

### Post by #&amp;thj^% on 2019-07-12
What shows here:
```
cat  /etc/resolv.conf
```

---

### Post by banaanas on 2019-07-12
```
# This file is managed by man:systemd-resolved(8). Do not edit.#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.


nameserver 127.0.0.53
options edns0



```
Thank You

---

### Post by #&amp;thj^% on 2019-07-12
First time I've seen this "options edns0" ,can you tell me about it? (Why is it there, I'm just asking)
Also can you show this:
```
sudo find /etc -name dhclient.conf
```

---

### Post by banaanas on 2019-07-12
I would enjoy to tell you about it, but I don't know either.... :-D

Here, in french, they say it's a "edns option"
[https://forum.ubuntu-fr.org/viewtopic.php?id=2038366](https://forum.ubuntu-fr.org/viewtopic.php?id=2038366)

Thank you

---

### Post by #&amp;thj^% on 2019-07-12
Sorry I added this to see also:
```
sudo find /etc -name dhclient.conf
```

---

### Post by banaanas on 2019-07-12
Of course. Here is the output:

```
cyril@cyril-desktop:~$ sudo find /etc -name dhclient.conf
[sudo] Mot de passe de cyril : 
/etc/dhcp/dhclient.conf



```

*mot de passe = password

---

### Post by #&amp;thj^% on 2019-07-12
Just had to be sure is all, 
Now lets have a look at:
```
cat /etc/dhcp3/dhclient.conf
```

---

### Post by banaanas on 2019-07-12
```
cyril@cyril-desktop:~$ cat /etc/dhcp3/dhclient.conf
cat: /etc/dhcp3/dhclient.conf: Aucun fichier ou dossier de ce type

```

--> No file or directory found

Muchas gracias,

---

### Post by #&amp;thj^% on 2019-07-12
one more then:
```
cat /etc/dhcp/dhclient.conf
```
Also 
```
lsb_release -a
```
Also:
```
apt policy unbound
```

---

### Post by banaanas on 2019-07-13
```
:~$ cat /etc/dhcp/dhclient.conf# Configuration file for /sbin/dhclient.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#


option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;


send host-name = gethostname();
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    dhcp6.name-servers, dhcp6.domain-search, dhcp6.fqdn, dhcp6.sntp-servers,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;


#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
supersede domain-name-servers 208.67.222.222,208.67.220.220;
#require subnet-mask, domain-name-servers;
timeout 300;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/sbin/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;


#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}


#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```[COLOR=#000000][COLOR=#222222]



[/COLOR]```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic



```[COLOR=#222222]
[/COLOR]
[/COLOR]
```
~$ apt policy unbound
unbound:
  Installé : (aucun)
  Candidat : 1.6.7-1ubuntu2.2
 Table de version :
     1.6.7-1ubuntu2.2 500
        500 http://fr.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     1.6.7-1ubuntu2.1 500
        500 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages
     1.6.7-1ubuntu2 500
        500 http://fr.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages



```

Merci beaucoup !

---

