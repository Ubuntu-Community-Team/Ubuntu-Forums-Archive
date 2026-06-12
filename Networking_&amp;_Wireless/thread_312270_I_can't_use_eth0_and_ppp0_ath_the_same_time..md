---
title: "I can't use eth0 and ppp0 ath the same time."
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by daniminas on 2006-12-04
Hi all.

I've a problem connecting to internet with the ubuntu server installation.

I have a eth0 configured to:

IP: 192.168.0.1
MASK: 255.255.255.0
GATEWAY: 192.168.0.1

when ubuntu boot up:

```
> ping 192.168.0.30 (other pc)
//And works!! ))

> but if i connect to interne:
>wvdial
//Works to!! :)

But:
ping google.com
//without response
```

And the thing is afer boot, or wherever:

If i make:
```
> ifdown eth0

> wvdial
//connection sussefull!

> ping google.com
//now it works! ))
```


Isn't a DNS servers problems because they are good configured in /etc/resolv.conf.

Ive the IP of eth0 and the gateway configured to: 192.168.0.1 to 'share' the connection (in the future, not rigth now)

Thanks for any help and sorry my dirrty english

Daniel

---

### Post by lloyd_b on 2006-12-04
Could you do the following:

Boot the machine.
Run "wvdial"
Run the "route" command.

And post the output from "route"?

What I *think* is happening is that eth0 is begin given a "default" route, so that all network traffic is being routed to eth0, even after you've started up ppp0 via the "wvdial" command.  When you "ifdown eth0", that default route is being deleted, and "wvdial" is correctly creating a new default route, directed to ppp0.

Could you also post a copy of your "/etc/network/interfaces" file?  I suspect that this is where the problem is...

Lloyd B.

---

### Post by daniminas on 2006-12-04
Yes, i think 'the default' is the problem, how can i set the ppp0 as the default? with the route command?

Thanks VERRY much :)

---

### Post by deanlinkous on 2006-12-04
> Ive the IP of eth0 and the gateway configured to: 192.168.0.1 to 'share' the connection (in the future, not rigth now)

Thats the problem. You should not be defining a default gateway...

---

### Post by daniminas on 2006-12-04
but, how can i fix that?.. :(

---

### Post by lloyd_b on 2006-12-04
Look in your "/etc/network/interfaces" file.  There's probably a line below "eth0" for "gateway".  Delete it.

Lloyd B.

---

### Post by daniminas on 2006-12-04
Ok! thanks for the answers. Now all works fine. THANKS! :D 

Daniel

---

