---
title: "sch_fq_codel"
date: 2020-12-15
forum: Networking &amp; Wireless
---

### Post by uafmaewo on 2020-12-15
Hi all
How do I get rid of the fq_codel on 20.04 ? I'm serving nfs4 to the local network and
the sch_fq_codel is really not helping in this situation. 

/etc/default/grub:11:GRUB_CMDLINE_LINUX_DEFAULT="blacklist=sch_fq_codel"
/etc/modprobe.d/blacklist-fq_codel.conf:1:blacklist sch_fq_codel

The module is still loaded despite kernel cmdline blacklist parameter

# tc qdisc sh
qdisc noqueue 0: dev lo root refcnt 2 
qdisc fq_codel 0: dev enp3s0f0 root refcnt 2 limit 10240p flows 1024 quantum 1514 target 5.0ms interval 100.0ms memory_limit 32Mb ecn 
# sudo tc qdisc del dev enp3s0f0
RTNETLINK answers: No such file or directory

The above used to work before. So, what is all this fq_codel mess and how do I get rid of it ? Thanks for any help

---

### Post by uafmaewo on 2021-05-01
So... one solution to this could be: create the file /etc/modprobe.d/blacklist-various.conf with contents:
install sch_fq_codel /bin/false

---

