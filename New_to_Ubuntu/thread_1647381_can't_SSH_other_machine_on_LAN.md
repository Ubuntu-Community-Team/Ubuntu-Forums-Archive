---
title: "can't SSH other machine on LAN"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by itsols on 2010-12-17
Hi, this seems like a common problem and there seems to be many posts out there about it but none of them seem to address my issue.

I have two Ubuntu PCs on a LAN going through a switch.
I CAN ping each one.

But I CANNOT SSH into the PC from the other one.
When I try "ssh user@address", it says CONNECTION REFUSED.

I have static IPs.

Any idea would really be appreciated!

---

### Post by iponeverything on 2010-12-17
> **itsols said:**
> Hi, this seems like a common problem and there seems to be many posts out there about it but none of them seem to address my issue.

I have two Ubuntu PCs on a LAN going through a switch.
I CAN ping each one.

But I CANNOT SSH into the PC from the other one.
When I try "ssh user@address", it says CONNECTION REFUSED.

I have static IPs.

Any idea would really be appreciated!

on each machine do:
```

sudo apt-get install openssh-server
```

---

### Post by itsols on 2010-12-17
Oh, how could I forget that!?

Thanks for the reminder. After I did the fresh install I lost all my settings. So that explains my problem :)

Many thanks !!!

---

