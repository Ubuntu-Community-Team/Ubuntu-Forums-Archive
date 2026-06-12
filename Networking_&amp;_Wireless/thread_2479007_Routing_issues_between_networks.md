---
title: "Routing issues between networks"
date: 2022-09-11
forum: Networking &amp; Wireless
---

### Post by franksantoro on 2022-09-11
My Ubuntu server is on 192.168.155.17 and I have another server on 192.168.1.143. I put in a custom route to be able to get to the gateway(192.168.1.1) of the 192.168.1.0/24 subnet. I am able to ping and traceroute to 192.168.1.1 but not to 192.168.1.143. Its unclear what more I need to add in from a routing perspective as I can get to the 192.168.1.1 gateway.

 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=291023&stc=1[/IMG]

---

### Post by TheFu on 2022-09-11
Please don't post images for text.  We cannot selectively copy the text to point out issues easily.  Plus, many people pay for internet by the byte still.
This would be helpful to get the columns to line up ... 
```
$ ip route | column -t
```

I miss the old **route -n** command. It was human readable. 

On first look, it seems there are two entries for the subnet you are trying to reach. That's bad.

---

### Post by franksantoro on 2022-09-11
Sorry about that. Here is the text output. I put in two routes because I was troubleshooting. I can delete the route to 155.1 but I still have the same issue 

```
[FONT=Arial]
default           via  192.168.155.1    dev    eth0    proto   dhcp  metric  100[/FONT]
[169.254.0.0/16]("http://169.254.0.0/16")[FONT=Arial]    dev  eth0             scope  link    metric  1000[/FONT]
[172.17.0.0/16]("http://172.17.0.0/16")[FONT=Arial]     dev  docker0          proto  kernel  scope   link  src     172.17.0.1      linkdown[/FONT]
[172.18.0.0/16]("http://172.18.0.0/16")[FONT=Arial]     dev  br-de26f5b9c101  proto  kernel  scope   link  src     172.18.0.1[/FONT]
[192.168.1.0/24]("http://192.168.1.0/24")[FONT=Arial]    via  192.168.155.1    dev    eth0[/FONT]
[192.168.1.0/24]("http://192.168.1.0/24")[FONT=Arial]    via  192.168.1.1      dev    eth0    metric  200   onlink[/FONT]
[192.168.155.0/24]("http://192.168.155.0/24")[FONT=Arial]  dev  eth0             proto  kernel  scope   link  src     192.168.155.17  metric    100
[/FONT]
```

---

### Post by TheFu on 2022-09-12
These forums have a way to get columns to line up. That's by using 'code tags'. All terminal output should be put into "code tags" so spacing is honored, like it is in the terminal.

Edit the post above - use the "Adv Edit" option and use the '#' key to wrap the output in code tags.  My post has an example of code tags, though it isn't exactly a good use since there aren't column data. Don't make it hard for others to help and see the issues.

It would be helpful if the source, destination, and all network devices in between were clearly described too and commands from each to the others shown.

I don't have time now to look in more depth. Routing isn't my specialty.  Sorry.

---

### Post by The Cog on 2022-09-12
Does your server 192.168.1.143 know how to send to 192.168.155.17? What route to use? I suspect that's your problem - no return route.

---

### Post by franksantoro on 2022-09-12
Yes I did a tracert on my windows server on 192.168.1.143: 

```

C:\Users\Frank_Server>tracert 192.168.155.17


Tracing route to santoro-guacamole [192.168.155.17]
over a maximum of 30 hops:


  1    <1 ms    <1 ms    <1 ms  unifi.localdomain [192.168.1.1]
  2    <1 ms    <1 ms    <1 ms  santoro-guacamole [192.168.155.17]


Trace complete.


C:\Users\Frank_Server>

```

---

### Post by TheFu on 2022-09-12
This is my summary of the first post.

GW            192.168.1.1
subnet        192.168.1.0/24
Ubuntu server 192.168.155.17  (aka santoro-guacamole)
Windows       192.168.1.143

What are all the other IPs in your posts?
What's the container IP?  If it isn't on

For Windows <--> Ubuntu Srv, you need routing on both sides.
Windowws --> Ubuntu and Ubuntu --> Windows.

I don't know from where the ping and traceroute are to and from. Please be clear.

Posting commands without a description for what you think they are proving, means we have to guess the meaning.

Is there a reason that the Ubuntu system isn't in the same subnet as the Windows system?  That certainly would make things easier.  Also, the container would be on the same subnet too.  Walk before trying to sprint.  How is the linux bridge setup?  Netplan.yaml file config?  I'd say to get this working first, before trying to get different subnets involved.

I'm ignoring all the 172.x.x.x/16 stuff.

And it appears there's some Ubiquiti wifi involved somewhere.

The general troubleshooting is to
a) Simplify
b) Test
c) Repeat until the problem area is clear.

---

### Post by The Cog on 2022-09-14
If I understand this right, you can traceroute from 192.168.1.143 to 192.168.155.17, but can't traceroute from 192.168.155.17 to 192.168.1.143. 
I don't think I understand the network you have there. On your server 192.168.155.17, please can you run these commands:
```
ip address
ip route
ip route get 192.168.1.143
```
and on 192.168.1.143 run
```
ip address
ip route
ip route get 192.168.155.17
```

The next step is to run this command on each, and try the ping. 
```
sudo tcpdump --nntl -i any icmp
```Then we can see who is sending and receiving ping packets. If 192.168.1.143 is receiving but not replying, then suspect the firewall there, probably blocking inbound pings (tcpdump shows what's on the wire, outside of the firewall processing).

---

### Post by SeijiSensei on 2022-09-15
Any Ubuntu machine acting as a router will not pass packets between interfaces. Edit (as root with sudo) the file /etc/sysctl.conf and remove the hash mark from the line "#net.ipv4.ip_forward=1" then run "sudo sysctl -p" to force a reread of the configuration file.  Any better?

Most distros now block ip forwarding by default as a security protection.

---

