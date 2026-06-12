---
title: "Writing a program that changes the port of all outgoing packets"
date: 2020-06-02
forum: Networking &amp; Wireless
---

### Post by traumatan on 2020-06-02
I started a side project to improve my networking and Linux skills. My goal is to write a client-server structure that tunnels packets out of an environment behind a proxy. Basically I want to encapsulate the packets with a header that lets them pass through the proxy.
 

 Client:  
 
[LIST=1]
[*]All outgoing packets are caught     before they hit the network 
[*]The port number is changed to 80     or 443 and the destionation IP is changed to the server
(Actual     port and actual port are stored somewhere in the package, so     bascially the package is encapsulated) 
[*]The packet is sent out to the     server 
[/LIST]
 

 Server:
 
[LIST=1]
[*]Packets from the client are     received 
[*]The encapsulation is removed and     the real port and destionation address are restored 
[*]The packet is sent out to the real     destination 
[*]Incoming responses are     encapsulated with with port 80/443 and sent back to the client 
[/LIST]
 

 So far, I have created a small C program and integrated it with "insmod". The packets are caught with "nf_register_net_hook" and I can either drop or accept them but I have trouble progressing from here.  

 

 Questions:
 
[LIST=1]
[*]What exactly is this ```
***skb     structure**
``` As far as I know it is a representation of the packet,     but I can not find a good documentation about how to handle it. I     tried

     ```
**struct iphdr *ip_header =     (struct iphdr *)skb_network_header(skb); **
```
But I do not     understand the output. 
[*]Are there introductory guides or     programming examples about how to work with Netfilter and especially     with libnetfilter_queue ? 
[*]I am not proficient with C. Is it     feasible to get the the packets into Python and put them back into     the Linux packet stack somehow? 
[/LIST]

---

### Post by TheFu on 2020-06-05
I'm struggling as to whether I should reply or not.  Exfiltration of data from a network that is obviously secured has a number of solutions.  For non-enterprise firewalls, it is a solved problem, mostly.  

I don't know the answers to your specific questions.

I don't know python.  Anything can be done in C, however. Programming at this level would need to be accomplished in C to ensure it isn't slow.  IMHO.

C functions and structures are in the manpages on any Unix system installed with C dev tools.  If you need more, *use the source Luke.*  Start under /usr/include with egrep/fgrep and find the header files with the structures. Often those will have developer comments. It is common to need to follow header files a few levels to finally get to the structure.

```
struct iphdr *ip_header
```
is a pointer that points at a specific type of structure, iphdr.  That's pretty clear. If that isn't understood, learn more about C structures and pointers.  Structures are relatively easy. Does python call them dictionaries?  IDK. I don't think python has pointers.  That's too bad, if true.  Pointers are extremely powerful.

There are Advanced Unix Network Programming books that cover all sorts of C/S and IPC and MT programming methods.  The ones I own are all in C.
[https://arstechnica.com/gadgets/2019/12/how-to-set-up-your-own-nebula-mesh-vpn-step-by-step/](https://arstechnica.com/gadgets/2019/12/how-to-set-up-your-own-nebula-mesh-vpn-step-by-step/) can proved some projects that accomplish what you seek, I believe.

BTW, pretty much **any** programming question here from bash to C to Client/Server architecture should be put into the Programming/Developer sub-forum. I'd guess the forums are 95% end-users, 4% admins and 1% programmers.

---

