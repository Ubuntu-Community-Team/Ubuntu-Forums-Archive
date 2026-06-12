---
title: "Wireless not working with shared key"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by dandelions on 2007-06-03
A friend helped me install Feisty on Friday, connecting to the internet via a wired connection, and I've since attempted to set up my wireless network to work on it. It works when the network is set to Open- there's nothing wrong with the wireless setup in itself- but when I put it on Shared, it can't connect and eventually just errors out.

So, I have the following settings for the network: hidden SSID, 64-bit hex WEP key, Shared system. It will connect using that key and Open, but not on Shared. I am fairly sure hiding the SSID isn't changing anything. Please don't suggest I change any of those settings; I have to make my wireless work with the existing settings, since I'm not paying for the internet connection and my dad is a stubborn fan of what he believes to be security for the network. Any ideas for how to make Shared work?

---

### Post by dandelions on 2007-06-03
If double posting isn't allowed, please tell me and I'll get rid of this, but I thought it might help if I bumped this with the fix I used.

- Make sure the wireless network isn't set to Roaming and enter the SSID, network key, etc.
- In the terminal, enter sudo iwconfig- if you look at what it says, the Security mode is probably still set to open, despite specifying Shared.
- Enter sudo gedit /etc/network/interfaces
- Scroll down to the bit where your network is listed- ssid, key, etc- and first check the key is correct, then when you're sure it is, put a space after it and write restricted. That section of the file should look something like this:
wireless-essid NETWORKNAME
wireless-key 1234567890 restricted
where 1234567890 is your actual network key and NETWORKNAME is your SSID. Save the file and close it.
- Back in the terminal, enter /etc/init.d/networking restart
- Once that's cycled through, ping google or somewhere similarly reliable. Voila, internet.

---

### Post by pee_gee_l on 2007-06-04
I just want to thank you, this ended my weeks of frustration :)

---

