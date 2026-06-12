---
title: "eth0 not available after fresh install"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by deanshultz on 2007-02-23
[COLOR="DarkGreen"]first post, thanks for any assistance.[/COLOR]

[COLOR="Blue"]os:  [/COLOR]   
kubuntu edgy

[COLOR="Blue"]hdwe: [/COLOR]
new machine. acer desktop, amd 64 4200+, one nic card. dsl modem.

[COLOR="Blue"]problem:[/COLOR]
network settings only show dial-up modem, not ethernet card
network settings have no entries on any tabs
/end problem



[COLOR="Blue"]background:[/COLOR]
if answer is in forums and i missed it, i apologize. however, i have searched and spent several days and many hours un/re-installing, to no avail.

1) initial os was vista. created new partition w/gparted, so a fresh install.

looked at /etc/network/interfaces, which looked ok. and while i do not have config written down here, i can post it.

'ifconfig eth0' up returns device not found error

'sudo pppoeconf' prompts throw modconf 447 error

fresh install attempts:
installed 64-bit kubuntu for greatest compatibility  (removed)
installed 32-bit kubuntu for more stability (removed)
installed 32-bit ubuntu for greatest chance at success, no user intervention required idea (removed)
installed 64-bit feisty fawn for long shot (removed)

2) to gain internet access and work with nic card in ubuntu, i deleted all partitions, reinstalled vista, then created a VM and installed ubuntu to it. there, the card works in ubuntu. while i realize VM may be passing vista-enabled connectivity to ubuntu, the VM test was proof enough to compel me to try kubuntu again.

3)current configuration and to keep some internet access from home while i sort this out, set up dual boot with vista and kubuntu (32-bit edgy). 

as an aside, i did have kubuntu up and working on other machine, a laptop, which i sold to finance the newer, faster, dual-core model.  so, while i feel/appear totally n00b at the moment, i have some prior experience.

---

### Post by Jussi Kukkonen on 2007-02-23
output of these commands will probably be useful:
```
lspci
dmesg | grep -i eth
cat /etc/network/interfaces
```

---

### Post by deanshultz on 2007-02-23
> output of these commands will probably be useful:
Code:

lspci dmesg | grep -i eth cat /etc/network/interfaces

Jussi,

Thank you, will do and post info later today, before 8:00 pm eastern.

---

