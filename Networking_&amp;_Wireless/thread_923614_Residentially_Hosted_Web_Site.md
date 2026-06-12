---
title: "Residentially Hosted Web Site"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by secondstage on 2008-09-18
Port forwarding is setup for my local IP behind the wireless router, but people still can't access my site when they put in my external IP address. According to the tester personel, they come to a web search of the IP. Any idea?

PS. They are using Internet Explorer 7 in Windows XP SP3

---

### Post by yogensha on 2008-09-18
This basically means that the far end browser wasn't able to connect to your server.  If the external port of your port forward is anything other than port 80, they must specify the port when connecting.  For example, if you external port is 1080, they would use http://<your_ip>:1080.

One good way to see if the forward itself is working is to use tcpdump on the server machine.  You may have to install tcpdump.  Fire up a terminal and, as root, run 'tcpdump host <your_ip> port 80'.  This command will show all packets to and from port 80 on the server.  If the forward is working correctly, you should see packets coming from the client.

Also, verify that you can access the server locally by entering your private side IP in your browser's URL field.

---

