---
title: "Wired network problems - reverting to Automatic DHCP"
date: 2024-01-13
forum: Networking &amp; Wireless
---

### Post by SreckoMicic on 2024-01-13
I am having problems with fresh Ubuntu 23.10 install and wired network. Was out of Linux world for a year. Purchased new workstation, want to have Ubuntu but Ubuntu does not want me :D

So I have  network were I have 2 windows machines and will have this new workstation. Previous workstation, had 22.04, and  everything was working fine if I setup manually DNS ipv4. Unfortunately this does not work with 23,10, cause every time I setup DNS manually when I hit Apply it will revert to Automatic and will not be able to connect to network. 

Anyone experienced this?

---

### Post by Doug S on 2024-01-13
Show us what you are doing. Show us the configuration files you are creating/editing. Show us the actual command(s) you are using.

---

### Post by SeijiSensei on 2024-01-13
On modern systems that use systemd, DNS resolution is handled by the systemd-resolved daemon. It's configuration file is /etc/systemd/resolved.conf. Put any static DNS server addresses in the "DNS=" and "Fallback=" lines, then reboot.

---

### Post by SreckoMicic on 2024-01-16
Here is the video showing what I am doing., it is Ubuntu 23.10.

[https://drive.google.com/file/d/1XkIXCYv0t4VOFL-aUk9jNA4qEwtF6MKa/view?usp=sharing]("https://drive.google.com/file/d/1XkIXCYv0t4VOFL-aUk9jNA4qEwtF6MKa/view?usp=sharing")

So when I setup IP address and Subnet it will connect immediately, but it will Reset setting back to Automatic DHCP. So if you disable and enable it will not connect. Same if you reset or log out. It just does not keep setting.

---

