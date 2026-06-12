---
title: "Can't get SSH working outside my network"
date: 2014-12-05
forum: Networking &amp; Wireless
---

### Post by brianatlarge on 2014-12-05
So here's  the deal. I've got Ubuntu server running in a VM in Virtualbox with a  bridged adapter on a static IP. My router has port 22 forwarded to that  static IP (192.168.1.10). I can not get SSH working outside my network.


  I know my ISP is not blocking port 22, I know my router is forwarding  port 22 correctly, and I know virtualbox is not messing up port  forwarding, because for testing purposes, I loaded up a VM of Windows 7  and installed an SSH server program called Bitvise SSH server and I was  successfully able to see port 22 on the WAN set up that way, so I know  now it's not my ISP, it's not my router. 

For my router situation,  I was previously using a Linksys EA2700 as my router, but I was still  having the same issues with getting SSH to work even through port 22 was  set up for my servers static IP. I swapped the router out for an older  WRT54G I had that has Tomato 1.28 firmware installed so hopefully that  would give me more control, fix the problem, or just give me more  visibility into the issue for debugging.

Since my ISP is not blocking port 22, my router can forward port 22, and VirtualBox is not interfering with passing the forwarded traffic, it has something to do with  Ubuntu as far as why I can't get SSH working on the WAN.


  I'm running Tomato 1.28 as my routers firmware. Here is my routers iptable: [http://pastebin.com/S7JSr4Bd](http://pastebin.com/S7JSr4Bd)
  Here is an example of the routers log showing the router is accepting traffic from port 22 and sending it to the correct IP: [URL="http://pastebin.com/cGN2m9Nd"]http://pastebin.com/cGN2m9Nd
[/URL]sshd is running: [http://pastebin.com/8G74tg3H](http://pastebin.com/8G74tg3H)
  Here is my sshd config file on my server: [http://pastebin.com/REXs7Pxq](http://pastebin.com/REXs7Pxq)
  Here is the iptables on my server: [http://pastebin.com/9Cjsj90j](http://pastebin.com/9Cjsj90j)
  Here is netstat for the listening ports: [http://pastebin.com/nfQcLTVC](http://pastebin.com/nfQcLTVC)
  Here is the results from nmap from both outside my network and inside: [URL="http://pastebin.com/LyHGjrkd"]http://pastebin.com/LyHGjrkd
[/URL]Results from nmap -Pn: [http://pastebin.com/n5zU9kig](http://pastebin.com/n5zU9kig)
  Finally here's a verbose SSH connection on my LAN: [http://pastebin.com/eMEMPFtd](http://pastebin.com/eMEMPFtd)
  
As you can see I've done extensive Googling on this issue and have  done everything and checked everything I can think of. I'm at a loss.  What am I missing?

EDIT: I also have apache running and can access websites on this server on my LAN, but not on the WAN when port 80 is forwarded.

Apache is running: [http://pastebin.com/VNqywYQg](http://pastebin.com/VNqywYQg)
Apache conf: [http://pastebin.com/Lvg0xhuj](http://pastebin.com/Lvg0xhuj)
Ports conf: [http://pastebin.com/FX1CGTVU](http://pastebin.com/FX1CGTVU)
Default vhost: [http://pastebin.com/0ZFXdbbd](http://pastebin.com/0ZFXdbbd)
Symlink in sites enabled: [http://pastebin.com/bK0nW91b](http://pastebin.com/bK0nW91b)

EDIT EDIT: I have an OpenVPN tunnel running. I turned it off and traffic was able to pass. I guess writing it all out helped me narrow things down.

On this note, any tips on getting SSH traffic to pass through eth0 instead of tun0? I'm guessing I need to put in some static routes on my server?

---

### Post by TheFu on 2014-12-05
In the sshd_config file (/etc/ssh/sshd_config), you can specify which ip address will be used to listen by sshd. [http://serverfault.com/questions/605446/make-sshd-listen-to-a-specific-interface](http://serverfault.com/questions/605446/make-sshd-listen-to-a-specific-interface) It doesn't seem possible to specify an interface, just an IP.

Before reading everything, I was thinking you had either setup iptables to block external ssh connections or that tcp-wrappers was getting in the way. tcp-wrappers is managed by the /etc/ hosts.allow and hosts.deny files. These may be helpful in the future.  I'd also strongly suggest using fail2ban and ssh-keys (test it to be certain it is working) to prevent brute force attacks. Do not use passwords for ssh logins on the internet. That is just asking for trouble.

---

