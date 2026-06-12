---
title: "Port Forwarding on Linux, specifically Ubuntu"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by MertTheGreat on 2009-09-20
Hi,

I am using vuze for torrent files but I need to that thing below, acording to vezu wiki page.

Problem I just migrate from windows I don't understand what to do.

If anyone translate it to beginner language, I would be glad.

> **Port Forwarding on Linux, specifically Ubuntu**

 Firstly the earlier notes on port forwarding for your router apply as before. Computers running Ubuntu, by default, come with all the ports locked down and you need to open the ports in ubuntu by using the iptables command. Other flavours of linux behave similarly 

The commands below can be entered in a root terminal session to open the ports (TCP and UDP) 
[quote][I]iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
[/I] *iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT* [I]
<your_port_number>[/I] is the port number you have used for port forwarding (Avoid 6881-6999, any from 49125-65535 is fine) 

Once you've established the port is open you need to make the change persist through a reboot 
       > **create a file** /etc/init.d/iptables_azureus **and add the lines below**
        (sleep 220
         /sbin/iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
         /sbin/iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT ) &The *(sleep 220* is there to make the script wait a few minutes to allow subsequent firewall configuration scripts to run. 220 seconds is a large value and you may choose to configure a lower value. The key is that the opening of the azureus port is not countermanded by the firewall initialisation which runs later. At the end is a *) &* which allows the script to let the rest of the boot continue, while the script waits. 
    
> chmod +x /etc/init.d/iptables_azureus **make the file executable**
   update-rc.d iptables_azureus start 51 S . **links the file into the startup sequence**Your configuration change will then persist through reboots.[/quote]I can not understand what to do exactly, please help.

Thanks

---

### Post by lovinglinux on 2009-09-20
> Firstly the earlier notes on port forwarding for your router apply as before. Computers running Ubuntu, by default, come with all the ports locked down and you need to open the ports in ubuntu by using the iptables command. Other flavours of linux behave similarly

Don't worry, that's BS. In fact it's exactly the opposite. Ubuntu comes with all ports closed just because there are no servers listening to any ports, so any incoming connections are refused. Nevertheless, it also comes without any firewall rules, so when you install a server like a BitTorrent client, there is nothing preventing it from connecting to the outside world or accepting incoming connections.

Those instructions are for opening the incoming ports in the built-in firewall, but you don't really need them if you did not created any firewall rules in the first place.

Just to clarify, if you want to use the firewall, which is probably not necessary, there are easy ways of creating firewall rules. The recommended method is using a firewall manager like [gufw](apt:gufw) [apt-get].

Anyway, I suggest you read the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923), since it will help you configure your Ubuntu machine for BitTorrent and also troubleshoot connection issues.

I also recommend that you try out Deluge. It's the best BitTorrent client imo. It's a lot easier to configure than Vuze and doesn't have all those features that are not really necessary for torrenting. I have used a lot of BitTorrent clients, including Vuze for a long time, but Deluge offers the best combination of features and easy of use, not to mention the nice the interface and remote capabilities.

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

---

### Post by sandyd on 2009-09-20
you don't need to mess with the ports on Ubuntu, only with the ports on your router.

---

### Post by MertTheGreat on 2009-09-21
Thank you guys

---

