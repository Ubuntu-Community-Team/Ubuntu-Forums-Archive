---
title: "ettercap and SSL.. iptable problem?"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by boojah on 2007-05-11
I've been messing around trying to make ettercap to sniff up my hotmail password. This is what i've done so far. i edit etter.conf to open up these commands by removing #

> #redir_command_on = "iptables -t nat -A PREROUTING -i %iface -p tcp --dport %port -j REDIRECT --to-port %rport"
#redir_command_off = "iptables -t nat -D PREROUTING -i %iface -p tcp --dport %port -j REDIRECT --to-port %rport"

now when i try to do an arp poison in -C , no packages seems to be forwardet (same in GTK)
when i try to run the chk_poison plugin ettercap crash and gives me this message

> ERROR : 1,  Operation not permitted
[ec_send.c:send_L3_icmp_echo:513]
 
 libnet_write(-1): libnet_write_raw_ipv4(): -1 bytes written (Operation not permitted)


but when i type command in the console

       ```
ettercap -T -q -i eth0 -M arp:remote /victim/ /router/
```

it seems packages is being forwarded... only problem is that when i try to log in to my hotmail on the victim host it wont connect. I get this message in the terminal:

> SEND L3 ERROR: 48 byte packet (0800:06) destined to XXX.XXX.XXX.XXX was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Operation not permitted)

(where XXX.XXX.XXX.XXX is the destination IP address off course)

I was wondering if someone has a solution to this, or where the problem might be. I have no idea what libnet_write_raw_ipv4 does, but i assume it has something to do with iptables?

Thanks for any help i can get.

---

### Post by Tex-Twil on 2007-08-14
Hello,
I have the same problem with Ettercap. Also when I quit Ettercap I got the followong errors several times

```

iptables v1.3.6: can't initialize iptables table `nat': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.

```

I've seen many people with this problem over different forums but I can't find the solution. 

Any ideas ? thanks

---

### Post by Tex-Twil on 2007-08-17
nobody ?

---

### Post by ioxer on 2007-09-10
Hmmm... Are you running "sudo ettercap [options]" or just "ettercap [options]". Try using "sudo" if you aren't.

---

### Post by Tex-Twil on 2007-09-10
Hi,
yes I'm.

Acrtually I solved the problem. I had to change the uid guid to 0 in the /etc/etter/conf file.

I also hap problem with ip forwarding with ettercap. The solution was to enable forwarding **once ettercap started**

> 
echo "1" > /proc/sys/net/ipv4/ip_forward


cheers

---

