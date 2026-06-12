---
title: "Extend IP Pool"
date: 2018-07-23
forum: Networking &amp; Wireless
---

### Post by limegroup on 2018-07-23
[SIZE=2][COLOR=#111111][FONT=Ubuntu]For iPXE I have re-written a dhcpd.conf file in which I have added/divined an IP pool/range.[/FONT][/COLOR]
```
range 10.10.1.5 10.10.1.254 
```
[COLOR=#111111][FONT=Ubuntu]I would like to extend this with a complete new range.

Like adding: ```
[FONT=Consolas]range 10.10.2.2 10.10.2.254 [/FONT]
```[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

How it is now:
(This is only the bottom part of the file) 
[/FONT][/COLOR]
```
subnet 10.10.1.0 netmask 255.255.255.0 {
option subnet-mask 255.255.255.0;
option broadcast-address 10.10.1.255;
option routers 10.10.1.1;
option domain-name-servers 10.10.1.1;
range 10.10.1.5 10.10.1.254;
if exists user-class and option user-class = "iPXE" {
      filename "boot.ipxe";
  } else {
      filename "undionly.kpxe";
  }
  }
```
[COLOR=#111111][FONT=Ubuntu]
I guess I need to add a second subnet or something, but whatever I have tried nothing worked. 

All tips and tricks are welcome! 
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Cheers Ray![/FONT][/COLOR][/SIZE]

---

### Post by Doug S on 2018-07-24
> **limegroup said:**
> I guess I need to add a second subnet or something, but whatever I have tried nothing worked.No, I think you need to make one bigger sub-net. However you started on an odd (verses even) boundary for the 3rd ip address byte, so it will be a challenge. Perhaps something like:
```

subnet 10.10.4.0 netmask 255.255.254.0 {
option subnet-mask 255.255.254.0;
option broadcast-address 10.10.4.255;
option routers 10.10.4.1;
option domain-name-servers 10.10.4.1;
range 10.10.4.5 10.10.5.254;
if exists user-class and option user-class = "iPXE" {
      filename "boot.ipxe";
  } else {
      filename "undionly.kpxe";
  }

```

---

