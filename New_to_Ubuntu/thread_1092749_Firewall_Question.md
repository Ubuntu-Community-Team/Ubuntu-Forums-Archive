---
title: "Firewall Question"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Geo_V on 2009-03-10
Hi everyone,

I'm familiar with working with a firewall on Windows, but not on Linux. I've installed Firestarter linux firewall on Ubuntu Studio, but the behaviour of the firewall seems very different from what i was used to...I mean, on Windows whenever an action takes place, the firewall asks the user for permission, something that has never occured with the particular firewall.

Am i doing something wrong or else could i have some explanation of the matter..?

Thanks..Geo

---

### Post by skymera on 2009-03-10
Firestarter is merely a GUI to IPTables (Linux's firewall)
It really isn't needed unless you want to configure other PCs access to yours. etc.

---

### Post by Geo_V on 2009-03-10
So is there a firewall on linux which works like on Windows or is this not needed?

---

### Post by brian_p on 2009-03-10
> **Geo_V said:**
> 

Am i doing something wrong or else could i have some explanation of the matter..?

No, nothing wrong. Firestarter configures iptables rules. I'd suggest a forum search using 'iptables' would be informative.

---

### Post by brian_p on 2009-03-10
> **Geo_V said:**
> So is there a firewall on linux which works like on Windows or is this not needed?

From recently:

[http://ubuntuforums.org/showthread.php?t=1090059](http://ubuntuforums.org/showthread.php?t=1090059)

---

### Post by Geo_V on 2009-03-10
Thanks guys, i'll check these things and maybe post any other question that rises..

---

### Post by kansasnoob on 2009-03-10
IMHO I'd remove Firestarter and enable UFW.

If you're using 8.10 (Intrepid) gufw is in the repos now so you can just go to Terminal and run:

```
sudo apt-get install gufw
```

Or go to synaptic and install it from there.

If you're using 8.04 (Hardy) then go here:

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

The download is a .deb so it's very easy.

Then in System Administration you'll see Firewall Configuration.

[ATTACH]106037[/ATTACH]

Just tick Firewall Enabled and you're good to go!

---

### Post by bodhi.zazen on 2009-03-10
This is a FAQ on these forums and the question is what do you want a firewall to do for you ?

Linux is modular and with a default installation a firewall is probably unnecessary, especially if you use a router.

See : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

Monitoring of your network traffic is called NIDS 

[http://en.wikipedia.org/wiki/Intrusion-detection_system](http://en.wikipedia.org/wiki/Intrusion-detection_system)

And this is not a function of the firewall. Snort is defacto standard, both on windows and Linux. Wireshark is also helpful, but that is more a packet sniffer then monitoring.

I am going to close this thread now as these open ended questions  all too often lead to poiintless debates (search these forums for "firewall" and you will find them) and the general question you are asking has been answered in the link I gave you.

---

