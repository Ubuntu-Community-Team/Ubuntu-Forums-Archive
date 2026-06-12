---
title: "Conflict btwn UFW and Windows Network NAS"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by jaycee23 on 2009-10-31
I am now using the Koala but I have an issue with trying to access my NAS which is on my Windows Network.

If I turn off UFW it will connect without issue but turn it on and all I see is Windows Network and when I click on it nothing appears.

I have googled it and searched this website but I can't find how I can allow the firewall to let me access the network.

If I turn off the firewall then access the NAS I can turn it back on and as log as I don't close the connection I can access my files quite freely with the firewall back up and running.

Does anyone have a simple solution to what I need to adjust on UFW

:(

---

### Post by jaycee23 on 2009-11-01
Any ideas anyone??

Still looking for a simple solution

---

### Post by jaycee23 on 2009-11-01
Eventually found a solution of sorts 

Used the command 
ufw allow from "ip address" seems to works

---

