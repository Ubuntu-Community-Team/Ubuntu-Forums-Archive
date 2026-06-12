---
title: "Atheros"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by rottenpunker on 2009-02-15
I just installed Ubuntu, and everything has been going well, except my wireless card. I have an Atheros card, and I downloaded the madwifi driver package thing, but I have no clue what to do from there. Help! Please. =P

---

### Post by tarps87 on 2009-03-11
You probably need to un-tar the downloaded file, open a terminal and navigate to the un-tar'd location.
Then make, install and activate the driver.
e.g.
```

make
sudo make install
sudo modprobe ath_pci

```
This is only a guess though, if you post where you downloaded it from I can be more specific
Also it would help to know what your card is so can you post the output of
```
sudo lshw -C network
```

---

### Post by lkraemer on 2009-03-14
You should try a SEARCH for HOWTO  &  AR242x

There is a good HOWTO: for 8.04 & 8.10 already posted.

Or, try booting a LiveCD of PCLinuxOS 2009 as Wifi enable is a few clicks
away from the Control Center.

lkraemer

---

### Post by cptrohn on 2009-03-14
> **lkraemer said:**
> You should try a SEARCH for HOWTO  &  AR242x

There is a good HOWTO: for 8.04 & 8.10 already posted.

Or, try booting a LiveCD of PCLinuxOS 2009 as Wifi enable is a few clicks
away from the Control Center.

lkraemer

I agree, I have the Atheros AR242x and the linux backports solution is by far the easiest way to get this card running..

just do a search for Atheros AR242x and linux backports if this is your card.

---

### Post by tarps87 on 2009-03-16
> **cptrohn said:**
> I agree, I have the Atheros AR242x and the linux backports solution is by far the easiest way to get this card running..

just do a search for Atheros AR242x and linux backports if this is your card.

It is the easiest but there are know problems under heavy net work usage.
@rottenpunker if you experience any problems with the backport driver I would suggest using the madwifi driver

---

### Post by binbash on 2009-03-16
[http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html](http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html)
[http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_27.html](http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_27.html)

---

