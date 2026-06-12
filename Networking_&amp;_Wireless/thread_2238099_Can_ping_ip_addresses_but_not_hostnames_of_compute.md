---
title: "Can ping ip addresses but not hostnames of computers on network"
date: 2014-08-06
forum: Networking &amp; Wireless
---

### Post by opus1 on 2014-08-06
Short version: I can ping the ip address but not the hostnames of the computers on the network (that is: "ping 192.168.1.100" works but "ping zippy.local" doesn't).  Only one computer on a 5 computer home network is having this problem.  All 5 computers have the same xubuntu precise install (I cloned the settings and home directories).  All are up-to-date with updates.  All 5 have static IP addresses. Basically, they're all the same, but one isn't working right and I don't know where to begin to troubleshoot.

This creates a ton of problems for me since the fstab entry for my fileserverand several cron jobs use hostnames. 

Plus, I ssh between machines quite often and it is behaving the same way: ssh by ip works, ssh by hostname does not.

Longer version (in addition to the above):  To make things easy, we'll call the troublesome computer "opus" and the fileserver "zippy". "Opus" worked fine until tonight. About a month ago I had to change all the computers on the network from dynamic to static IP addresses. A couple of weeks ago I shut all the machines down, went on vacation, and started them all up when I got back.  "Opus" worked fine. on Saturday, I updated "opus" (I think it had to reboot afterwards).  Sunday, I used "opus" and could still mount "zippy" (the fileserver). Today, my son rebooted it and when I got home, "zippy" couldn't be mounted ("mount.nfs: Failed to resolve server zippy.local: Name or service not known").  

I started troubleshooting by doing "ping zippy.local" and got "unknown host zippy.local".  Doing "ping 192.168.1.100" worked fine. I did a "avahi-browse -at" and "opus" can see itself and one other machine on the network, but none others (although I couldn't successfully ping the one machine it could see by using the hostname).

When I go to another computer on the network ("tux"), I cannot ping or ssh "opus" using hostname, but can using ip address. "tux" can ping and ssh all the other computers on the network using both  hostname and ip. So, there seems to be something fundamentally wrong with "opus".

I really don't know where to begin troubleshooting.  I looked at the log file and found nothing suspicious. I couldn't find the exact problem by googling for 2 hours.  I reset the machine to dynamic ip addressing, but that didn't work. I've rebooted a half dozen times. I turned off the ufw (uncomplicated firewall).  None of this solved the issue.

I realize I should be posting more detailed info (e.g., log files, etc.) but I am such a newbie at hostname issues that I don't even know where to begin.  Host names have "just worked" up until this point! :p

I'll be happy to provide any additional info to help diagnose the problem. Thanks!

---

### Post by opus1 on 2014-08-23
Well, I have not been able to find any help on the internet to diagnose the root cause of the problem.  I found a way to work around it, which is a pretty fundemental solution, and that is to add all the computers in my network to the /etc/hosts file of the computer that isn't working right (in the previous example "Opus"). in the /etc/hosts file I put the following entries:
```

192.168.1.100     zippy.local
192.168.1.101     tux.local

```
so now, on "opus" I can do a "ping zippy.local" or a "ssh [email]me@zippy.local[/email]" and it works as expected.  Similarly, I added the ip address and host name for "opus" to the /etc/hosts files of all the other computers in the network.

While this technically solves the problem, I'm not sure if I should mark this solved since I haven't fixed the root cause of the problem.  I don't even know what the root cause of the problem is, so I would appreciate any suggestions.

---

### Post by steeldriver on 2014-08-23
Is the avahi daemon running on the troublesome computer?

```

service avahi-daemon status

sudo lsof -i :5353

```

What do you get if you run 

```

avahi-browse -a

```

---

