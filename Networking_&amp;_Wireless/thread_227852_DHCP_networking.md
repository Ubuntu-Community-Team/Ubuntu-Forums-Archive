---
title: "DHCP networking"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by vj2k on 2006-08-02
Hi,

I work for an educational institute. I have limited networking knowledge. Currently our instiotute has a peer 2 peer network with static IPs. We now are facing a crunch with IPs and would like to use a DHCP server, I have persuaded my institute to use ubuntu.

Now, here is the issue
we have IP addresses from 192.168.11.0 to 192.168.11.255 with 192.168.11.250 being the gateway which runs SUSE 8

I have setup my DHCP configuration like this

# A slightly different configuration for an internal subnet.
 subnet 192.168.10.0 netmask 255.255.254.0 {
  range 192.168.10.3 192.168.10.250;
  option domain-name-servers 202.54.1.30, 202.54.9.1;
  option domain-name "abc.edu";
  option routers 192.168.11.250;
  option broadcast-address 192.168.11.255;
  default-lease-time 600;
  max-lease-time 7200;
}

I have also changed the subnet maskon the gateway to 255.255.254.0

Now when I connect a windows machine it gets the DHCP lease (192.168.10.250) but is unable to connect to the gateway? I have no idea whatsd wrong.
When i try to ping this machine from the gateway the gateway tries to access a m/c 192.168.10.2 which does not exist.

Kindly help

Another query, Our institute is wifi enabled and I would like the laptops also to user this DHCP server, In this case what should be done regarding the access points, should they be given static IPs
thanks
vijay

---

### Post by mips on 2006-08-03
Why are you mixing 192.168.10 & 192.168.11 and why that netmask, also specifying a router in another network , I'm a bit confused ?

Plse let us look at your interfaces file and give us a layout of your network and what you want to achieve as I find your post a bit confusing.

---

