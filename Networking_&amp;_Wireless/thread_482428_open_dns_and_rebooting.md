---
title: "open dns and rebooting?"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by richieboy on 2007-06-23
hi.  i changed my dns to open dns following these instructions from the opendns site:

1. Open a terminal window and type the following:

    $ sudo network-admin 

Note: Root access is required for this step.
2. Change to the DNS tab and enter the following two addresses in the top of the first field labeled DNS Servers:

    208.67.222.222
    208.67.220.220 

You may leave your ISP's DNS addresses underneath the OpenDNS addressses as backup.

 it runs super fast but the problem is that i have to reboot the wireless about twice a session using these instructions from the same site:



If your settings get revoked after reboots, or after periods of inactivity, you can try this:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ sudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

You may be required to change eth0 to your own network device's name if it uses a non-standard name.
Visit [http://welcome.opendns.com/](http://welcome.opendns.com/) to test your new settings.

You should see the Welcome page from OpenDNS, as shown below.

Welcome to OpenDNS screenshot


what happens that i have to reboot and can i do something to stop that thing from happening?

i created an alias for the ifdown and ifup bit.  should i add the rest to the alias?

thanks,

rich

---

