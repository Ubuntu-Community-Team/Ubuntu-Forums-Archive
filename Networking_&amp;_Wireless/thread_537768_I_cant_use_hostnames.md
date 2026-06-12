---
title: "I cant use hostnames"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by spedsta on 2007-08-29
My network runs fine, except, I cant hit another machine via thier hostname.
Is it something on the router's side, or is it something the pc should be broadcasting onto the lan?

Thanks

---

### Post by noob12 on 2007-08-29
If you are using DHCP, you should generally be getting your DNS server addresses from your DHCP server.  Most home internet router/gateways have DHCP service in them.

Posting the output of the following commends would help people diagnose your problem and help you out.  Cut and paste each command into a terminal window and post the resulting output.

```

ifconfig -a

cat /etc/network/interfaces

cat /etc/resolv.conf

grep dhclient /var/log/syslog | tail -50

```

UPDATE:  Did you mean hostnames on your LAN only?  If so, you probably want winbind.  Let me know.

---

### Post by spedsta on 2007-08-29
i meant host names like if i ping a nother pc , 'wells", i get a "unknown host"  error.

sorry will try to post later, im at work now so i cant get you that messages.

Thanks!

---

### Post by noob12 on 2007-08-30
OK.   You need not send that output.  I thought you meant DNS names on the internet at large.

It is possible to resolve the PC hostnames on the lan, but you need to install another package called winbind.  Here's how.

```

sudo aptitude install winbind

```

Then run these
```

xhost +
sudo gedit /etc/nsswitch.conf

```
This will bring up an editor editing the /etc/nsswitch.conf file.

Find the line that begins with **hosts:**.  It will look something like this
```

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```
Change it so that it reads:
```

hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4

```
Note the added "wins".  Then save, exit, and reboot.

New processes started after the change should see the effect immediately, but the reboot will ensure everything is able to resolve the local PC names.

---

### Post by kevdog on 2007-08-30
Why the xhost + command???

I think you may have explained this before but I cant find the explanation.

---

### Post by noob12 on 2007-08-30
> **kevdog said:**
> Why the xhost + command???

I think you may have explained this before but I cant find the explanation.

Bit of a digression, but good question.  Strictly speaking it shouldn't be needed but I keep running into users for whom gksudo or plain sudo gedit runs into  issues connecting to the x server as root.  So this just cuts to the chase; I avoid an extra round of interaction dealing with "Um,  I get this X server connection error when I type that."

---

### Post by kevdog on 2007-08-30
I remember that command back in college working with unix on the DEC machines.  I was terrible on those machines -- pre internet days -- never understood anything and why things worked and why things didnt.  Ohhhh- I got bad memories thinking about it and trying to complete those damn engineering assignments.

---

