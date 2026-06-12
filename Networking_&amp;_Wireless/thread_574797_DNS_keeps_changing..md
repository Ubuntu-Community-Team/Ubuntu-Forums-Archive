---
title: "DNS keeps changing."
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by rahimveron on 2007-10-13
I have a ADSL modem that connects with Ethernet and have 256 kbps connection.
I have a DNS problem.
My ISP have provided with two DNS numbers

```
218.248.240.208
218.248.240.135
```

But when i am connected to the Wired Network the primary DNS is set to
```
192.168.1.1
```

When i run ```
sudo gedit /etc/resolv.conf
```
Sometimes there are two DNS server provided by my ISP, but sometimes it is set to 198.162.1.1. Why is this so.
My ISP provides Dynamic IP.

Finally the problem is my line gets hanged or disconnected ,ie, Firefox or Opera does not load webpages,every few minutes , say every 10 minutes.

People have suggested that it is a DNS problem and adviced me to enter the two DNS number provided by my ISP manually.
So i clicked on Network Manager on the notification panel and selected Manual Connection, went to the DNS tab and entered the two DNS one by one.
After connecting it seems to slve the problem but only till i reboot, as it sets the Primary DNS back to 198.162.1.1
Now again i have to do it manually to get connected and to keep my line alive for longer period.

How should i go about resolving this?

---

### Post by noob12 on 2007-10-13
It looks like your local modem/router is configured to be a DNS proxy.  If it is not working well for you, you may be able to disable this feature in your router's configuration interface.

There are also ways to override the DNS provided via DHCP using \ **prepend domain-name-servers** or **supersede domain-name-servers** directives in **/etc/dhcp3/dhclient.conf**.  See **man dhclient.conf** for details.

For examples you can see this thread: [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by kvonb on 2007-10-13
I would think that the dsl modem is doing the actual connecting to your ISP.

Is your computer set to DHCP?

Maybe check the settings on the dsl modem, make sure it is set to "persistent connection", it might be hanging up due to a setting.

Your modem's IP address should be the DNS server for your computer, but the modem's DNS server would be the addresses that your ISP gave you.

It should set those automatically on connection though.

Maybe try a hard reset of the modem, see if that helps.

---

