---
title: "Everything works fine but I cannot load pages in any browser"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by xiphor on 2008-10-21
Hello, 

I have Ubuntu 8.04 installed on a desktop PC. The problem is that sometimes I cannot browse the internet. When I try to access an internet page, Firefox hangs on pretty much with the message "Waiting for www.example.com..." and after that it displays an empty page with the message “Ready”. However after sometime something unblocks, because it works very good for a while an then it blocks again. In this time, the pidgin is working fine and also I can ping the sites. 
I have an Edimax BR-6104K router. I use it to share the internet to three PCs, 2 desktops with Linux and one laptop with XP installed. So, when I cannot browse on my desktop, I cannot browse on the other desktop on which I have installed Debian Etch. In Debian I tried to use Epiphany but there is no difference. During these falloffs I tried with **w3m**, Live CD of Kubuntu Hardy, Ubuntu Feisty, Ubuntu Edgy and PCLOS 2007, but the same behavior. **w3m** displays at the bottom: “[www.example.com](www.example.com) contacted. Waiting for reply...”. The annoying thing is that on the Laptop with WinXP, Firefox works just fine. 

After I googled a lot, I've tried the following: 
	a. I deactivated **ipv6** in Firefox and then on the all system. 
	b. I deactivated "tcp_window_scaling" and I modified "tcp_wmem" and “tcp_rmem" 
		( [http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/](http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/) ) 
		( [http://lwn.net/Articles/92727/](http://lwn.net/Articles/92727/) ) 
	c. I set static IP for my desktop 
	d. I set up other DNS servers first on the router, then on my PC
	e. I decreased the MTU 
	f. I removed the router 
	g. In Virtual Machine 2.0 I installed Win XP SP1. Of course that IE works only when Firefox works in Linux. 
	h. I used **mtr (v0.72)** to diagnose the connection, but everything looks OK (lost percentage is 0%).

However, somehow I can enter on [www.tuxsoftware.com](www.tuxsoftware.com). I think that it might be cached on server, I don't know.

Before Hardy I had Feisty for about 1 year and everything worked fine . This problem is pretty recent. I think that something from ISP server don't match with Linux Kernel. This behavior: sometimes works, sometimes don't, intrigues me most.

I do not know what else to try. Any help would be appreciated. Thanks.

---

### Post by xiphor on 2008-10-28
OK, I have tried the network utilities from ubuntu (ping and traceroute) and again with MTR. Everything looks very good, and still browser hangs on sometimes. Is there any other tool which can be used only for http pages? Because it seems that it receives all packages except the ones for a http page. 

It is possible that "somebody" to see that I use a linux system and to block http packages? But not all the time? Maybe is a "feature" of the ISP provider?

Or maybe is some kind of buffer which is floaded, and after some time it is flushed and http works again for a while I say that because i saw the following behavior: at the begining, the pages are loading very fast, after some time it take a little longer to load them. And of course, in the end, a blank page is loaded.

Please, just give me a hint, a tool name, anything. Thanks.

---

### Post by xiphor on 2008-11-17
Everything worked great for about 10 days. I thought that it solved by it self. But today it happened again.

New remark: I observed that I can download a page using wget.

Any suggestions?

---

### Post by jonobr on 2008-11-17
Just out of curiosity, could you try installing swiftsweasle,
see if that works out any better


[http://swiftweasel.tuxfamily.org/](http://swiftweasel.tuxfamily.org/)

---

### Post by xiphor on 2008-11-18
ok, I installed swiftweasel, and no improvement. :( The only page I could load was [www.tuxsoftware.com](www.tuxsoftware.com). This convinced me completely that not the browser is the problem.

---

### Post by DaBigWig809 on 2008-11-18
I have a similar problem. The internet works but then it doesn't for awhile. I'm using Verizon DSL in NYC with a Westell 7500 Modem. I'm trying to fix it, does anyone have an idea ?

---

### Post by xiphor on 2008-12-15
I found another interesting thing: I've noticed that I always can enter on a securized page like https. That's why I can load page https//mail.yahoo.com. But only the log page. After I authentificate, the trafic in regular (http) ang again blank pages are loaded. At first I thought that the log page in stored in the cache.

Another story is with an online banking site/page. Here everything is secured between login and logout. Strange, I can pay my bils, but can't load google page.

Any ideas?

---

### Post by drpawansharma on 2009-01-02
hi, i have similiar problem, initially everything worked fine, later firefox 3.0 stopped loading webpages with [http://,](http://,) i could access https:// allright.
then i downloaded opera, it worked fine for a day then developed the same problem.
then i downloaded dillo which worked fine, however i need my opera or firefox.
i use a compaq laptop and have ubuntu 8.04. i use a wired connection with lan modem.
i have used all the fixes mentioned on the web. nothing works.
by the way some times the problem resolves spontaneously but redevelops.
please help.

---

### Post by xiphor on 2010-12-30
Hello all,

This topic remained suspended for almost 2 years. One reason is that the problem has solved by itself for me. I do not know exactly when, somewhere at the beginning of 2009. I still do not know what it was and probably I will never  know.

Just FYI. Better later than never.

---

