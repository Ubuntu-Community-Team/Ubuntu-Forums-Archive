---
title: "My Ubuntu server doesn't connect to Ethernet when rebooted"
date: 2020-10-13
forum: Networking &amp; Wireless
---

### Post by shottyman on 2020-10-13
For some reason every time my Ubuntu server restarts the LAN Ethernet adapter just goes kaput I'm not quite sure why and not sure what to put in to help since I just started using Ubuntu server yesterday. I apologize for my complete lack of knowledge.

---

### Post by TheFu on 2020-10-14
Try a new cable?
Try a different port in the switch?

---

### Post by chili555 on 2020-10-14
Please open a terminal and show us the result of these terminal commands:

```
ip addr show
cat  /etc/netplan/*.yaml
```

---

### Post by shottyman on 2020-10-14
[IMG]https://ibb.co/jJvZBpM[/IMG]https://ibb.co/sCTD7c0
[https://ibb.co/jJvZBpM](https://ibb.co/jJvZBpM)

---

### Post by chili555 on 2020-10-14
Are you wanting to use ethernet or wireless? The wireless seems to be well and truly connected in both cases.

Where is the netplan result?

---

### Post by shottyman on 2020-10-18
I was planning to use Ethernet since the wireless form what I have seen only has 70 Mbps of transfer and the ether has 100 and I was thinking of using the server as a NAS so the faster transfer speed was welcomed and the samba doesnt seem to be working under wireless but I'm not quite sure if that is the original reason. Also I apologize for responding a bit late

edit: I should have mentioned I am using a laptop as the server an hp notebook 15 I believe with the Insyde bios (not quite sure if it has another bios)

---

### Post by chili555 on 2020-10-18
The netplan file is remarkably empty. I wonder, therefore, how, exactly, the wireless is connected. Ordinarily, in a server, netplan controls all networking. Since your netplan yaml enumerates neither wireless nor ethernet, we are confused.

Is Network Manager installed? Wicd? Or...what?

---

