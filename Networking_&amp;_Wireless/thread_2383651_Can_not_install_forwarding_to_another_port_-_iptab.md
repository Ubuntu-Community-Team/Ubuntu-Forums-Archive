---
title: "Can not install forwarding to another port - iptables"
date: 2018-01-28
forum: Networking &amp; Wireless
---

### Post by otto58 on 2018-01-28
I try to reach my controller (running at port 8443) in a Google Cloud from outside port 443.

```

sudo iptables -I INPUT 1 -p tcp --dport 8443 -j ACCEPT
sudo iptables -I INPUT 1 -p tcp --dport 443 -j ACCEPT
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 443 -j REDIRECT --to-port 8443

```

But is does not work and I found no information about the forwarding

```

otto_cloud@neu2701:~$ sudo iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:443
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:8443
sshguard   all  --  0.0.0.0/0            0.0.0.0/0           
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
Chain sshguard (1 references)
target     prot opt source               destination         
otto_cloud@neu2701:~$ 

```

Sorry but my Linux knowledge is very limited.

---

### Post by SeijiSensei on 2018-01-28
To see the NAT table us :
```
sudo iptables -t nat -L -nv
```

Where are these rules running? Your setup isn't really clear. Are you trying to redirect outbound traffic to port 443?

---

### Post by otto58 on 2018-01-28
[SIZE=2]Thanks, I can see the prerouting rule now.
But it does not work:

