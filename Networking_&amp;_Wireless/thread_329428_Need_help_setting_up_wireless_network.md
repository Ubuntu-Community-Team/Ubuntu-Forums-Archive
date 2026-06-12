---
title: "Need help setting up wireless network"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by rqian on 2007-01-01
I need help setting up my wireless network.  I've tried many tutorials from this forum and other sites, but I couldn't quite get it to work.  I'm new to Linux.

First, I have a D-Link DWL-G510 wireless card for desktop.  I have Ubuntu 6.10, the Edgy Eft.

I have ndiswrapper installed from the drivers in the CD I got for the wireless card.  When I type ```
ndiswrapper -l
``` it says driver installed, hardware present.  I am able to do ```
modprobe ndiswrapper
```

Next, my ```
/etc/netowrk/interfaces
``` is a bit messed up.  I have many interfaces: lo, eth0, eth1, eth2, wlan0, wifi0, and ath0.  When I open up Networking under System > Administration, I setup my wireless connection there, and the interface is called ath0.  But when I go to Network Tools under System > Administration, I have 3 network devices to choose from: loopback interface (lo), unknown interface(wifi0), and unknown interface (ath0).  However, I cannot configure any of the three becaue the configure button is grayed.  When I switched to wifi0, the the interface information says hardware address and all the options down the column: not avaialble, but I see the transmitted and received bytes and packets increase every second.  Under the IP information on top, it does not have any information.  When I switch to ath0, there is an entry under IP information - IPv6 for rotocol and an IP Address of fe80::211:95ff:fe88:fc57.  However, it does not have any hardware address and the transmitted and received bytes is at 0.

So I think there is a mismatch between the interfaces.  Can anyone help me to fix this problem?  Thanks!

Happy New Year!

---

### Post by Crooksey on 2007-01-01
Ok, this is dead easy...

```

iwconfig

```

Look for the card that shows wireless extensions, lets assume its ath0, you know want to set the network essid.

```

sudo iwconfig ath0 essid hostname

```

Now you want to set the network key, if you have one, if not skip this

```

sudo iwconfig ath0 key yourwebkeyhere

```

Now all thats left is to connect

```

sudo dhclient ath0

```

That should do it ^^

---

### Post by rqian on 2007-01-01
That did not work.  I have WPA-PSK.  I followed the tutorial on [http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136), and it still didn't work.

The message says No DHCPOFFERS received.  No working leases in persistent database - sleeping.  Please help.

---

### Post by rqian on 2007-01-02
I tried ```
sudo iwconfig ath0 key yourwebkeyhere
``` and it did not work.  Please help, thanks!

---

### Post by phossal on 2007-01-02
Have you connected without wep/wpa? There are reports that *enabling wep/wpa* have resolved connection issues, but it's almost always better to do your initial configuration without.

---

### Post by rqian on 2007-01-02
> **phossal said:**
> Have you connected without wep/wpa? There are reports that *enabling wep/wpa* have resolved connection issues, but it's almost always better to do your initial configuration without.

Thanks for the idea.  It works now when I disabled WEP and WPA.  Now how would I enable it since I want security over my network?

Thanks.

---

### Post by phossal on 2007-01-02
Congratulations. Unfortunately, the options and procedure for configuring your network security may depend on your hardware. I would review an Ubuntu how-to for your network interface device (hopefully you'll find information regarding which methods are supported). I've read reports that only wep OR wpa is supported in certain cases.

Once you know, you'll configure the settings on your router. And then you'll use iwconfig to set the wireless device configuration. 

For details:
```

man iwconfig

```

---

### Post by jamesstansell on 2007-01-02
> **rqian said:**
> Thanks for the idea.  It works now when I disabled WEP and WPA.  Now how would I enable it since I want security over my network?

Thanks.

Enabling WEP and WPA are different from each other.  I have WEP running here but I've failed with WPA so far.

WEP can be configured from your /etc/network/interfaces file.  It's a front-end for the iwconfig command.  I guess there are graphical frontends for the interfaces file but I'm not really familiar with them.

Getting WEP running before you tackle WPA would be a good idea.

From my reading WPA will require wpa-supplicant and/or rutilt.  Also iwpriv may or may not be needed.

As it sounds like you're using ath0 I'd suggest you check out the docs for wpa_supplicant first.  Here's one link: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

HTH

-james.

---

