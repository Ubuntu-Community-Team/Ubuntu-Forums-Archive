---
title: "Issues Forcing Brand New IP using DHCP"
date: 2016-07-25
forum: Networking &amp; Wireless
---

### Post by tippy86 on 2016-07-25
Hello guys, I've been hitting my head on the wall trying to figure out how to accomplish this. I've been following the directions on this thread [https://ubuntuforums.org/showthread.php?t=1163482](https://ubuntuforums.org/showthread.php?t=1163482) but I still have the same IP. Please do not open a discussion about why I want a new ip, or spoofing my MAC address to get a new ip, being that I've not only tried that, but im pretty sure that this can be done without any spoofing a mac. :)

I have the following running equipment::
ubee dvw3201b  - Cable Modem
netgear wnr 2000  Netgear Router

When i use these commands in my terminal my ip stays the same::

```

sudo dhclient -r
sudo rm /var/lib/dhcp/dhclient.leases
sudo dhclient

```

Please can anyone help me with this???? Thanks

---

### Post by SeijiSensei on 2016-07-25
You need to flush the entry from the router.  Otherwise it will give you the same IP address each time it sees your MAC address until the lease expires.  How you would do that depends on your router's software.

Why not simply use a static address?  That's the best choice if you want to control the machine's IP.  Most routers let you designate a range of addresses to allocate via DHCP.  Pick an address outside that range and assign it statically to the machine.

---

### Post by tippy86 on 2016-07-25
@SeijSensei, by looking at my web login for both my modem, and my router, the only option of changing a static address for both my Modem, and Router is by LAN. not WAN 
Example:: They only allow me to set the static ip addresses via Local Area Network such as -- 192.168.xxxx. I would like change my public Ip and not my local ip.


**example Router::**
[IMG]https://s32.postimg.org/4xciqd7e9/Screenshot_from_2016_07_25_13_34_17.png[/IMG]
[B]
example Modem:[/B]
[IMG]https://s32.postimg.org/bcbjn1e41/Screenshot_from_2016_07_25_13_34_42.png[[/IMG]
[TABLE]
[TR]
[/TR]
[TR]
[TD][/TD]
[/TR]
[/TABLE]

---

### Post by tippy86 on 2016-07-25
If anyone can help,that would be great!! Thanks

---

### Post by SeijiSensei on 2016-07-25
You want to change your public IP?  You should have said so to begin with.  For that, the only option is to turn off the router and wait an hour or two.  Whether the address will change in that time depends on how the ISP has its DHCP servers configured.  If the address is still the same after a couple of hours, you can try turning off the router overnight.  Otherwise you have no control over the IP address assigned to you.

---

