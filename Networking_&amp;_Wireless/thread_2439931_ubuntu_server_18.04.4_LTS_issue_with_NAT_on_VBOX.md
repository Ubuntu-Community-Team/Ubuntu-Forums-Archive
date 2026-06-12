---
title: "ubuntu server 18.04.4 LTS issue with NAT on VBOX"
date: 2020-04-03
forum: Networking &amp; Wireless
---

### Post by natasha1999 on 2020-04-03
Hi there,
  I am new to ubuntu and I am struggling now with virtual box .I have 4 VMs of ubuntu server 18.04.4 LTS
I have set up two Ubuntu servers with NAT in VBOX   but one machine gets the address and other one doesn't
then I have two more machines with two adaptors to both machines 
first is internal and second is NAT   this time NAT is guessing ipv6 from MAC address (that I think) I tried to give manual IP of NAT but the internet doesn't work.

so i have two problems 
first is with 2 VMs with NAT what is the way to enable connectivity of one machine to internet

secondly why NAT as second adptor does not connect to internet if ip address is assigned to it (same ip address of NAT)



Thanks

---

### Post by TheFu on 2020-04-03
virtualbox manual has an entire chapter about the different network options and caveats.
[https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)
Start there.

If you want two VMs to communicate, then you want host-only networking.
If you want outbound only, but not to other VMs behind NAT, use NAT.  The NAT subnets for each VM are separate.
If you want in/out connections with a VM on the same subnet as the hostOS, use bridged networking.

If using bridged networking and DHCP, then the LAN dhcp server needs to have an address space to support all the different devices. Usually, I set the DHCP address space to be 3x the number of devices I expect and lease period to be 1 day.

Be certain to carefully read and understand the caveats in that link.  For example, using wifi for anything on the VM-host usually breaks some stuff. Not all wifi chips support the necessary modes required for VM networking.

---

### Post by SeijiSensei on 2020-04-03
If you're intending for the VMs to provide services to other machines on your network, you need to dump NAT and use Bridged Networking. Then all the VMs will get an address from your DHCP server and be visible to other machines in the same network subnet.

As TheFu says, it's worth reading the networking section of the VB manual.

---

