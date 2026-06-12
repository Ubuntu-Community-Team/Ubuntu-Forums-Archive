---
title: "set up vpn on ubuntu server remotely"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by Korijn on 2008-09-19
I'm having immense trouble setting up a VPN server on my Ubuntu server box. I have never done this before and am having a hard time grasping the whole idea.

This is our network setup:

Internet --> Router (wired) --> Several computers & a wireless router --> laptops/nds/wii

Among the 'several computers' is my Ubuntu Server box. It's fully up-to-date and has no extra packages installed yet.

I use it as a development box for websites and such, and also to toy around with in order to get adept at linux shell. It is a headless system with no monitor etc. meaning I operate it through PuTTy.

Now, it also has some drives which are shared via Samba. I have those drives mapped on my laptop. Now what I'd like to do is the following: the ubuntu box should have something like a VPN server set up so I can connect over the internet and reach those samba shares. I'd prefer it if this were secured with for example SSH or a user/pass system. Again, I know nothing about this yet, please enlighten me.

Thanks a lot in advance. :) Oh, I am familiar with using the terminal commands etc. by now.

---

### Post by Korijn on 2008-09-22
Bump?

---

### Post by NoReflex on 2008-09-22
Hello!

I've used OpenVPN (it was running on a Windows box but this doesn't matter). It's easy to setup and very configurable. As a starting point you could check : [http://www.thebakershome.net/?q=node/56](http://www.thebakershome.net/?q=node/56)

Best wishes,
NoReflex

---

