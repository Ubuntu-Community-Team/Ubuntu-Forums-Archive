---
title: "wireless only works in roaming mode"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by neoroses on 2007-12-15
hi guys im using 7.10 and i can connect to my wireless flawlessly, however this is only when roaming is enabled.....i need to set up a static ip you see,,,but i cannot even see the network when i disable roaming what can u guys suggest?

---

### Post by coolbrook on 2007-12-15
So long as you know the name of the ESSID that the router is broadcasting then you should be able to manually enter the name and set up a static IP to connect.

System...Administration...Network

---

### Post by neoroses on 2007-12-15
doesnt work :S i have tried,...just  doesnt connect? worked in 7.04

thanks for the quick responce

---

### Post by romca on 2007-12-15
i can confirm it, i cannot connect (or dont know how), only in roaming mode the network is shown, but cant set its ip address. And when i go to manual config (when roaming enabled), the manager simply disappears (looks like it crashes in the background) which is annoying

---

### Post by ethoms on 2008-01-14
I'm having the same problem, although I still want to use DHCP, I just don't want roaming mode enabled. The roaming mode allows you to select more detail in encryption type e.g. WEP 64bit or WEP 128bit. The manual configuration doesn't though, I think this is the problem. The reason I want manual configuration with DHCP instead of roaming mode is that it is an NIS client and NIS doesn't seem to work in roaming mode, wireless or not. The GUI "Networ Admiitsartor" is very good on the whiole, it just needs a bit more configuration options adding to it.

In the meantime, does anybody know where the wifi config files are located so that I can force WEP 64bit wepkey=1 wepkey1=password to the manual configuration.

---

### Post by roofone on 2008-02-23
I have the same issue:

Gutsy on a Lenovo T61. I can connect to using WPA/DHCP only through roaming. Trying to use the same settings manually results in not being able to get an IP address (though I appear to connect to the router).

---

### Post by dbsanders on 2008-02-27
Confirmed here too. Using Netgear WG511U card (Atheros), and can only get connected to the access point in roaming mode. Manual mode doesn't ever associate.

I've tried numerous ifconfig/iwconfig commands but can't seem to get it working either.

---

### Post by Netsurfer on 2008-03-15
I have the same problem. Using roaming mode it works fine.

I executed this command to restart connection:

$ [COLOR="Red"]sudo /etc/init.d/networking restart[/COLOR]

I don't need roaming mode because I'n using a desktop workstation.

How can I get connect automatically?

---

### Post by ugm6hr on 2008-03-15
Network Manager doesn't like fixed IP.  It will only behave with DHCP.

If you need fixed IP, I would suggest Wicd (or manual connection).

---

### Post by dbsanders on 2008-03-15
I solved my issue by installing Wicd (uninstalls network manager at the same time). Wireless net is solid now.

---

### Post by Netsurfer on 2008-03-16
Thank you. I will try WICD.

---

