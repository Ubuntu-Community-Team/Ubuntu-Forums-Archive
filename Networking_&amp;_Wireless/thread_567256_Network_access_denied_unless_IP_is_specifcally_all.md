---
title: "Network access denied unless IP is specifcally allowed"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by Sevets on 2007-10-04
I am running 7.04, and am able to ping the server.

I am unable to ssh or vnc into the server unless the IP is specifically allowed.  I would use host names but that would be prohibitive and is undesired.  

SSH server is installed and Remote Desktop connections are enabled in administrative options.

I have also tried explicitly allowing the ports but that does not work either.

edit: I get a connection refused message when attempting to connect to either server.

---

### Post by Sevets on 2007-10-04
Any information would be greatly appreciated on this.

---

### Post by noob12 on 2007-10-04
When you say you are "specifically allowing" the IP, what are you doing to allow it?

Are you using a firewall or is this in a hosts.allow or similar file?

---

### Post by Sevets on 2007-10-04
I am using firestarter.

I can add ports to the exceptions, I can add the IP of the ssh/vnc client computer, and I can add the IP by adding it when the connection is blocked.

The thing is the ssh/vnc client is on a DHCP network and also frequently goes between seperate wireless and wired networks.

---

### Post by noob12 on 2007-10-04
Try opening the port using these steps:

Open the Firestarter GUI.   Select the Policy tab.  Click once in the lower window where the headers are "Allow Service, Port, For".   Select Add Rule.  Select the service SSH in the pull-down;  port 22 should get filled in; For "When the source is" keep the selection on Anyone".  You can enter a comment if you want.  Click Add.  Click Apply Policy.

I don't think you need to stop and start the firewall, but you can do that to be sure.

Then check that things look right by using

```

sudo iptables -nL

```
to list the actual firewall rules and look at the INBOUND chain in the filter table; make sure it has a line like this
```

ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22 

```

Then see if you can connect from your client.

---

