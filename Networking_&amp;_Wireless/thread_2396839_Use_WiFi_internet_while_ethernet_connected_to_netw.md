---
title: "Use WiFi internet while ethernet connected to network"
date: 2018-07-21
forum: Networking &amp; Wireless
---

### Post by kazakore on 2018-07-21
I have some devices I wish to monitor and administer which are on a physical network and not connected in any way to the outside world. I would like to be able to still browse the internet via my WiFi connection while the ethernet is connected to the network these devices are on but as soon as I enable my ethernet connection I can no longer see the outside world! How do I get Ubuntu to use the correct device/interface for the internet? Windows and OSX both just do this automatically!! As it is usually reported if a network is connected to the internet or not why does this not happen with Ubuntu?

Limiting my browser to only use one device or another will not suffice as most of the devices are monitored and administered over http web interfaces! Thus the browser needs to check both connections when an address is entered.

---

### Post by kazakore on 2018-07-21
Yes I can do it using a VM but that really shouldn't be required! What if the device was a NAS or similar instead which I needed on the main OS? This really should Just Work(tm)!!

---

### Post by The Cog on 2018-07-21
First let's have a look at possible routing issues. 
Please can you run these two commands while your PC is connected to both the wired and the wireless network, and then copy/paste the text here:
```
ip address
ip route
```
I'm looking for overlapping networks or possibly a bad default route.
Are all the local devices on the same subnet?

---

### Post by kazakore on 2018-07-21
```
$ ip address
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 58:20:b1:74:43:9e brd ff:ff:ff:ff:ff:ff
    inet 192.168.30.45/16 brd 192.168.255.255 scope global noprefixroute enp0s25
       valid_lft forever preferred_lft forever
    inet6 fe80::217f:1006:37b5:7ac2/64 scope link 
       valid_lft forever preferred_lft forever
3: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 5c:e0:c5:4e:09:6c brd ff:ff:ff:ff:ff:ff
    inet 192.168.100.142/24 brd 192.168.100.255 scope global dynamic noprefixroute wlo1
       valid_lft 25398sec preferred_lft 25398sec
    inet6 fe80::a9fb:c971:87b4:2f7b/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```
```

$ ip route
default via 192.168.100.254 dev enp0s25 proto static metric 100 
default via 192.168.100.1 dev wlo1 proto dhcp metric 600 
169.254.0.0/16 dev enp0s25 scope link metric 1000 
192.168.0.0/16 dev enp0s25 proto kernel scope link src 192.168.30.45 metric 100 
192.168.100.0/24 dev wlo1 proto kernel scope link src 192.168.100.142 metric 600 
```

---

### Post by kazakore on 2018-07-21
> **The Cog said:**
> 
Are all the local devices on the same subnet?

Currently it's just a peer to peer straight connection to one item. .30 is the Broadcast subnet generally though and .100 the general purpose one. It's my network at work, but as I say currently only trying to get it work when the ethernet is directly connected to one single device.

---

### Post by The Cog on 2018-07-21
Eew! That's a mess. 
It seems that your LAN is 192.168.0.0/16, encompassing addresses 192.168.*.* which includes all addresses on your wireless 19.168.100.*. The chances of getting that to work are negligible. 

You also have two default routes (for reaching the internet). One via wireless, and one via the LAN. The chances of getting that to work are also slim. 

It looks to me as thought the LAN is statically configured. I think you need to reconsider the settings there. 

Firstly, don't put a default route on that interface. You won't  be able to reach the internet that way.At the moment he route via the LAN has priority because it has a lower metric, so that's where your attempts to connect to the internet will go. Find out which device is your proper working default gateway, by running the **ip route** command with the LAN disconnected and the internet working. 

Secondly, double-check the correct subnet mask for the LAN. I think it is unlikely that /16 is correct (though it is possible). I guess you will have to ask someone. If the LAN and WAN really do overlap then one of them may have to change.

You just might be able to get it working as it is by removing the default route via the LAN but it depends on which is the correct default gateway. Try:
```
sudo ip route delete default via 192.168.100.254
```

---

### Post by kazakore on 2018-07-21
> **The Cog said:**
> Eew! That's a mess. 
It seems that your LAN is 192.168.0.0/16, encompassing addresses 192.168.*.* which includes all addresses on your wireless 19.168.100.*. The chances of getting that to work are negligible. 

You also have two default routes (for reaching the internet). One via wireless, and one via the LAN. The chances of getting that to work are also slim. 

It looks to me as thought the LAN is statically configured. I think you need to reconsider the settings there. 

