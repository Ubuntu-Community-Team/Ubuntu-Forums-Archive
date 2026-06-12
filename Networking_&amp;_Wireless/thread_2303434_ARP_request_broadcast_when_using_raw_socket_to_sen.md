---
title: "ARP request broadcast when using raw socket to send raw IP packets with sendto"
date: 2015-11-18
forum: Networking &amp; Wireless
---

### Post by esolve3 on 2015-11-18
First, let me describe the problem briefly. I have to programs which send IP packets from a host(192.168.0.101) to another host(192.168.0.106). These two programs are written respectively with C and C++ but have the same functionalities. 


If I run the C program, when a raw socket is going to send IP packets (the program makes the IP packet without MAC/Ethernet header) with destination IP of 192.168.0.106, from tcpdump-captured packets, I notice the host broadcast an ARP query for the MAC of 192.168.0.106, and so it can successfully deliver the packets to that host.


If I run the C++ program, it doesn't broadcast ARP to query for the MAC of 192.168.0.106 and it add a wrong MAC header to the IP packets and thus develiver it to the wrong host(which is also communicating with the host 192.168.0.101 in both C program and C++ program scenarios ) 


** I'm really puzzled by the fact that ARP broadcast happens in the first scenario but not in the second scenario, are there any potential reasons for such difference? **




------------------------
** Long story: **


I have three laptops in a WLAN, A and C uses wlan0, but B is connected to the wireless router via cable, and it uses eth0.


I wrote a C program to do a TCP hijacking experiment, and then modified it to C++ program. 


 1. A establishes a TCP connection with B
 2. C runs the program and masquerades as B, so it sends out packets with
    src_ip = IP(B) and dst_ip = IP(A)
 3. I use tcpdump to capture packets on A, B, and C
 4. It is expected that tcpdump on A can capture the IP spoofing
    packets. With the original C program, this is the case. But when I run the
    C++ program, it is strange that tcpdump on B captures the packets
    but tcpdump on A can't.


After some investigation, I noticed it is due to the MAC address. When the C++ program ran, the kernel/system adds the MAC address of B as destination MAC to the IP-spoofing packets (it is expected that the kernel adds the MAC address of A because the destination IP address is of A). However, I wrote packets on IP level and I used a raw socket as below in both C program and C++ program:


    send_sd = socket(AF_INET, SOCK_RAW, IPPROTO_RAW));
    ...
    sendto(send_sd, packet, ip_len, 0, (struct sockaddr*)&client_addr, addr_len);




It is strange that when I ran these two programs, the kernel/system added different destination MAC addresses. What are the potential causes?

---

