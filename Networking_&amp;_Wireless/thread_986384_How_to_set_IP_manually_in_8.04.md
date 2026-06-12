---
title: "How to set IP manually in 8.04"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by mojo_man on 2008-11-18
How can I assign an IP manually in ubuntu 8.04?

Currently my /etc/network/inerfaces has the following:

auto lo
iface lo inet loopback

And my ifconfig -a is as follows
root@mohit-desktop:/etc/network# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:b9:2c:8f:51  
          inet addr:10.20.202.155  Bcast:10.20.255.255  Mask:255.255.0.0
          inet6 addr: fe80::219:b9ff:fe2c:8f51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:302067 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82258741 (78.4 MB)  TX bytes:17329300 (16.5 MB)
          Interrupt:16

---

### Post by hictio on 2008-11-18
I don't understand...
What IP address do you want to assign to that NIC?

---

### Post by mojo_man on 2008-11-18
> **hictio said:**
> I don't understand...
What IP address do you want to assign to that NIC?

I need to assign 10.20.100.9 subnet mask 255.255.0.0

---

### Post by hictio on 2008-11-18
```

sudo ifconfig eth0 10.20.100.9 netmask 255.255.0.0 up (ENTER)

```

Do you have the default gateway IP address and the IPs of the DNS servers as well?

---

### Post by mojo_man on 2008-11-18
> **hictio said:**
> ```

sudo ifconfig eth0 10.20.100.9 netmask 255.255.0.0 up (ENTER)

```

Do you have the default gateway IP address and the IPs of the DNS servers as well?

No I do not. I just need to set this information so I can test a firewall via crossover cable. Will this command write the information to my etc/network/interfaces file? Is there a command that will allow me to set my ethernet interface back to DHCP?

---

### Post by benhur99ph on 2008-11-18
go to System>Administration>Network and edit it from there. It's a GUI so its easy enough. No messing with the terminal.hehehe....

---

### Post by hictio on 2008-11-18
> **mojo_man said:**
> No I do not. I just need to set this information so I can test a firewall via crossover cable. Will this command write the information to my etc/network/interfaces file? Is there a command that will allow me to set my ethernet interface back to DHCP?

No, this settings are not permanent, won't survive a reboot, and they are not written any where.
To get an IP (etc) via DHCP, type:

```

sudo dhclient -r (ENTER)
sudo dhclient (ENTER)

```

Or, like benhur99ph says, go to the Network Manager.

---

### Post by caljohnsmith on 2008-11-18
I think [this thread]("http://ubuntuforums.org/showthread.php?t=974382") might be what you are looking for; let me know if that helps. :)

---

### Post by dmizer on 2008-11-18
> **benhur99ph said:**
> go to System>Administration>Network and edit it from there. It's a GUI so its easy enough. No messing with the terminal.hehehe....

Just for future reference, this is not available in Intrepid 8.10.

Moving this thread to networking and wireless.

---

### Post by mjezell on 2008-11-19
If you need the network GUI in 8.10 go to a terminal and enter 
```
sudo apt-get install gnome-network-admin
```You should then be able to go to 'System>Administration>Network' and make the changes you need to you network connections. I have used this to install it on Mythbuntu 8.10 alternate AMD64 successfully.
Hope this helps.

---

### Post by benhur99ph on 2008-11-23
> **dmizer said:**
> Just for future reference, this is not available in Intrepid 8.10.

Moving this thread to networking and wireless.

Yeah. When I first tried doing this with Intrepid I was a little confused. But the network manager with 8.10 is somewhat easier to use.

---

