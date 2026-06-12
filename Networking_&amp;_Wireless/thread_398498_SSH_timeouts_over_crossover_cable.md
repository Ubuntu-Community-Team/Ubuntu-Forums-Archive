---
title: "SSH timeouts over crossover cable"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by rvbhute on 2007-04-01
I am using a crossover cable to connect my Feisty and Edgy machines. Their setup is as follows:

Feisty (eth0 is used to connect to ADSL modem)
eth0 = 192.168.1.2/255.255.255.0 gw 192.168.1.1
eth1 = 192.168.0.1/255.255.255.0 gw 192.168.0.2

Edgy
eth0 = 192.168.0.2/255.255.255.0 gw 192.168.0.1

I have setup SSH server, NFS and Apache on Edgy - all for transferring data from Edgy to Feisty :) 

However, I'm only able to login from a terminal through SSH i.e. ```
ssh rohit@192.168.0.2
``` *No other method works*!! "The connect to server" option in Places menu times out. When run from terminal, there is a noticeable time lag before the password prompt appears. After that its fast.

I can ping both machines from each other.

I also tried SCP from [http://ubuntuguide.org/wiki/Dapper#SSH_Server]("http://ubuntuguide.org/wiki/Dapper#SSH_Server").  Even here, the password prompt came after considerable delay. On starting the file transfer, it stalled at a 700  MB ISO file and then aborted with the following error.
```

Disconnecting: Timeout, server not responding.
lost connection

```

Despite SCP aborting the job, the LEDs on both the LAN cards are flashing, indicating that data is being transferred.

I have uninstalled Firestarter completely on Edgy machine. A port scan from Feisty shows SSH, NFS and HTTP ports open. Yes, even Apache and NFS cannot be accessed.

/etc/hosts.allow contains "ALL: ALL" directive. Also Apache's config file has "Allow from all" in the relevant directory config sections. The folders shared through NFS contain 192.168.0.1 in the list of allowed hosts.

I'm missing something very obvious here. Please help me out. 
Should I just plugin the hard disk from the Edgy machine to the Feisty machine? I so wanted to try out the networking method.

---

### Post by Sencer on 2007-04-01
> I am using a crossover cable to connect my Feisty and Edgy machines. 

Was that a munally crimped cable? Or can you see any damage on the cable? Your description sounds like it could well be an issue with the cable (that would be my number one guess). Try out "mtr otherip", let it run for a while and see if it reports any packetloss.


The other odd thing is, that you are setting a gw at all for the crossover connection - you do not have a router, so gw should not be set. But I don't know if that could cause intermittent problems (I would expect that it either works, or doesn't work at all).

---

### Post by rvbhute on 2007-04-01
Problem solved, Sencer! I removed the gateways from both sides. The SSH is now fast as it should be! What's more, I can now connect through the "Connect to server" option. :grin: Thanks!

I also ran mtr from both sides. There is no packet loss, but yes, the cable is manually crimped.

---

