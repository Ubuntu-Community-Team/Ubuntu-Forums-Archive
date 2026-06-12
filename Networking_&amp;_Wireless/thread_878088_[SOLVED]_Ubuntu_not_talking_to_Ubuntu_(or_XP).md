---
title: "[SOLVED] Ubuntu not talking to Ubuntu (or XP)"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by NickZA on 2008-08-02
Hi All

My setup:

Gateway Server:

Ubuntu 8.04
Win XP
3 NICs, eth0 Via Rhine, eth1 LNE100, eth2 Attansic L1 (the problem card, it seems).

Workstation:

Ubuntu 8.04
Win XP
1 NIC, eth0 (can't remember what it is but that's moot as it works perfectly, see below)

When booted into XP on the gateway server, ICS and file sharing work fine whether I'm booted into Ubuntu or XP on my workstation. (OK, so NICs are working fine...)

When booting into 8.04 on the gateway server, internet works fine locally (eth0), but won't share... neither the workstation nor the gateway's local interface card get IPs assigned.

The funny thing is, when I was running 7.10 on the server it was fine. I installed 8.04 the night before last and I'm now having problems getting my two machines talking when the server is booted into 8.04.

Some other details: I at first thought this was an Attansic L1 driver issue on the server, but if I set both systems Ubuntu network settings to DHCP, they can ping each other (but they each remain on 169.254.*.*).  So def not a driver issue.

Is this as simple as a DHCP issue? But if so, why would the automatic network config settings have screwed up between my installation of 7.04 on the server a few days ago and my upgrade to 8.04 a few hours ago?

I get the feeling whatever is going on here is quite straightforward, i.e. I have to setup a proper DHCP server and perhaps set static IPs? --I don't particularly want to set these kind of settings on either machine if I don't have to, as I want them to talk regardless of which OS is booted on either, with no hassles as they did before, automatically and with no extra configuration as they did previously when the gateway was running 7.04.

:confused: Please help, I'm really tired of fooling about with system setups, I just wanna get back to programming with a couple of stable machines...

-Nick

---

### Post by NickZA on 2008-08-02
*Hi All,*
[I]
Just thought I'd reply to myself and give you an idea of how to set yourself up with a DHCP server in order to rid yourself of your internet/file sharing woes. Here's the guide...[/I]

My Setup: 2 systems, each running XP and Ubuntu 8.04. Gatweway server with 3 NICs, Workstation with 1 NIC.

My Problem: When I upgraded my server system from 7.10 to 8.04, internet sharing no longer seemed to work.

I needed it to work with both systems regardless of whether the server was booted into Ubuntu or XP, or whether the client was booted into Ubuntu, XP or Mac OSx86 (yeah that too).

After much faffling about trying to find out whether my server's local interface card was a goner / had driver issues or whatever, I worked out that was not the case since the pair of machines talked in XP just fine.

So I realised I might have to install a DHCP server as the workstation just wasn't getting an IP when server was booted into Ubuntu.

Installed DHCP server on the server's LAN (not internet) interface, which for me was eth2. (I had an ETH1 as well which I will at some point attempt to get working with the DHCP server as well). Internet interface was eth0.

Thanks to linuxtopia, see original article I followed at [http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html). I followed this NEARLY to the letter... So read on before you go and look at that article.

Things I needed to do differently from the linuxtopia article:

First, REMEMBER TO LOGOUT/restart after the step where you install dhcp3-server using the Synaptic Package Manager. To check that your DHCP server daemon is actually running in the background, do sudo /etc/init.d/dhcp3-server restart. If that says "starting/stopping" etc. then you are in business, the daemon is running. (Don't worry if it says "fail" next to starting/stopping as you still need to set it up properly, that's the next step. At least this "[Fail]" thing happened to me but all was okay ultimately when I'd configured the rest.

Furthermore: I did not insert the line "option domain-name xxx" line into /etc/dhcp3/dhcpd.conf -- it wasn't needed, and may even have interfered. I obvsiously also adapted the name servers to the ones for my ISP. For the noobish (like me) if you want to get your DNS info without actually calling your ISP, then (if you have Windows installed), just go into Windows, go to Start->Run->type "cmd", then type "ipconfig /all" and you'll see your domain name servers listed for your internet connection.

Lastly, I uncommented the "authoritative" line in /etc/dhcp3/dhcpd.conf -- this allows this DHCP server to have the final say on IP address assignment. It will send a DHCPNAK signal to a non-conforming client, telling it to stop using an inappropriate address. It is like a sort of overbearing but well-meaning mother-in-law.

So, NOW you can go ahead and follow the linuxtopia instructions for setting up the dhcp config files.

DO NOT, DO NOT forget (as I did!) to actually set your DHCP server interface (in my case, eth2) to be a static address! That is exactly what you are telling the DHCP server config files to expect when you put 192.168.0.1 in there, so don't let that poor daemon down! (It might find you in the afterlife.)

Note that your client can be set to "roaming mode" (default) or DHCP client, either worked for me (roaming appears to just default to being a DHCP client anyway) -- I prefer to keep things on defaults when possible.

A VERY useful article I used to troubleshoot the process can be found here [http://www.howtoforge.com/dhcp_server_linux_debian_sarge](http://www.howtoforge.com/dhcp_server_linux_debian_sarge) ...superb stuff.

If I remember anything else or if anyone points anything out, I will do updates to this post. Hope it helps some of you!

Good Luck,
-Nick

---

