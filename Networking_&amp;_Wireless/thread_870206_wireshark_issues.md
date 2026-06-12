---
title: "wireshark issues"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by e24ohm on 2008-07-25
forum,
I installed wireshark from Add/Remove, but I am unable to get my nic to show up in the Interface drop down menu.

any help, because i am not sure what i should do to even begin to troubleshoot this issue.

Thank you
E

---

### Post by agenthex on 2009-03-16
You must run wireshark as root.

gksu wireshark

It will warn you that you are running as root, but I don't see my interfaces if I'm running as a limited user.

---

### Post by jonobr on 2009-03-16
agenthex is right about having to run wireshark as root, but just FYI  you could also run the trace in terminal and open using wireshark

```
sudo tcpdump -w file.pcap -s 1600 -i eth0 
```
where
-w creates a file wireshark can read
-s sets the packet capture size
-i defines the interface to trace
and you could also define the port number you want to capture

like so
```
sudo tcpdump -w file.pcap -s 1600 -i eth0 port 25
```

this example will capture all SMTP traffic and create in a file called file.pcap and place it in the current directory.,

---

