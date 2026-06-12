---
title: "Searching for Network Devices by IP address and Manufacture"
date: 2023-11-25
forum: Networking &amp; Wireless
---

### Post by josiahb1 on 2023-11-25
Hi, I'm wondering if there is any suggestions for searching for what devices are connected on a network.  I know there is the arp command but it only shows current traffic to the computer where the command was sent. In windows I have used programs like Belarc Advisor or Advanced IP Scanner.  I'm wondering what commands or applications Linux has and what IT administrators like to use.  Thanks

---

### Post by Morbius1 on 2023-11-25
Angry IP Scanner sorta kinda looks and acts like Advanced IP Scanner.

You will need to download and install the *.deb file: [https://angryip.org/](https://angryip.org/)

---

### Post by SeijiSensei on 2023-11-25
We installed Nagios at a client site. Worked fine for what we needed. Here are other options:

[https://www.comparitech.com/net-admin/open-source-network-monitoring-tools/](https://www.comparitech.com/net-admin/open-source-network-monitoring-tools/)

However, if you just want something fast and quick, [**nmap**]("https://nmap.org/") is the product for you.

You can do a ping scan ("-sP") that also collects other information about the connected devices. The "-n" switch tells nmap not to try and resolve IP addresses to hostnames.

```

$ sudo nmap -sP -n 192.168.100.0/24
Starting Nmap 7.93 ( https://nmap.org ) at 2023-11-25 14:37 EST
Nmap scan report for 192.168.100.1
Host is up (0.0067s latency).
MAC Address: 50:EB:F6:11:2D:00 (Asustek Computer)
Nmap scan report for 192.168.100.5
Host is up (0.0073s latency).
MAC Address: 30:05:5C:43:BC:B3 (Brother industries)
Nmap scan report for 192.168.100.27
Host is up (0.088s latency).
MAC Address: D0:73:D5:36:96:4C (Lifi Labs Management)
Nmap scan report for 192.168.100.36
Host is up (0.017s latency).
[etc.]

```

Trinity uses nmap in The Matrix so you know it must be good!

---

