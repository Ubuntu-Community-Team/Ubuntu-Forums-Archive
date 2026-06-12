---
title: "Making TUN/TAP Permanent"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by TDave on 2008-06-16
I recently setup a TUN/TAP connection for a WinXP VM within VirtualBox as per the instructions here: [https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03](https://help.ubuntu.com/community/VirtualBox#head-ac88c03223e773c78dbb46b4b13c109de1143a03)

It worked perfectly and was fairly easy to do.

However, unsurprisingly, when I came to restart the connection was 'forgotten' and I was back to plain old eth0 - no br0, no tap1, etc.

I can understand why these would be forgotten (not written into /etc/network/interfaces), but my question is how do I go about making it permanent?

So I have an idea as to what I need to do, I'm just not entirely sure how to do it. Do I need to add a command to rc.local to create the bridge first? How about for creating tap1?
And how would the notation look within /etc/network/interfaces to set eth0 to promiscuous?
```
iface eth0 inet 0.0.0.0 promisc
```
??

Pretty sure these will be obvious answers that I've failed to spot, but any pointers would be appreciated!

Thanks

---

### Post by SpaceTeddy on 2008-06-16
i am not sure if this answeres your question, but check out part2, step 3 on this [[COLOR="Blue"]tutorial[/COLOR]]("http://ubuntuforums.org/showthread.php?t=752127"). It shows how to permanently add bridges via the /etc/network/interfaces. The tun is only when the openvpn is loaded tho... 

hope it helps :)

---

### Post by TDave on 2008-06-17
Thanks for that, that certainly helps a good way along the road.

Does your final comment mean that creating the tap1 connection isn't possible automatically? Or just not through /etc/network/interfaces?

Would there be a way to run this, perhaps via /etc/rc.local ?

I'm throwing theories out here - I would try them out more readily, but it's a work desktop and I want to try to avoid breaking it as much as possible!

Cheers,

TD

---

### Post by SpaceTeddy on 2008-06-17
you can add the tap device via the rc.local. Since that is ran AFTER the network has been initialized, you can just create the tap there and then add it to the bridge... 

my comment was for adding it via the /etc/network/interfaces... but i am getting an idea now and will google it for a while...
[searching...]

right-o. This is not the most elegant way i can think of, but i found a way to add tap devices to your /etc/network/interfaces. Check this [[COLOR="Blue"]page[/COLOR]]("http://www.ctserver.org/ftopic1446.html") to see examples (and where i got mine )

```
iface tap0 inet manual
        pre-up tunctl -t tap0
        up ifconfig tap0 up
        down ifconfig tap0 down
```

if you add this to your /etc/network/interfaces (and add it BEFORE the br0 device) you should have the tap0 ready when the bridge is configured. So you should be able to add the tap0 to the bridge via the normal network config.
As i said, this is not elegant, as this really only runs commands and DOES NOT use the actual logic behind real network cards. But it is better than nothing... 

tell me how it works :)

---

### Post by TDave on 2008-06-18
:-( No joy unfortunately, but thanks for the recommendation!

I tried adding it as per your recommendation (which, judging by the output on the link, was correct), but no joy. After startup:

```

MyUser@Desktop:~$ sudo ifconfig tap1 up
tap1: ERROR while getting interface flags: No such device
```

/me sighs.

Any ideas as to a way to add everything in to create the TAP before the bridge, then bring it up after the bridge?

As I understand from the first guide I was following, the commands I need to run are:
```
~$ sudo tunctl -t tap1 -u MyUser
~$ sudo brctl addif br0 tap1 
~$ sudo ifconfig tap1 up
```

Of course, it's not the end of the world manually running those commands each time I start up the machine (would a simple shell script handle this easier?), but if I can get it automated it would be slick :-)

At least the Bridge is created fine... :-)

Thanks again,

TD

---

### Post by SpaceTeddy on 2008-06-18
i take you changed tap0 into tap1 ??? the little snipped did work here on my ubuntu 8.04 server (vm - fresh install) - i am a little surprised about this... 

anyway, good look hunting the solution

---

### Post by TDave on 2008-06-18
Yep, sorry, just have specified that.

The snippet from my /etc/network/interfaces is as follows:

```
iface tap1 inet manual
        pre-up tunctl -t tap1
        up ifconfig tap1 up
        down ifconfig tap1 down
```

Hmmm... looking at it again, does it need an auto tap1 line ? I would have thought that wouldn't make any difference though, seeing as manually trying to up tap1 failed without first running through the tunctl and brctl bits.

Running 8.04 here as well.

Is all a tad confusing and, like I said, not really the end of the world in and of itself. Adding the bridge was the one part that was nice to get automated, it would just be nicer if I could find some convenient way to add the tap as well, seeing as I'm going to need to be opening it and running through it every time I startup.

Would the Shell Script idea work? Alas my knowledge of shell scripts sucks (read: I'll spend the afternoon googling how to do it right) but if I got on that works then forcing it to run on startup should be a simple matter, right?

Thanks again for your help on this, it is appreciated :-)

---

### Post by TDave on 2008-06-30
Finally bit the bullet and went for the /etc/rc.local approach.

Added the following lines to it:
```
tunctl -t tap1 -u MyUser
brctl addif br0 tap1
ifconfig tap1 up
```

And it seems (on the first reboot at least...) to have worked!

Thanks for your help on this SpaceTeddy. I'm still at a loss as to work out why we had different results using /etc/network/interfaces and we tried some variations here, but, for now, it works! :-)

---

### Post by neon777 on 2008-09-23
The "right way"  ;)

cat /etc/network/interfaces:

blablabla....

auto tap30
iface tap30 inet static
        address 10.10.30.1
        netmask 255.255.255.0
        pre-up /usr/sbin/tunctl -t tap30

---

### Post by xiphos45 on 2009-08-21
I for whatever reason was not able to get this to work using /etc/network/interfaces. I, however, was able to get it to work with rc.local. I was trying to bridge tap interfaces to vmnet interfaces, so that I could both access my GNS3 lab and my VM network. If I wanted it to work without the VM network, I would just leave out the VMnet interfaces in the configuration. This works across reboots. 

rc.local:

tunctl -t tap1 -u *user*
brctl addbr br1
brctl addif br1 tap1
brctl addif br1 vmnet1
ifconfig tap1 0.0.0.0 promisc up
ifconfig vmnet1 0.0.0.0 promisc up
ifconfig br1 5.5.5.1/24 up

---

### Post by csmiga on 2010-08-06
All:

The solution provided earlier in this thread has been verified.

#> vi /etc/network/interfaces

auto br0
iface br0 inet static
    hwaddress ether 00:06:5B:3C:44:BF
    address 172.16.0.1
    netmask 255.240.0.0
    network 172.16.0.0
    broadcast 172.31.255.255
    gateway 172.16.0.2
    bridge_ports eth1
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off

auto tap0
iface tap0 inet static
    hwaddress ether 00:06:5B:3C:44:C0
    address 172.16.0.10
    netmask 255.240.0.0
    network 172.16.0.0
    broadcast 172.31.255.255
    pre-up /usr/sbin/tunctl -t tap0

Thank you for your contributions.

-- Christopher

---

