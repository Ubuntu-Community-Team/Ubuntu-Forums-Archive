---
title: "[iptables] Block WAN Access"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by Hoshimaru on 2007-10-04
Hello :)

Recently I've been asked by a few fellow students if I could open my wireless network for means of file sharing. It's a good idea, but everyone will be able to use my internet connection as well then. 
I had a D-Link DI-524 and it's very limited concerning rules for accessing the internet. It works only IP based and once someone uses a the right static IP, they do what they want.

So... to fix this, I replaced the DI-524 with a Linksys WRT54GL and flashed it with OpenWRT.

To grant access to my network, I thought of blocking WAN access for all clients, except my own.
Making a rules based on MAC addresses seems the best choice. I think it's quite hard to figure out which MAC address is allowed to go on internet compared to testing a few IP addresses.

So I installed iptables-mod-ipopt, loaded the ipt_mac kernel modules and did some reading about iptables. It's the first time I use iptables ^^"

The chain I've to use according to the OpenWRT doc is **forwarding_rule**.
I issued this command
```
iptables -A forwarding_rule -m mac --mac-source ! NN:NN:NN:NN:NN:NN - j drop
```
This worked like a charm. I could access the internet using the wireless connection, but not using the wired one. That's what I need.
So from this point, I added a similar line for the wired ethernet adapter.
```
iptables -A forwarding_rule -m mac --mac-source ! MM:MM:MM:MM:MM:MM - j drop
```
This didn't get the expected result. Instead I can't connect to the internet at all. Neither wired, nor wireless.

Is there a way in iptables to specify a rule to block every mac address except a limited list?
I've been searching for AND, OR,&& and || but that doesn't seem to exist!?

Any suggestions on how to solve this?

---

### Post by twistedtwig on 2007-10-04
at a guess I would say they are bumping into each other.  I would suggest drop ALL connections and only allow your two mac addresses.

iptables -A forwarding_rule -m mac  - j drop

iptables -A forwarding_rule -m mac --mac-source  NN:NN:NN:NN:NN:NN - j ACCEPT

the drop part is a guess. hope it helps point you... the idea is drop all then accept your two mac cards

---

### Post by Hoshimaru on 2007-10-04
> **twistedtwig said:**
> at a guess I would say they are bumping into each other.  I would suggest drop ALL connections and only allow your two mac addresses.

iptables -A forwarding_rule -m mac  - j drop

iptables -A forwarding_rule -m mac --mac-source  NN:NN:NN:NN:NN:NN - j ACCEPT

the drop part is a guess. hope it helps point you... the idea is drop all then accept your two mac cards

Thanks for your reply. The use of -m mac implies that you specify the MAC address using --mac-source, but what you said was a good idea I think. Maybe I should look into blocking any kind of connection and then accept these two mac addresses?
However I have this little feeling that it's not such a gentle solution.

---

### Post by Hoshimaru on 2007-10-04
Ok ... I've got it working.
I don't have any idea whether or not this is an gentle or rough rule and how much more load this would generate on such a small device.

These are the commands used:
```
iptables -A forwarding_rule -m mac --mac-source NN:NN:NN:NN:NN:NN -j ACCEPT
iptables -A forwarding_rule -m mac --mac-source MM:MM:MM:MM:MM:MM -j ACCEPT
iptables -A forwarding_rule -j DROP
```

---

