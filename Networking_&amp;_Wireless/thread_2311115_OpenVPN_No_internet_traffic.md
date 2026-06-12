---
title: "OpenVPN No internet traffic"
date: 2016-01-24
forum: Networking &amp; Wireless
---

### Post by KoW210 on 2016-01-24
So I set up a fresh VPS with Ubuntu 14.04 X86 64. I am trying to set up a personal VPN. I have used this guide - [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04) which has me installing ufw, uncomplicated firewall. Both my phone and my desktop, which have two seperate keys and such, can both connect to it no problem but there's no traffic at all. I have tried disabling ufw, triple checking everything, especially with the firewall and iptables. I tried this guide - [http://arashmilani.com/post?id=53](http://arashmilani.com/post?id=53) and it didn't work either. I'm not sure where to start.

---

### Post by QDR06VV9 on 2016-01-24
You know I just Love digital ocean for other reference's but not this one..
Have a look here  [http://learnaholic.me/2014/01/09/ubuntu-vps-step-by-step-config-notes/](http://learnaholic.me/2014/01/09/ubuntu-vps-step-by-step-config-notes/)
Good Luck..

---

### Post by KoW210 on 2016-01-24
> **runrickus said:**
> You know I just Love digital ocean for other reference's but not this one..
Have a look here  [http://learnaholic.me/2014/01/09/ubuntu-vps-step-by-step-config-notes/](http://learnaholic.me/2014/01/09/ubuntu-vps-step-by-step-config-notes/)
Good Luck..

That's how to config a fresh VPS, which is fine, but I'm having trouble getting my VPN to work.

---

### Post by QDR06VV9 on 2016-01-24
> **KoW210 said:**
> That's how to config a fresh VPS, which is fine, but I'm having trouble getting my VPN to work.
Ok that would have been good to know..:D
Personal VPN(Free) or a subscribed VPN?
What have you done so far? Besides the links you sent.

---

### Post by KoW210 on 2016-01-24
> **runrickus said:**
> Ok that would have been good to know..:D
Personal VPN(Free) or a subscribed VPN?
What have you done so far? Besides the links you sent.

I thought it was obvious... 

It's a personal VPN, I'm using OpenVPN.

Anyways I have installed and configured OpenVPN. I have created keys and such for all the devices that will be connected to it. I have installed ufw and configured it. I have also changed the iptable to allow OpenVPN to work. All of my devices connect to the VPN fine but there's no traffic at all. Nothing is getting through. I have tried disabled ufw, and double checked everything and I still can't get it to work.

Interesting enough when I connect to the VPN with the Windows program it says that it has connected and the ip has been assigned to 10.8.0.10, which is not the IP of the VPN server.

I've tried changing all instances of eth0 to venet0:0 which is what it says in ifconfig and it still doesn't work. Time to try something else.

---

### Post by KoW210 on 2016-01-24
I just tried this script and it works. Thanks - [https://github.com/Nyr/openvpn-install](https://github.com/Nyr/openvpn-install)

---

