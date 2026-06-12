---
title: "Make Network Bridge avalable off-line"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by lachild on 2008-09-29
Ok I've been looking around for days but can't seem to find the answer.  So if it's already out there I'm sorry in advance.

Here's what I'm looking to do.  I have installed some guest os's on this machine and created a bridge to share files and services.  It all works great when I'm connected at work.  What I'd like to do is also make this network avalable while I'm traveling and can not connect to a network.

I have tried setting up a bridge of the LO device and this, as you can imagine, failed.  I have also attempted to setup the bridge while I was disconnected.  This let me create the bridge but the computers were unable to talk to one another.  

Is there a way to get this done?

Thanks in advance,
Lachild

---

### Post by cariboo on 2008-09-29
You will have to let us know what virtualizing soffware you are using, as the setups are all different.

Jim

---

### Post by lachild on 2008-09-30
I am using Virtual Box and using a script I found online to create the bridge.  I am currently using DHCP to generate the ip address's but can easily change these to static if needed.

Here is a copy of the startup script

```
#!/bin/bash
brctl addbr br0
ifconfig eth0 0.0.0.0
brctl addif br0 eth0

#if you have a dhcp-server uncomment this line:
dhclient3 br0

#If you have a static IP uncomment the following lines and

#change the IP accordingly to your subnet:
#ifconfig br0 192.168.178.5 up
#route add default gw 192.168.178.1

#Now we will create the tap device for the vm,!

# change your username accordingly
tunctl -t tap0 -u user
tunctl -t tap1 -u user

#Now add the tap-device to the bridge:
ifconfig tap0 up
ifconfig tap1 up
brctl addif br0 tap0 tap1
```

Thanks for your help
Lachild

---

### Post by lachild on 2008-10-29
Bump...

---

