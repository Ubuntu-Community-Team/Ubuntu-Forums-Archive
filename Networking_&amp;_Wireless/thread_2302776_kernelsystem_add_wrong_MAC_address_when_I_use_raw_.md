---
title: "kernel/system add wrong MAC address when I use raw socket to send IP packets"
date: 2015-11-13
forum: Networking &amp; Wireless
---

### Post by esolve3 on 2015-11-13
I have three laptops in a WLAN, A and C uses wlan0, but B is connected to wirelss router via cable and it uses eth0.


I wrote a C program to do TCP hijacking experiment. And then modified it to C++ program. 


      1) A establishes a TCP connection with B 
      2) C runs the program and masquerade as B, so it sends out packets with src_ip = IP(B) and dst_ip = IP(A)
      3) I use tcpdump to capture packets on A,B,C
      4) it is expected that tcpdump on A can capture the IP spoofing packets. With the original C program, it is the case. But when I run C++ program, it is strange that tcpdump on B captures the packets but tcpdump on A can't. 


after some investigation, I notice it is due to the MAC address. When the C++ program ran, the kernel/system adds the MAC address of B as destination MAC to the IP-spoofing packets(it is expected that the kernel adds the MAC address of A coz the destination IP is of A). However, I wrote packets on IP level and I use raw socket as below in both C program and C++ program:


    send_sd = socket(AF_INET, SOCK_RAW, IPPROTO_RAW));
    ...
    sendto(send_sd, packet, ip_len, 0, (struct sockaddr*)&client_addr, addr_len);




so it is strange that when I ran these two programs, the kernel/system added different destination MAC addresses, what are potential causes?

---

