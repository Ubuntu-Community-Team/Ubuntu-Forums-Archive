---
title: "persisten route via Network interface settings dialog box"
date: 2023-02-20
forum: Networking &amp; Wireless
---

### Post by kent2612 on 2023-02-20
When configuring Static IP address or static route on Ubuntu Desktop  via Network interface settings dialog box, where can I see this exact  change on the files as I notice there is no change to  '01-network-manager-all.yaml' file at all?

kent@ubuntu:/etc/netplan$ cat 01-network-manager-all.yaml 
# Let NetworkManager manage all devices on this system
network:
    version: 2

    renderer: NetworkManager

Also /etc/network/interfaces is no longer available, as shown below:
kent@ubuntu:/etc/network$ ls -la
total 32
drwxr-xr-x   6 root root  4096 Aug  1  2020 .
drwxr-xr-x 134 root root 12288 Feb 20 13:37 ..
drwxr-xr-x   2 root root  4096 Mar 26  2022 if-down.d
drwxr-xr-x   2 root root  4096 Jul  9  2021 if-post-down.d
drwxr-xr-x   2 root root  4096 Mar  5  2021 if-pre-up.d
drwxr-xr-x   2 root root  4096 Mar 26  2022 if-up.d

---

