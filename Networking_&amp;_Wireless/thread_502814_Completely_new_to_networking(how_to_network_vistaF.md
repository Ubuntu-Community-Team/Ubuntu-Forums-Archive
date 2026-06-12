---
title: "Completely new to networking(how to: network vista/Feisty, just to share internet)"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by nite owl on 2007-07-17
Hi I am completely new to networking and do not know what I should research into, hubs or routers? etc... or what equipment I need. My desktop(running Feisty) is the one connected to the internet through a usb modem that picks up wireless internet(So I cannot just have a router connected to the modem, because theres no ethernet interface on the modem)I would like to completely protect my new notebook(Vista bus) from the internet so I was thinking putting a firewall router between my desktop and my notebook?? So the setup would be (usb modem -> desktop -> router -> notebook) would this be possible? Anyway just looking for some advice on some hardware I should look at and the cableing I'll need. This network does not have to do anything else other then connecting the notebook to the internet(no file sharing capabilities etc.. are needed) Thanks

---

### Post by nite owl on 2007-07-17
I basically just need to know what hardware is required for this setup, what software would I need to install on my desktop/notebook and what type of cableing I would need. Thanks

---

### Post by alex77 on 2007-07-17
Ok, you dont need to install any extra software, everything you need is already built into your opereating systems. What you do need is an adsl router, (i assume you are on an adsl line?) Into this you plug your laptop and desktop using cat5 cables, and plug the router into the phone socket. You can chuck your usb modem.

The adsl router acts as a hardware firewall. Don't go spending extra money on a router that explicitly says its a firewall too, the  NAT in a router hides your computers from the Internet which makes it a simple and effective firewall. A hardware firewall is a more expensive bit of kit that probably does other cool stuff like stateful packet inspection, but isnt really necessary. 

You will still need software firewalls on both your computers to monitor outbound connections.

```

PC      >> 
              ADSL Router >> Phoneline
Laptop  >>

```

---

### Post by nite owl on 2007-07-17
Hi thanks for your reply alex. Actually I am not on adsl because I am too far from the exchange. I am on wireless broadband(doesn't go through phone lines or cables). However the only interface on the modem is a usb port to connect to the computer

---

### Post by alex77 on 2007-07-17
I'm not sure i understand- if you aren't connected to a phone line or cable, why do you have a modem? Where does the wireless broadband signal come from that you are picking up?

Could you post the make and model no of your modem?

---

