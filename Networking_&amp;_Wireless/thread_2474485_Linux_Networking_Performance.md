---
title: "Linux Networking Performance"
date: 2022-04-30
forum: Networking &amp; Wireless
---

### Post by kcchalk on 2022-04-30
I have two identical Ubuntu VMs running in Vmware, using VMXNET3. I am running SIPp, which generates UDP voice traffic. On one of the systems, I get up to around 70K pps of 214Byte UDP traffic before I start seeing packet loss. During that 70K pps of UDP traffic, the sipp process is running about 35% CPU and **negligible **ksoftirqd CPU.
 


On the other system, I can only generate about 30K pps of the same traffic before ksoftirqd spikes, and I start getting packet loss. sipp CPU stays low - around 20%, but ksoftirqd goes up dramatically with higher pps and packet loss gets significant - eventually ksoftirqd pegs at 100%.
  


Again, these machines are identical, and I'm using the same vSwitch in ESXi. I have tried pinning sipp to a CPU, I've tried adjusting the receive queues (ens192-txrx-0 and ens192-txrx-1) affinity. I even made an OVA out of the  machine where I get 70K pps and made a new VM with it, and I only get the 30K pps.



I can not figure out what is unique, and working about that machine that gets 70K pps.


Any ideas or things to look at?

---

