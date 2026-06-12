---
title: "No response to some SYN packets when timestamps are enabled"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by andrew-n1by9anq9 on 2014-03-20
I have a TCP server listening on a machine ("the server") running 12.04.3 (3.8.0-31-generic). It receives connections from 2 different client machines. Machine A is running 12.04.4 (3.11.0-17-generic) and machine B is running 11.10 (3.0.0-32-server).

If TCP timestamps are enabled on the server (sysctl net.ipv4.tcp_timestamps) then sometimes SYN packets from machine A are ignored by the server. Using tcpdump on the server (in non promiscuous mode) I can see they arrive OK and with correct checksumss - there is just no response - no SYN/ACK and no RST. Machine A retries a number of times before giving up. The client software running on machine A (wget in this case) immediately retries and succeeds.

Machine B has no problems with the same server and all looks normal - it is using the same TCP options as machine A from what I can see from the capture files. Disabling TCP timestamps on the server makes everything work as expected, including from machine A. The timestamps in the ignored SYN packets seem to be valid to me however.

I attach an (anonymised) PCAP (in a tar archive so the forum software accepts it). It was taken on the server (10.76.0.74) showing machine A (10.4.0.76) successfully performing an HTTP GET (packets 1 to 10) and then 1 second later trying to fetch the same URL again (packets 11 to 17) but instead has its SYNs ignored. Packets 18 to 27 is another success.

Whilst disabling timestamps is a workaround I would like to understand what is going on. There is no local firewall running. The server handles quite a few TCP connections (approx 32K at any one time) but has plenty of free memory/CPU. There is no sign that the server application's accept queue is suddenly filling up (besides which that should affect both clients).

---

