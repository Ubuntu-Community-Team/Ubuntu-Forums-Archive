---
title: "amule is messed up"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by linux noooob on 2007-06-13
ok so i am using amule (or atleast i want to) on ubuntu 7.04 but but it is not working!! it says kad off even when connected and when i try to download somthing it takes like an hour and still does nothing it is way to slow!! help

---

### Post by Hallvor on 2007-06-14
Don`t worry about Kad. It needs enough sources from the servers to function properly.  Kad will work just fine once you have downloaded a few popular files. Just give it a little time.

Secondly, make sure you are not firewalled. The arrows around the little globe on the bottom right on your screen should be green. (*One* of them may be red or yellow if you just started using aMule for the first time.) If the arrow(s) are yellow, then you are firewalled, and that will slow down all downloads. It is a good idea to change the default ports in aMule, and opening those ports on your router. If you don`t know how, check your router manual. Also, open the ports in Ubuntu using Firestarter (in the repos).

Thirdly, aMule is not bittorrent. The average user shares hundreds of files and leave their computers on 24/7. Their upload bandwidth is shared among all these files, so the first chunk of data (9,28 mb) may be slow to get. (Personally, I share more than 300 rare ebooks.) Once you have it, however, you will be able to upload the chunk to other users, and because there is a credit system that rewards uploaders, downloading will be significantly faster after that.

However, if you want to download as fast as possible and leech like crazy, bittorrent is the obvious choice.

---

### Post by linux noooob on 2007-06-14
thanks but i am confuzed one arrow is red and the other is yellow!!?? and i dont use bittorrent because it alwase says i have a nat problem??

---

### Post by Hallvor on 2007-06-14
One red and one yellow arrow? Yellow arrows mean you are firewalled, while red arrows mean you are not connected. One yellow and one red arrow probably means you are connected to a server and firewalled, but not to Kad.

Bottom line: You are firewalled.

You have to open the ports in your firewall *and* with Firestarter to solve this problem.

How to forward the ports on your router:
[http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm)

Install Firestarter through the terminal with:
> sudo apt-get install firestarter or get it via add/remove programs.

Configure Firestarter:
[http://www.fs-security.com/docs/tutorial.php](http://www.fs-security.com/docs/tutorial.php)

Once that is done, try connecting to a server again. If you get a green arrow or two, you are fine!

---

### Post by linux noooob on 2007-11-22
HEY! back and i am giving it another try i have opened both tcp and udp ports in my firwall and router:

4662
4242
5000
4672
4665 
and yes i also added way more on my firewall!!!!
 

HELP!!!

---

