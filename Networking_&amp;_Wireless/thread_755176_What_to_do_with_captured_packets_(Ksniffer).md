---
title: "What to do with captured packets? (Ksniffer)"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by nappymonster on 2008-04-14
hi all,
I've just been trying out, **On my own network**, Ksniffer. I went to hotmail, sent my self a message, went to inbox, started ksniffer, opened messeage, stopped ksniffer.

It gave 81 packets, all "IP Packet information" 
Having never used a sniffer before, how do i then turn this into information, What information would it give? (E.g the contents of the e-mail? Just the date? Just the sender? Just the web site?)

There is something quite strange in the lower right, a text box of various characters, seperated by many full stops. 

Thanks,

Nappymonster

---

### Post by The Cog on 2008-04-14
I hadn't heard of ksniffer before. It looks like a wireshark clone to me.

If you google for "wireshark intro" or "ethereal intro" (wireshark's former name) you will turn up a lot of useful links.

You need to now that all internet communidations happens in packets - messages of a limited length. Each packet is made of up to 1500 bytes. The numbers in the bottom pane of each packet is the hexadecimal values of each bte in the packet. To the right is the characters those bytes represent, or a dot if that byte doesn't represent a printable character. Each packet has a series of bytes at the front (called the header) which indicates where the packet is to and from, and what the contents are all about. 

Looking at packets and their decodes in a sniffer can greatly improve your understanding of what's going on, but you really need some introductory books on networking and the IP and TCP protocols too. Possible google searches are "ethernet frame format" and "ip packet format", and maybe "tcp ip intro". Be warned, the subject is huge.

---

### Post by nappymonster on 2008-04-14
So is there a piece of software that decodes these packets then into something i can read ? :D

Nappymonster

---

### Post by lundholmj on 2008-04-14
I agree with The Cog, wireshark is very similar and is much easier to use.
its in the repos

---

### Post by nappymonster on 2008-04-14
Thanks, but in the but in the repos it says:



Wireshark

This application is provided by the Ubuntu community.
Wireshark cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.



I'm going to try it, but i don't think it will work :(

Nappymonster

---

### Post by nappymonster on 2008-04-14
I tried it, and after updating various parts of my system it's installed :D

Nappymonster

---

### Post by The Cog on 2008-04-15
It's good to see you got in installed. Not that I want to dis ksniffer - I've never looked at it. It's just that wireshark has been around for years and has acquired a lot of documentation in that time. It's very much the established standard. It'll be  tough one for ksniffer to beat, but maybe they have some ideas.

> So is there a piece of software that decodes these packets then into something i can read ?
Sorry, but this is it. ksniffer / wireshark **is** software to turn the packets into something you can read. Not only does it show you the exact packet contents, it breaks down the protocols inside into readable text. It's like the blueprints for each packet. Exactly what information are you trying to extract from the captured packets? Maybe a sniffer isn't the tool you are looking for. There are other tools for looking at traffic in different ways, but a sniffer is the most detailed, low-level one. If you want to learn about what goes in packets and what all the bits mean, this is as good as it gets.

Although I would point out a real handy feature of wireshark where you can right-click a TCP packet and choose "follow TCP stream" which picks out all the data contents of a single TCP connection and shows it in one window. This feature can be incredibly informative if you are trying to debug application problems like email failures etc.

---