I initially didn't seem to be able to get it to work at all without setting the ip address manually. No DHCP server to connect to and the Share To Other Computer option wasn't giving me the right IP range before (maybe as it wasn't in the history of Manually set ones??) but appears to give me the same result of local net only when I just tried now. What setting should I use here when there is no DHCP server? (I also noticed it automatically gave me the wrong Gateway, which if it was on the full network should be .30.254 and not .100.254 but changing that as well as mask to /24 made no difference.)

> Firstly, don't put a default route on that interface. You won't  be able to reach the internet that way.At the moment he route via the LAN has priority because it has a lower metric, so that's where your attempts to connect to the internet will go. Find out which device is your proper working default gateway, by running the **ip route** command with the LAN disconnected and the internet working. 

I haven't *put* a route on anything, I've just connected a cable and let it connect (until I disconnected it as it killed the internet.)

> Secondly, double-check the correct subnet mask for the LAN. I think it is unlikely that /16 is correct (though it is possible). I guess you will have to ask someone. If the LAN and WAN really do overlap then one of them may have to change.

Just tried with 255.255.255.0 mask instead and same results. We do have certain items of other subnets, and if I want to access the file servers with documentation of etc I would need to also see the .100 subdomain the internet. But if it could be got working on just the .30 subdomain that would definitely still be an improvement.

> You just might be able to get it working as it is by removing the default route via the LAN but it depends on which is the correct default gateway. Try:
```
sudo ip route delete default via 192.168.100.254
```


Well that seems to have done it! :D
(Well along with correcting the gateway and reducing the subnet range anyway. As I said ideally 192.168.x.x would be preferred as there are other subnets with important infrastructure on them.) 


But it does beg the question as to why it was automatically put into this mess when the propriety operating systems seem to just work when connected in a similar manner??....... :-/


EDIT additional:
So I set the mask back to /16
Internet connection dies!
ip route shows "default via 192.168.30.254 dev enp0s25 proto static metric 100"
Delete this route as you instructed above.
All comes good again!

So why is Ubuntu automatically adding a more preferred route to the internet which doesn't actually have any internet access?? Surely it should check this route actually sees the outside world before adding it as the preferred route!!


...


Now if I really wanted to confuse matters I would ask how to get this working with the WiFi using my VPN (via Wireguard) while the ethernet doesn't but I do think that's really outside the scope of this thread/question!..... ;)

---

### Post by The Cog on 2018-07-21
OK, I suggest:

1: Set the LAN address back to 192.168.30.45/24. Then you will have access to the LAN's 192.168.30.*. 

2: Don't configure a default gateway on the LAN. I don't know how you are configuring the LAN interface so I can't help there. If you can't work out how to stop whatever method you are using from adding the default route then you can use a different method or manually remove the default route after the interface comes up.

3: Assuming that :
    a) 192.168.30.0/24 is actually the correct LAN subnet (i.e. the LAN really is 256 /24 subnets and not one giant /16), and
    b) You can find the proper IP address for the router on that subnet (192.168.30.254 might be a good guess, but better to ask someone, maybe whoever told you to use 192.168.30.45)
then:
    Add a static route to 192.168.0.0/16 via whatever the router's address on the LAN is. This should enable you to reach all of 192.168.*.* on the LAN, except for 192.168.100.* which is of course locally connected to your wireless interface. This can perhaps be done as part of the interface config so it happens automatically, or later by a command like:
```
sudo ip route add 192.168.0.0/16 via 192.168.30.254
```

If you are fixing up the static routes by script, then it would make sense to put both commands in the one script.

---

### Post by kazakore on 2018-07-22
> **The Cog said:**
> OK, I suggest:

1: Set the LAN address back to 192.168.30.45/24. Then you will have access to the LAN's 192.168.30.*. 

It works with /16 as long as I delete the created route so that's not too much of an issue.

> 2: Don't configure a default gateway on the LAN. I don't know how you are configuring the LAN interface so I can't help there. If you can't work out how to stop whatever method you are using from adding the default route then you can use a different method or manually remove the default route after the interface comes up.

I initially hadn't and that's when it auto-set it as .100.254
How can I find out what application/process a window is from? I use Studio so it's XFCE based, accessing it via the Notification Area widget (I can't stand Indicator) if that gives you any pointers. Unfortunately it has no About option in the menus.

A friend of mine who has worked in hardware pen testing for years, so regularly connecting point to point on the ethernet and wanting wifi separate, told me you'v always had to delete the ethernet route on connecting and it's normal but annoying Linux behaviour....

> 3: Assuming that :
    a) 192.168.30.0/24 is actually the correct LAN subnet (i.e. the LAN really is 256 /24 subnets and not one giant /16), and
    b) You can find the proper IP address for the router on that subnet (192.168.30.254 might be a good guess, but better to ask someone, maybe whoever told you to use 192.168.30.45)
then:
    Add a static route to 192.168.0.0/16 via whatever the router's address on the LAN is. This should enable you to reach all of 192.168.*.* on the LAN, except for 192.168.100.* which is of course locally connected to your wireless interface. This can perhaps be done as part of the interface config so it happens automatically, or later by a command like:
```
sudo ip route add 192.168.0.0/16 via 192.168.30.254
```

If you are fixing up the static routes by script, then it would make sense to put both commands in the one script.

if I was actually on the full network I would use DHCP mode and get that to issue me a IP in the correct range (which if on the Broadcast network would be 192.168.30.x) but as I was configuring this in point2point connection and knew the items IP address (192.168.30.211) I just gave myself a random one for the moment within that subnet to be able to connect and configure it. In fact this is behaviour that might be in use more often, and when equipment has come from the manufacturer the default IP could be just about anything within the private network ranges. So there is a need to be able to plug into a piece of equipment not on a larger network and configure it (through http/ssh/telnet or whatever) as well as a desire to be able to connect to the larger company network.

I know each subnet (or what I believe are separate subnets) have their own firewalls and filter settings so assume they are truly separate subnets but it's not within my areas of expertise....

I actually think our WiFi has changed in the last couple of months, I'm not sure if it's actually been moved onto the wired general subnet of 192.168.100.x (which is what the general desktops, file servers, domain controllers etc are on) or if it's just coincidence. Fairly sure it used to be somewhere in the 172.16-31.x.x PN range. Might be interesting to find out.... I don't really want to congest the network which is actually in use with the likes of nmap though......

I think I'll just have to get used to deleting the route once it auto-creates it. At least I now know that is what needs to be done. Happy to mark this as Solved even if I think this could be handled better internally (afterall Ubuntu does know the network can't see the outside work and gives you a network icon to indicate this, so why set the route when it sees it hits a wall?)

---

