---
title: "hostnames provided by tomato firmware on router broke with 17.04"
date: 2017-04-15
forum: Networking &amp; Wireless
---

### Post by macho3 on 2017-04-15
I have tomato firmware running on my router, whose "Static DHCP" section allows you to set a static IP address and hostname for devices throughout on the LAN.

This has always worked fine until I upgraded to 17.04 yesterday. Now the hostnames set in the router don't resolve on my laptop. They still work fine on my mobile device, and if I add local entries  into /etc/hosts this successfully works around the problem. But it's not ideal.

Any thoughts on how I diagnose and ideally fix this would be greatly appreciated. I know little enough about networking that I don't understand what mechanism allowed this to work in the first place (beyond "it's dhcp", that is), and have no idea how my local machine tries to query the router for this information.

Thanks!

---

### Post by TheFu on 2017-04-15
There are 2 protocols.
* DHCP
* DNS

DNS does the IP <---> Name stuff.
DHCP provides clients with network setup info, including the DNS server to be used.  DHCP provides the IP, netmask, gateway, MTU at a minimum.

I'd restore from a backup made prior to moving to 17.04 and wait for a month and try again, if I needed 17.04.  I don't and don't plan to run it, but we're LTS-only operation here.

BTW, if your tomato firmware hasn't been updated with newer than Feb release, it is a huge, major, back door in the kernel that anyone can exploit over the internet.  The major Linux releases patched this a few months ago, but didn't announce it until this week. It was THAT serious.

I've pulled all my consumer Linux-based routers from the WAN over this. There have been similar issues previously.

---

