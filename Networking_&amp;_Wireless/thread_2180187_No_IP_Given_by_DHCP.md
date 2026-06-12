---
title: "No IP Given by DHCP"
date: 2013-10-11
forum: Networking &amp; Wireless
---

### Post by ylafont on 2013-10-11
Need some guidance  configuring the necessary services required for PXE boot on ubunt0 12.10. Currently the DHCP server is not issuing  IP address to clients. I haven’t even gotten to the PXE stuff yet. There is another DHCP server on the network (default cable modem 192.168.1.1).   I wanted to  leave this router on since the Linux machine will not always be on. 
 
I have installed and configured the following:
inetutils-inetd
tftpd-hpa
isc-dhcp-server
 
Configuration is as follows:
 
**INETUTILS-INETD** *(/etc/inetd.conf)*[INDENT]tftp    dgram   ***udp4  ***  wait    root    /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s ***/srv/pxetftp***[/INDENT]
 [INDENT]changed udp to udp4 fir ipv4.
Changed /srv/tftp to srv/pxetftp[/INDENT]
 
**TFTPD-HPA** *(/etc/default/tftpd-hpa)*
# /etc/default/tftpd-hpa
 [INDENT]**RUN_DAEMON="YES"**  à Line was added
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/srv/**pxetftp**"   à Line was modified to the /pxetftp folder
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure **--ipv4**"   à line was modified –ipv4 was added
**OPTIONS="-l -s /var/lib/tftpboot"**  à line was added[/INDENT]
 
**ISC-DHCP-SERVER **
**(/etc/default/isc-dhcp-server)**
 [INDENT]INTERFACES = “ETH0  **em1**”   à added  “em1”
Not sure why the ehternet card is listed as “em1”, I expected ETH0[/INDENT]
 
**(/etc/dhcp/dhcp.conf)**[INDENT]ddns-update-style none;
option domain-name "eclipse.pxe";
option domain-name-servers 209.18.47.61;
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
        next-server 192.168.1.1;
 [/INDENT]
 
I have placed pxelinux.0  in /srv/pxetftp  - but not really expecting that to start yet,. I am however expecting the PXE client to receive a IP. (Am I Wrong?)
 
I am attaching a copy the syslog, if anyone has the time. Thank you in advance,
 
[https://dl.dropboxusercontent.com/u/58850968/syslog](https://dl.dropboxusercontent.com/u/58850968/syslog)

---

