---
title: "quick networking / samba question / interface priority"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by Underpants on 2007-01-13
I've been using this command for some time to mount my windows share:

```

sudo smbmount //bluebox/bluebox-data /home/aaron/Desktop/bluebox-data -o credentials=/home/aaron/.smbpasswd,uid=aaron 0 0

```

I've started to get this error

```

Packet send failed to 192.168.97.255(137) ERRNO=Operation not permitted
5135: Connection to bluebox failed
SMB connection failed

```

It looks like it's trying to find "bluebox" (my server) through my vmware interface instead of eth0 which is my physical network card. 

I'm not sure what changed. I've had vmware running for a long time and never had that issue before. I'm sure there's a way to change what adapter is used first. If I change "bluebox" to "192.168.1.10" everything works fine. 

How do I change that?

---

