---
title: "Advanced network setup with two active network cards on different LANs"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by jorno on 2007-04-02
Hello all!

This is my first forum-post as a Ubuntu-member, and I will say Ubuntu has come a long way in a short time. I can't wait to explore more of it. But as of now, I've got a little problem...


I'm a earlier Gentoo-user, and have used many other distros also. I would like to look at myself as a relatively experienced linux-user. But I have not found a "Ubunty-way" of fixing my current problem, which has not been a problem in either Gentoo or Windows (please, this is not a flame-war).

I'm currently running Debian Feisty, and my workstation has got two network cards - one 10/100 and one 10/100/1000.

At my network here at home (this would be a static setup for my computer, as I never move it around - got a laptop for that) , I've done this;
* INTERNET --- GateWay/FileServer box  --- Internal LAN with Gigabit, sharing the net for all the other computer, and with a connection to the current workstation. BUT, I have also another direct connection to the internet:
* INTERNET --- Current Workstation (to the 100mbit-card).

Why I do this is; I need a fast (gigabit) connection from my Workstation to my FileServer, as I store absolutly all my data and documents directly on the FS. But, I do also need a direct connection to the internet from my Workstation, and not one that goes trough the GW/FS. 

To solve this earlier, I've setup the gigabit-nic with 192.168.0.3 without default_gw-setting, and then received from DHCP with my internet-nic. That way I can both access everything on my internal lan, with the gigabit-nic, and the internet-nic is used for all external traffic.

BUT, in Ubuntu, I've got this "NetworkManager Applet" running. And I can't seem to enable both the NICs at the same time... If I enable eth0 (default when booting), I can connect to my internal network. If I enable eth1 (must do manually), I can connect to the Internet, but NOT my internal network. But I want them BOTH connected at the same time...

Is there a way to do this "The Ubuntu Way (tm)" ? Or do I need to get rid of the NetworkManager-Applet, and hack my way trough the /etc/network/interfaces by myself? (I _could_ do it, but if Ubuntu has some nice way to solve this - I'd like to hear it).


Thanks in advance for those of you who will reply, and please ask if there's something unclear. English is not my native language, so I've probably done a poor job explaining this. ;-)

---

### Post by spd106 on 2007-04-02
Feisty hasn't been released yet, so I have no idea and anything I suggest could be thrown out of the window after an update tomorrow. I suggest that you stay with Edgy for the moment, unless you're willing to fix it come the next breakage.

That said, I think the best way is to try and set one interface as static and the other controlled by Network Manager. I'm not yet sure how to do this, I suspect it will involve network-admin. I struggle to get even one card working at a time, never mind two. I'll reboot into feisty and have a look tomorrow, unless you solve it before then. 

The feisty sub-forum might be a better place to ask, though you'll probably be told to remove Network Manager. It's not getting much love at the moment.

---

### Post by jorno on 2007-04-03
Hehe. Ok, thanks man.

As my whole network-setup is pretty static, I can see that I don't actually have any use of the NetworkManager applet on my workstation. So I could just rip it out. :-)

I think that NetworkManager is a needed app in Ubuntu, as many many users wouldn't get theire network up and running without it. And especially when it comes to wireless.. I've always found it hard to connect to wireless network, fast, with my laptop, in linux. So something like NetworkManager is actually nice to finally se!

---

