---
title: "disable ethernet card?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by seamustry on 2009-02-17
how do i disable my ethernet card on my laptop? 

is there a menu in ubuntu, kind of like "device manager" in windows?

---

### Post by Fire_Chief on 2009-02-17
Not specifically but you may be able to disable it in your laptop BIOS.

---

### Post by dannyboy79 on 2009-02-17
> **seamustry said:**
> how do i disable my ethernet card on my laptop? 

is there a menu in ubuntu, kind of like "device manager" in windows?

I am still using Feisty so maybe this isn't an option but I would think you could just uncheck the box within the network manager screen under Admin pulldown. See picture. otherwise maybe you could mess around with commenting out the eth0 line with your /etc/network/interfaces file.
[[IMG]http://img253.imageshack.us/img253/5999/networkmanagerku9.th.jpg[/IMG]](http://img253.imageshack.us/my.php?image=networkmanagerku9.jpg)

---

### Post by seamustry on 2009-02-19
> **dannyboy79 said:**
> I am still using Feisty so maybe this isn't an option but I would think you could just uncheck the box within the network manager screen under Admin pulldown. See picture. otherwise maybe you could mess around with commenting out the eth0 line with your /etc/network/interfaces file.
[[IMG]http://img253.imageshack.us/img253/5999/networkmanagerku9.th.jpg[/IMG]](http://img253.imageshack.us/my.php?image=networkmanagerku9.jpg)

thanks but i can't find that in intrepid...any other ideas?

:)

---

### Post by Kareeser on 2009-02-19
That might work... but I'm not sure whether that would conserve batt power, as may be what the OP is looking for...

---

### Post by seamustry on 2009-02-19
yep..exactly why i want to disable my nic

---

### Post by GavinZac on 2009-02-19
> **seamustry said:**
> yep..exactly why i want to disable my nic

If its a fairly new laptop, its more than likely closely integrated into the motherboard and as such, disabling it via software won't save much/any battery. It's not like the old days when it was a PCI card in your tower :)

---

### Post by seamustry on 2009-02-20
my laptop's 4 years old...i'll check my bios also.

---

### Post by Tek-E on 2009-02-20
Not 100% sure but if you open the terminal and type:
```

ifconfig eth0 down

```
That should do the trick in shutting it down.
At least it is what I do.
And to start it back up again.
```

ifconfig eth0 up

```

---

### Post by rgb96 on 2009-02-20
Yeah. ifdown eth0 will disable it to the point that you can't use it. But I doubt that would actually stop it from drawing power.

---

### Post by Tek-E on 2009-02-20
> **rgb96 said:**
> Yeah. ifdown eth0 will disable it to the point that you can't use it. But I doubt that would actually stop it from drawing power.

You are probably right.  It will shut it down but It is likely it will still draw power but it wont draw as much power as it would being up.

---

