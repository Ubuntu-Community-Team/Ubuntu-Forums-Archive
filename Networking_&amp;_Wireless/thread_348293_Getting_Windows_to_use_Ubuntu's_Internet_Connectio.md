---
title: "Getting Windows to use Ubuntu's Internet Connection"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by bullit on 2007-01-28
Well, I have a wireless router that's connected to my ubuntu box via cable (it's sitting right under my desk, just under my cpu). 

Problem is: I need to connect windows XP to the internet via ubuntu. 

How do I do this? I've read and done the setup (dnsmasq etc) but I still couldn't get XP to get with the programme. Any ideas? I've also tried setting the preferred dns and gateway as a single IP (192.168.0.1) on XP (is it this laughable? well, since I'm a newbie - i believe it is :D)

I'm tired of reading the posts but not getting any working solutions. It's either me or Linux needs a lot of help to get this done elegantly, IMHO. 

Any help would be appreciated. Thanks in advance.

---

### Post by kidders on 2007-01-28
Hi there,

> **bullit said:**
> Well, I have a wireless router that's connected to my ubuntu box via cable (it's sitting right under my desk, just under my cpu). 

Problem is: I need to connect windows XP to the internet via ubuntu. 

How do I do this? I've read and done the setup (dnsmasq etc) but I still couldn't get XP to get with the programme. Any ideas? I've also tried setting the preferred dns and gateway as a single IP (192.168.0.1) on XP (is it this laughable? well, since I'm a newbie - i believe it is :D)

I'm tired of reading the posts but not getting any working solutions. It's either me or Linux needs a lot of help to get this done elegantly, IMHO. 

Any help would be appreciated. Thanks in advance.

Sharing an internet connection is **not** trivial, and is not something worth attempting unless you have a basic understanding of what's involved at the IP level. Unfortunately, dumbing it down so it would be easier to accomplish would only make Linux less flexible. Linux's flexibility is one of its major assets!

First, you should try to pin down your problem, and make sure you know what's happening on your network. For instance:

[LIST]
[*]Can you ping XP from Ubuntu and vice versa? If not, internet connectivity is not to be expected.
[*]Do you have DHCP servers running in places they shouldn't be, such as on your wireless router.
[*]Are all your cables working?
[*]Is your router properly configured?
[/LIST]

The trouble with your post is that there are literally hundreds of things that could be wrong. We have to try to figure out which one(s) first!

---

### Post by mips on 2007-01-28
> **bullit said:**
> Well, I have a wireless router that's connected to my ubuntu box via cable (it's sitting right under my desk, just under my cpu). 

Problem is: I need to connect windows XP to the internet via ubuntu. 

How do I do this? I've read and done the setup (dnsmasq etc) but I still couldn't get XP to get with the programme. Any ideas? I've also tried setting the preferred dns and gateway as a single IP (192.168.0.1) on XP (is it this laughable? well, since I'm a newbie - i believe it is :D)

I'm tired of reading the posts but not getting any working solutions. It's either me or Linux needs a lot of help to get this done elegantly, IMHO. 

Any help would be appreciated. Thanks in advance.

You should not really hijack someone elses thread as your situation seems a bit different.

Start your own thread and you will get help. Unfortunately you provide very little information and that makes it hard to help. it also sounds as if you have done more than you should.

ICS is not that hard to setup. You just have to understand a few things. If you want you can search for posts by myself with the keyword 'firestarter'.

---

### Post by aysiu on 2007-01-28
> **mips said:**
> You should not really hijack someone elses thread as your situation seems a bit different.

Start your own thread and you will get help. Even if the situations are not different at first, to make things less confusing, it makes sense for the two to have their own individual threads, as they will progress at different rates and encounter different problems or need different levels of clarification on directions.

I've made this its own thread, so it can get the attention it deserves.

---

### Post by kosmic on 2007-01-28
If you have a Router why don't you connect your Windows box to the router directly ??

It is more simple that working with DHCPs, PortForwarding and iptables ;)

---

