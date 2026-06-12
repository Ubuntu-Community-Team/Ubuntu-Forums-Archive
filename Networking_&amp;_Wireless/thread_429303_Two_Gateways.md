---
title: "Two Gateways"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by sub5 on 2007-05-01
[B][COLOR="RoyalBlue"]I'm a new linux (ubuntu) user,
and trying to configure my system to be applicable with our MS. NW.

we use two gateways, 
the default gateway is 10.1.66.6 for all out routes except if the ip is from 10.10.0.0 netmask 255.255.0.0

in windows we add the following route in the CMD prompt:[COLOR="Red"]
route add -p 10.10.0.0 mask 255.255.0.0 10.1.66.1
[/COLOR]
while I tried to do so in ubuntu by typing the following in the terminal

[COLOR="Red"]:~$ route add -net 10.10.0.0 netmask 255.255.0.0 10.1.66.1[/COLOR]

BUT the terminal replies with the following message:
[COLOR="Red"]SIOCADDRT: Operation not permitted[/COLOR]


Any help please!!!![/COLOR][/B]

---

### Post by Sendervictorius on 2007-05-01
Try ```
route add -net 10.10.0.0 netmask 255.255.0.0 gw 10.1.66.1
```

Syntax is: ```
       route  [-v]  [-A  family]  add  [-net|-host]  target [netmask Nm] [gw Gw] [metric N] [mss M] [window W] [irtt I] [reject]
              [mod] [dyn] [reinstate] [[dev] If]

```

Type "man route" for help

---

### Post by sub5 on 2007-05-01
> **Sendervictorius said:**
> Try ```
route add -net 10.10.0.0 netmask 255.255.0.0 gw 10.1.66.1
```

Syntax is: ```
       route  [-v]  [-A  family]  add  [-net|-host]  target [netmask Nm] [gw Gw] [metric N] [mss M] [window W] [irtt I] [reject]
              [mod] [dyn] [reinstate] [[dev] If]

```

Type "man route" for help


[COLOR="RoyalBlue"]**unfortunately, same problem and message**[/COLOR]

---

### Post by sdide on 2007-05-01
you need to execute the route command as root user, 

hence log in as root, or use sudo (eg. :

~$ sudo route add -net 10.10.0.0 netmask 255.255.0.0 gw 10.1.66.1

)

---

### Post by Sendervictorius on 2007-05-01
Are you doing by prefixing your command with "sudo". You must be root to modify routing tables.

Also - the command as stated will route 10.10.0.0 through  the 10.1.66.1 gateway - which may not be what you intended.

---

### Post by sub5 on 2007-05-01
> **sdide said:**
> you need to execute the route command as root user, 

hence log in as root, or use sudo (eg. :

~$ sudo route add -net 10.10.0.0 netmask 255.255.0.0 gw 10.1.66.1

)



[COLOR="RoyalBlue"]**thanX a million I think it's working now with the sudo**[/COLOR]

---

