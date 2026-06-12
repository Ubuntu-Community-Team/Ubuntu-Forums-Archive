---
title: "Open DNS settings dhclient.conf"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by bill45 on 2007-10-18
I changed my DNS address to that of OPENDNS as shown below.  My moden is dev/ttyS1
Are the instructions below ("avoid having settings revoked") correct for use with dial-up serial modem?


These instructiuons are form OPEN DNS help page
[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)
-----------------------------------------------------------------------------------------
Change to the DNS tab and enter the following two addresses in the top of the first field labeled DNS Servers.

    208.67.222.222
    208.67.220.220

To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ sudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

You may be required to change eth0 to your own network device's name if it uses a non-standard name.

---

### Post by kerry_s on 2007-10-18
it doesn't matter the connection, they all check resolv.conf before the internet. just make the change, reboot and your good to go.

---

### Post by bill45 on 2007-10-19
Very good, thank you.

---

