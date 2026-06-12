---
title: "How to set CIDR IPv4 during Server Setup?"
date: 2023-09-27
forum: Networking &amp; Wireless
---

### Post by jderosa32 on 2023-09-27
I am setting up a new Ubuntu server. I need to set the address of the NIC to be 192.168.50.103, but I get the error below.

How do I set this? I am not familiar with CIDR address rules. Thanks.

[IMG]https://i.ibb.co/gWYzTb1/Screenshot-2023-09-27-at-9-41-47-PM.png[/IMG]

---

### Post by TheFu on 2023-09-28
You've confused the netmask with the subnet.  There's no question here about the netmask. The CIDR takes care of that.

BTW, you aren't the only one having a problem with this screen.  I don't setup servers more than 1-2 times a year and I almost always guess the wrong answers because the installers don't provide an example for what's expected.  I remember being so frustrated during one install a few years ago that I didn't setup any networking at install time, then post-install, manually setup the netplan.yaml/interfaces file as I needed.

BTW, is your name server really the same as your gateway?

---

### Post by The Cog on 2023-09-28
I'm guessing that the subnet field should be **192.168.50.0/24**.

---

### Post by TheFu on 2023-09-28
> **The Cog said:**
> I'm guessing that the subnet field should be **192.168.50.0/24**.

Too bad they don't just have us use the IP/CIDR, which handles the subnet and netmask and IP all in just a few characters.  Plus, an example to the right of the text entry really would be nice, so we wouldn't be guessing.  The lack of an example has bothered me nearly 4 yrs.

---

### Post by jderosa32 on 2023-09-29
As a new comer I am glad I am not the only one that was stumped here. I appreciate the explanations. I got it working and yes I confused the netmask with the subnet.

---

### Post by TheFu on 2023-09-29
192.168.50.45/29   provides multiple answers.

[LIST]
[*]It says that the IP is 192.168.50.45
[*]It says that the netmask is 255.255.255.248 
[*]It says that the network address is 192.168.50.40/29
[*]that 5 useful IPs are available. 192.168.50.41 - 192.168.50.46 with 
[*]192.168.50.47 used for network broadcasts.
[/LIST]

Any online network calculator can do this. Those tools are useful for learning IPv4.  Also, basic networking can be quickly understood by reading/listening to **Security Now** podcasts "How the internet works" eps 25 and a few right after that.  That's for IPv4.  IPv6 is more complex ... for people like me who **need** to know exact data.  

If I could drop that detailed knowledge requirement, then I suppose IPv6 would e easier? Thinking in abstract, nebulous, ways isn't easy for everyone.  For IPv6, there are so many addresses it is hard for humans to grasp.  "Bigger than we can truly imagine or understand" isn't a number.  The fact that most ISPs will provide a /56 public network to their IPv6 customers and that will give each customer more IPs than the entire IPv4 possible range is hard to understand.  Does your house need 4 Billion+ IPs?  Most people don't know what to do with just 256 IPs (/24 in CIDR notation).

Anyway, if someone with a landscape account made the suggestion for the server installer that an example next to or inside each field would really save lots of time for people who don't do this every day, that would be nice. Seems like a little thing and Canonical has probably discussed it, but nobody on that team decided it would be helpful, though clearly it would.

---

