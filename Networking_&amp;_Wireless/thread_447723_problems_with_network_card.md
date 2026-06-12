---
title: "problems with network card"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by t.slothrop on 2007-05-18
Hello everybody,
I'm new to linux (and to this forum: hello again) and I installed Xubuntu 6.06 on an old acer 
Travelmate notebook with a 3Com Megahertz 589E network card. When I boot from the live-cd I don't have any problems, using pppoeconf I can configure my internet access in a minute. But the installed system somehow doesn't detect my network card, pppoeconf doesn't find an eth0 device, and 
```

me@slothrop:~$ ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device 

``` 
What seems even stranger to me is this: on the live system, dump_cis yields
```

ubuntu@ubuntu:~$ sudo dump_cis
Socket 0:
no CIS present

Socket 1:
dev_info
no_info
attr_dev_info
EEPROM 150ns, 8kb
manfid 0x0101, 0x0589
funcid network_adapter
vers_1 4.1, "3Com", "Megahertz 589E", "TP/BNC LAN PC Card", "005"
config base 0x10000 mask 0x0003 last_index 0x03
cftable_entry 0x01 [default]
Vcc Vnom 5V Iavg 30mA Ipeak 50mA Idown 5mA
timing wait 700ns ready 500us
io 0x0000-0x000f [lines=4] [8bit] [16bit]
irq mask 0xffff [level]
cftable_entry 0x03
Vcc Vnom 5V Iavg 200mA Ipeak 200mA Idown 5mA
attr_jedec 0x00 0x00
checksum 0x0000-0x0079 = 0x00

```
while on the installed system nobody even wants to talk to me:
```

me@slothrop:~$ sudo dump_cis
sudo: dump_cis: command not found

```
When I load the driver 3c589_cs manually nothing happens either...
Can anybody help?
Thanks alot,
Christoph

---

