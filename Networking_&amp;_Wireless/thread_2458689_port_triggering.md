---
title: "port triggering"
date: 2021-03-02
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2021-03-02
I am trying to set up a port trigger over WAN on a remote asus router (rt ac 88u) for rdp access. I understand port forwarding but am trying to make use of port triggering with no luck. The remote xubuntu computer has the firewall allowing 3389 and 3355. So I am trying to have rdp go to the remote router on 3355 and then the remote xubuntu on 3389. So I have remmina set to the remote ip:port 3355. It doesn't work. I also tried reversing the numbers on port triggering and still no luck. I have total access to the remote router and computer.

[ATTACH=CONFIG]288041[/ATTACH]

---

### Post by TheFu on 2021-03-02
Allowing rdp over the internet is a security failure.  **Use a VPN** and tunnel the rdp traffic through that. 
[https://www.techrepublic.com/article/how-to-better-secure-your-microsoft-remote-desktop-protocol-connections](https://www.techrepublic.com/article/how-to-better-secure-your-microsoft-remote-desktop-protocol-connections)

Every week, are international stories about how some utility/infrastructure IT person decided to allow rdp into work for convenience and got hacked. Please don't do it. 

Use x2go into a Linux machine over the internet if you don't want a full VPN. x2go just needs ssh, which we know how to secure.

I've never heard of a router specifically supporting port triggering. Where is the magic packet specified to open the service?

I'll go away now.

---

