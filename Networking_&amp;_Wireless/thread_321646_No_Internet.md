---
title: "No Internet"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by Mac70 on 2006-12-19
I have a D-Link DSL624T which works fine with Windows but nothing happens on Ubuntu. Ive re-ran the setup wizard, Ive checked out other threads and links following their advice, and Ive done some pinging.
When I ping my router, Mozilla, Google, and a couple of the IP addresses I found in the router it seems to be doing so successfully.
What am I doing wrong?

---

### Post by jbus on 2006-12-19
If you can ping by IP it could be that your DNS servers were not configured correctly. Is your network adapter configured to obtain its setting automatically from your router? If it is it should get the DNS servers configured, but you should check and enter it manually if necessary. This is usually your routers IP address if your router is set up with your ISP's DNS servers.

---

### Post by Mac70 on 2006-12-19
When I look at the DNS in Network it has my routers IP.Ive added others and last night it worked long enough for me to reach the Mozilla Homepage then stopped.
I tried gedit /etc/dhcp3, etc and tried a couple of addresses to no avail.
Im with BT Yahoo BB if that helps but I cant seem to find their IP.
Ive tried the start address from the router which pinged fine but the other address didnt.

---

### Post by disabled_20220313 on 2006-12-19
**ignore suggestion**

---

### Post by jbus on 2006-12-19
One other thing you should check real quick is to make sure that your gateway is set to your routers IP. I'm not sure what version of ubuntu you are using, but I remember setting up a couple of machines with Dapper using DHCP and the gateway didn't automatically configure for some reason.

---

### Post by Mac70 on 2006-12-19
Im using 6.06.
How do I set up the gateway? 
I have so many IP addresses written down now Im getting confused.

---

### Post by Mac70 on 2006-12-19
I have noticed onething. Ubuntu talks of PPPoE whereas BT says PPPoA.Can this be a problem?

---

### Post by Mac70 on 2006-12-19
Ive just checked on this. BT Yahoo insists on the encapulation being PPPoA. ](*,)

---

### Post by Mac70 on 2006-12-19
I have solved it.:-D 
I went into the router and changed to PPPoE.I am now writing this from my Ubuntu OS.:KS

---

