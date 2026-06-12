---
title: "cannot find my NIC"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by benben841212 on 2008-08-23
Hi, everyone:

i got this problem:

i used kubuntu 6.06 LTS, kernel 2.6.15, my NIC works well.
however, after i compiled my own kernel 2.6.15.7(didn't change net options, just turned on the multi-processing support) and installed it and restarted, everything works fine except that i can't find my NIC any more.

if i type "mii-tool", it says there is no mii interface. and "ifup eth0/eth1" returns no such device. "ifconfig" returns only the lo interface.

i think it may be the driver problem, so i installed the e1000 driver(i'm quite sure i should use this one) and successfully inserted it by using "modprobe e1000". by using "lsmod" i can see it loaded. but still the problem remains.

and "cat /proc/net/dev" returns only lo there.

i also looked /etc/udev/rules.d/ and cannot see any file related to net.

i think maybe linux has a procedure of enumerate(discover? map?) devices into the system, and my system fails to enumerate NICs as eth0,1,etc, even though i installed the module.

anyone may help?

thanks.

here is some other information:
lspci:
ethernet controller: intel corporation enterprise southbridge DPT copper lan

dmesg:
shows that intel pro/1000 network driver loaded.

lsmod:
e1000 14400 0

---

### Post by livestockPimp on 2008-08-23
well first of all "ifconfig" only returns devices that are configured, try "ifconfig -a"

---

### Post by benben841212 on 2008-08-23
thank you.

yeah. i tried "ifconfig -a" yet there is no ethx at all.
i've read some threads about no NIC and they seem to have some problems with mac address. however, my problem can't be solved in the same way as i tried.
as i turn back to the prior kernel(2.6.15), it works. and dmesg shows e1000:eth0_probe and something like that. however, in my compiled kernel there is nothing there. and if i insert e1000, it says intel pro/1000 network driver loaded. so i think there are something that hampers linux to find my NIC.

the problems remains

---

