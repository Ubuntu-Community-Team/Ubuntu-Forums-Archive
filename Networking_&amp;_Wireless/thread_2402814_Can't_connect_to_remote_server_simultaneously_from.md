---
title: "Can't connect to remote server simultaneously from two machines in same local network"
date: 2018-10-04
forum: Networking &amp; Wireless
---

### Post by Javierhermosa on 2018-10-04
When I try to connect to my ubuntu server 16.04 from my home or work network, I cannot have both the laptop (a macbook pro 13" 2017) and either the mac mini (at home) or my associate's laptop (at work) connecting to the server in any way at the same time. 

If one is connected, the other won't be able to connect on all or some protocols. I have owncloud installed, webserver, mailserver and can access over ssh. If right now the mac mini is connected to the mailserver, the other computer cannot connect and gets timeouts on the mail client or browser when trying to connect. I turn wi-fi off on the one computer that has access... and magically the other computer gets access after a few seconds and can connect normally to the server. The server is a VPS and the hosting company says they don't have any kind of filtering or anything that might hinder the connection. 

I have reset the iptables on the linux firewall to defaults and opened the mail ports. Still I get the same problem. My phone is in the same network and seems to work properly which makes it even more strange. 

I also can ping the server from the "non-connecting" machine and it will get some pings replied with a lot of latency, some will timeout, but pinging works at least.

Can anyone think of any reason why this might be happening?

thanks in advance!

---

### Post by TheFu on 2018-10-04
IP address conflict? Do you have both clients setup with the same static IP or with the same spoofed MAC for the ethernet cards?

---

### Post by SeijiSensei on 2018-10-07
What are you using to connect?  SSH?  I can have lots of simultaneous SSH connections from one machine to another.  I don't recall ever hitting a limit.

Oh, I saw something about turning off wifi making things work better.  You don't happen to have a machine connected to your local network with both its Ethernet and its wifi adapter, do you?  If so, dump the wifi connection and  just use Ethernet.  You'll have routing problems otherwise, which your other symptoms also suggest.

There is no performance benefit for using both adapters unless you implement "[bonding]("https://help.ubuntu.com/community/UbuntuBonding")."  Otherwise having multiple adapters connected to the same router can cause problems.

---

### Post by Javierhermosa on 2018-10-09
I thought of this too, but one machine is 10.0.0.4 and the other 10.0.0.3 in the local network. No MAC Address spoofing.

---

### Post by Javierhermosa on 2018-10-09
> **SeijiSensei said:**
> What are you using to connect?  SSH?  I can have lots of simultaneous SSH connections from one machine to another.  I don't recall ever hitting a limit.

Oh, I saw something about turning off wifi making things work better.  You don't happen to have a machine connected to your local network with both its Ethernet and its wifi adapter, do you?  If so, dump the wifi connection and  just use Ethernet.  You'll have routing problems otherwise, which your other symptoms also suggest.

There is no performance benefit for using both adapters unless you implement "[bonding]("https://help.ubuntu.com/community/UbuntuBonding")."  Otherwise having multiple adapters connected to the same router can cause problems.

It doesn't matter the type of connection. I connect https for nextcloud, SSH, or https for webmin or wordpress. It just won't reach the ubuntu server and will time out. I need to drop the connction in the other computer (that means closing nextcloud client if it's open and then it will work. Also I haven't got any computer using both ethernet and wifi adapters. Both are connected over wifi. 

My router at home is a Netgear R8000 nighthawk X6.

I am really desperate with this issue, cause I can't seem to find a logical explanation to it.

---

### Post by TheFu on 2018-10-09
I've never seen anything like the issue described. Seems like a router problem.

Start by checking everything.
* drivers (are there known issues with the drivers being used?)
* IPs
* subnetting
* gateways
* routing
* DNS
* and probably most important - the wifi.  Try a different wifi AP.

Wifi is always a problem, regardless of the OS. I've done thousands of wifi deployments and that taught me to avoid wifi whenever possible.  I even use a USB3-to-GigE adapter for my chromebook. I've had issues connecting with netgear wifi lots of places, BTW.  At 1 place it was so bad that we bought a Ubiquiti AP and disabled the netgear wifi. The netgear routing part was excellent, just not the wifi.

If you need to get deep into wifi after checking everything else first, then make a table of each device, which standards it claims, and the major options like channel-width that each uses.  Make certain the netgear is configured for the worst/oldest standard you **Must** have on your network.  If the X6 allows it, setup different SSIDs for fast and slow devices.  This can really make a difference, if you have control like that.  But if you don't want to spend hours figuring all these details out, an $80 Ubiquiti AP will solve it.

---

### Post by SeijiSensei on 2018-10-10
Could it be that the limit of MaxSessions is just one?  From the sshd_config man page

```

    MaxSessions
             Specifies the maximum number of open shell, login or subsystem
             (e.g. sftp) sessions permitted per network connection.  Multiple
             sessions may be established by clients that support connection
             multiplexing.  Setting MaxSessions to 1 will effectively disable
             session multiplexing, whereas setting it to 0 will prevent all
             shell, login and subsystem sessions while still permitting for&#8208;
             warding.  The default is 10.

```

Look in /etc/ssh/sshd_config and make sure this setting is either larger than one or not set at all so it uses the default value of ten.

Remember that the remote server sees all the connections as coming from the router's public IP address, so this restriction applies.

---

