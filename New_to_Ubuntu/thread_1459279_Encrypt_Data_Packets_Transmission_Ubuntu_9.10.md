---
title: "Encrypt Data Packets Transmission Ubuntu 9.10"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by happytimelogan on 2010-04-21
Does anyone know what kind of information you can get from monitoring data packets sent and received?
Also a good program to use in order to monitor my own data packets, mainly so I can see what anyone else could see about my data packets so I can tell if they are encrypted or not.
Lastly, is it possible to set Transmission (or any other P2P client) up so all data sent and received is encrypted to such an extent that someone could not tell the difference between downloading an mp3 / avi / even a pdf other than the amount of data being sent and received on an ISP level?

Would appreciate any ideas you have on this.

Thank you!

---

### Post by jpaugh64 on 2010-04-21
Look into ssh. I use open-ssh. It was a bit messy for me to figure out how to use it, but a web search will reveal some decent tutorials and how-to's. 

Specifically for the last question, you can use ssh to do this for any network program. It is called *tunneling*, or *port forwarding*. Basically, you set up a ssh client to listen on some port number X, and to transfer all data received to the correct port on the server (whatever the P2P client normally connects to). Then, connect the P2P client (or whatever) to your own machine on port X.

I think that is how ssh tunneling works, but I have yet to try it.

---

### Post by dwarfolo on 2010-04-21
> **happytimelogan said:**
> Does anyone know what kind of information you can get from monitoring data packets sent and received?
Also a good program to use in order to monitor my own data packets, mainly so I can see what anyone else could see about my data packets so I can tell if they are encrypted or not.
Lastly, is it possible to set Transmission (or any other P2P client) up so all data sent and received is encrypted to such an extent that someone could not tell the difference between downloading an mp3 / avi / even a pdf other than the amount of data being sent and received on an ISP level?

Would appreciate any ideas you have on this.

Thank you!

What you are looking for is actually a sniffer.
You can use tcpdump to perform some basic traffic analysis, but there are many other tools around that can do advanced things.

---

### Post by e4uforums on 2010-04-21
Wireshark is a great packet analyzer.

---

