---
title: "BIOS Flash caused loss of network"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by shdwlrd on 2006-12-07
Hi All,

I have a MSI K9A Platinum Mobo and when I flashed the BIOS I can no longer access the network.

I go into the Network Admin GUI and I see eth0 is still there and I can change it for dhcp to static and it give a new ip address on my network and it seems to take it but still unable to ping the router. When I set it back to DHCP or run dhclient it times out when trying to get an IP address.

Is there a way to force the reconfiguration of the NIC? I did not see how to do it in the GUI. Something like remove the device in windows and reboot and windows automatically puts the device back?

Thanks,

---

### Post by ciscosurfer on 2006-12-14
> **shdwlrd said:**
> Hi All,

I have a MSI K9A Platinum Mobo and when I flashed the BIOS I can no longer access the network.

I go into the Network Admin GUI and I see eth0 is still there and I can change it for dhcp to static and it give a new ip address on my network and it seems to take it but still unable to ping the router. When I set it back to DHCP or run dhclient it times out when trying to get an IP address.

Is there a way to force the reconfiguration of the NIC? I did not see how to do it in the GUI. Something like remove the device in windows and reboot and windows automatically puts the device back?

Thanks,Hello!  First off, it's important to know that the new BIOS firmware you've installed is the absolute most correct version for the BIOS that you own.  That's step one.  Be very certain that it is.  That said, you probably did everything correctly otherwise you wouldn't be able to get into Ubuntu (hence, the BIOS upgrade worked -- but just to be sure, make sure you have installed the correct version of the BIOS upgrade by going to your BIOS/Hardware manufacturers site and confirming that it is indeed the correct version).

Next, once you've confirmed that you flashed your BIOS correctly, then go into a Terminal from within Ubuntu and enter in the following:```
sudo /etc/init.d/networking restart
```That will restart your connection and pull a new IP address for your eth0 (if that's where the line is connected, if not, then for eth1) connection.  Basically, it will restart the network.

Some words of advice:[LIST=1]
[*]If the above instructions don't work, you need to reset your router as well as your actual modem.  First, unplug your modem, let it reset, give a 20 or 30 seconds, then plug the AC cord back in.  While the modem is resetting, now would be a good time to unplug the AC from your router as well.  Let it reset, too.
[*]Plug the AC to your modem back in and let it come fully back up.
[*]Plug the AC to your router back in and let it come fully back up.
[*]From Ubuntu, issue again```
sudo /etc/init.d/networking restart
```
[*]Now try pinging your router, usually 192.168.1.1
[*]If that works, then try pinging 72.14.207.99 (that's one of Google's servers)
[*]If that works, then try pinging by name: ping [www.google.com]("http://www.google.com")[/LIST]Hope this get you own the right track.  If you need help with reflashing your BIOS, check out my signature below :-)

---

