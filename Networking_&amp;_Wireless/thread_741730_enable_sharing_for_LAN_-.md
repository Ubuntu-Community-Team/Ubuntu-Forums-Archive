---
title: "enable sharing for LAN -"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by cortical on 2008-04-01
Ubuntu 8.4 beta

 recognise it is a beta, but had no results last I tried 3 months ago with 7 either.  The lxbx box is offline; have wireless broadband using a HUAWEI connected to an intel iMac24.
want to 
1. connect lxbx to mac, to transfer files, via LAN using NFS
2. ideally connect the lxbx to the internet by sharing the iMac WAN connection

- can't connect to the mac because Sharing can no be enabled on the lx
- can't enable Sharing without nfs-common; download file, and install; nope dependency, dependency not satisfied: portmap|rpcbind

Maybe connect  HUAWEI modem to lx, in order to config internet
- modem nowhere recognised; so no internet

pita

## install nfs=common;  dependency not satisfiable:
try Gutsy updates: [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)
Network:  [http://packages.ubuntu.com/gutsy/net/](http://packages.ubuntu.com/gutsy/net/)

find portmap (6.0-1ubuntu1)
The RPC portmapper
check dependent packages installed:
debconf
libc6
libwrap0
lsb-base

download 32KB, trasfer to lx, open with GPI, all dependencies satisfied, install, completed, portmap daemon started

## install nfs common_1.1 
>> dependency not satisfiable:  libevent 1 
ffs
locate: libevent1_1.3b-0_i386.deb, transfer, install>> ok

## install nfs -common >> >> dependency not satisfiable:libgssapi2
search ubuntu [http://packages.ubuntu.com/hardy/net/](http://packages.ubuntu.com/hardy/net/)  >> not listed
search libraries: [http://packages.ubuntu.com/hardy/libs/](http://packages.ubuntu.com/hardy/libs/) >> found;  7 related packages
	•	libasn1-8-heimdal &#8232;Heimdal Kerberos - ASN.1 library &#8232;
	•	libc6 (>= 2.7-1) &#8232;GNU C Library: Shared libraries 
	•	also a virtual package provided by libc6-udeb &#8232;
	•	libcomerr2 (>= 1.33-3) &#8232;common error description library &#8232;
	•	libheimntlm0-heimdal &#8232;Heimdal Kerberos - NTLM support library &#8232;
	•	libkrb5-22-heimdal &#8232;Heimdal Kerberos - libraries &#8232;
	•	libroken18-heimdal &#8232;Heimdal Kerberos - roken support library &#8232;
	•	libssl0.9.8 (>= 0.9.8f-1)


check the above item in Synaptic, these are not found, so need to be downloaded
libasn1-8-heimdal 
libheimntlm0-heimdal 
libroken18-heimdal 

## install, libheimntlm0-heimdal   dependency not satisfiable; libkrb5-22-heimdal
back to search , download install, dependency not satisfiable; libhx509-1-heimal
download libhx509-1-heimal, transfer, install, ok (what a bloody surprise)

##install the intermediate packages

##install nfs-common: dependency not satisfiable; libgssapi2
locate and download (the ubuntu server is ultra slow) libgssapi2 does not exist, only libgssapi2-heimdal (1.0.1-5ubuntu4) [universe]
Heimdal Kerberos - GSSAPI support library, which is already installed


so nfs-common will not install, because libgssapi2 can not be located in hardy lib repository
search libgssapi2 , gutsy item; libgssapi2_0.11-1_i386.deb
download, transfer, install>> conflicting packages; not installing libgssapi2; libgssapi2-heimak conflicts with libgssapi2

How do people get  functions such as these installed if they do not have the box networked?

---

### Post by Eiríkr on 2008-04-01
If you ever get your connectivity issues figured out (and they definitely sound like the first priority), have a look at [post=4387032]this post[/post] about setting up Lin -> Mac NFS sharing advertised via Avahi for no-nonsense automagic mounting on the Mac side.  

Cheers,

Eiríkr

---

