---
title: "tracing package in network?"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by penguinKabuki on 2006-09-17
i have a print screen here..using the windows and ethereal because im in a lab in my university.

here i attach the print screen...
any one can help me?

question:
1)the ip address is 192.168.0.101?why?
2)in the packet 5,how large is the ip header?? The IP datagram? The TCP header? The TCP segment? can i have picture of the packet with each of these pieces identified?
3)In packet 11, we saw that actual portion of the packet that contained file data was 21 bytes long. Was this 21 bytes part of the Ethernet Frame? The IP datagram? The TCP segment? Why or why not?
4.	If we had wanted to use the “Limit packet to X bytes” option for this particular capture, what is the lowest we could set X to and still capture all the transport layer headers? All the application layer protocol messages? Explain your answer.
5.	What is the largest possible IP packet? (Hint: How big is the total length field in the IP header?) How did you determine this?
6.	Experiment with capturing traces using Limit packet to X bytes. What does Ethereal display look like if you truncate the packet in the middle of the IP header?

....i wonder~~~

---

### Post by tturrisi on 2006-09-18
study network basics, fundamentals & protocols:  (rtfm)
[http://www.ethereal.com/links.html](http://www.ethereal.com/links.html)

---

