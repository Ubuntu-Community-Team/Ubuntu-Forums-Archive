---
title: "While comes first the forward or the firewall"
date: 2018-02-11
forum: Networking &amp; Wireless
---

### Post by Andrew_Welham on 2018-02-11
I have a feeling i know the answer, however

if i have a ubuntu server with multiple interfaces. One internet facing and the other internal facing. The internal facing interface has multiple IP addresses.
I have the [FONT=Consolas][COLOR=#111111]net.ipv4.ip_forward=1 set and all routes ok.[/COLOR][/FONT]

[FONT=Consolas][COLOR=#111111]However i cant seem to stop packets via  iptables   packets from one of the ip range on the internal nic to another ip range on the same inerface.[/COLOR][/FONT]
[FONT=Consolas][COLOR=#111111]
I image this is because the forwarding happens before the data flows through iptables?[/COLOR][/FONT]

[FONT=Consolas][COLOR=#111111]Can anyone confirm is this is correct and also if it is possible to change the order.

[/COLOR][/FONT]The OS being used is Ubuntu 18.04, and there is NO NAT, nor should there be.

[FONT=Consolas][COLOR=#111111]Kind Regards[/COLOR][/FONT]
[FONT=Consolas][COLOR=#111111]Andrew[/COLOR][/FONT]

---

### Post by SeijiSensei on 2018-02-11
Suppose the networks you want to block are 192.168.1.0/24 and 192.168.2.0/24.  Then I'd add these rules to the firewall:
```

sudo iptables -I FORWARD -s 192.168.1.0/24 -d 192.168.2.0/24 -j REJECT
sudo iptables -I FORWARD -s 192.168.2.0/24 -d 192.168.2.0/24 -j REJECT

```

---

### Post by Andrew_Welham on 2018-02-12
[COLOR=#000000][FONT=MS Shell Dlg 2]
I had 

```

$IPTABLES -N RULE_7[/FONT][/COLOR]
[COLOR=#000000][FONT=MS Shell Dlg 2]$IPTABLES -A FORWARD  -s 192.168.1.4   -d 192.168.0.7   -j RULE_7[/FONT][/COLOR]
[COLOR=#000000][FONT=MS Shell Dlg 2]$IPTABLES -A RULE_7  -j LOG  --log-level info --log-prefix "RULE 7 -- DENY "[/FONT][/COLOR]
[FONT=MS Shell Dlg 2][COLOR=#000000]$IPTABLES -A RULE_7  -j DROP[/COLOR][/FONT]

```

[FONT=MS Shell Dlg 2][COLOR=#000000]Which did not work, and i'm wondering if it is to do with both ip address ranges being on the same interface, and the kernel routing being processes before the iptables rules.
If this is the case, is there a way to change the order?

[/COLOR][/FONT]

---

### Post by SeijiSensei on 2018-02-15
It depends on where these rules lie in the chain.  Perhaps the traffic is being permitted by a rule above the one you cite.

You'll notice I used -I rather than -A to ensure that the forwarding rules were above everything else.

---

### Post by Andrew_Welham on 2018-02-18
If i change the IP's to individual NICS it works, so I can only assume (probably make me an idiot) the kernel gets to the packet first

---

