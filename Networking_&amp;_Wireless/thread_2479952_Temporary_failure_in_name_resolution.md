---
title: "Temporary failure in name resolution"
date: 2022-10-13
forum: Networking &amp; Wireless
---

### Post by turtley-linux on 2022-10-13
Hello,
I had Ubuntu Server running as a web server on one PC which I  recently switched for another. I simply transferred the hard drive.  However, now I am having trouble doing anything that has to do with it  accessing the internet. I tested out a ping and got the message  'Temporary failure in name resolution". I have tried things like editing  the remov.conf file to nameserver 8.8.8.8, changing its permissions,  restarting the systemd-resolved service, and checking the status of it.  Nothing seems to be working. I was wondering what else I might be able  to try? Sorry for my incompetence when it comes to the command line.
Thanks in advance.

---

### Post by TheFu on 2022-10-14
The server network configuration is tied to the NICs in the machine, which are likely different brands and different models.  Each model can have a different kernel driver, which creates a different device name.  So, if the device in the old system was named ens0 and in the new system, it is named emp0, those aren't the same and the network configuration needs to be changed for the new name.  Until that is fixed, it won't work.

Networking on servers has changed drastically the last few LTS releases and since you didn't provide any release or hardware information, I won't guess at a solution.

---

### Post by chili555 on 2022-10-14
Please run and post:

```
ip a
cat /etc/netplan/*.yaml
ls -al /etc/resolv.conf
```

---

### Post by turtley-linux on 2022-10-14
I apologise for not including more information in the original post.  That makes sense about needing to change the network configuration in a  different system. I am running 20.04LTS. I ran the commands; sorry for  the bad picture.
Thanks

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291131&stc=1[/IMG]

---

### Post by chili555 on 2022-10-14
Your ethernet interface is eno1. Your netplan file refers to enp2s0. Edit your netplan file to manage eno1, reboot and you should be all set.

---

### Post by turtley-linux on 2022-10-14
I think I changed it correctly and rebooted but I still seem to not be able to get it working?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291132&stc=1[/IMG]

---

### Post by TheFu on 2022-10-14
Can you ping 8.8.8.8?
If not, it is an internet problem. Troubleshoot that. Check the routing table.
If you can ping it, then it is a DNS settings issue.  I ripped out the default way that Ubuntu runs a caching DNS locally due to issues to avoid that. There's no need if you have a local DNS. Someone else can help, perhaps, with the local caching DNS, perhaps.  Let us know which ping works and doesn't work.

BTW, servers should have static IPs.  There are many reasons these should be set manually in the netplan.yaml file.

---

### Post by turtley-linux on 2022-10-14
Thank you, that is good to know about the static IPs. I will work on configuring that. However, I am unable to ping 8.8.8.8. I am confused with where the issue would be, though, because the connection up to the server seems to work. I tried plugging the Ethernet cable into another computer with the same connections and all, and I am using it to send this message. You mention checking the routing table, but none of the commands work. "ip route" gives me a blank, and "netstat -rn" and "route -n" tell me that I have to install net-tools, which I cannot because I can't access the internet on the server to download the file.

---

### Post by chili555 on 2022-10-15
I suggest that you fine-tune your netplan file a bit:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: true

```Also, your file says en01 (E N zero one) but the system reports that your interface is eno1 (E N O one).

Follow with:

```
sudo netplan generate 
sudo netplan apply
```Did you get an IP address?

```
ip a
```

Are you connected?

```
ping -c3 www.ubuntu.com
```

---

### Post by TheFu on 2022-10-15
In post #2 above, I suggested that the wrong device name was being used.  Details matter as Chili points out, 

eno1 != en01

Fix that and it is 90% likely you'll have internet.
route and ifconfig commands haven't been maintained since 2011. They've been replaced by 'ip' commands, so you should learn to use those instead. There are 1-for-1 replacements and most provide the same or more information.  There are many extra options available now too, which makes scripting easier.

---

### Post by turtley-linux on 2022-10-15
Yes, thank you so very much for both of your help. I would have never figured it out. That worked! I also missed the difference between eno1 and en01. Now I will worked on configuring the static IP. I probably will run into many more hiccups (certificates, vhost, etc.) because the server has not been up and running for a while. :eek:

---

### Post by chili555 on 2022-10-15
> Now I will worked on configuring the static IP. Please see the template here:

```
cat /usr/share/doc/netplan/examples/static.yaml
```Please post a new question if you get stuck and need a step-by-step. Also, please be certain to select an address outside of the DHCP pool in the router.

Glad it's working!

---

