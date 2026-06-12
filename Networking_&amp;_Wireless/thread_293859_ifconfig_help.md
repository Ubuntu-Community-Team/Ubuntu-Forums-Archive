---
title: "ifconfig help"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by lavda on 2006-11-05
hi people
i have install ubuntu 6.10 and when iconfig my network interface example
ifconfig eth0 192.168.0.1 netmask 255.255.255.0 up ok this work but when i restart pc all configure is lost is a posible to help me any user here

---

### Post by DaveBorealis on 2006-11-05
Hello,

On Dapper (6.6, Gnome) you'd go to 'System->Administration->Networking', select 'Ethernet Connection' and click 'Properties'.  Then you can check 'Enable this connection' and use 'Static IP Address' for connection, and enter you IP and netmask.

If it's different in Edgy, maybe someone can step in and note the changes.

Best regards,
Dave

---

### Post by lavda on 2006-11-05
yes but i need to configur network interface via terminal

---

### Post by DaveBorealis on 2006-11-05
Oh...in that case make a backup copy of '/etc/network/interfaces' 
```
sudo cp interfaces interfaces_orig
```
and assuming I fully understand your setup, replace what's there with
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway <whatever the IP address of your gateway is>

```

If my suggestion messes anything up, return the original and at least you'll be no further back than square one.

Dave

---

### Post by lavda on 2006-11-06
thnx for replay

---

