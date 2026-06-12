---
title: "Searching through captured packets"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by hershey101 on 2008-06-19
Hi,
I am new at UNIX and programing in general and only have a basic knowledge of C++. I am helping out with some research at a college and was given the task to sort through captured packets via IP addresses. I was wondering if anyone could help me with writing a code which filters through pcap files by ip addresses and then records the timestamps. I know a few programs that do this type of thing such as WireShark but they take up too much memory when analyzing gigabytes of data and that is why I am looking to write a relatively simple code which just gets my task done and gathers data for me. Please email me at [email]hersh92@gmail.com[/email], any help is appreciated.

---

### Post by hershey101 on 2008-06-23
I have heard of Wireshark however there are several problems with that program since it takes up a lot of memory which makes it impossible to analyze large pcap files (I will be working with files upto a few hundred gigabytes) and it becomes too tedious when I am trying to find patterns using hundreds of different IP addresses. I was thinking something more along the lines of using a separate text file for the IP addresses and some how use the 'tcpdump -r myfile.pco -w out.pcap ip src "1.2.3.4"' command to make it so that it matches the IPs with the text file. Also I am only interested in the time stamps and don't require the rest of the details of the packets, so it would be helpful if I wrote a code which filters through the clutter and gives me only the time stamps.
Thank You

---

### Post by daRealScanMan on 2008-06-23
Why don't you post a few lines of the captures (sanitize if you like).  Something like this can easily be done with a scripting language like perl.

---

