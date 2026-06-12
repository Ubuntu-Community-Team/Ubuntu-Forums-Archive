---
title: "Question on a company whos hacking people"
date: 2019-08-04
forum: Networking &amp; Wireless
---

### Post by kidsusukigsxr on 2019-08-04
Hi everyone, My background is in computers.  I'm new to Ubuntu and new to the community.  Unfortunately I have a strange question about a company.  Any assistance would be appreciated.  I'm hoping you network guys can shed some light, was I hacked or is this a new method of the internet working in is topology?????? 

After install and using Ubuntu for a few months now, I began having network problems with slow internet connections, etc.   

I began checking do speed test and checking my router.  I did ping tests and discovered my lan ip address to my systems internally was not pinging back with my lan ip address's and was being replaced by 

   
PING franco-ubuntu.belgan (23.217.138.107) 56(84) bytes of data.
 64 bytes from ubuntu.belgan (23.217.138.107): icmp_seq=1 ttl=45 time=108 ms

 64 bytes from ubuntu.belgan (23.217.138.107): icmp_seq=2 ttl=45 time=103 ms

 64 bytes from ubuntu.belgan (23.217.138.107): icmp_seq=3 ttl=45 time=104 ms

 64 bytes from ubuntu.belgan (23.217.138.107): icmp_seq=4 ttl=45 time=102 ms

Instead of: 

                       
64 bytes from ubuntu (192.168.2.5): icmp_seq=1 ttl=64 time=0.033 ms

 64 bytes from ubuntu (192.168.2.5): icmp_seq=2 ttl=64 time=0.054 ms

 64 bytes from ubuntu (192.168.2.5): icmp_seq=3 ttl=64 time=0.132 ms

 64 bytes from ubuntu (192.168.2.5): icmp_seq=4 ttl=64 time=0.078 ms

I checked into the company and I'm very suspicious.  Any ideas?   Or do I need to provide more information.  

Thanks

---

### Post by TheFu on 2019-08-04
Exactly what did you type?  Don't hide the commands or IPs.

---

### Post by kidsusukigsxr on 2019-08-04
Hi Fu.  Ping my computer name within my network and it keep returning 64 bytes from ubuntu.belgan (23.217.138.107): icmp_seq=2 ttl=45 time=103 ms  instead my internal ip 192.168.2.5.  I turned on my vpn and I'm able to ping and resolve 192.168.2.5.   And after a while I'll turn off my vpn and i'll be able to resolve my ip and any one I ping.  Not hiding commands.    PING franco-ubuntu.belgan (23.217.138.107) 56(84) bytes of data. Pinging my own internal system and shouldn't it read my lan ip 192.168.2.5
  


  Thank you

---

### Post by TheFu on 2019-08-05
> **kidsusukigsxr said:**
> Hi Fu.  Ping my computer name within my network and it keep returning 64 bytes from ubuntu.belgan (23.217.138.107): icmp_seq=2 ttl=45 time=103 ms  instead my internal ip 192.168.2.5.  I turned on my vpn and I'm able to ping and resolve 192.168.2.5.   And after a while I'll turn off my vpn and i'll be able to resolve my ip and any one I ping.  I'm looking into how to use that command.  Thank you

What **EXACTLY** did you type?
I expect to see exactly what you typed and the exact output.  It should look something like this:
```
$ ping hadar
PING hadar (172.22.22.6) 56(84) bytes of data.
64 bytes from hadar (172.22.22.6): icmp_seq=1 ttl=64 time=0.568 ms
64 bytes from hadar (172.22.22.6): icmp_seq=2 ttl=64 time=0.445 ms
64 bytes from hadar (172.22.22.6): icmp_seq=3 ttl=64 time=0.534 ms
^C
--- hadar ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2051ms
rtt min/avg/max/mdev = 0.445/0.515/0.568/0.058 ms

```
Please.  It isn't hard. ** I don't want an explanation.  I want to see EXACTLY WHAT the command used was.**  Thanks.

---

### Post by kidsusukigsxr on 2019-08-05
PING franco-ubuntu.belgan (23.217.138.107) 56(84) bytes of data.
 64 bytes from ubuntu.belgan (23.217.138.107): icmp_seq=1 ttl=45 time=108 ms

 64 bytes from ubuntu.belgan (23.217.138.107): icmp_seq=2 ttl=45 time=103 ms

 64 bytes from ubuntu.belgan (23.217.138.107): icmp_seq=3 ttl=45 time=104 ms

 64 bytes from ubuntu.belgan (23.217.138.107): icmp_seq=4 ttl=45 time=102 ms

---

### Post by kidsusukigsxr on 2019-08-05
Fu. Nothing is being hidden. Mine is the same as yours, with the exception of the bottom part (stats).  Do you see the information? What I did leave out is the name Franco.

---

### Post by TheFu on 2019-08-05
> **kidsusukigsxr said:**
> Fu. Nothing is being hidden. Mine is the same as yours, with the exception of the bottom part (stats).  Do you see the information? What I did leave out is the name Franco.

I give up.  Good luck.

The first step is to find out what you typed.  You've been unable to provide that for reasons I don't understand.  I even showed an example.
a) open a terminal.
b) type in the ping command <<<<<< I want to see THAT
c) view the output  <<<<< you keep showing that - helpful, but not without the actually typed in ping command.
d) copy/paste b and c into a reply here. Wrap them in code tags. See my example above.

The next step would be to research from where the name resolution was coming.  The IP looks like Akamai, which is a reputable world-wide content server company.
If that still leaves questions, then doing some dig commands.


good luck.

---

