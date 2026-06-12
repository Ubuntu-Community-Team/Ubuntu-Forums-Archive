---
title: "port fowerding local web server"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by Baconfatty on 2008-06-19
so ill make this brief im trying to set up a web server off of my computer that's at home, i have everything installed on ubuntu that i need to to run it however. my external ip is 72.189.83.212 and i have my router set up to froward ports 80-89 to my local ip 192.168.1.108 but i dont know the address i need to put into a computer on another network to get to my local web server. everyone ive asked about this doesnt know and google has been to no assistance do you know what to do here?

---

### Post by SpaceTeddy on 2008-06-19
first off - you only need to forward ports 80 and 443 (http and https). 81-89 are not necessary for a web-server. 

The easiest way to always have a home server running is to get yourself a hostname that is held active by your computer. I, personally, use no-ip.com for that, but any will do (others are dyndns, etc). 

Once you have the hostname, lets say example.no-ip.org, you can then give out that name to others to connect to your webserver. Also, note that you will need to distinguish between internal and external access. While the internal access will work through your internal ip and NOT via the no-ip hostname, the access from the internet will ONLY work via the no-ip hostname. The reason behind this is that normal routers do not allow port forwarding from internal to internal - only from external to internal. 

hope it helps (a little) :)

---

### Post by superprash2003 on 2008-06-19
you should be able to access using the static ip you mentioned 72.x.x.x.x .. but as spaceteddy said its better to register with a service like no ip which is free.. here's how you set it up [http://prash-babu.blogspot.com/2008/05/how-to-setup-no-ip-on-your-computer.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-no-ip-on-your-computer.html)

---

### Post by Baconfatty on 2008-06-20
thank you so much it was a great help what was stoping it was i didnt have the other port unblocked

---

