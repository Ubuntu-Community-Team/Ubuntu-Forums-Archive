---
title: "Ubuntu 8.10 Intrepid as Dom0/DomU"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by chetan punekar on 2010-10-18
[SIZE=4]I have installed xen 3.0 on my laptop. These are detailed configurations - 
[/SIZE][SIZE=4]
[/SIZE][SIZE=4]root@chetan-laptop:/# xm info
host                   : chetan-laptop
release                : 2.6.26-2-xen-686
version                : #1 SMP Mon Aug 30 10:02:38 UTC 2010
machine                : i686
nr_cpus                : 2
nr_nodes               : 1
cores_per_socket       : 2
threads_per_core       : 1
cpu_mhz                : 2094
hw_caps                : bfebfbff:20100000:00000000:00000140:0008e3bd:00000000:00000001:00000000
virt_caps              : 
total_memory           : 2046
free_memory            : 126
node_to_cpu            : node0:0-1
node_to_memory         : node0:126
xen_major              : 3
xen_minor              : 3
xen_extra              : .0
xen_caps               : xen-3.0-x86_32p 
xen_scheduler          : credit
xen_pagesize           : 4096
platform_params        : virt_start=0xf5800000
xen_changeset          : unavailable
cc_compiler            : gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 
cc_compile_by          : buildd
cc_compile_domain      : buildd
cc_compile_date        : Mon Mar  9 10:34:08 UTC 2009
xend_config_format     : 4

I want to install ubuntu 8.10 as Dom0/DomU
Can anybody help me out...?

[/SIZE][SIZE=4]
[/SIZE][SIZE=4]
[/SIZE][SIZE=4]
[/SIZE][SIZE=4]
[/SIZE][SIZE=4]
[/SIZE]

---

### Post by sandyd on 2010-10-18
> **chetan punekar said:**
> [SIZE=4]I have installed xen 3.0 on my laptop. These are detailed configurations - 
[/SIZE][SIZE=4]
[/SIZE][SIZE=4]root@chetan-laptop:/# xm info
host                   : chetan-laptop
release                : 2.6.26-2-xen-686
version                : #1 SMP Mon Aug 30 10:02:38 UTC 2010
machine                : i686
nr_cpus                : 2
nr_nodes               : 1
cores_per_socket       : 2
threads_per_core       : 1
cpu_mhz                : 2094
hw_caps                : bfebfbff:20100000:00000000:00000140:0008e3bd:00000000:00000001:00000000
virt_caps              : 
total_memory           : 2046
free_memory            : 126
node_to_cpu            : node0:0-1
node_to_memory         : node0:126
xen_major              : 3
xen_minor              : 3
xen_extra              : .0
xen_caps               : xen-3.0-x86_32p 
xen_scheduler          : credit
xen_pagesize           : 4096
platform_params        : virt_start=0xf5800000
xen_changeset          : unavailable
cc_compiler            : gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 
cc_compile_by          : buildd
cc_compile_domain      : buildd
cc_compile_date        : Mon Mar  9 10:34:08 UTC 2009
xend_config_format     : 4

I want to install ubuntu 8.10 as Dom0/DomU
Can anybody help me out...?

[/SIZE][SIZE=4]
[/SIZE][SIZE=4]
[/SIZE][SIZE=4]
[/SIZE][SIZE=4]
[/SIZE][SIZE=4]
[/SIZE]
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

---

### Post by mörgæs on 2010-10-18
Are you aware that 8.10 is unsupported and hence a security risk?

---

### Post by Hippytaff on 2010-10-18
> Intrepid does not include a dom0 linux kernel
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

---

### Post by chetan punekar on 2010-10-19
thanks people for your answers.....

---

