---
title: "can i reverse ssh to 2 different clients from server"
date: 2014-11-24
forum: Networking &amp; Wireless
---

### Post by billtill8 on 2014-11-24
hi i have a machine in work and a server in the cloud i can reverse ssh to my server from work with 
ssh -R 6333:127.0.0.1:user_server@server
this will tell the server to send any data on 6333 my work machine. so if im at home i can connect to my work with 
ssh user_computer@server -p 6333
this will connect to my server and send data to work due to the work connection listening on 6333

however if i had another computer at different ip address BUT THE SAME PORT 6333 how could i tell the server which computer to log onto?

would specifying the username (user_computer) work or is there a better way?

---

### Post by Lars Noodén on 2014-11-24
You would need to specify a different port on your server in the "cloud".  The same port cannot be used twice.  So on one machine you coud use one port:

ssh -R 6333:localhost:22 user_server@server1

and then on another machine use another port:

ssh -R 6334:localhost:22 user_server@server1

Otherwise, if the port on the server is already in use you will get an error like this when trying to reverse forward:

"remote port forwarding failed for listen port *xxxx*"

---

### Post by billtill8 on 2014-11-24
but this would require me add another socket and forward another port which i am trying to avoid i need to use 1 port and find some way to instruct the server what ip to send the data onto

---

### Post by Lars Noodén on 2014-11-24
If you have this network:

```

machine1 -----+
              |
              LAN ----- Internet ----- server1 ------ Internet ----- home
              |
machine2 -----+

```

Then you will have to use different ports on server1, one port will be a reverse forward to machine1, the other to machine2.  What about using two ports / sockets causes trouble?  There should be a way around that.

---

### Post by billtill8 on 2014-11-24
thanks for replys

---

