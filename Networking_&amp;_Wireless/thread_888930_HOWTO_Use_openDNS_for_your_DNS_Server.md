---
title: "HOWTO: Use openDNS for your DNS Server"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by mozillar on 2008-08-13
I was having DNS issues with my ISP recently, which got me looking for alternate DNS servers to use. After researching them, I settled on openDNS. The change was very easy.

First, edit the dhclient configuration file:

```
gksudo gedit /etc/dhcp3/dhclient.conf
```
Note: your dhclient.conf may exist in **/etc/dhcp** folder instead.

Append the following line to the bottom of the dhclient.conf file

```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```

Then save the file and reboot. After rebooting, right click on the Network Manager and view Connection Information.
You should then see openDNS servers for your primary and secondary DNS:
```
208.67.222.222
208.67.220.220
```

That was the only change I needed to make while running Ubuntu 8.04 (hardy) with Gnome Network Manager. 


If you **manually configure** your network connection instead, I expect you will have to also assign the DNS values manually by using the command:
```
gksudo network-admin
```
Where you will assign the primary and secondary DNS values as:
```
208.67.222.222
208.67.220.220
```


More detail than you wanted to know:

OpenDNS claims to have been better prepared for the recent DNS Cache poisoning issue. They were certainly better prepared than my ISP. OpenDNS also automatically provides typo correction, so if you fat finger a URL like yahoo.cmo their servers will figure out what you really meant. You do not need to create an account with OpenDNS to use their **FREE** service. You may find web surfing faster using their DNS versus your ISP's default DNS servers.

If you do create an account, you can use additional features like content filtering for your kids or your parents. You can also assign the DNS servers on your router, in lieu of setting it on each PC. If you use VPN, you will need to create an account to get Virtual Private Networking to work.

More info can be found here:

[http://www.opendns.com]("http://www.opendns.com")

You can test your DNS here:

[http://www.doxpara.com/]("http://www.doxpara.com/")

To undo this change and revert back to your ISP's default DNS servers:
```
gksudo gedit /etc/dhcp3/dhclient.conf
```

And remove the following line from the dhclient.conf file

```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```

---

