---
title: "make wireless network information persist?"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2008-07-16
Hi I'm using Hardy on my desktop, which is on a wireless network.

Everytime I reboot the machine, I have to reconfigure the wireless network connection.
Is there a way to make this information to persist, so that my machine will attempt to connect with the same credentials on boot?

At the moment, upon boot I click on the nm-applet, unlock it and tell it the encryption type and password. Every time I start a session, this information seems to be have changed. The password type is changed and the password is random.
Is this a bug? Is there a good reason for this default behaviour?

Anyway, is there a way to configure my wireless network connection once and for all, without having to rejig it every time?

Thanks

---

### Post by chili555 on 2008-07-16
Network Manager is great for laptops that are carried down to the coffee shop or other hotspot because it allows you to select from among several networks and, assuming you have any needed encryption details, connect.

I don't believe this is your case, if you have a desktop computer that sits at home all day. The key is to add your details to */etc/network/interfaces* and turn off 'Roaming' in System -> Administration -> Network. Here is a sample */etc/network/interfaces* for a WEP encrypted network:```
auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp
wireless-essid mylilrouter
wireless-key 096c7f280blahfoo


#auto eth0
iface eth0 inet dhcp
```Here is a guide to setting up a WPA encrypted network: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

After you get this all done, do:```
sudo ifdown eth1 && sudo ifup eth1
```Substitute your details here. Assuming you connect, you can safely go to Synaptic and remove Network Manager and dhcdbd.

You should connect on boot forever more.

---

### Post by bobdobbs on 2008-07-17
> **chili555 said:**
> Network Manager is great for laptops that are carried down to the coffee shop or other hotspot because it allows you to select from among several networks and, assuming you have any needed encryption details, connect.

I don't believe this is your case, if you have a desktop computer that sits at home all day. The key is to add your details to */etc/network/interfaces* and turn off 'Roaming' in System -> Administration -> Network. Here is a sample ...

Hm...
It seems that my interfaces file is configured already.
It's got the right generated passphrase key in it, the correct ssid, encryption method and everything.

Yet, it doesn't run on startup.

If I do:
/etc/init.d/networking restart
then the network comes up on the restart - no problems.

But, if I do restart after a boot, no cigar.
My system still refuses to get on the network after boot.


What could be going on here?
How do I fix it?

---

### Post by chili555 on 2008-07-17
Let's try a little trick. Please *sudo gedit /etc/rc.local* and add a line above *exit 0*:```
/etc/init.d/networking restart
```Proofread, save, close and reboot. Did you connect on boot?

---

