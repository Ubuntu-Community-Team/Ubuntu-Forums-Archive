---
title: "lamp server connection refused"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by pspsampsp on 2009-03-22
i have set up a lamp server using this guide [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) and all computers on my lan can visit the website by typing in my local ip which is 192.168.1.195 however when i type in my external ip adress i get connection refused. i have setup port fowarding of port 80 and i am almost 100% sure my isp doesnt block port 80 does anyone have any suggestions or any alternative ports i copuld use?

---

### Post by cariboo on 2009-03-22
Check [canyouseeme]("http:///www.canyouseeme.org/") to to be sure that port 80 is open. I would also suggest if port 80 is open, have a friend on a different subnet try to access your web page.

Jim

---

### Post by pspsampsp on 2009-03-23
canyouseeme said Success: I can see your service on 222.153.147.60 on port (80)
Your ISP is not blocking port 80. i am starting to think it might be my router that is the problem as i set it to log all incoming connections and it has said there have been none.

---

### Post by pspsampsp on 2009-03-23
lol this was something so stupid i made a noob mistake , if you use your external ip to access your server from within your lan it won;t work , you have to use a proxy or set up a dns/ddns , i set up a ddns and everything is working fine now thanks for your help  , sam

---

