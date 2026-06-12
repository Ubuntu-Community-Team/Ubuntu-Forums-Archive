---
title: "2Wire Router Changes /etc/resolv.conf"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by krashoveride on 2008-09-26
Okay, so I just reinstalled Ubuntu Hardy(not because of this problem) but I had this problem in the last install too.

When I connect to my 2wire Router everything connects fine, but my /etc/resolv.conf changes to this:

```

search gateway.2wire.net
nameserver 192.168.1.254

```

and that doesn't work for me.
So I have to manual change it to:

```

nameserver 68.94.156.1
nameserver 68.94.157.1

```

Before I just made a script that changed it every minute or so, but that's a hassle because sometimes I can't connect to a page for a minute.

---

### Post by doug-M on 2008-09-27
Do you have control over the 2wire router?

You could try this:

Try going to: [http://192.168.1.1](http://192.168.1.1)
  this should be your 2wire router, you will need the admin password for the 2wire.

Click on Broadband Link
Click on Advanced Settings

In the "Broadband DNS" settings area put in your settings:
 Primary Server: 68.94.156.1
 Secondary Server: 68.94.157.1
 Domain Name: myhome.local

Your menus might be different. But you should look for either the DHCP settings or the broadband connection setting where it talks about DNS settings.

---

### Post by krashoveride on 2008-09-27
Yes, I do control the router.

I did that, disconnected from the network, and later I reconnected, and it still changes resolv.conf to the same thing. I checked to make sure the router saved the settings and it did.

Oh, and the menus were set up exactly like that.

---

### Post by doug-M on 2008-09-27
You might find that it is using the correct DNS servers now though.

If that isn't the case you could use a static IP or potentially add additional DNS servers. If you are using Network Manager then click on it and choose Manual Configuration.
Go to the DNS tab and add your DNS servers there.

---

### Post by krashoveride on 2008-09-28
The DNS Servers were already added in the network manager, but changing it to a static IP fixed that problem. I changed it to a static IP on wifi-radar, but now when I start up the computer, I have to open wifi-radar, disconnect and then reconnect in order for networking to work.

This is what I have for the profile on wifi radar:

Network Name: 2WIRE396

Wifi Options:
Mode: auto
Channel: auto

IP: 192.168.1.111
Netmask: 255.255.255.0
Gateway 192.168.1.254
Domain: (blank)
DNS1: 68.94.156.1
DNS2: 68.94.157.1

---

