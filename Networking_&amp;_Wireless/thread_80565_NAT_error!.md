---
title: "NAT error!"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by Ocxic on 2005-10-22
I am trying to get Azureus working and it keeps giving me a NAT error, I have opened the proper ports and UPnP is enable so it can map by itself (successfully), is there a firewall or something that is in ubuntu preventing me from having this work.

---

### Post by mlomker on 2005-10-22
> is in ubuntu preventing me from having this work.

Only if you've installed Firestarter.

---

### Post by graabein on 2005-10-23
[QUOTE=Ocxic]I am trying to get Azureus working and it keeps giving me a NAT error, I have opened the proper ports and UPnP is enable so it can map by itself (successfully), is there a firewall or something that is in ubuntu preventing me from having this work.[/QUOTE]

I am desperatly trying to get Azureus starting myself. I just get a **(uPnP) mapping udp tracker client port udp/6881 fail** message when I start the app and I get down speed of about 0 B/s. I had it working before I upgraded to Breezy. Maybe there is something that has changed in my router or is this Azureus settings? 

I do not know how to open ports. Could you fill me in on this? What are the addresses and ports to open? I have this in my router NAPT after I start Azureus:

```
10.0.0.3:6881 - unspecified:6881 - udp
10.0.0.3:6881 - unspecified:6881 - tcp
```


Another thing: Azureus gives off alot of warnings. How do I dump them to a text file instead of the console?


I've done a NAT/Firewall test from Azureus and it gave me **Testing port 6881 ... OK !**

---

### Post by mlomker on 2005-10-23
> I do not know how to open ports. Could you fill me in on this? What are the addresses and ports to open? I have this in my router NAPT after I start Azureus:


You'll have to look at the manual for your router.  Most of them have web interfaces that you can connect to.

You'll want to forward 6881-6891 or any other range of ten ports.  You can tell Azureus what range to use in your configuration.

---

### Post by graabein on 2005-10-24
[QUOTE=mlomker]You'll have to look at the manual for your router.  Most of them have web interfaces that you can connect to.

You'll want to forward 6881-6891 or any other range of ten ports.  You can tell Azureus what range to use in your configuration.[/QUOTE]

I have looked at the web interface and did not understand it fully... See my post, it says 10.0.0.3:6881 (inside IP address) and *unspecified*:6881 (outside) with both UDP and TCP protocol.

Do you mean I have to punch in two (UDP + TCP) forwarding port sets for each port 6882, 6883... up to 6891 to get the usual down speed from Azureus? With the same IP address pair? 

The NAT/Firewall Test in Azureus okayed port 6881... I have tried with the default GNOME BitTorrent client and down speed is good there with the same torrent files. 

I am at work now so I don't have time to look at it but I found [this tread]("http://ubuntuforums.org/showthread.php?t=67667") that I will look at when I get home.

Maybe I have to update java? I can't remember what version I have installed.

---

### Post by mlomker on 2005-10-24
> Do you mean I have to punch in two (UDP + TCP) forwarding port sets for each port 6882, 6883... up to 6891 to get the usual down speed from Azureus? With the same IP address pair? 


It only uses TCP, so you can skip UDP.  I assume you're only supposed to have to forward the one port but I forwarded all 10 (to support 10 incoming connections) and it works well for me.

---

### Post by graabein on 2005-10-25
I solved it by installing java 1.5. It works great now. Both down speeds and processor usage is normal.

I used these links:
[LIST]
[*][Azureus not working.]("http://www.ubuntuforums.org/showthread.php?t=81436")
[*][HOWTO: Building your own Java 1.5 package]("http://www.ubuntuforums.org/showthread.php?t=70428")
[*][Ubuntu Wiki - RestrictedFormats - Sun Java]("https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca")
[/LIST]

---

