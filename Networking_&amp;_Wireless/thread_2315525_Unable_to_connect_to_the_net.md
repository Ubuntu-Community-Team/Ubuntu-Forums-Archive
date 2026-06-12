---
title: "Unable to connect to the net"
date: 2016-02-29
forum: Networking &amp; Wireless
---

### Post by pedro62 on 2016-02-29
Hello,

I have a simple net config in the /etc/network/interfaces  [http://prntscr.com/a9hqy5](http://prntscr.com/a9hqy5)
and the system continues giving me this error: [http://prntscr.com/a9hrib](http://prntscr.com/a9hrib)

Can someone help me?

Thanks,
Pedro

---

### Post by Hadaka on 2016-02-29
Hi pedro62, please post the output of..
```
ifconfig
iwconfig
```
thanks.

---

### Post by pedro62 on 2016-02-29
There it is: [http://prntscr.com/a9jpqz](http://prntscr.com/a9jpqz)

thanks

---

### Post by Hadaka on 2016-02-29
Hi, the numbers you have chosen wont work.
please allow network manager to manage it so we can see numbers that do work.
please copy and paste.
```
sudo mv /etc/network/interfaces /etc/network/interfaces.old
echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
boot and test. *if it activates correctly then please do and post.
```
ifconfig
```
then we can build your interface.
*To restore what you had you can do..
```
sudo mv /etc/network/interfaces.old /etc/network/interfaces
```
thanks.

---

### Post by pedro62 on 2016-03-01
Why the numbers are wrong if I have another linux workin with them: [http://prntscr.com/aa3gg0](http://prntscr.com/aa3gg0)

---

### Post by SeijiSensei on 2016-03-02
Hadaka asked me to take a look.  To begin with, can I ask that you copy and paste results inside of [noparse]```

```[/noparse] tags here rather than directing us to some other site.  

It's possible that you have the correct values for the host's address and its gateway, but the configuration is very unusual.  The host's IP address usually needs to be in the same subnet as the gateway unless you have some type of funky point-to-point routing set up.  Can you please post the results of the command "route -n" in code tags?  The fact that eth0 has an identical IP address and broadcast address, and that the netmask is 255.255.255.255, is also very uncommon.  It might work if you have point-to-point routing set up, but you would have to configure that manually.  Just entering two dissimilar IP addresses for the host and gateway into /etc/network/interfaces will probably not work.

I haven't used point-to-point connections for a very long time.  Typically they were used over dialup connections via SLIP or PPP rather than Ethernet.  I believe the syntax for declaring a p2p connection looks something like this:

```
/sbin/ifconfig eth0 10.10.10.10 netmask 255.255.255.255 pointopoint 192.168.0.1
```

where 10.10.10.10 would be the local address, and 192.168.0.1 the address of the remote.  If that is set up correctly, then you can declare the default route via 192.168.0.1.

Typically these connections are made over a direct wire from one machine to the other rather than via a hub or switch.  If you're using a dialup service, the telephone line takes the place of the the direct link. Usually if you're using something like [PPP]("http://www.tldp.org/HOWTO/PPP-HOWTO/") to connect, the pppd scripts would handle all this for you.

I spent about twenty minutes perusing articles on the Internet about p2p routing, but there aren't many, and the applications are pretty arcane.  Some of this functionality now appears to have migrated to iproute2, particularly the "ip tunnel" command.  Still I'd bet the original pointopoint keyword works for the ifconfig command.

That's about all I can tell you.  Who provided you with the network parameters?  Can you ask them how to connect?

---

### Post by pedro62 on 2016-03-04
Maybe the connection is unusual, but why ubuntu server does not accept that values, and xubuntu desktop is fine with it?
And what I am trying to do with this values is make an vps work with the values that my companny (ovh) provided me, and well as using an ipfailover for the vps and a mac virtual address.
```

Kernel ip routing table
Destination    gateway    genmask    flags metric ref    use iface

```

That is what appears when I do route -n

---

### Post by SeijiSensei on 2016-03-04
Well, without any routes, you won't be going anywhere.  At a minimum the machine should have a routing table like this:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 wlan0
192.168.100.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

The second line tells the operating system that hosts in the 192.168.100.0/24 network can be reached by broadcasting packets out through wlan0.  The first line tells it that all other traffic should be handed to 192.168.100.1, my default gateway, for forwarding out to other machines and the Internet.

---

### Post by pedro62 on 2016-03-04
And how can I solve that?

---

### Post by SeijiSensei on 2016-03-05
If the xubuntu machine connects, open a terminal, post the results of "ifconfig" and "route -n" on that machine, and maybe we can figure out what to do with the server.

---

### Post by pedro62 on 2016-03-10
Here is the ifconfig: [http://prntscr.com/adkh69](http://prntscr.com/adkh69)  (at the moment I can not use code tags because I can not copy the text
here the route -n: [http://prntscr.com/adkhnv](http://prntscr.com/adkhnv)

---

### Post by pedro62 on 2016-03-14
Bump

---

### Post by pedro62 on 2016-03-20
@hadaka @seijisensei are you going to answer?

---

### Post by Hadaka on 2016-03-20
Hi, Because of your unusual network configuration, it is beyond my knowledge
and experience level, sorry I am unable to help you resolve your situation.
Good luck to you.

---

