---
title: "[SOLVED] no-ip and connecting through it"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by ene_dene on 2008-02-29
With no-ip you can have a known address of your computer at any time. I have registered on their site, and installed their software. When you run the noip2 -C you enter the account information that you gave on no-ip site and then you start a service which sends your current ip address to their computer and you get an address for example bla.no-ip.org. Here's how it looks when you run info on service:
```
someone@bla:~$ sudo noip2 -S
[sudo] password for someone:
1 noip2 process active.

Process 24340, started as noip2, (version 2.1.7)
Using configuration from /usr/local/etc/no-ip2.conf
Last IP Address set 79.11.53.218
Account someone@gmail.com
configured for:
        host  bla.no-ip.org
Updating every 5 minutes via /dev/eth0 with NAT enabled.
1 noip2 process active.
```
When I go to their site they have my host updated.
Now if I wanted to connect to my host by ssh, I would write:
```
ssh someone@bla.no-ip.org
```,
and I should be asked a password for user someone. But nothing happens. For example if I write:
```
ssh someone@192.168.0.1
```
I do get connected and I'm asked a password.
When I look at the firewall activity (I have firestarter) it doesn't block anything when I'm trying to connect to my host by address given by no-ip.

What am I doing wrong?

---

### Post by ruy_lopez on 2008-02-29
The no-ip hostname points to the external IP address of your router.

When you connect using ssh you are supplying a private (internal) IP address. You cannot connect using the no-ip hostname because you do not have port forwarding enabled. It is your router's firewall that is blocking incoming connections.

Enable port forwarding on port 22 (on your router's config page) to point to an address inside your network. Make sure you have a good ssh password.

Whenever I enable port forwarding for SSH, and use a no-ip hostname, I get lots of brute force attempts on my password.

---

### Post by .nedberg on 2008-02-29
> **ruy_lopez said:**
> 
Enable port forwarding on port 22 (on your router's config page) to point to an address inside your network. Make sure you have a good ssh password.

Whenever I enable port forwarding for SSH, and use a no-ip hostname, I get lots of brute force attempts on my password.

I would recommend moving to a different port and maybe use fail2ban to stop those brut force attempts!

---

### Post by ruy_lopez on 2008-02-29
> **.nedberg said:**
> I would recommend moving to a different port and maybe use fail2ban to stop those brut force attempts!

Good idea. Or use public keys.

---

### Post by ene_dene on 2008-02-29
> The no-ip hostname points to the external IP address of your router.

When you connect using ssh you are supplying a private (internal) IP address. You cannot connect using the no-ip hostname because you do not have port forwarding enabled. It is your router's firewall that is blocking incoming connections.

Enable port forwarding on port 22 (on your router's config page) to point to an address inside your network. Make sure you have a good ssh password.

Whenever I enable port forwarding for SSH, and use a no-ip hostname, I get lots of brute force attempts on my password.
Yes, it works! Thank you Ruy_Lopez (3.Bb5!).

> I would recommend moving to a different port and maybe use fail2ban to stop those brut force attempts!
Yes, I will do that. Thank you!

---

