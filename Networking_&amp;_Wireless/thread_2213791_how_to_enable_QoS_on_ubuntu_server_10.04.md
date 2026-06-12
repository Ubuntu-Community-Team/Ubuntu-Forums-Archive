---
title: "how to enable QoS on ubuntu server 10.04"
date: 2014-03-28
forum: Networking &amp; Wireless
---

### Post by Rajib_Pan on 2014-03-28
Hi,
     **_My setup is following ._**
     (a)   I have a server ubuntu vers 10.04 installed at loc A. 
      (b)  I have application Big Blue Button vers 0.81 loaded on server 
      (c)  I have three client of Big Blue Button vers 0.81 at loc X,Y,Z
      (d)  I have a QoS  enabled network between all the three client loc  and the server . In my network video packet has         
            **highest priority** .
   **         _Problem Statement_**
            (a)   When even I am running multiparty video conf between these three location on BIig Blue Button ver 0.81 my         
            network between client & server is not able to read video packet as **priority packet** and are traces-singas normal data packets. This is giving this multiparty conf feature of Big Blue Button ver 0.81 less priority on the network viir a vir other applications running on the network.

**         _Action already done_**

            IP Tables have been Installled

**          _Kindly Assist on_**

            (a)  Priority packet to be provided to video packets of BBB ver 0.81 passing through Ubantu ver 10.04 server so that QoS  enabled network in between can recognize DSCP Value 46 and give priority incoming and outgoing packet of this application packets.

---

### Post by Old_Grey_Wolf on 2014-03-28
You should probably ask Cisco or bigbluebutton.org.

---

### Post by papibe on 2014-03-28
Move to **Networking & Wireless**.

---

### Post by papibe on 2014-03-28
Hi Rajib_Pan.

AFAIK, the QoS should be set on the routers/switches that connect the networks between locations A, X, Y and Z.

Unless, the Ubuntu server is serving as in one of those functions, I don't think it would make a difference.

In any case, this may help:
[LIST]
[*][Shape and/or throttle an ip on the network (QoS)]("http://askubuntu.com/questions/388390/shape-throttle-an-ip-on-the-network-qos").
[*][Linux Advanced Routing & Traffic Control HOWTO]("http://lartc.org/howto/").
[/LIST]
Hope it helps.
Regards.

---

