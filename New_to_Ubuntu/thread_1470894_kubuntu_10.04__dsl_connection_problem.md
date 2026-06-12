---
title: "kubuntu 10.04  dsl connection problem"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by j_goldie on 2010-05-03
Hi, 
I'm trying to set up dsl connection (modem connection, not router) in kubuntu 10.04. I added new dsl connection, set up my username, service (pppoe) and password. However, the kde's network manager doesn't show my new connection on connection's list.
I had no problem setting up the connection in gnome via gnome's network manager (username, service and pass are the same as in kde's network manager, of course). 
best regards,
j_goldie

---

### Post by madjr on 2010-05-03
not too sure about kubuntu, so you may want to search what others are saying or post at kubuntu forums

[http://www.kubuntuforums.net/forums/index.php](http://www.kubuntuforums.net/forums/index.php)

---

### Post by -humanaut- on 2010-05-03
Do you have a web GUI to setup your modem such as Qwest Does?

---

### Post by j_goldie on 2010-05-03
> **madjr said:**
> not too sure about kubuntu, so you may want to search what others are saying or post at kubuntu forums

[http://www.kubuntuforums.net/forums/index.php](http://www.kubuntuforums.net/forums/index.php)
thx, will try there.
@ -humanaut-
don't understand the question. I used knetworkmanager, and set up the dsl connection there. sorry if i understood wrong
best regards,
j_goldie

---

### Post by -humanaut- on 2010-05-03
Whose your service provider?

---

### Post by j_goldie on 2010-05-04
> **-humanaut- said:**
> Whose your service provider?
my provider is t-com. As I said, I have no trouble setting up the connection in gnome's nm-applet. Only with kde's GUI/applet/plasmoid, whatever it is.  
best regards,
j_goldie

---

### Post by azhar0106 on 2010-05-30
> **j_goldie said:**
> Hi, 
I'm trying to set up dsl connection (modem connection, not router) in kubuntu 10.04. I added new dsl connection, set up my username, service (pppoe) and password. However, the kde's network manager doesn't show my new connection on connection's list.
I had no problem setting up the connection in gnome via gnome's network manager (username, service and pass are the same as in kde's network manager, of course). 
best regards,
j_goldie
I am also facing the same problem.
This problem is keeping me from using kubuntu all the time.
BTW, I have installed kde-desktop over ubuntu installation, ubuntu's network manager is working fine.

But, I really want to move to kde completely.
:(

---

### Post by kirantheja on 2010-06-22
> **j_goldie said:**
> Hi, 
I'm trying to set up dsl connection (modem connection, not router) in kubuntu 10.04. I added new dsl connection, set up my username, service (pppoe) and password. However, the kde's network manager doesn't show my new connection on connection's list.
I had no problem setting up the connection in gnome via gnome's network manager (username, service and pass are the same as in kde's network manager, of course). 
best regards,
j_goldie

Even i installed KDE over gnome version of ubuntu... In gnome the DSL works fine but unable to get d same in KDE. Though i have added the new connection in DSL it doesn't show up when i click the icon in d tray...

Even local home networking isn't working :popcorn:

---

### Post by lolara on 2010-11-27
Same problem here.. :)

---

### Post by lkraemer on 2010-11-28
j_goldie,
You didn't mention if you are trying an Ethernet connection or if it is a
Wifi Connection.

Be sure to check your browser to make sure it isn't set for OFFLINE.

Check all your DSL Modem Lights.
They all should be GREEN when you have a valid connection.  If one isn't GREEN
post back the color and the LED name.

Try the following commands:
```

route
route -n
route -nee
netstat -r
ping yourgatewayIPaddress

```

If you can't ping the Gateway IP address then your Login & Password
for your ISP are incorrect.

Connect via an Ethernet Cable, then make sure ENABLE NETWORKING is checked.
Then open a Terminal Window and do:
```

ping www.yahoo.com

```
CNTL C will terminate the transmission.  You should see:
```

[larry@localhost ~]$ ping www.yahoo.com
PING any-fp.wa1.b.yahoo.com (72.30.2.43) 56(84) bytes of data.
64 bytes from ir1.fp.vip.sk1.yahoo.com (72.30.2.43): icmp_req=1 ttl=53 time=76.8 ms
64 bytes from ir1.fp.vip.sk1.yahoo.com (72.30.2.43): icmp_req=2 ttl=53 time=81.3 ms
64 bytes from ir1.fp.vip.sk1.yahoo.com (72.30.2.43): icmp_req=3 ttl=53 time=79.7 ms

```

If that doesn't work try:
```

ping 72.30.2.43

```

If you can't get to [www.yahoo.com](www.yahoo.com), double check your DNS Servers are 
set in the DSL Modem.  You might want to set the OpenDNS Servers instead.
Google OpenDNS Servers
```

208.67.222.222
208.67.220.220

```


Then try setting up Wifi after this is working.

lk

---

### Post by lkraemer on 2010-12-04
How is it going?  

We would Greatly Appreciate a Follow-Up Post.

lk

---

