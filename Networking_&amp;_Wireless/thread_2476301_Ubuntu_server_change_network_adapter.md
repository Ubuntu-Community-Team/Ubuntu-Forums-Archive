---
title: "Ubuntu server change network adapter"
date: 2022-06-22
forum: Networking &amp; Wireless
---

### Post by betalabs on 2022-06-22
Hi i use Ubuntu server 20.04.transfer the hdd in one new pc.ubuntu boot ok but  network not working.how to configure new network adapter ???.

---

### Post by TheFu on 2022-06-23
Use the netplan YAML file.
What likely happened was the NIC name changed, so you just need to find where the device is in that file and use the new ethernet device name.

The **ip addr** will show all the recognized devices.  They are usually numbered.
```
1: lo: <LOOPBACK,UP,LOWER_UP> ......
2: **ens3**: <BROADCAST,MULTICAST,UP,LOWER_UP .....

```
So, my /etc/netplan/01-ens3-static.yaml file has this:

```
network:
  version: 2
  renderer: networkd
  ethernets:
     **ens3:**
       addresses:
          - 172.22.22.3/24
       dhcp4: false
       dhcp6: false
       gateway4: 172.22.22.1
       nameservers:
         addresses: [ "172.22.22.80","172.22.22.81" ]
         search: [mydomain.lan,mydomain.com]

```
Yours will be different. Don't worry too much about the filename, just the directory matters. I like to name the file with the settings for a specific adapter just for documentation.
If you get stuck, post the yaml file wrapped in forum code tags (like I've done), since without the proper indentation yaml doesn't work. Without code tags, we can't tell anything.

Also, use **sudoedit** to edit system files. It is the safest way and honors the EDITOR environment variable, so any editor can be used.

---

