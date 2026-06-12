---
title: "Networking reliability issues -- Win 7 host / Ubuntu 14.04 guest"
date: 2015-03-19
forum: Networking &amp; Wireless
---

### Post by grahamsaa on 2015-03-19
I have virtualbox 4.3.26 running on a Windows 7 host with an Ubuntu  14.04 guest.  Ever since upgrading virtualbox to the latest version this  week and installing system updates through Aptitude, my network interface on the guest (NAT, I've tried all the  adapter types available including virtio) disconnects every few minutes  and then immediately reconnects.  This is annoying as I work primarily  in Linux (though I can't run it on my host machine because of company  policies).

Dmesg shows this, over and over.  Note that I'm  currently using the e1000 adapter type, but essentially the same thing  happens with all available adapter types:
[ 3847.752236] e1000: eth0 NIC Link is Down
[ 3847.752363] e1000 0000:00:03.0 eth0: Reset adapter
[ 3852.207690] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3853.816533] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[ 3853.816853] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4328.768220] e1000: eth0 NIC Link is Down
[ 4332.776535] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[ 4509.128250] e1000: eth0 NIC Link is Down
[ 4513.136564] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[ 5408.960262] e1000: eth0 NIC Link is Down

My  machine is connected by a single ethernet cable and I have noticed no  network issues on the host at all.  Wifi is completely disabled.  I'm at  a loss.  Does anyone know what might be causing this?

---

