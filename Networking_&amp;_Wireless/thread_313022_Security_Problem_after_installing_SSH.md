---
title: "Security Problem after installing SSH ?"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by Panasonica on 2006-12-05
I'm a beginner who has just installed Ubuntu (Dapper) for the first time. Hooray :D .

I've installed SSH (using Syanptic) so that I can open a graphical Ubuntu session from my XP machine on the same LAN.

But I read the following warning on a website about installing SSH onto a graphical Linux machine:

> 
If you have a GUI session open on one of your Linux systems, that host is probably listening to TCP port 6000 (between 6000 and 6063). You can check this with the netstat -tna command. It is okay for it to be listening on the 127.0.0.1 address, but not on 0.0.0.0 or your Ethernet address(es). Although this is not an X over SSH problem, it is a typical issue with running a GUI desktop on one of your machines. This can leave you vulnerable to keystroke sniffing, destruction of windows, unrequested windows popping up, arbitrary commands being executed, or your screen being grabbed. There are two easy ways to handle this, assuming that the only remote X access will be through SSH:


a) start your X session with the "-nolisten tcp" option, either in your command line or your GUI startup scripts. You will probably have to dig into the documenation if you want to do this in runlevel 5. If you start your X sessions from the command line in runlevel 3, you can enter the following:

startx -- -nolisten tcp or startx -- :1 -nolisten tcp (and so on...) 


b) use your ipchains or iptables firewall to block TCP ports 6000-6063 on your Ethernet addresses.  

Indeed, netstat confirms that I do have a TCP port listening on my 0 ethernet address in the above port range (6000 to 6063).

Can someone help me with the following points:

1) Why is it dangerous to have an open port listenting in the range 6000 to 6063 ?
2) How can having this port listening, enable keystroke sniffing, destruction of windows, unrequested windows popping up, arbitrary commands being executed, or your screen being grabbed ?
3) How can I start my X session with the "-nolisten tcp" - which configuration file do I have to change ?
4) What effect will starting my X session with the "-nolisten tcp" have on other Ubuntu programs/processes ?
5) Why does Ubuntu running SSH listen on port range 6000 to 6063 ?

Many thanks in advance for your help to a worried beginner,
P

---

### Post by scrooge_74 on 2006-12-08
> **Panasonica said:**
> I'm a beginner who has just installed Ubuntu (Dapper) for the first time. Hooray :D .

I've installed SSH (using Syanptic) so that I can open a graphical Ubuntu session from my XP machine on the same LAN.

But I read the following warning on a website about installing SSH onto a graphical Linux machine:



Indeed, netstat confirms that I do have a TCP port listening on my 0 ethernet address in the above port range (6000 to 6063).

Can someone help me with the following points:

1) Why is it dangerous to have an open port listenting in the range 6000 to 6063 ?
2) How can having this port listening, enable keystroke sniffing, destruction of windows, unrequested windows popping up, arbitrary commands being executed, or your screen being grabbed ?
3) How can I start my X session with the "-nolisten tcp" - which configuration file do I have to change ?
4) What effect will starting my X session with the "-nolisten tcp" have on other Ubuntu programs/processes ?
5) Why does Ubuntu running SSH listen on port range 6000 to 6063 ?

Many thanks in advance for your help to a worried beginner,
P


Why do you want to have X over SSH into a XP machine?  In any case you can easily do command from that other OS and be a little safer.  

Forget about doing remote X is more fun to sit in front of hte Linbox in question

---

