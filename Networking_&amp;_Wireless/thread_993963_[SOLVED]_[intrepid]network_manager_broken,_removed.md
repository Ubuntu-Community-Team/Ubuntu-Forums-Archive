---
title: "[SOLVED] [intrepid]network manager broken, removed -&amp;gt; no browsing"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Wisp2006 on 2008-11-26
Hy all,
By mistake I removed the applet from the bar. I couldn't, by any means, to bring it back (the command nm-applet returned an error - Network Manager Service is already busy, something like that). So I couldn't select my network configuration. I deleted Auto eth0, I connected through my connetion and worked fine until restart. Then the custom connection lost it's subnet mask, the Auto eth0 did not occur anymore, so the link to internet was lost. I said to go the old fashioned way:

[FONT="Courier New"]sudo apt-get remove network-manager
sudo gedit /etc/network/interfaces[/FONT]

where i input the standard config (static adress, with no other thingies needed):

[FONT="Courier New"]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask 255.255.254.0
gateway xxx.xxx.xxx.xxx[/FONT]

Now, i can ping/traceroute any adress I wish, even outside my provider, BUT i can't browse the web in any way. I will post soon the ifconfig output, but i guess it should be fine. Is there something I missed in manual configuration?

---

### Post by TFX360 on 2008-11-26
I think you are missing DNS'ses post the contents of

```
cat /etc/resolv.conf
```

---

### Post by Wisp2006 on 2008-11-26
I thought of that too, but my DNS has the same IP as the gateway... will go home and post it's content. Thank you for your prompt response.

---

### Post by TFX360 on 2008-11-26
You're welcome. Let me know. Post

```
ifconfig eth0
```


too!

---

### Post by Wisp2006 on 2008-11-26
Problem solved. Indeed, the /etc/resolv.conf was empty, all i needed was just to set
```

#here goes the dns server
nameserver xx.xx.xxx.xxx
```. Thanks again for your time.

---

### Post by TFX360 on 2008-11-26
You're welcom. Happy Ubuntuing!

---

