---
title: "Remote Assistance How-To?"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Chou on 2007-03-29
I'm working for a small promotions company and I have just changed my boss' OS to Ubuntu 6.10.

I want to be able to utilize remote assistance to her computer from home. Can this be done over the internet? or do i have to be directly connected to her computer via router/switch/etc...

I've never used remote assistance before, so any help/tips/hints/cesspools-of-knowledge would help greatly

---

### Post by Chou on 2007-03-29
has anyone even looked at my post?

---

### Post by Mr. C. on 2007-03-29
Well, I just did.  Have some patience. :-)

You can do what you want.  You need to:

1) Enable the companies firewall to allow some sort of secure connection into the corporate network.  You can either setup a VPN to/from your home, or use SSH to make a secure connection to a corporate SSH server (like on your boss' system).

2) Enable Remote Desktop on your boss' station.

3) Establish your secure connection to work (VPN or SSH).

3) Use a VNC connection from home to control your boss' station

If you use SSH, you configure the SSH server to allow a tunnel, which you establish to your boss' station when you connect.  If you use VPN, no tunnels are required.  VPN configuration is much more difficult, and many small company's use inexpensive routers that provide no support for VPN.

This is the basic idea.  When you have some more information as to how your network is setup, and what you can do, we'll help more.

MrC

---

### Post by Chou on 2007-03-29
Bosses computer is plugged directly through DSL line

My home computer is wired into a router that goes directly into a DSL line

When i say i need info. i mean... i need it ALL. im stupid when it comes to complex networking.

I want to be able to access her computer from miles away when she needs help.

we will both be using v6.10

what i really need is for someone to take me step by step through the setup process of making this happen.

i hope im not asking too much

/.chou <--- look, im hiding!

---

### Post by Mr. C. on 2007-03-29
Well, you are asking a lot.  You are getting paid to do the job - we aren't.  So you must bear the burden of the time and cost.

First step, go out and purchase a router/firewall/NAT device to connect between the DSL line and your bosses computer.  Most all consumer router's will provide what you need.  While you can configure your boss' system go act as such a device, this is far beyond your desire for an easy solution.

When you have that device in place and configured to provide internet, let's talk more.

MrC

---

