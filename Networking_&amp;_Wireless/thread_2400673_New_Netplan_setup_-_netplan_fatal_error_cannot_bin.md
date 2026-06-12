---
title: "New Netplan setup - netplan: fatal error: cannot bind to port 2983, is another daemon"
date: 2018-09-08
forum: Networking &amp; Wireless
---

### Post by jamiegordon on 2018-09-08
[SIZE=3]Hello,
I upgraded my 14.04 install to 18.04. I'm attempting to setup Netplan for my wired and wireless I've created a yaml file and placed it in /etc/netplan

Here's the file contents:
[/SIZE][SIZE=3]01-larry_net.yaml[/SIZE]

[FONT=courier new]network:[/FONT]
[FONT=courier new]  version: 2[/FONT]
[FONT=courier new]  renderer: networkd[/FONT]
[FONT=courier new]  ethernets:[/FONT]
[FONT=courier new]    enp2s0:[/FONT]
[FONT=courier new]      addresses: [/FONT]
[FONT=courier new]          -192.168.1.102/24[/FONT]
[FONT=courier new]      wakeonlan: true[/FONT]
[FONT=courier new]      dhcp4: no[/FONT]
[FONT=courier new]      gateway4: 192.168.1.1[/FONT]
[FONT=courier new]      nameservers:[/FONT]
[FONT=courier new]        addresses: [/FONT]
[FONT=courier new]    -192.168.1.1[/FONT]
[FONT=courier new]        -8.8.8.8[/FONT]
[FONT=courier new]        -8.8.4.4[/FONT]


[SIZE=3]If I run[/SIZE] #[FONT=courier new]sudo netplan -d try

[/FONT][SIZE=3]I get the following:[/SIZE]
[FONT=courier new]bind: Address already in use[/FONT]
[FONT=courier new]netplan: fatal error: cannot bind to port 2983, is another daemon running?, exiting.
[/FONT] 
[SIZE=3]Netstat shows the port in use by Netplan.
[/SIZE]
#netstat -pnlt | grep ':2983'
tcp        0      0 0.0.0.0:2983            0.0.0.0:*               LISTEN      1509/netplan


Any clues would be appreciated. 

Thanks
Jamie

---

### Post by mdvorak on 2018-10-12
Jamie - I am having a similar issue and now am unable to access the net.  Did you ever find a solution to this issue?

---

### Post by mypdns on 2018-10-23
Well I had the very same issue, it turns out that for some reason that the package netplan.io had disappered.

But a quick response on irc fixed this with the following response for answer

> you've probably confused the netplan calendaring tool with netplan the network configuration tool
install netplan.io not netplan
(sudo) apt install netplan.io netplan-

After a ```
netplan generate; netplan try
``` then applied the old working config and everything worked again

---

