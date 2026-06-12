---
title: "Network stops working"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by Xsandros on 2008-07-16
Hello,

**The system:** 
Ubuntu 8.04 64 bit
I have a virtualization program (Virtualbox) installed. The virtual ized systems connect to the network through a network bridge.

**The problem:**
Sometimes, apparently random, networking stop working in Ubuntu, mail, browser, also automatic updates cannot connect to the network.

If I run a virtual machine (either after of before the network stop occurs), from inside the virtual machine I can access the network with no problems at all.

**What I suppose:**
1) The network bridge creates some problems on the Ubuntu side, so it prevents to connection from Ubuntu, but not from inside the virtual machines, OR
2) The problem is not in the networking (that is working from inside a virtual machine) but on another level inside Ubuntu (I do not figure which)

**Help requested:**
How can I understand what is happening? Where to search? Configuration files? Diagnostic tools? I am quite new to Ubuntu, and still I do not understand where to puts my hands on.

Just some points more: 
- removing and re-creating the network bridge did not solve the problem.
- On Ubuntu 7.10 the network configuration was the same (I did not change anything from default before or after the upgrade, except creating the network bridge), but I never experienced the problem.
- Please excuse me for my bad english

Any suggestion will be *really* appreciated

Xs

---

### Post by Xsandros on 2008-07-17
Ok, no one seems to know anything about this issue.

I asked for this problem in different forums and different languages too, with absolutely no answer. Maybe I'm not asking in the right way, maybe my english, and french and italian are not so good. :(

Let me ask something easier: if the network does not work in Ubuntu and the network card is correctly installed, which steps should be done to diagnose the problem? 
I think that network problems should be more common than bridge problems.

---

### Post by alspal on 2008-07-17
I feel your pain. I dont really see the point of this forum seeing that noone is prepared to help??? Sorry.

---

### Post by jmbagnall on 2008-07-17
I too have a network problem and have virtual box installed. Virtualbox may or may not be relevant at all. Hardy and both wired and wireless networking has been working well for several months but now when I boot into hardy my wired connection (eth0) does not start.  If i start it with ifup it seems fine. Does anyone have ideas on how to make it start automatically again?

Any ideas gratefully received.

---

### Post by markwyatt on 2008-08-03
I just got this working:
VirtualBox
Host: Windows XP - Wireless Internet
Guest: Ubuntu 8

I hope this helps

[IMG]http://s15242348.onlinehome-server.com/i/FCKeditor/userfiles/CLIENTPORTAL/WebSoft%20-%20internal/Image/virtualbox_networking.jpg[/IMG]

---

### Post by jebova2301 on 2008-09-09
i have the same problem, but i am running gutsy(7.10). I will work, and then in the middle of doing my work, the internet just quits on me. I can still go online from other computers in the house and get on xbox live, so i know the internet is still working. the only emulation software i have on my machine is wine. this has only started recently. i have had wine installed for a long time now. does anyone know the cause or how to fix it? if so, thanks in advance

---

