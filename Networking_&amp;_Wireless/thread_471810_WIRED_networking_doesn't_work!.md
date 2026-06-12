---
title: "WIRED networking doesn't work!"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by firsttry on 2007-06-12
First time I've installed Ubuntu 7.04 - and neither my wireless IPW3945ABG nor my wired Realtek RTL8111/81688 connections work!
I've never come across a distro where not even the wired connection works!
I don't have dhcpcd, so I can't reset it, I'm stuck as I'm not familiar with any of the tools of Ubuntu!

I've tried ifconfig eth0 down and up again, but that doesn't seem to be doing much...

Also, though Ubuntu says it's using restricted drivers for my wireless the driver doesn't appear anywhere... I get eth0 which is my wired, eth0:avah (what's this?) and the lo (obviously). Wireless doesn't even appear when I ifconfig -a nor in the network tools gui...

No IP address is given to my machine, the cable works with another one so the problem is undoubtedly with my setup.

I'd be happy getting just my eth0 working. Actually my friend once had the same problem - again, OUT OF THE BOX UBUNTU and his wired connection didn't work! This is frustrating as it's supposed to be the most popular distro and easy to set up... he said Ubuntu automatically set up two dhcp's? It's my friend's machine and so far Ubuntu has been a bit of a letdown...

Anyway, apologies for the rambling there but I'm really stuck. Any help would be appreciated!

Thanks!

---

### Post by S29K on 2007-06-12
Assuming you are using Feisty, you can left click on the network icon on the taskbar and select 'Manual Configuration' or alternatively go to System -> Administration -> Network to configure your network settings for both wired and wireless connections.

---

### Post by firsttry on 2007-06-12
Ok, when I left-click on it I get a greyed out Wired network entry and another below it Manual settings.

Which I click on. Then I get wired connection Address: dhcp and Modem connection underneath it (though the modem's irrelevant).

Clicking properties tells me the configuration is DHCP and everything else in the window is blank.

Clicking on the general tab just has the hostname and the Automatic service discovery is ticked.

DNS tab - There are no DNS Servers or Search Domains present. Though to my understanding there shouldn't be any anyway if I'm using DHCP.

Hosts tab: 127.0.0.1 - localhost
127.0.1.1 miniasus
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02:3 ip6-allhosts

Is anything wrong in the setup?

Just out of curiosity - has anyone else had problems with wired networking out of the box installing Ubuntu?

---

### Post by firsttry on 2007-06-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Turns out this is a bug.

---

