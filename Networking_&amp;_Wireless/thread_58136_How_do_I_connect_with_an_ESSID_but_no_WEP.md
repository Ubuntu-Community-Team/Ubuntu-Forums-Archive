---
title: "How do I connect with an ESSID but no WEP"
date: 2005-08-18
forum: Networking &amp; Wireless
---

### Post by schmidty on 2005-08-18
I have a Linksys WPC54G PCMCIA card plugged into my laptop and have it working fine with my local wireless connection. I go to 'networking' and punch in the ESSID and WEP key and have it up an running with no problems. 

The issue is that my neighbor has a wireless signal that I would like to connect to but can't seem to. When I do an 'iwlist wlan0 scan' I get all the necessary info but no WEP key, even with an 'iwlist wlan0 key'. What do I put in the WEP key text box if the wireless signal doesn't have WEP up and running (i.e - no security)?  ](*,) 

Hope this is clear. I'm kinda new to wireless networking... :wink: 

Schmidty

---

### Post by drummer on 2005-08-19
[QUOTE=schmidty]I have a Linksys WPC54G PCMCIA card plugged into my laptop and have it working fine with my local wireless connection. I go to 'networking' and punch in the ESSID and WEP key and have it up an running with no problems. 

The issue is that my neighbor has a wireless signal that I would like to connect to but can't seem to. When I do an 'iwlist wlan0 scan' I get all the necessary info but no WEP key, even with an 'iwlist wlan0 key'. What do I put in the WEP key text box if the wireless signal doesn't have WEP up and running (i.e - no security)?  ](*,) 

Hope this is clear. I'm kinda new to wireless networking... :wink: 

Schmidty[/QUOTE]
 You can use wireless without WEP if it isn't enabled on your neighbour's router, just don't enter a key or select 'no security' or somesuch in the connection settings area. In the gnome networking interface, you can also create different profiles so that you can select to connect to your or another router easily, without reentering info & keys, etc.

Hope that helps.

---

