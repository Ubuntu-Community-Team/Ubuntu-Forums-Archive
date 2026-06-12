---
title: "Accessing an Ubuntu Server on a private network via the Internet"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by zoon_unit on 2010-05-23
I am doing Drupal cms development on a local Ubuntu server on my private network.  Everything works fine, but I want to access my server securely over the Internet when traveling.

I want to be able to do the following:

1) Access my server via openssh over the Internet
2) Access my server's Drupal web pages over the Internet
3) Do it all SECURELY without the dangers of hackers accessing my local server.

Here's my current setup:

I have a private network that includes Windows XP, Windows 7 and my Ubuntu server, all working properly using Samba.

My private network is behind a firewalled router.  My question is this: Do I need a VPN, even though my router provides firewall capability?  Can I access my Ubuntu server using SSH by providing the router's IP address?  If so, how can I access the Ubuntu server's web server through the Internet?

My router allows me to "punch through" the firewall by defining which ports I can access through the router to which device, but I assume that ANYONE who uses these ports would have access to my server.  (obviously, they couldn't get SSH access without the password, but what about web access?) I want to limit access to myself with some kind of functionality similar to a VPN.

Is that what I need? Or is there a simpler way? (remember, I need SSH and Web access) If so, what is a reasonably secure and easy configuration?  Poptop?  OpenVPN?  Other?

---

### Post by nhasian on 2010-05-23
I wonder if this would be better answered if you post it instead to [Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338") or [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")

yes though your right, you need to install the package openssh-server if you would like to ssh into your server.  also you need to forward the ports (or punch holes in your firewall as you described) to forward the ports of the apps you want to use.  port 22 for ssh, port 80 for web and port 443 for secure http, etc.

---

