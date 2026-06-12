---
title: "Ethernet network router"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by snip3r8 on 2010-07-05
I have 3 PCs and no ethernet router but one of them (peta) has two ethernet cards so both the other machines are hooked up to  peta. how can i get these two PCs to share files by using peta as a router?

---

### Post by snip3r8 on 2010-07-05
This thread has had 9 views but no reply ,any reply would be appreciated,even if you just call me a retard,i will appreciate it.

---

### Post by Telengard C64 on 2010-07-05
> **snip3r8 said:**
> I have 3 PCs and no ethernet router but one of them (peta) has two ethernet cards so both the other machines are hooked up to  peta. how can i get these two PCs to share files by using peta as a router?

You said you don't have a router, but do you have a hub or switch?

How are the other two computers *hooked up* to peta? If you simply connected standard cat5 cable between the network cards then you don't have a network. The cable required to connect to two ethernet network cards together is called an [_ethernet crossover cable_](http://www.answers.com/topic/ethernet-crossover-cable)

After you have a physical network you will probably want to assign IP addresses to each machine. Then you can verify your network with the ping command.

Finally you can install either [_Samba_](https://help.ubuntu.com/community/SettingUpSamba) or [_NFS_](https://help.ubuntu.com/community/SettingUpNFSHowTo) file server software on peta to make sharing easy. There are other ways to share files between computers on a LAN too.

---

### Post by snip3r8 on 2010-07-05
peta has one cable going to pc1 (nano) and another cable going to pc2 (salt) there is no hub or switch but i want to use peta as the hub/switch/router

---

### Post by snip3r8 on 2010-07-05
I know i should probably get a hub but i just want to see if it can be done using some sort of network bridging application.The point of this is to test what a pc can do,with help from forum brains.

---

### Post by Bachstelze on 2010-07-05
Yes, it is perfectly possible. I don't know how to do it in Linux, though, I usually use OpenBSD for such network appliances. Try Google for "linux ethernet bridging", it gives a lot of results, what you're looking for is in there. ;)

---

### Post by snip3r8 on 2010-07-05
I got something off the repositories called bridge-utils but not sure how to configure it.

---

### Post by Telengard C64 on 2010-07-05
> **snip3r8 said:**
> peta has one cable going to pc1 (nano) and another cable going to pc2 (salt) there is no hub or switch but i want to use peta as the hub/switch/router

Unless those are [_ethernet crossover cables_](http://www.answers.com/topic/ethernet-crossover-cable), you don't have a network. What I am trying to get across here is that the network card can't transmit and receive data on the same wire, at least not for standard cat5 ethernet cables.

If someone knows how to do it without a hub, switch, router, or crossover cables, I'd really love to read about it.

---

### Post by snip3r8 on 2010-07-06
After installing bridge-utils i ran the following code which allowed salt to see nano and vice versa but now peta is all on its own and cant see either so right now ive turned peta into a cable connector,not a switch

```

brctl addbr br1
brctl addif br1 eth0
brctl addif br1 eth1
ifconfig br1 up

```

---

### Post by Xianath on 2010-07-06
Basically, you want both cards (and the respective machines attached to them) in two separate subnets, and route between the two. You need to add "net.ipv4.ip_forward = 0" to /etc/sysctl.conf. It will take effect on restart but you can "sudo sysctl -w net.ipv4.ip_forward=0" to force it now. Then for each of your other two boxen you need to set a route to the other's network via peta. This is OS specific so we'll need to know what the other boxen are running. I'm pretty sure you will have to set a simple iptables rule, too, but let us know how the above is working and we'll take it from there.

Telengard C64, this hasn't been true for years ever since automatic crossover was invented. My home NAS has a dedicated 1GB for my diskless Windows box, and they've been living happily for three years connected with a through cable. I guess someone just got fed up with patching crossover cables and came up with a solution :)

And as a side note, this might look like a basic question but unless you want to have your hand held and not understand a thing (doubtful, given that you've already tried the hard way), it probably belongs to the Wireless & Networking section.

---

### Post by Telengard C64 on 2010-07-06
> **Xianath said:**
> 
Telengard C64, this hasn't been true for years ever since automatic crossover was invented. My home NAS has a dedicated 1GB for my diskless Windows box, and they've been living happily for three years connected with a through cable. I guess someone just got fed up with patching crossover cables and came up with a solution :)

Really? That's the first I've heard of it. Can you please direct me to somewhere I can read more about how this works?

---

### Post by gsocker on 2010-07-06
This is frequently  known as auto MDI/MDI-X. It is required as part of the Gigabit Ethernet spec, and is also implemented by many fast Ethernet cards and switches.

---

### Post by Telengard C64 on 2010-07-06
Ty  :)

@OP, sorry but it seems my networking knowledge is a little dated.

---

### Post by snip3r8 on 2010-07-09
> **Xianath said:**
> Basically, you want both cards (and the respective machines attached to them) in two separate subnets, and route between the two. You need to add "net.ipv4.ip_forward = 0" to /etc/sysctl.conf. It will take effect on restart but you can "sudo sysctl -w net.ipv4.ip_forward=0" to force it now. Then for each of your other two boxen you need to set a route to the other's network via peta. This is OS specific so we'll need to know what the other boxen are running. I'm pretty sure you will have to set a simple iptables rule, too, but let us know how the above is working and we'll take it from there.

Telengard C64, this hasn't been true for years ever since automatic crossover was invented. My home NAS has a dedicated 1GB for my diskless Windows box, and they've been living happily for three years connected with a through cable. I guess someone just got fed up with patching crossover cables and came up with a solution :)

And as a side note, this might look like a basic question but unless you want to have your hand held and not understand a thing (doubtful, given that you've already tried the hard way), it probably belongs to the Wireless & Networking section.


all machines running karmic

---

### Post by snip3r8 on 2010-07-11
i added what you said i should and im still sitting with a connection bredged between salt and nano and peta still sees nothing

---

### Post by snip3r8 on 2010-07-12
ok i have sucess ,peta now sees nano and salt,i summed up what i did...

-Download Bridge_utils

-Create the following script:

```
brctl addbr br1
brctl addif br1 eth0
brctl addif br1 eth1
ifconfig br1 up
ifconfig br1 192.168.35.1
```

the IP adress should be the same as other two (eth0 and 1)

-add  "net.ipv4.ip_forward = 0" to /etc/sysctl.conf
 and then restart or "sudo sysctl -w net.ipv4.ip_forward=0"

-run script

---

