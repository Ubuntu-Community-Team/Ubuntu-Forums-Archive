---
title: "Lost communication with HOST NIC on KVM Setup  18.04.4"
date: 2020-04-06
forum: Networking &amp; Wireless
---

### Post by glued-2-keyboard on 2020-04-06
[FONT=Helvetica]Hello[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Recently built a VM Host utilizing Ubuntu Server 18.0.4 LTS with multiple NIC’s.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]System was running well until recently when I started experiencing weird networking issues.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]For reasons unknown I can no longer reach the host via the IP / NIC interlace that I assigned to it.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I CANNOT  ping, ssh, etc… the host (onboard nic 192.168.2.2) from the LAN [/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I CAN access the internet from the host (onboard nic 192.168.2.2) for example ping google.com, download updates etc….[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I CAN access the VM’s running on the host from the LAN and the INTERNET with no problems.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Arial][FONT=Helvetica]HOST was/is hanging on boot for 2 minutes with the message “[/FONT][COLOR=#52565A]**A start job is running**[/COLOR][COLOR=#3C4043] for [/COLOR][COLOR=#52565A]**wait for network to be configured”**[/COLOR][/FONT]
[COLOR=#52565A][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Menlo][COLOR=#52565A][FONT=Arial]**I now have **[/FONT][/COLOR]disabled systemd-networkd-wait-online.service[/FONT][/COLOR]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Here is a basic diagram of my network.[/FONT]
[FONT=Helvetica]
pfSense 2.4.4 
tp-link switch TL-SG1016DE


[/FONT]```

[FONT=Helvetica]    INTERNET  <——>  pfSense  <——> tp-link switch[/FONT]
[FONT=Helvetica]                                                                     |          |[/FONT]
[FONT=Helvetica]                                                                     |          |[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]                                                         192.168.1.x.   192.168.2.x[/FONT]
[FONT=Helvetica]                                                               /                     \[/FONT]
[FONT=Helvetica]                                                               /                        \[/FONT]
[FONT=Helvetica]                                                       IoT / PC’s                     (1) onboard nic 192.168.2.2[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]                                                                                            (2) single port nic 192.168.2.3[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]                                                                                            (3) two port nic 192.168.2.4  <—VM Guest IP —> 192.168.2.10[/FONT]
[FONT=Helvetica]                                                                                                                     192.168.2.5  <—VM Guest IP —> 192.168.2.11[/FONT]

```[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I believe this issues started after an update but I can not be sure as the majority of the time I am accessing the GUESTS and not the HOST.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]If I delete the ARP entry for 192.168.2.2 on pfSense I can then ping or ssh to 192.168.2.2 but this is only temporary and drops out again in a minute or less.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]However if I quickly ssh into 192.168.2.2 and then start pinging out to say 192.168.1.1 then the connection does not drop and I am able to accesses 192.168.2.2 as normal.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]I am at a loss and hope that someone will be provide assistance. [/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]FYI I had disabled ipv6 but have since enabled.

See attached file for system output and logs.  Tried to include in post but received error.

Thanks for your time.


[/FONT]

---

### Post by kingof1981 on 2020-04-08
i've almost the same problem om my virtual mashine's.

---

