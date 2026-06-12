---
title: "getting wireless going on my minimal install"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by pikaia on 2008-01-30
First of all thanks ahead of time for any assistance.

I've done a minimal install of ubuntu gutsy and my pcmcia Ethernet card works fine, and in the Xubuntu LiveCD I can get the Wireless DWL-G630 running within a minute with minimal issues.  I've looked through the installed packages on the cd and mirrored that on my IBM 600e but I can't even get the wireless card to be seen by the software.  If I do a iwconfig I get no wireless installed.

I believe its an Atheros chipset (not 100%) but what package(s) do I need to install to get it up and running?  Heres what I currently have (shortened list)

avahi
bind9
dnsutils
dhcp-client and common
iproute
iptables
iputils
libnmglib0 and util0
miidiag
mimsupport
mtr-tiny
netcat
net-tools
network-manager
network-manager-gnome
ntpdate
openssh-client
pppoconf
tcpdump
telnet
wireless-tools
wpasupplicant
xvnc4viewer

Again thanks.

---

### Post by pikaia on 2008-01-30
I've added Restricted-drivers
and Restricted-drivers-core 
to my packages with no luck.

Any help is again apprciated.  What are the packages I need to install to get this working?  I've gone through the Xubuntu LiveCD 3 times now and searched for all the keywords I can think of in Synaptic and have mirrored that on my OS, but still nothing.  What am I missing, or better yet, was do I need to get it going.

Thanks.

---

### Post by pikaia on 2008-01-31
I just tried BeaFanatIX (minimal distro built on ubuntu) and it recognizes the wireless card but will not connect.  I think it may have something to do with the wpa encoding, since the only options it lists for the password are 'Plain ASCII' and Hexidecimal.  Whereas Xubuntu lists "WPA personal" which is the setting that seemed to work.

The OS on my hard drive (minimal Ubuntu + xfce) won't even recognize it with the packages listed above.

So again, looking for the packages needed to facilitate getting this card to work on my minimal install.

---

