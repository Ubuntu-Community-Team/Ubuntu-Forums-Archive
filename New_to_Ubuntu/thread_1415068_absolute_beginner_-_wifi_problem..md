---
title: "absolute beginner - wifi problem."
date: 2010-02-24
forum: New to Ubuntu
---

### Post by lakebuckner on 2010-02-24
Hello, this is quite literally my first day of using ubuntu. It's working perfectly on my laptop, wifi and all. However, on my boyfriend's laptop, the wireless is spotty. When i boot it up, it connects to my network immediately, but disconnects quickly after, and never regains the connection.
His computer is a Gateway NV53, and his wireless card is an Atheros AR5b93.
I've seen many people suggest madwifi and ndiswrapper, but honestly, i looked into both programs, and i have no idea how to install them ._.

And, on another note, I just realized that his computer is 64 bit. Could problems be caused by running the 32 bit version of ubuntu?

any help is greatly appreciated. 
thanks so much.
-Lake

---

### Post by chaanakya_chiraag on 2010-02-24
I don't think so.  I'm not on my Ubuntu computer right now, but you can create a static network configuration, which might increase network reliability.  Let me post my network config when I get home.  Basically you have to stop network-manager, edit /etc/network/interfaces and /etc/resolv.conf, and restart the networking daemon.  Again, I'll post a better tutorial later.  Until then, check this link:
[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html")

---

### Post by spiderbatdad on 2010-02-24
Perhaps this will solve the problem:
[http://ubuntuforums.org/showpost.php?p=8599246&postcount=5](http://ubuntuforums.org/showpost.php?p=8599246&postcount=5)

---

### Post by lakebuckner on 2010-02-24
I looked at both links, and I am still lost.

---

### Post by Greenwidth on 2010-02-24
spiderbatdad is saying you need to install these packages:
linux-backports-modules-karmic-generic.
linux-backports-modules-wireless-karmic-generic.

Paste this into a terminal:
```
sudo apt-get install linux-backports-modules-karmic-generic && sudo apt-get install linux-backports-modules-wireless-karmic-generic
```

Or start Synaptic (System > Admin > Synaptic) and quick search for them, mark, and install.

---

### Post by mikeyphi on 2010-02-25
> **lakebuckner said:**
> Hello, this is quite literally my first day of using ubuntu. It's working perfectly on my laptop, wifi and all. However, on my boyfriend's laptop, the wireless is spotty. When i boot it up, it connects to my network immediately, but disconnects quickly after, and never regains the connection.
His computer is a Gateway NV53, and his wireless card is an Atheros AR5b93.
I've seen many people suggest madwifi and ndiswrapper, but honestly, i looked into both programs, and i have no idea how to install them ._.

And, on another note, I just realized that his computer is 64 bit. Could problems be caused by running the 32 bit version of ubuntu?

any help is greatly appreciated. 
thanks so much.
-Lake

32 bit OS will run just fine on a 64 bit system however, I believe there is no support for the Atheros AR5b93 yet; you need to use the driver supplied by madwifi, the procedure is slightly complicated but it works!

---

### Post by lakebuckner on 2010-02-25
Thank you guys!
Now, that code that was posted, is that how you install madwifi?
If not, could someone explain to me how exactly to install it.
I've downloaded the madwifi-hal-0.10.5.6-current.tar.gz package.
What do I type into the terminal?

---

