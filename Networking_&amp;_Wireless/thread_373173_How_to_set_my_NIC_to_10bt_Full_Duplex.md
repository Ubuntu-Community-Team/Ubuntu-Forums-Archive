---
title: "How to set my NIC to 10bt Full Duplex?"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by reyfer on 2007-03-01
Hi

I have been looking around and I have found some people with my same problem, but seems only a few got where the problem lies: whenever the power goes down here, once I restart my onboard network card doesn't work on Kubuntu, but it does on Windows. I found out it's because when the power comes back, the card starts with autonegociation on, and my router needs the card to connect at 10BT Full Duplex. I have to start Windows every time so the driver there sets the connection to 10BT, so I can reboot to Kubuntu with that setting.
Is there a way to set the connection type in Kubuntu or Ubuntu? That way I can finally get rid of the MS OS. Thanks

---

### Post by reyfer on 2007-03-01
Found an answer on another forum: on terminal type
```
sudo ethtool -s eth0 speed 10 duplex full autoneg off
```

Problem now is that I have to type it everytime I restart.

---

