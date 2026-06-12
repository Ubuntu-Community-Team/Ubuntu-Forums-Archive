---
title: "Can't join the domain..."
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by muddymind on 2007-08-13
hi!

I managed to make a ubuntu workstation to authenticate against an AD and I made a script to configure everything with that configuration in order to create more ubuntu workstations... the thing is i can't join a new workstation to the domain...

I made
```
sudo net ads join -U user
```
and it always gived me an error of domains but if i make 
```
sudo net rpc join -U user
```
It works just fine and tell me that I had joined the domain...

But if I make
```
sudo getent group
```
I can't see any group from the domain :(

any ideas?

ps-I attached the script I made based on Steve Postema script... It's in portuguese (sorry) and I added kerberos authentication to it :)

---

### Post by muddymind on 2007-08-13
~~up~~

---

### Post by muddymind on 2007-08-13
~~bump~~

---

### Post by tuaris on 2007-08-13
I remember playing around with AD and Ubuntu about a year ago.  I found it to be way too involved to support.

You have to make sure your krb5.conf file has your Active directory domain is caps.

---

### Post by muddymind on 2007-08-14
> **tuaris said:**
> I remember playing around with AD and Ubuntu about a year ago.  I found it to be way too involved to support.

You have to make sure your krb5.conf file has your Active directory domain is caps.

The problem isn't in krb5.conf cuz I can get a kerberos ticket with no problems and that file is the same as the one in the machine that has the AD working...

It must be something that I did in the workstation that it's working and was forgotten on the script but I just can't see what is it :(

In meantime I'm trying SUSE 10.2 on another machine because it comes with decent AD tools to see if can manage to put it working... But honestly, I prefer debian based linux and I was not in the mood to switch to suse....

[]

---

### Post by muddymind on 2007-08-14
~~up~~

---

### Post by muddymind on 2007-08-16
~~bump~~

---

