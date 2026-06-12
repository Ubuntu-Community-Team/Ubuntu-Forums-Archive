---
title: "mount.nfs: mount system call failed"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by Unewbeginner on 2011-01-11
Hello everyone. I'm trying nfs mount but I keep getting the same error message:

```
mount.nfs: mount system call failed
```

I searched in this forum but can't get my answer.

My /etc/exports on server:

```
/share 192.168.1.3(rw,sync)
```

I created /share folder on server and client machine. The hostname for the server is "server".

I execute the command below on my client machine:

```
sudo mount server:/share /share
```

but I just got the error message. Anyone knows how to handle it? Thanks!

---

### Post by Unewbeginner on 2011-01-11
please help......

---

### Post by dysentry on 2011-01-11
on your server type:
showmount -e



on your client type:
showmount -e <server ip address>


show us the outputs.

---

### Post by Unewbeginner on 2011-01-12
On my server (IP addr: 192.168.1.6, hostname: server)

```
showmount -e
Export list for server:
/share .168.1.3
```

On my client (IP addr: 192.168.1.3)
```

showmount -e 192.168.1.6
Export list for 192.168.1.6:
/share 192.168.1.3
```

---

### Post by mikechant on 2011-01-12
Just checking, have you done the following:
1/ Installed nfs-kernel-server, nfs-common, portmap on the server
2/ Installed nfs-common, portmap on the client
3/ Rebooted after 1/ + 2/ to ensure all services running (or restarted the services)
4/ Configured your router to allow all local traffic through
5/ Tried mounting with IP address specified instead of domain name

Probably all obvious apart from maybe 5/ but I don't if you've ever had this working before or if it's your first go with nfs.

---

### Post by Unewbeginner on 2011-01-13
thanks mikechant. I changed my server name to IP address and it worked well. But could you let me know why the name doesn't work in my case?

---

### Post by mikechant on 2011-01-16
> But could you let me know why the name doesn't work in my case? 

Unfortunately I can't help with this problem. In my local network setup, I've got my router configured to give a fixed IP address for my NFS server PC (still using DHCP but with a table mapping MAC address to IP) so I always use this IP address for NFS mounts.

I've searched around a bit but I can't see anything obvious to help you with this.

---

### Post by Zill on 2011-01-16
> **Unewbeginner said:**
> thanks mikechant. I changed my server name to IP address and it worked well. But could you let me know why the name doesn't work in my case?
I suggest you ensure your server /etc/hosts file is edited to include this information. eg.
```
127.0.0.1	localhost
127.0.1.1	my_server_name

# List other LAN PCs here
192.168.0.4	my_client_name_1
192.168.0.5	my_client_name_2
192.168.0.6	my_client_name_3
```
As I find NFS/portmap client/server configuration confusing, I tend to use "mirror" config files thoughout my LAN so that all PCs can share info both ways.  I also stick to using fixed IP addresses, rather than names.  With this method, everything "just works" :-)
[URL="https://help.ubuntu.com/community/SettingUpNFSHowTo"]
SettingUpNFSHowTo[/URL]
[hosts - The static table lookup for hostnames]("http://manpages.ubuntu.com/manpages/lucid/en/man5/hosts.5.html")

---

