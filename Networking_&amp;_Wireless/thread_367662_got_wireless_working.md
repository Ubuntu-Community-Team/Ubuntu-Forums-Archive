---
title: "got wireless working"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by jsarndt53 on 2007-02-22
This is how I got my wireless connection working....before I start I must say that I am by no means an expert in linux. Although I have been playing around with linux for awhile. I can not answer any questions mainly cause I feel that I don't have enough experience with linux.

I have 4 computers connected to a dsl wireless router, one is a desktop wired to the router, the other 3 are laptops that connect wirelessly. Two of the laptops are windows and one is ubuntu. The linux laptop stopped connecting to the internet. It took me a couple of days to figure out what was going on and this is how I finally did it.

On the windows computer I did this..... start-control panel-network connections-wireless network connection-support-details. Note that when you click on support it gives you the default gateway address. Ok so this was a start, I went to the linux computer and typed this...Route add default gw xxx.xxx.xxx.xxx dev eth0 When I clicked on details it gave me two dns server addresses. Just by reading the various posts in this forum I knew that resolv.conf had something in it so I did this cat /etc/resolv.conf it gave me a .net address and a IP address which was my default gateway address.....that didn't sound right to me. So I took one of the dns server addresses I found from the windows computer and did this 
gedit /etc/resolv.conf and replaced the default gateway address with one of the dns server addresses from the windows computer. Saved it and closed gedit. Opened up firefox and it worked.

I hope this helps someone.

---

