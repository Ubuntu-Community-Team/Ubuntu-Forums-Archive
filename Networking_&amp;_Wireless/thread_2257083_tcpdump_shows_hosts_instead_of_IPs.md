---
title: "tcpdump shows hosts instead of IPs"
date: 2014-12-16
forum: Networking &amp; Wireless
---

### Post by chris137 on 2014-12-16
Hi,
I am trying to log every packet on a certain port to find out where the DoS-attacks I'm getting come from.
Yes, I already realized that could blow up my harddrive but that is not the problem yet.
With iptables I filed - not sure why but I got to tcpdump.
Sadly it shows the hostname instead of the IP. Used my ssh port as an example:
```
# tcpdump -w logwithout-n "port 2212"
# tcpdump -r logwithout-n
reading from file logwithout-n, link-type LINUX_SLL (Linux cooked)
22:57:33.313408 IP servers.domain.de.2212 > ip-my-ip.hsi06.unitymediagroup.de.49391: Flags [P.], seq 3926736771:3926736899, ack 3512811390, win 249, options [nop,nop,TS val 2585677185 ecr 1739531], length 128
22:57:33.323163 IP ip-my-ip.hsi06.unitymediagroup.de.49391 > servers.domain.de.2212: Flags [.], ack 128, win 1444, options [nop,nop,TS val 1739577 ecr 2585677185], length 0
22:57:37.412887 IP ip-my-ip.hsi06.unitymediagroup.de.49391 > servers.domain.de.2212: Flags [P.], seq 1:49, ack 128, win 1444, options [nop,nop,TS val 1740599 ecr 2585677185], length 48


# tcpdump -n -w logwith-n "port 2212"
# tcpdump -r logwith-n
reading from file logwith-n, link-type LINUX_SLL (Linux cooked)
22:57:23.605527 IP servers.domain.de.2212 > ip-my-ip.hsi06.unitymediagroup.de.49391: Flags [P.], seq 3926734707:3926734835, ack 3512809662, win 249, options [nop,nop,TS val 2585667477 ecr 1737110], length 128
22:57:23.615869 IP ip-my-ip.hsi06.unitymediagroup.de.49391 > servers.domain.de.2212: Flags [.], ack 128, win 1444, options [nop,nop,TS val 1737150 ecr 2585667477], length 0
22:57:27.351969 IP ip-my-ip.hsi06.unitymediagroup.de.49391 > servers.domain.2212: Flags [P.], seq 1:49, ack 128, win 1444, options [nop,nop,TS val 1738081 ecr 2585667477], length 48
```
As you can see the output is almost identical.
Did I use a wrong syntax (my first guess but could not find the error)?

---

### Post by Lars Noodén on 2014-12-17
You'll have to use the -n option when you display the output of the saved pcap file, instead.  The file only contains the unmodified packets, tcpdump decides how to display them.  So it is then when reading the file that you need to tell it not to look up the host names.  

```

tcpdump -n -r logwith-n

```

---

