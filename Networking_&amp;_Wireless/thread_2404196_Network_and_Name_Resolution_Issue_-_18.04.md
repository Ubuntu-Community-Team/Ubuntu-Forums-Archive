---
title: "Network and Name Resolution Issue - 18.04"
date: 2018-10-21
forum: Networking &amp; Wireless
---

### Post by penguinpages2 on 2018-10-21
VMWare hosted VM.  18.04 basic deployment if server+gui


When it boot, I logged into the UI and under Wired Connected-> Wired Settings :  VPN and Proxy were the only boxes

Uh.. ok..  go to shell  and ens160  is up but I need it static (no dhcp on those VLANs)

So vi  /etc/network/interfaces
##
iface lo inet loopback
auto lo


auto ens160
iface ens160
        address 172.20.15.242
        netmask 255.255.255.0
        network 172.20.15.0
        broadcast 172.20.15.255
        gateway 172.20.15.1
dns-nameservers 172.20.12.100 172.20.13.100 8.8.8.8
##


on internet.. update.. now in GUI "Wired" box shows ..

Try to install docker but it fails saying cannot resolve host 
##
TASK [check : Validating Hostname is resolvable] *************************************************************************************************************************************************************** fatal: [172.20.15.252]: FAILED! => {"changed": false, "msg": "Please configure your hostname to resolve to an externally reachable IP"}
##

Uh... DNS ping of that host A and PTR record work fine...
##
PING icpdemo01.ibm.aessatl.arrow.com (127.0.1.1) 56(84) bytes of data.
64 bytes from icpdemo01.ibm.aessatl.arrow.com (127.0.1.1): icmp_seq=1 ttl=64 time=0.052 ms
^C
--- icpdemo01.ibm.aessatl.arrow.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.052/0.052/0.052/0.000 ms##

Read forums... recommend addding static entry in /etc/hosts  (and them more about "put on top")
##
172.20.15.252 icpdemo01.ibm.aessatl.arrow.com icpdemo01
127.0.0.1       localhost
127.0.1.1       icpdemo01.ibm.aessatl.arrow.com icpdemo01

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters##

still fails.. same result back to 127.. so cloud install fails..  

check /etc/resolv.conf because it should just.. work sudo vi /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
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
#nameserver 127.0.0.53
nameserver 172.20.12.100
nameserver 172.20.13.100
#Still failing to figure out its IP..


Posted on other forum and was told to remove from /etc/hosts   DNS from /etc/network/interfaces  and let the GUI do it.

So I did.. IP static,  DNS static..  still ping results to 127.0.1.1



This seems like a very basic thing it should be able to figure out..   Not sure where the name resolution is coming from and how to effect its resolution order.

---

