---
title: "Problem with my internet - please help"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by Epperly on 2006-11-08
Hi, in Ubuntu recently for some reason, my internet has been going on and off randomly it seems. I check the network monitor/manager periodically, and most of the time I can play with things and get it to work again.
Today it was on, then went off, and I went into Network Tools and saw under network device it was on lo rather than eth0, and actually just now as I'm typing I checked and it was back to lo but in the network-monitor it says it's set to eth0..

Is the network device what's causing my random internet goings off?
Because the network device sets to lo(even though network monitor says eth0)?

I'd really appreciate any help/input on this..
Thanks!

---

### Post by Epperly on 2006-11-08
Well if anyone can help me I have updated information..

I set my Network IP to static and made the static work, but it seems the problem is that the "default gateway device:" which is eth0, sometimes changes to blank, and when I try and select it it'll be seen there until I close out of network settings, then if I open it again it'll be blank again.

I don't know why it's doing this, Ubuntu never did this before (especially because I just reformatted because I thought something in Ubuntu became the problem)
This is getting aggrivating..

---

### Post by bioman85 on 2006-11-08
Hey there,

I'm having the same problem, but with my ath0 wireless NIC. Connectivity will go down at random, but I haven't seen it go back up again. All I have to do to get it started again is to go to my System -> Administration -> Networking, and disable and enable ath0, and it works again. 

I'm not using ndiswrapper yet.

Not really sure how to troubleshoot this issue.

-Chris

---

### Post by Peepsalot on 2006-11-08
Hey guys.  I haven't had these specific problems before, but I thought I'd chime in to see if I could help anyways.

Are you editing your network config through the GUI tools?  If so, maybe try editing the config file directly to see exactly what is going on.  The file path is "/etc/networks/interfaces"

I set mine to static, and deleted all the unused devices(maybe the extras are somehow causing conflicts for you?)

This is what mine looks like now
```

auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1

```
One nice side effect is that you can shave a couple seconds off your boot time by removing extraneous devices from here.

BTW, lo is the loopback device, which I think is necessary for many programs to function, (though I'm not exactly sure why).  So I wouldn't recommend removing that one.

run "man interfaces" in terminal for more info.

and remember to back up before you try any changes ;)

---

### Post by jakethesnake on 2006-11-09
Peepsalot I think I found out what is wrong with my connection. 

But when I try to edit that file I'm getting the warning that I do not have the permissions necessary to do that. ?

---

### Post by Epperly on 2006-11-09
in /etc/network/interfaces this is what I have (also I have set my eth0 connection to static, and so far it has yet to shut down[but it is running very slow and sluggish, which is new to me])
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.100
netmask 255.255.255.0
gateway 192.168.2.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by Peepsalot on 2006-11-09
> **jakethesnake said:**
> Peepsalot I think I found out what is wrong with my connection. 

But when I try to edit that file I'm getting the warning that I do not have the permissions necessary to do that. ?
You need to edit it with administrative permissions.  in terminal, run "sudo gedit /etc/network/interfaces"

> in /etc/network/interfaces this is what I have (also I have set my eth0 connection to static, and so far it has yet to shut down[but it is running very slow and sluggish, which is new to me])

eth0,eth1,eth2 represent standard ethernet jacks.  If you only have or use one of them, then you should be able to safely delete the others.
ath is for dialup modems.  
wlan is for wireless (wifi) adapters.
So for any of those that you aren't using, you can remove those lines from the file.  I honestly don't know if that will really help your particular problem, but I think it is worth a shot.

---

### Post by Epperly on 2006-11-09
ok well luckily I messed up my permissions so I can't edit now hah sweet
(sarcasm)
:(

---

### Post by trubblemaker on 2006-11-09
> **jakethesnake said:**
> Peepsalot I think I found out what is wrong with my connection. 

But when I try to edit that file I'm getting the warning that I do not have the permissions necessary to do that. ?

you got to use 
```
sudo vim /etc/network/interfaces
```
next time it goes down run 
```
dmesg
``` and post the output it might give us some info.

---

