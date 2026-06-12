---
title: "IP Tables rules not forwarding properly with squid"
date: 2020-11-17
forum: Networking &amp; Wireless
---

### Post by Tadaen_Sylvermane on 2020-11-17
I've been tinkering with the idea of a custom router. I was advised to use OPNSense or PFSense. They seemed far more than I needed. I can't get it out of my head to do it the hard way (at least for me). Here is where I'm at so far. This script for routing works great. I however cannot solve why my proxy function isn't working. I had it working before I made the routing part so much more involved. Now anything times out as soon as the squid function is triggered.

This is how my script started.

```
[COLOR=#000000]for interface in $(find /sys/class/net/ -maxdepth 1) ; do
[/COLOR] ifname=$(basename "$interface")
 case "$ifname" in
  net|lo|veth*)
   continue
   ;;
  *)
   ifip=$(ip addr | grep 'inet ' | grep "$ifname" | awk '{print $2}' | cut -d\/ -f 1)
    if [ ! -z "$ifip" ] ; then
     case "$ifip" in
      192.168.*.*|172.17.*.*)
       MODIFIEDIP=$(echo "$ifip" | rev | cut -d"." -f2- | rev).0/24
       route add -net "$MODIFIEDIP" dev "$ifname"
       ;;
      *)
       iptables -t nat -A POSTROUTING -o "$ifname" -j MASQUERADE
       ;;
     esac
    fi
    ;;
 esac
done
```

Now I keep it on Git.


[https://github.com/jmgibson1981/scripts/blob/main/sources/homerouter.source](https://github.com/jmgibson1981/scripts/blob/main/sources/homerouter.source)


My Squid.conf

```
acl mylan src 192.168.100.0/24
acl docker src 172.17.0.0/24
acl SSL_ports port 443
acl Safe_ports port 631        # print server
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 70        # gopher
acl Safe_ports port 210        # wais
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl CONNECT method CONNECT
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost manager
http_access deny manager
http_access allow localhost
http_access allow mylan
http_access allow docker
http_access deny all
# begin modifications #
http_port 3128
http_port 3129 intercept
https_port 3130 intercept ssl-bump generate-host-certificates=on dynamic_cert_mem_cache_size=20MB cert=/etc/squid/certs/myCA.pem
sslcrtd_program /usr/lib/squid/security_file_certgen -s /var/spool/squid/ssl_db -M 20MB
acl step1 at_step SslBump1
ssl_bump peek step1
ssl_bump bump all
# end modifications #
maximum_object_size 2000 MB
cache_dir ufs /var/spool/squid 30000 16 256
coredump_dir /var/spool/squid
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .        0    20%    4320
refresh_all_ims on
```

---

### Post by Tadaen_Sylvermane on 2020-11-17
Marking solved. Completed working script at git. My problem was in my global input chain drop all. Once that was found it made it easy. Just had to add input rules to accept my squid ports before the drop.

[https://github.com/jmgibson1981/scripts/blob/main/sources/homerouter.source](https://github.com/jmgibson1981/scripts/blob/main/sources/homerouter.source)

---

