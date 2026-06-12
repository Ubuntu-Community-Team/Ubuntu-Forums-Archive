---
title: "Bind9 Server Not Starting 18.04 LTS"
date: 2018-08-23
forum: Networking &amp; Wireless
---

### Post by Tadaen_Sylvermane on 2018-08-23
I can't get my bind server running. Just fails instantly. I can't find my error. Near as I can tell this is a direct copy from my previous working Ubuntu 16.04 installation. named-checkconf is coming back with zero problems as well.

```
named-checkzone mylan.home /etc/bind/zones/mylan.zone zone mylan.home/IN: loaded serial 4
OK
```

```
;; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     failbox.mylan.home. root.failbox.mylan.home. (
                              4         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
        IN      NS      failbox.mylan.home.
kodi.mbr.mylan.home.    IN      A       192.168.1.40
user.dvdrip.mylan.home. IN      A       192.168.1.41
main.router.mylan.home. IN      A       192.168.1.1
failbox.mylan.home.     IN      A       192.168.1.2
mc.baybesh.mylan.home.  IN      A       192.168.1.2
mc.creative.mylan.home. IN      A       192.168.1.2
mc.osmosis.mylan.home.  IN      A       192.168.1.2
mc.noeanahi.mylan.home. IN      A       192.168.1.2
mc.ourfamily.mylan.home.        IN      A       192.168.1.2
printserver.mylan.home. IN      A       192.168.1.2
printer.mylan.home.     IN      A       192.168.1.3
laser.mylan.home.       IN      A       192.168.1.4
yansell.laptop.mylan.home. IN   A       192.168.1.5
jason.laptop.mylan.home.        IN      A       192.168.1.6
west.bridge.mylan.home. IN      A       192.168.1.251
east.bridge.mylan.home. IN      A       192.168.1.252
gst.router.mylan.home.  IN      A       192.168.1.253
yard.ap.mylan.home.     IN      A       192.168.1.254




; minecraft srv
_minecraft._tcp.mc.baybesh.mylan.home. 7200     IN      SRV     0       5       50000   mc.baybesh.mylan.home.
_minecraft._tcp.mc.creative.mylan.home. 7200    IN      SRV     0       5       50001   mc.creative.mylan.home.
_minecraft._tcp.mc.osmosis.mylan.home.  7200    IN      SRV     0       5       50002   mc.osmosis.mylan.home.
_minecraft._tcp.mc.ourfamily.mylan.home. 7200    IN      SRV     0       5       50003   mc.ourfamily.mylan.home.
_minecraft._tcp.mc.noeanahi.mylan.home. 7200    IN      SRV     0       5       50004   mc.noeanahi.mylan.home.
```

And reverse file, where the error appears but I can't find it.

```
named-checkzone mylan.home /etc/bind/zones/revmylan.zone 
zone mylan.home/IN: NS 'failbox.mylan.home' has no address records (A or AAAA)
zone mylan.home/IN: not loaded due to errors.
```

```
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     failbox.mylan.home. root.failbox.mylan.home. (
                              4         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
        IN      NS      failbox.mylan.home.
40.1    IN      PTR     kodi.mbr.mylan.home.
41.1    IN      PTR     user.dvdrip.mylan.home.
1.1     IN      PTR     main.router.mylan.home.
2.1     IN      PTR     failbox.mylan.home.
2.1     IN      PTR     mc.baybesh.mylan.home.
2.1     IN      PTR     mc.creative.mylan.home.
2.1     IN      PTR     mc.osmosis.mylan.home.
2.1     IN      PTR     mc.noeanahi.mylan.home.
2.1     IN      PTR     mc.ourfamily.mylan.home.
2.1     IN      PTR     printserver.mylan.home.
3.1     IN      PTR     printer.mylan.home.
4.1     IN      PTR     laser.mylan.home.
5.1     IN      PTR     yansell.laptop.mylan.home.
6.1     IN      PTR     jason.laptop.mylan.home.
251.1   IN      PTR     west.bridge.mylan.home.
252.1   IN      PTR     east.bridge.mylan.home.
253.1   IN      PTR     gst.router.mylan.home.
254.1   IN      PTR     yard.ap.mylan.home.
```

---

### Post by Tadaen_Sylvermane on 2018-08-23
Was a one off. Did a reboot for something else and the service came up just fine on its own. Not sure why but it's running so gonna chalk it up to a fluke.

---

