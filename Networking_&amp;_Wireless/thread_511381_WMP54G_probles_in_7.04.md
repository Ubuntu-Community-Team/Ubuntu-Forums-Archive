---
title: "WMP54G probles in 7.04"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by jan00b on 2007-07-27
Here are some facts ill throw out to help

Ubuntu Version: 7.04
CPU: AMD Athlon64 3200+
Wifi Card: Linksys Wireless-G WMP54G
Router:  Dlink DI-524
Service provider: Wowway

My friend just installed Ubuntu on my computer and got me internet without downloading any special drivers but using a Manuel Install for wireless, so i know all my hardware is compatible. I reinstalled Ubuntu and it was going swell at first. I tried to get myself wireless but it won't work for some reason.
when I go to my router here are the feilds i see.

> 
SSID: default
Key
Password: 7i88y (the password prompted after typing the routers gateway IP in browser)
WEP Encryption: 64bit
Key Type: Hex
Authentication: Shared Key
Key1: 0123456789 (The only key i use to connect wireless windows computers)
DHCP Server: Enabled


With this knowlage I go click on the upper right hand black moiter icon. Now i choose manel Connection, Wireless then make the previous feilds

Roaming Mode: Disabled
ESSID: default
Key Type: WEP 64/128bit
Network Password: 7i88y
Connection Type: DHCP

I saved, closed out then started firefox. I can't load any sites with it. Weird thing is, In Ubuntu it says default is at 87% (i assume this is signal strength) and my router says "linux-desktop" is connected but i still can't use firefox to brows the web, what does that mean?

Now I put the connection on roaming modejust so i can edit some other stuff.

Now I try "Connect To New Network". I put in default as my network name, choose 64/128bit WEP and finaly 0123456789 as my key with a Shared Key enebled

What am i doing wrong?, how do i get this to work? My friend did it in 30 seconds, how hard cold it be?

---

### Post by kevdog on 2007-07-27
Do you know the chipset of your wireless device: Linksys Wireless-G WMP54G?

Either googling for the answrer, or posting the following would help me a lot (type command at command prompt and cut and paste output:

lspci -nn
lshw -C network

---

### Post by liquidstate on 2007-07-30
"Network Password" may actually mean your WEP key (or "Key 1") the "passphrase" for my home network does not work with any network setup that I have tried, instead i enter the fully encrypted 128bit WEP key, and it works every time.
hope that helps.

---

