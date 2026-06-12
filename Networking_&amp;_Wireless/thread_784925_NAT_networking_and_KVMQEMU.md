---
title: "NAT networking and KVM/QEMU"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by ivom on 2008-05-06
I have been googling a lot recently and I cannot find a good tutorial about setting up a NAT network with KVM/QEMU - something that works so nicely in VMware. 

Here is what if found so for: 

1. On [http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers](http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers) I found out how to install virtio drivers on a guest machine and it works if you run the NAT in a user mode: 

kvm -hda guest_os_hdd.img -net nic,model=virtio -net user ...

2. On [http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/QemuAndTuntap](http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/QemuAndTuntap) I found some details about seting up tun/tap devices, and after following all the steps, my guest OS could not see anything on the network. On the host side (Ubuntu 8.04) I could ping the IP address assigned to the guest. 

After I set the guest IP address manually (it didn't obtain the IP address on its own, so I used on of the IP addressess in the tap address space), I was not sure what to put for the gateway IP and for the DNS server. So, I could ping the guest from the host, but the guest has no working network. 

Even if it is trivial to fix this, it is not quite obvious to me. I still think that the info given in the web page given above is useless or at least incomplete. 

3. After installing virtlib and virt-manager, I've noticed a 'vnet0' network, but I have no idea how to use it. If virt-manager uses it somehow, too bad, because it is ridden with so many bugs that it is totally useless.  

It is my impression that the focus is on explaining bridged networks, which is fine, except that many people have ISPs which give then only one IP address, and not several of them. 

The default NAT works (in user mode), but it is my understanding (maybe I am wrong) that this NAT type is not optimal. The super-geeky explanations go something like this: you can either setup tap device, or you may use vde !!! Really? If it was that easy why doesn't somebody write a nice script to emulate what VMware does? Or, if it is indeed difficult to setup a network, then, please, somebody write a tutorial that works.

---

### Post by ivom on 2008-05-07
Well, I had an exchange of messages with Haydn Solomon at:

[http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers#comment-32](http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers#comment-32)

and if I understood him properly, there is nothing more to NAT then the user-mode. Somehow, from reading many posts about KVM networking, I was under impression that there was a better way of doing NAT. 

Probably, what everybody meant was that there is a better way THAN (instead of OF) doing NAT. 

Still, I think that VMware's NAT is better.

---

