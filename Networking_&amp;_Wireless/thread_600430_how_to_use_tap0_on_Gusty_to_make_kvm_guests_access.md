---
title: "how to use tap0 on Gusty to make kvm guests access the internet?"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by maxalken on 2007-11-02
I am trying to make a kvm virtual machine access internet via NAT on tap0, but I have got a permission problem.

I did the following:
> sudo tunctl -u jerry
sudo ifconfig tap0 192.168.100.1 up


then I tried to start kvm and got the error message
> 
kvm -hda mldonkey.img -cdrom /home/DATA/images/ubuntu-7.10-server-amd64.iso -boot d -net nic,vlan=0 -net tap,vlan=0
[B]warning: could not configure /dev/net/tun: no virtual network emulation
Could not initialize device 'tap'
[/B]


I don't get the error massage if I run kvm as root. I just can't get it work as a normal user even i setted the permission of /dev/net/tun as 777

However I get this error message when I run kvm as root
> can't add tap1 to bridge eth0: Operation not supported

It seems kvm automatically trys to assign the next tap device to itself (eg, when tap0 exists, it tries to get tap1)

---

