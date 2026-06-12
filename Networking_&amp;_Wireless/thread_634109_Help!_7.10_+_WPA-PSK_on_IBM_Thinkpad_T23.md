---
title: "Help! 7.10 + WPA-PSK on IBM Thinkpad T23"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by bubuyaga on 2007-12-07
I am trying to connect to a wireless network with an IBM THinkpad T23 using Ubuntu 7.10.
The laptop has a built in wireless "minipci" card, that some googling suggests is an Intersil Prism 2.5 (though I do not know how to verify this). I have successfully connected to another open network and yet another one using "browser identification". Also, the laptop does see the wireless network and correctly identifies its ESSID.

Another laptop's settings tell me that the network uses WPA-PSK encryption.

Ubuntu sees the wireless network,and prompts me with a request for passphrase. It gives me 4 "Wireless Security" options: three with WEP (passphrase, ascii, hex) and one with LEAP. No mention of WPA.
Any hints?

Thank you in advance!

[EDIT] I noticed that if I select "connect to other wireless network" from the menu, and I manually insert the data of the connection including the ESSID, I do get the chance to select wpa security - and in particular wpa-personal which corresponds to wpa-psk. However, I fail to use the network and I still have to understand why :(

---

### Post by Original Brownster on 2007-12-07
Hi,
You can find out more about the hardware by using the command 
$sudo lspci -v

scan through and you'll find an entry for your wireless card.
once you confirm what card / chipset, you need to confirm if this chipset  / driver supports wpa 

HTH

---

### Post by bubuyaga on 2007-12-07
Thanks! I checked with lspci, and it is indeed an Intersil Prism 2.5 (02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)). This should be supported by the default driver for wpa_supplicant, hostapc. Once again:

- Network manager does see the ESSID, but does not provide the WPA options when you click on the network (only WEP and LEAP).
- If I manually choose to "connect to another wireless network" and put in all the data, I do get the option of WPA "Personal" (i.e. PSK), and I get no complains.

However, I still cannot get onto the Internet. It's not a DNS problem because even pinging for a known IP fails. (Note that I am writing from another laptop using WinXP on the same network, and it works perfectly well). 

Any suggestions? I am growing desperate :( I was so happy about the purported support in Ubuntu 7.10 for wireless and laptops, but a lot seems still to be missing :(

---

### Post by Original Brownster on 2007-12-07
Hi,
My own experience has been that if you are getting no-where with the gui tools, go back to the underlying system and check what's happening, gui tools are great when things just work but when they do not you are often just left scratching your head with no meaningful error messages or output to see why.

I configured mine manually which I can help you do, but you might like to take a look at this howto which describes a couple of pointers in getting it working, give it a go and see if it helps, otherwise it's gloves off and the command line :-)

check this [wiki article]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29")

---

