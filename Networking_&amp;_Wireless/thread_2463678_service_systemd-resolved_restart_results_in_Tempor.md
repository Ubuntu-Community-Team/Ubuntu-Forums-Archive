---
title: "service systemd-resolved restart results in Temporary failure in name resolution"
date: 2021-06-16
forum: Networking &amp; Wireless
---

### Post by killwarez on 2021-06-16
EDIT - solution here - [https://ubuntuforums.org/showthread.php?t=2463678&p=14043964#post14043964](https://ubuntuforums.org/showthread.php?t=2463678&p=14043964#post14043964)

Hi All, I hope I am posting in the correct section. 

I run pihole and plex server on x86 version of ubuntu (18.04). This setup has worked for quite a while (over a year), but today I noticed that I cannot reach my Plex server from the outside. I SSHd into the box and ping results in:

[FONT=Arial]**ping google.com returns:**[/FONT]
[FONT=Arial]ping: google.com: Temporary failure in name resolution

**pinging an ip works fine:**
[/FONT][FONT=Arial]ping 8.8.8.8[/FONT]
[FONT=Arial]PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.[/FONT]
[FONT=Arial]64 bytes from 8.8.8.8: icmp_seq=1 ttl=118 time=10.9 ms[/FONT]
[FONT=Arial]64 bytes from 8.8.8.8: icmp_seq=2 ttl=118 time=10.9 ms[/FONT]
[FONT=Arial]64 bytes from 8.8.8.8: icmp_seq=3 ttl=118 time=12.2 ms[/FONT]
[FONT=Arial]^C[/FONT]
[FONT=Arial]--- 8.8.8.8 ping statistics ---[/FONT]
[FONT=Arial]3 packets transmitted, 3 received, 0% packet loss, time 2002ms[/FONT]
[FONT=Arial]rtt min/avg/max/mdev = 10.903/11.371/12.213/0.608 ms

[/FONT][FONT=Arial]Interestingly all of my clients on the network are able to be routed through pihole on this server and reach the outside, no issues. It is only the server itself that is unable to resolve DNS.

After doing some digging I was able to work around the issue by adding 
**nameserver 1.1.1.1** (or any other DNS server) to **resolv.conf**

This allows the server to resolve DNS and everything is fine. While this works for now, any sort of  [/FONT][FONT=Arial]**service systemd-resolved restart **[/FONT][FONT=Arial]overwrites that file and breaks things again. When this happens contents of it are:

[/FONT][FONT=Arial]nameserver 127.0.0.53[/FONT]
[FONT=Arial]options edns0

[/FONT][FONT=Arial]now my question is. What is the proper way to fix this? Is there some other place I need to set DNS resolver in Ubuntu? Id like to make sure that all of the LAN traffic is still routed through pihole though and does not somehow bypass it.

Thanks!


[/FONT]

---

### Post by TheFu on 2021-06-16
systemd-resolved is completely optional and not needed on networks with a DNS server.  
You can stop the service, mask it, and manually setup a non-symbolic link /etc/resolv.conf file to point at your pi-hole setup.
Adding a non-pi-hole nameserver defeats the protection that a pi-hole provides. Good for emergency use, but don't leave it that way.

The challenge comes from laptops and other portable computers that need to behave different based on the network connected.

A DNS server really needs to be on a non-desktop system. Just sayin'.

---

### Post by killwarez on 2021-06-16
> **TheFu said:**
> systemd-resolved is completely optional and not needed on networks with a DNS server.  
You can stop the service, mask it, and manually setup a non-symbolic link /etc/resolv.conf file to point at your pi-hole setup.
Adding a non-pi-hole nameserver defeats the protection that a pi-hole provides. Good for emergency use, but don't leave it that way.

The challenge comes from laptops and other portable computers that need to behave different based on the network connected.

A DNS server really needs to be on a non-desktop system. Just sayin'.

Thanks for the reply. Can you clarify on what you mean DNS server needs to be on non-desktop system? This is a Ubuntu headless server, not a computer someone uses as a Desktop. By x86 i was just conveying that this isnt an ARM system, i.e. I am running the full stack 18.04 server not a specialized build of 18.04.

Since Pi-Hole is running on the same server, how do I point /etc/resolv.conf to it? It would have to be some sort of loopback?

Thanks!

---

### Post by killwarez on 2021-06-16
Ok , I attempted to use netplan to add DNS servers:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: false
      dhcp6: false
      addresses:
        - 192.168.1.79/24
      gateway4: 192.168.1.1
      nameservers:
        addresses: [ "1.1.1.1", "8.8.8.8" ]
        search: []



```
But sad to report, no improvement. Same issue.

---

### Post by killwarez on 2021-06-16
Ok figured it out. Whoever is doing development on Ubuntu needs to stop changing things around so much that pretty much any documentation you look at is obsolete.

So the issue was that in 18.04 resolv.conf is no longer used and instead netplan is used. Fine. No problem.

But then why the heck not just use the same old symlink location? 

```
resolv.conf -> ../run/systemd/resolve/stub-resolv.conf
```

For some reason that is still the symlink, YET netplan edits this file instead 

```
resolv.conf -> /run/systemd/resolve/resolv.conf
```

So you cant just use netplan to edit the DNS, you have to also change the symlink location. Now that I pointed it to the correct file that netplan actually does modify everything is working.

Frustrating to spend a day debugging issues that were really in my opinion created unnecessarily. I am all for improving and making things better, but in this case here, seeing how netplan edits a file that is not actually used for config.. its like someone dropped the ball at the last yard.

---

### Post by TheFu on 2021-06-17
> **killwarez said:**
> Frustrating to spend a day debugging issues that were really in my opinion created unnecessarily. I am all for improving and making things better, but in this case here, seeing how netplan edits a file that is not actually used for config.. its like someone dropped the ball at the last yard.

a) You are preaching to the choir.  DNS setup has been a complaint of mine since they forced resolvconf (the package) onto everyone to fix problems I never had.  editing /etc/resolv.conf has always been possible, since at least 1991. It just works.

b) People running a DNS have different needs than the rest of the world, especially for desktops expected to be used by grandmas.

c) The symlink is a systemd issue. It has nothing at all to do with netplan.  Blame the right project.  Systemd broke lots of things, and years later, it is clear some will never be fixed.  In general, whenever systemd breaks something, I rip out that part and use whatever worked previously. Sometimes that isn't possible.  systemd-resolved, systemd-time, systemd-automount are 3 things I remove.  They are overly complex.  If I could, I remove systemd-mount so the old **sudo touch /forcefsck** worked again. I really miss that capability.

Regardless, happy you found a solution.  You'll not forget it soon.  

There are lots of things like that in every OS. Learning each comes with time, experience, and mentoring.  For example, the last line of every config file needs to be a blank/empty line. I learned that the hard way.  While having every config file setup that way isn't always mandatory, the few times where the config file parser fails will convince you to do it for every file you touch.  EOL and EOF are **not** the same. Just sayin'. Parsers care when they are looking for EOL for every "line" to apply a setting and only get an EOF for the very last line.

Please mark this thread as SOLVED - thread tools button near the top. Only you can do that and it really helps save the community time. Not just today, but for years going forward.

---

### Post by SeijiSensei on 2021-06-17
The best solution is to edit /etc/systemd/resolved.conf and add the DNS servers you want to use to the "DNS" and "FallbackDNS" lines. Then restart systemd-resolved.

---

### Post by killwarez on 2021-06-17
> **TheFu said:**
> a) You are preaching to the choir.  DNS setup has been a complaint of mine since they forced resolvconf (the package) onto everyone to fix problems I never had.  editing /etc/resolv.conf has always been possible, since at least 1991. It just works.

b) People running a DNS have different needs than the rest of the world, especially for desktops expected to be used by grandmas.

c) The symlink is a systemd issue. It has nothing at all to do with netplan.  Blame the right project.  Systemd broke lots of things, and years later, it is clear some will never be fixed.  In general, whenever systemd breaks something, I rip out that part and use whatever worked previously. Sometimes that isn't possible.  systemd-resolved, systemd-time, systemd-automount are 3 things I remove.  They are overly complex.  If I could, I remove systemd-mount so the old **sudo touch /forcefsck** worked again. I really miss that capability.

Regardless, happy you found a solution.  You'll not forget it soon.  

There are lots of things like that in every OS. Learning each comes with time, experience, and mentoring.  For example, the last line of every config file needs to be a blank/empty line. I learned that the hard way.  While having every config file setup that way isn't always mandatory, the few times where the config file parser fails will convince you to do it for every file you touch.  EOL and EOF are **not** the same. Just sayin'. Parsers care when they are looking for EOL for every "line" to apply a setting and only get an EOF for the very last line.

Please mark this thread as SOLVED - thread tools button near the top. Only you can do that and it really helps save the community time. Not just today, but for years going forward.

Marked as solved. Unfortunately editing /etc/resolv.conf wasnt really working as I mentioned, my changes would work for a short time (less than 24 hours) then get overwritten by some process (still not sure which)

---

### Post by TheFu on 2021-06-17
> **killwarez said:**
> Marked as solved. Unfortunately editing /etc/resolv.conf wasnt really working as I mentioned, my changes would work for a short time (less than 24 hours) then get overwritten by some process (still not sure which)

a) /etc/resolv.conf is usually a symbolic link to somewhere else.  Quickly break that link and put the /etc/resolv.conf you want there.

b) the process that would try to update the /etc/resolv.conf is either systemd-resolved or resolvconf.  Disable and "mask" both of those and this won't happen again.

There are lots of tools that can help determine which process is opening a file.  **lsof** is one of those.  Google is another.

---