[FONT=arial]The running situation is an unifi controller in a Google Cloud instance Ubuntu 17.10.
[https://help.ubnt.com/hc/en-us/articles/218506997-UniFi-Ports-Used](https://help.ubnt.com/hc/en-us/articles/218506997-UniFi-Ports-Used)
The controller needs open ports, which I have opened in the Google Cloud firewall: 
[/FONT][/SIZE][FONT=arial][SIZE=2]tcp:8880[/SIZE]
[SIZE=2]tcp:8443[/SIZE]
[SIZE=2]tcp:8843[/SIZE]
[SIZE=2]tcp:8080[/SIZE]
[SIZE=2]tcp:6789[/SIZE]
[/FONT][FONT=Roboto][FONT=inherit][FONT=inherit][SIZE=2][FONT=arial]udp:3478
I can reach the controller at [https://my-ip:8443](https://my-ip:8443) and all works fine.

But I want reach the controller at [https://my-ip](https://my-ip) 
Google Cloud firewall is additional opened at tcp:443. [/FONT]

[/SIZE][/FONT][/FONT][/FONT]

---

### Post by SeijiSensei on 2018-01-28
Hmm.  I use a nearly-identical rule to redirect traffic on a gateway router so that HTTP traffic goes through a Squid proxy listening on port 3128.  However this is on the browsing side of the connection, not the server end, which is what I think you want. 

Based on the rules I use to forward traffic arriving on a server to a machine behind it, you might try something like this:
```
/sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 443 -j DNAT --to-destination localhost:8443
```
Make sure the process listens on 127.0.0.1:8443 as well as on eth0.  I'm not sure this will work, but you can give it a try.

You might also want to check and make sure that packet forwarding is enabled in the kernel.  Edit /etc/sysctl.conf and remove the hash mark from the front of the line reading
```
net.ipv4.ip_forward=1
```
then reboot.

---

### Post by linuchsan on 2018-01-28
Can you post: **iptables -L -n -v**
When you have edit **/etc/sysctl.conf**  to set **net.ipv4.ip_forward** to **1** , there is no restart necessary. **sysctl --system** is sufficient.

---

### Post by linuchsan on 2018-01-28
Oeps...you did a  iptables -L -n. I don't see a iptables FORWARD rule.

---

### Post by SeijiSensei on 2018-01-28
He has a default ACCEPT policy for the FORWARD chain.

---

### Post by otto58 on 2018-01-29
Thanks!
But I have no access at [https://my-IP](https://my-IP)
Please have a look at that, if have done:

```

otto_cloud@n2901:~$ [B]sudo iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 443 -j DNAT --to-destination 127.0.0.1:8443
[/B]
otto_cloud@n2901:~$ [B]sudo nano /etc/sysctl.conf 
[/B]
otto_cloud@n2901:~$ **sudo sysctl --system**
* Applying /etc/sysctl.d/10-console-messages.conf ...
kernel.printk = 4 4 1 7
* Applying /etc/sysctl.d/10-ipv6-privacy.conf ...
net.ipv6.conf.all.use_tempaddr = 2
net.ipv6.conf.default.use_tempaddr = 2
* Applying /etc/sysctl.d/10-kernel-hardening.conf ...
kernel.kptr_restrict = 1
* Applying /etc/sysctl.d/10-link-restrictions.conf ...
fs.protected_hardlinks = 1
fs.protected_symlinks = 1
* Applying /etc/sysctl.d/10-lxd-inotify.conf ...
fs.inotify.max_user_instances = 1024
* Applying /etc/sysctl.d/10-magic-sysrq.conf ...
kernel.sysrq = 176
* Applying /etc/sysctl.d/10-network-security.conf ...
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.tcp_syncookies = 1
* Applying /etc/sysctl.d/10-ptrace.conf ...
kernel.yama.ptrace_scope = 1
* Applying /etc/sysctl.d/10-zeropage.conf ...
vm.mmap_min_addr = 65536
* Applying /etc/sysctl.d/11-gce-network-security.conf ...
net.ipv4.tcp_syncookies = 1
net.ipv4.conf.all.accept_source_route = 0
net.ipv4.conf.default.accept_source_route = 0
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0
net.ipv4.conf.all.secure_redirects = 1
net.ipv4.conf.default.secure_redirects = 1
net.ipv4.ip_forward = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_ignore_bogus_error_responses = 1
net.ipv4.conf.all.log_martians = 1
net.ipv4.conf.default.log_martians = 1
net.ipv4.tcp_rfc1337 = 1
kernel.randomize_va_space = 2
kernel.panic = 10
* Applying /etc/sysctl.d/99-cloudimg-ipv6.conf ...
net.ipv6.conf.all.use_tempaddr = 0
net.ipv6.conf.default.use_tempaddr = 0
* Applying /etc/sysctl.d/99-gce.conf ...
vm.mmap_min_addr = 65536
net.ipv4.tcp_syncookies = 1
net.ipv4.conf.all.accept_source_route = 0
net.ipv4.conf.default.accept_source_route = 0
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0
net.ipv4.conf.all.secure_redirects = 1
net.ipv4.conf.default.secure_redirects = 1
net.ipv4.ip_forward = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_ignore_bogus_error_responses = 1
net.ipv4.conf.all.log_martians = 1
net.ipv4.conf.default.log_martians = 1
net.ipv4.tcp_rfc1337 = 1
kernel.randomize_va_space = 2
fs.protected_hardlinks = 1
fs.protected_symlinks = 1
kernel.kptr_restrict = 1
kernel.yama.ptrace_scope = 1
kernel.perf_event_paranoid = 2
* Applying /etc/sysctl.d/99-sysctl.conf ...
net.ipv4.ip_forward = 1
* Applying /etc/sysctl.conf ...
net.ipv4.ip_forward = 1

otto_cloud@n2901:~$ **sudo iptables -L -n -v**
Chain INPUT (policy ACCEPT 599 packets, 293K bytes)
 pkts bytes target     prot opt in     out     source               destination         
  599  293K sshguard   all  --  *      *       0.0.0.0/0            0.0.0.0/0           
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
Chain OUTPUT (policy ACCEPT 516 packets, 71576 bytes)
 pkts bytes target     prot opt in     out     source               destination         
Chain sshguard (1 references)
 pkts bytes target     prot opt in     out     source               destination 
        
otto_cloud@n2901:~$ **sudo iptables -t nat -L -nv**
Chain PREROUTING (policy ACCEPT 4 packets, 3877 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DNAT       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:443 to:127.0.0.1:8443
Chain INPUT (policy ACCEPT 4 packets, 3877 bytes)
 pkts bytes target     prot opt in     out     source               destination         
Chain OUTPUT (policy ACCEPT 22 packets, 1733 bytes)
 pkts bytes target     prot opt in     out     source               destination         
Chain POSTROUTING (policy ACCEPT 22 packets, 1733 bytes)
 pkts bytes target     prot opt in     out     source               destination         
otto_cloud@n2901:~$ 


```

---

### Post by SeijiSensei on 2018-01-30
Try removing "-i eth0" and let the rule apply to all traffic for now.  Any better?

The iptables report shows that no packets met the rule, so you need to play with the rule's parameters until you get them to match what you want.

---

### Post by otto58 on 2018-01-30
Thanks I have tryed it, but I get furthermore no answer.


```

otto_cloud@n2901:~$ **sudo iptables -L -n -v**
Chain INPUT (policy ACCEPT 74816 packets, 19M bytes)
 pkts bytes target     prot opt in     out     source               destination         
 231K  194M sshguard   all  --  *      *       0.0.0.0/0            0.0.0.0/0           
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
Chain OUTPUT (policy ACCEPT 73734 packets, 17M bytes)
 pkts bytes target     prot opt in     out     source               destination         
Chain sshguard (1 references)
 pkts bytes target     prot opt in     out     source               destination         

otto_cloud@n2901:~$ **sudo iptables -t nat -L -nv**
Chain PREROUTING (policy ACCEPT 19 packets, 1044 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DNAT       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:443 to:127.0.0.1:8443
  110  5720 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:443 to:127.0.0.1:8443
Chain INPUT (policy ACCEPT 19 packets, 1044 bytes)
 pkts bytes target     prot opt in     out     source               destination         
Chain OUTPUT (policy ACCEPT 40 packets, 2859 bytes)
 pkts bytes target     prot opt in     out     source               destination         
Chain POSTROUTING (policy ACCEPT 40 packets, 2859 bytes)
 pkts bytes target     prot opt in     out     source               destination         
otto_cloud@n2901:~$ 

```

 I saw eth0 days ago, but that must have changed.

```

otto_cloud@n2901:~$** ifconfig**
ens4: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1460
        inet 10.142.0.2  netmask 255.255.255.255  broadcast 10.142.0.2
        inet6 fe80::4001:aff:fe8e:2  prefixlen 64  scopeid 0x20<link>
        ether 42:01:0a:8e:00:02  txqueuelen 1000  (Ethernet)
        RX packets 71011  bytes 154129987 (154.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 36032  bytes 4011527 (4.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 168911  bytes 42286439 (42.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 168911  bytes 42286439 (42.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
otto_cloud@n2901:~$ 

```

How can I delete iptables rules?

---

### Post by SeijiSensei on 2018-02-02
```
sudo iptables -F CHAIN
```

For instance

```
sudo iptables -F INPUT
```

flushes the rules in the INPUT chain.

---

