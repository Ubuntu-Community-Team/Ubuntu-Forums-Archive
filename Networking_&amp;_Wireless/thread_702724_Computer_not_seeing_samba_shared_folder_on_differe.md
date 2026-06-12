---
title: "Computer not seeing samba shared folder on different subnet"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by Alt69 on 2008-02-20
Hi, I have recently made some changes to my setup at home and have lost the ability to see my Samba share folder.

1) I now have two routers connected. yes too many computers, not enough slots. :)

    - 192.168.1.100   - 1st router 
    - 192.168.2.100   - 2nd router


2) My Xp laptop is connected to the 1st router.

3) My samba server is on the 2nd router.

4) I can see the Samba share when I connect with a new Ubuntu box, also attached to the 2nd router. Installed today- desktop version. So they are sharing the same ip range.

I am not sure what I am doing wrong or missing to get the XP box to recognize the Samba share. Any suggestions?


thanks

---

### Post by Iowan on 2008-02-20
Compare the **/etc/samba/smb.conf** files between the working and non-working machines. In particular, see if the non-working machine has a **hosts allow=** parameter that limits access to the subnet.  Verify that both servers are in the 192.168.2.X range (I think you said they were).  Can you access the shares (on the non-working server) from the other Ubuntu box?

---

### Post by jhetrick62 on 2008-02-20
I'm assuming that you can ping the server on the second subnet?

---

### Post by Alt69 on 2008-02-23
Hi, here is what I tired:

1) Ping the server from the XP laptop, connect wireless to router - 192.168.1.1xx - 1st router .
      a.Failed – timed out

2) Ping the 2nd Ubuntu box from the XP laptop, connect wireless to router - 192.168.1.1xx - 1st router .
      a.Failed – timed out

3) Ping the XP laptop from the Samba server,  wire connected to router 192.168.2.1xx - 2nd router
     a. Success – 100%

4) Ping the XP laptop from the Ubuntu desktop,  wire connected to router  192.168.2.1xx - 2nd router
     a. Success – 100%

5) Able to ping both Ubuntu server and  Ubuntu desktop from each other.
     a. Success – 100%

Additional Info
-The  2nd router 9192.168.2.1xx - is not a wireless router. It is an old Linksys that I had lying around the house. Both routers are Linksys.


Any thoughts? Are there settings on the 2nd router that need to be changed to allow for incoming traffic?

thanks

---

### Post by Alt69 on 2008-02-23
Ok, I have also tried the following:

1) while connected to the wireless router.192.168.1.1xx, i decided to also plug directly into the 2nd router, 192.168.2.1xx.

I now have two separate ip addresses, one for each subnet.

Volia, I am now able to see the Samba box located on the 192.168.2.1xx.
I figure the lan connection, with the 192.168.2.1xx, is allowing me to see this.

So, how do I get the ability to see on the 192.168.2.1xx, with my other computers connected to the 192.168.1.1xx?

Once I can work this out, the next step is to attach and share my printer, so everyone will be able to use that as well.

thanks

---

### Post by Iowan on 2008-02-23
Just my guess... sounds like the first router doesn't know where to send packets for the second subnet.

---

### Post by Alt69 on 2008-02-23
Hi, and what do I need to do to correct this? 

thanks

---

### Post by Iowan on 2008-02-23
I haven't dealt with them, so I'm no expert... but I suspect the routing tables need to be adjusted to forward traffic.

---

### Post by jhetrick62 on 2008-02-24
Ok,

I've been away.  BUT, I have a couple of systems that employ stacked routers, meaning that the second one is plugged into the lan of the first one.

Is this how you have your network configured, or do you have both routers plugged into a common switch?

Your issue is that MS will not add a route destination for a network that it doesn't belong to, in other words, it doesn't know that it belongs to 192.168.2.xxx network.  So, you need to add a dual ip address to your XP system.  Then it will always belong to both networks and windows will usually push all of that traffic over the first default gateway.

You server should be located on the first network, the one that gets it's connection from your broadband source.  Any computers on the second network, the one that has it's WAN connection fed from the first one's lan connection, all need to be dual-ip'd.  Linux can also handle having more than one address on the same adapter.  You MAY need a custom route statement for any linux machine on the second network, I'm not sure.  The windows machines should be fine though like this with just dual ip addresses.

Goodluck,
Jeff

---

### Post by Alt69 on 2008-02-25
Hi jhetrick62, yes the connection you described is what I have, "the second one is plugged into the lan of the first one".

As I am not looking to add extra cards to all of my machines, are there any other approaches? Iowan mentioned ip tables. I need to look into that. Is that something that would work?

thanks,

---

### Post by jhetrick62 on 2008-02-25
Alt69,

You don't have to add second nic cards, you just have to add second addresses.  Setting up custom routing tables is not easy by itself especially in windows and unless you have a commercial or high end router, you won't be able to add custom subnet routing like in a normal linksys router.

In a WinXP system, you get to your TCP/IP properties configuration box and click the "advanced" box.  Then in the IP settings tab, click on "add" and add an ipaddress on the second subnet.

So if your machine is 192.168.1.20 you could add another address at 192.168.2.20.  When you run an ipconfig command in the command console, you will then see both ip addresses listed.

This is a software thing, not an added nic card for the machine.

Jeff

---

