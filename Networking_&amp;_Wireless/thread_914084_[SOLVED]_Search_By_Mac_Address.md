---
title: "[SOLVED] Search By Mac Address"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by gali98 on 2008-09-08
Okay I know this cannot be that hard, but I cannot find any info anywhere...

Okay so I am in a Domain environment. It is Windows Active Directory, but I have a few linux machines.

There was an IP conflict with one of our NAS servers, and I was given the charge to find where the other claim was coming from.

The only thing we have is a Mac Address. I need to find as much info as I can on this Mac address. 

How do I go about doing this. I can use windows or linux, but I need to figure this out :)

Kory

Edit: I have tried wireshark, but I don't know how to filter it correctly...

---

### Post by timcredible on 2008-09-08
you could try turning off your nas server and then doing a ```
nbtstat -A <ip address>
``` to find out what user is using that address.  if that doesn't work or isn't feasible, you're going to have to search each switch for the offending mac's port.  on cisco switches, it'd be:
```
sh mac-address-table | inc <mac>

```

---

### Post by gali98 on 2008-09-08
Okay I will try that...

Is there no way to just collect data with wireshark and filter it for that mac?

---

### Post by caljohnsmith on 2008-09-08
> **gali98 said:**
> Okay I will try that...

Is there no way to just collect data with wireshark and filter it for that mac?
Try using this as your filter in Wireshark:
```
eth.addr == A1:23:bf:d6:da:12
```
Of course replace the MAC above with the one in question.

---

### Post by gali98 on 2008-09-09
Thank you so much, that is exactly what I needed caljohnsmith!
Kory

---

