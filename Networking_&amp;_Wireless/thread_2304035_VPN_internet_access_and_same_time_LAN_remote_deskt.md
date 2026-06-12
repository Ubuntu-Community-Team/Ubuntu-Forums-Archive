---
title: "VPN internet access and same time LAN remote desktop, is this possible?"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by Janiporo on 2015-11-23
So I have "headless" Ubuntu 14.04 32 bit machine in my home network, that I control with remote desktop only via said network, I do have monitor, keyboard and mouse for it for limited use, but in the end I will NOT be using these after setting up VPN-service do to the location of the computer. Please do not try to solve this by saying "move the computer". It is where it is and stays there.

Question is, when I set up VPN-connection to the internet from this headless machine, can I use my home LAN to connect to headless machine with remote desktop somehow? I have learned that it might be difficult, since it tunnels all traffic to the internet when using VPN.

 Does anybody have any idea that can this be done? Or has someone allready done this? :roll:

 Thanks in advance ;)

---

### Post by ozzie1 on 2015-11-23
when you set up the vpn, it should only effect traffic going outside of your local LAN, you should still be able to VNC to your headless box on the same IP as always. you could have a configuration issue that would break it, but as a rule it shouldn't be a problem.

---

### Post by Janiporo on 2015-11-23
Ok, thanks a lot! That was fast :3

---

### Post by matt_symes on 2015-11-23
Hi

If you have a compatible desktop environment, take a look at x2go. That may work for you.

[http://wiki.x2go.org/doku.php/doc:de-compat](http://wiki.x2go.org/doku.php/doc:de-compat)
[https://launchpad.net/~x2go/+archive/ubuntu/stable](https://launchpad.net/~x2go/+archive/ubuntu/stable)

It's routed over ssh so can be accessed over the LAN and Internet like any ssh session. Just port forward on your router. Configure ssh and use keys and not password authentication.

Kind regards

---

### Post by ozzie1 on 2015-11-23
You're welcome! I happened to be lurking hoping for an answer to my own vpn questions, I'm setting up an openvpn server to access a business network remotely ;)

---

### Post by Janiporo on 2015-11-24
Remote desktop works fine inside LAN with active VPN connection. No problems there, thanks ozzie1 :3

---

