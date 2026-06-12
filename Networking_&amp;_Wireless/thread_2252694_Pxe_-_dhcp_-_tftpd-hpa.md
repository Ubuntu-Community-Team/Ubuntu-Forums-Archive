---
title: "Pxe - dhcp - tftpd-hpa"
date: 2014-11-13
forum: Networking &amp; Wireless
---

### Post by ylafont on 2014-11-13
I have done this before, and the last time I did this, I documented my steps in the event it needed to be redone. However!  This time I am missing something or something has changed. 

During this installation I have been getting  the following error with TFTPD-HPA in syslog. 

```

Nov 13 16:42:27 MediaTwo in.tftpd[1199]: cannot bind to local IPv4 socket: Address already in use
Nov 13 16:42:27 MediaTwo kernel: [ 16.920039] init: tftpd-hpa main process (1199) terminated with status 71
Nov 13 16:42:27 MediaTwo kernel: [ 16.920059] init: tftpd-hpa main process ended, respawning

```

I narrowed this to an entry in /etc/inetd.conf

```
tftp dgram udp wait root /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /srv/pxeboot
tftp dgram udp4 wait root /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /srv/pxeboot

```
Which I could had sworn was needed for the TFTP server.  Without those lines commented out, TFTPD-HPA Does not load.   When it does load i get absolutely nothing in syslog. a client cannot connect and no DHCP address are given to a PXE host.  What has gone wrong. 

Here are my config files. 

DHCP


```
ddns-update-style none;
option domain-name "eclipse.com";
option domain-name-servers 192.168.1.7;
default-lease-time 86400;
max-lease-time 604800;
option time-offset -18000;
authoritative;
log-facility local7;
allow booting;
allow bootp;
subnet 192.168.1.0 netmask 255.255.255.0 {
        get-lease-hostnames on;
        use-host-decl-names on;
        range 192.168.1.200 192.168.1.210;
        option routers 192.168.1.1;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.1.255;
        filename "pxelinux.0";
        next-server 192.168.1.7;
}



```

/etc/default/isc-dhcp-server
> INTERFACES="em1"

/etc/default/tftpd-hpa

> # /etc/default/tftpd-hpa


#TFTP_USERNAME="tftp"
#TFTP_DIRECTORY="/var/lib/tftpboot"
#TFTP_ADDRESS="[::]:69"
#TFTP_OPTIONS="--secure"


RUN_DAEMON="YES"
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/srv/pxeboot"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure --ipv4 --map-file /srv/pxeboot/tftpd.map --verbose"
##TFTP_OPTIONS="--secure"
OPTIONS="-l -s /var/lib/tftpboot"






Have i missed something? Thank you.

---

### Post by levi7 on 2014-12-13
Just curious if you figured this out? I am using dnsmasq and docker to build a pxe server and have it configure and install ubuntu on several hundred machines, along with formatting the harddrives to pinging a server on completion. I am setting up the mirror server and then i'll give it a go using virtualbox in pxe installer mode and try to install on a couple vm's over my network. 
did you ever figure this out? or did you attempt a different solution? I am interested in seeing what is different between the documented much older versions of ubuntu for pxe related installations and more recent versions. 
I will update here in this thread as I go just so anyone looking for pxe related stuff has a place to get an answer :)


--also it might be binding on the 0.0.0.0 and not directly to the address that is causing issues?

---

