---
title: "eth0, eth1 and eth2 configuration, please read!!!"
date: 2019-02-06
forum: Networking &amp; Wireless
---

### Post by fasantos on 2019-02-06
Hello all,

[COLOR=#000000]I was able to configure the **eth0** without problem, but how do I configure the **eth1** and **eth2, as shown bellow. I am using vSphere for my lab, which I had to create 3 NIC: eth0 to have access to the internet. eth1 as a NAT intranet and eth2 as a NAT with **[FONT=Roboto]**Promiscuous mode checked. please help me with example. **[/FONT]
[/COLOR]
[TABLE="width: 403"]
[TR]
[TD="colspan: 2"]auto eth1[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD="colspan: 3"]iface eth1 inet manual[/TD]
[TD][/TD]
[/TR]
[TR]
[TD="colspan: 4"]  up ip link set dev eth1 up[/TD]
[/TR]
[TR]
[TD="colspan: 4"]  down ip link set dev eth1 down

[/TD]
[/TR]
[TR]
[TD="colspan: 2"]auto eth2[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD="colspan: 3"]iface eth2 inet dhcp[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

---

