---
title: "How do I set up networking in xen?"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by kotter71 on 2006-11-02
I set up xen via this wonderful howto located here: [https://wiki.ubuntu.com/XenOnEdgy](https://wiki.ubuntu.com/XenOnEdgy)

Great howto!  However, I have absolutely no idea how to set up networking.  None whatsoever.  I read this step here:

> 
Change whatever you want to be changed before the first boot (/mnt/etc/apt/sources.list, /mnt/etc/network/interfaces, /mnt/etc/hostname, /mnt/etc/hosts)


And I see that I have to do something to /mnt/etc/network/interfaces, which is a big clue.  So, I added in all the loopback stuff, which is good.  But I have no idea what to do after that.

I boot my new image and check if networking is somehow enabled automatically by magic, and I am not at all surprised to see only the loopback interface answering me.

Does anyone have a good example of how they enabled networking for their xen guest?  Or can anyone point me in the direction of a good thread?

---

### Post by kotter71 on 2006-11-03
All I am actually looking for here is an example of syntax.  If I want the guest OS to connect to the internet, do I need to enable NAT?  If so, what do I type in the the xen config file, and what do I type in the guest OS config file?  You know, that sort of thing...

Someone who has actually successfully done this, can you please just share your config file syntax?

---

### Post by cinderdust on 2006-11-13
I am using Xen 3.03 on dapper but network setup should be the same as on edgy. My guest OS uses actual disk partitions.

/etc/xen/guest1 ( on dom 0)
--- code start ---
# -*- mode: python; -*-
kernel = "/boot/vmlinuz-2.6.16-xen"
ramdisk = "/boot/initrd.img-2.6.16-xen"
memory = 256
name = "guest1"
vif = ['mac=00:16:3E:00:00:02, bridge=xenbr0']
#vif = ['bridge=xenbr0']
#vif = [ '' ]
disk = ['phy:hda3,hda1,w','phy:hda6,hda6,w','phy:hdc,hdc,r']
#ip = "172.18.137.50"
#netmask = "255.255.248.0"
#gateway = "172.18.136.1"
#dhcp="dhcp"
#hostname = "ubuntu2"
root = "/dev/hda1 ro"
extra = "4"
--- code end ---
I used the vif setting to fix the mac address but that is not required.
I was unable to get the network running using the settings in the xen guest config file so I commented them out.  Interface eth0 would not work on the guest. I kept getting following errors after running 'ifup -a'
--- error --
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
--- end error ---
Finally I tried calling it eth1 and that worked.  dom 0 is using eth0 so maybe that was the problem? I guess it is possible to use the xen guest config file to tell system to use eth1 instead of eth0 but I haven't got that far... ;)

/etc/network/interfaces  (guest OS )
--- start code ---
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface (original)
#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet static
   address 172.18.137.50
   netmask 255.255.248.0
   broadcast 172.18.136.255
   gateway 172.18.136.1
   dns-nameservers 172.18.137.20
--- end code ---
The loopback is pretty standard and it sounds like you have that ok. I believe it is in the file by default.  My default also included the  'auto eth0' /newline/ 'iface eth0 inet dhcp' which would bring up eth0 at startup and use dhcp to get the ip/net mask/gateway/dns server.  I have commented it out in favor of a static ip.
Also look at /etc/resolv.conf to set your nameservers
--- code ---
search yourdomain.org
nameserver 172.18.137.20
nameserver 172.18.137.21
---- end code ---

---

