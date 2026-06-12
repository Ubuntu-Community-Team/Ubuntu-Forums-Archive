---
title: "Two instances of all modules"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by derickcyril on 2009-02-08
Hi,

I see two instances of all the modules loaded in the memory. How can I avoid this?

top - 21:00:14 up 5 min,  2 users,  load average: 0.17, 0.22, 0.11
Tasks: 109 total,   3 running, 106 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.8%us,  0.6%sy,  0.0%ni, 95.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1020764k total,   489512k used,   531252k free,    14508k buffers
Swap:  1951856k total,        0k used,  1951856k free,   217404k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
  886 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                                                           
  962 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/1                                                                                           
  967 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                         
  972 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                       
  975 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                       
 1133 root      15  -5     0    0    0 S    0  0.0   0:00.00 kjournald

---

