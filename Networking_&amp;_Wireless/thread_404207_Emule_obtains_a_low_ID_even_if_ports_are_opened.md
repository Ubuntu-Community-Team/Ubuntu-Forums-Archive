---
title: "Emule obtains a low ID even if ports are opened"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by darkmaster on 2007-04-08
Hi everyone, I'm running on Ubuntu Edgy and installed Amule. Everything should go right but it doesn't. I've got a 3com wireless router and there are 3 computers connected right now. A windows one (My phater's) and 2 Ubuntu Computers (mine), a Mac Mini and a Laptop. 

On both Ubuntu computers, if I try to connect to any port, I get a low id in amule. Why? First I have to say that the firewall of the router is not enabled to see if this can be fixed... the windows PC obtains an high ID. Ubuntu cannot obtain it! I even changed amule's ports to the Ubuntu PC so that it has those of the windows one and vice versa... no solution. Windows is allways high ID, Ubuntu low ID even switching the ports. I also controlled in the router configuration: the ports I use are opened.

Why does this happen? Is it possible that Ubuntu has an internal firewall of some kind that I have to deactivate?

---

### Post by Jakobe on 2007-11-03
I am having the same problem. Amule used to work well and with High ID, but one day I just opened it and I got Low-ID, I have changed the ports but doesn't work.

I don't know why I can get High ID :(

---

### Post by aperrado on 2007-11-03
hello

wait a little time and voila

high id

---

### Post by Hallvor on 2007-11-04
You get a low ID if your IP address ends with a zero, even if the ports are forwarded correctly.

Here are different topics on low id on the eMule forums. (It also applies for aMule.)
[http://forum.emule-project.net/index.php?act=Search&CODE=show&searchid=69aed614d8b577a8802da2847482208e&search_in=posts&result_type=topics&highlite=%2Blowid](http://forum.emule-project.net/index.php?act=Search&CODE=show&searchid=69aed614d8b577a8802da2847482208e&search_in=posts&result_type=topics&highlite=%2Blowid)

---

