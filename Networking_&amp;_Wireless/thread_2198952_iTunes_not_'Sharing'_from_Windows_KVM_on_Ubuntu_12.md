---
title: "iTunes not 'Sharing' from Windows KVM on Ubuntu 12.04"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by Casey_Friday on 2014-01-11
I'm currently running a bit of a convoluted setup.  My cable modem sends CAT5 into an AirPort Extreme (WiFi N) router.  I've just purchased a [WD AC1300 WiFi AC router]("http://www.amazon.com/gp/product/B00A14ZUIM/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00A14ZUIM&linkCode=as2&tag=cbte-20") and a [WD AC Bridge]("http://rcm-na.amazon-adsystem.com/e/cm?lt1=_blank&bc1=000000&IS2=1&bg1=FFFFFF&fc1=000000&lc1=0000FF&t=cbte-20&o=1&p=8&l=as4&m=amazon&f=ifr&ref=ss_til&asins=B00A66WJWK") to go with it, to get AC speeds to the NAS on the other side of the house.  They were both [on super clearance]("http://slickdeals.net/f/6588702-wd-my-net-wireless-ac-bridge-21-ac1300-wireless-ac-dual-band-router-33-or-less-office-depot-clearance-low-stock-availability") at Office Depot for about $20 each, so I figured let's give this wireless gigabit thing a try, eh?

So on my NAS, which is connected to the AC Bridge via ethernet, I'm running Ubuntu 12.04 Server headless.  I just installed a Windows VM via KVM, so I can run an always-on iTunes server.  To make understanding my network setup easier, here's a diagram.

[IMG]https://lh6.googleusercontent.com/-3MB_Vxk0Q8s/UtF9e6I9mqI/AAAAAAAAGSY/Qp_v_PdQPdg/s800/Home%2520Network%2520Setup.jpg[/IMG]

When I fire up iTunes on the Windows KVM, I can't see the library on all the other computers running iTunes on the network.  Sharing works from all other laptops/iPads, etc, but it's not working from this Windows KVM.  When I plug my laptop directly into the WiFi AC Bridge, I can see the share, so the AC Bridge must be doing something that's throwing off the network settings; however, I'm pretty sure I've set it up correctly (no DHCP, static IP on the same subnet as everything else).

The real kicker is that I can still stream Plex, access the NAS, and do everything else that resides on the Ubuntu part of my NAS.  So it's just the Windows KVM that needs me to be plugged into the AC Bridge in order to see it.  I can ping the Windows instance from my laptop connected to the AirPort Extreme, so there's no connection problem there either.

I've read that IPv6 causes iTunes sharing issues, but I've disabled it in Ubuntu 12.04 and in Windows, and no joy.  Could this be an iTunes Bonjour problem?  Anyone else running something like this and have ideas for how I can get it working?

---

### Post by tomearp on 2014-01-11
There is a [page on the linux-kvm site]("http://www.linux-kvm.org/page/Networking#public_bridge") that explains the different networking options, which is probably worth a read. From a cursory glance it appears you want to configure it as a public bridge to allow other hosts on the network to communicate with the VM.

---

### Post by Casey_Friday on 2014-01-11
I'm pretty sure I have the bridge set up properly, so unless I have it wrong, I don't think that's it.  Here's my /etc/network/interfaces

> caseyfriday@fridaynode:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
    address 192.168.0.100
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
    gateway 192.168.0.1
    dns-nameservers 208.67.222.222 208.67.220.220
    bridge_ports eth0
    bridge_fd 0
    bridge_stp off
    bridge_maxwait 0

Does anything look off in my syntax?

Edit: I can ping the VM from my Mac laptop connected as shown above, so I can obviously talk to the VM wirelessly, yet when I try to access my Plex Media server (192.168.0.100:32400) from within the VM, it doesn't work.  I can even ping my laptop from the VM.  I just don't know why I can't share iTunes!

---

### Post by Casey_Friday on 2014-01-11
Well, I might have an idea now of what's causing this issue, but I'm not totally sure.  Here's the output of brctl show:

```
caseyfriday@fridaynode:~$ brctl show
bridge name    bridge id        STP enabled    interfaces
br0        8000.7427ea486386    no        eth0
                            vnet0
virbr0        8000.000000000000    yes        
caseyfriday@fridaynode:~$
```

So I'm guessing vibr0 is the virtual bridge being used by the kvm?  If so, that could be problematic, because here's the output of ifconfig:

```
caseyfriday@fridaynode:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 74:**:**:**:**:**  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:312848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:744171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:879466873 (879.4 MB)  TX bytes:747974155 (747.9 MB)

eth0      Link encap:Ethernet  HWaddr 74:**:**:**:**:**  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:282190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:363054215 (363.0 MB)  TX bytes:40208598 (40.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:22308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20714933 (20.7 MB)  TX bytes:20714933 (20.7 MB)

virbr0    Link encap:Ethernet  HWaddr d2:**:**:**:**:**  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr fe:**:**:**:**:**  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:388443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:927506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:881273680 (881.2 MB)  TX bytes:1069554225 (1.0 GB)

caseyfriday@fridaynode:~$
```

vibr0 has an IP address not in the same subnet as the rest of my devices.  So how can I set the IP address for vibr0, so that my VM's network bridge keeps it on the same subnet as everything else?

Edit: I've just read that vibr0 is for NAT only, and I'm not using NAT in my kvm - just using a bridge.  I still don't know why I can't access my NAS's services, share iTunes, etc, while internet access is working fine.

---

### Post by tomearp on 2014-01-11
The only thing that I would say looks a bit off is this part:

```
.....
# The primary network interface
auto eth0
iface eth0 inet manual


auto br0
iface br0 inet static
.....
```

The linux-kvm site suggests that [the br0 part completely replaces the eth0 part]("http://imgur.com/Ghq2LZn").

It does seem unusual that bi-directional pinging is possible but not other things. Have you tried disabling Windows Firewall and testing the sharing, just in case it's that doing something daft? (e.g. it might see the network as a 'public' network, and only allows the bonjour service to have full access on a 'home' network)

---

### Post by Casey_Friday on 2014-01-12
Yeah, that was one of the first things I tried.  Disabled the 'local' and 'public' firewalls in Windows 7.  I even went in and found the rules for each Bonjour service and made sure they were wide open for communication.

---

### Post by Casey_Friday on 2014-01-12
> **tomearp said:**
> The linux-kvm site suggests that [the br0 part completely replaces the eth0 part]("http://imgur.com/Ghq2LZn").

If I do that, will it screw up the ethernet connection in Ubuntu, though?

Edit: Just tried that, and although everything still works normally, still no joy with iTunes sharing.

---

### Post by tomearp on 2014-01-12
Hmm, have to be honest I'm running out of ideas! Daft questions; I assume in the Windows 7 VM that you're signing in with the same Apple ID as the rest of your devices? Also, how many devices do you have? A maximum of 5 devices can use Home Sharing with the same Apple ID.

From the [Apple site]("http://support.apple.com/kb/ts2972"):

A maximum of five computers can use Home Sharing at one time. If this limit has been reached and you want to add a new Home Share, deauthorize one or more computers by choosing Deauthorize Computer from the Store menu in iTunes. For more information about authorization and deauthorization, see About iTunes Store authorization and deauthorization.

---

### Post by Casey_Friday on 2014-01-12
That's for Home Sharing, which allows you to drag/drop/copy stuff from one computer to another.  Although I tried that too, regular iTunes sharing should work as well.  You simply click "Share this library on my local network" in Preferences, so that you can stream to other users.  That's not working either.  I am logged in with the same Apple ID.

I ran ipconfig in Windows, and it reports 192.168.0.25 as an IP address, and 192.168.0.1 as the gateway - which is correct!  I just don't know why sharing's not working.

I think the solution lies in the fact that I can't access the services on my NAS (the host) from the Windows VM.  For instance, I can't access Plex.  I can ping my NAS host (192.168.0.100) successfuly, but when I try to go to 192.168.0.100:32400/manage/index.html, It doesn't load.  Same with SABnzbd, Webmin, etc.  Could it be some sort of port blocking going on, that I need to open up ports inside of the Windows VM?

BTW - thanks so much for offering your help.  I hope we can get this figured out!

---

### Post by tomearp on 2014-01-12
No worries, there will be a solution!

Have just found [this page]("https://help.ubuntu.com/community/KVM/Networking") in the Ubuntu community help wiki. It has some info about setting up bridging for VMs; might be worth having a read through to see if there are any extra steps that might not be other documentation. There is mention of [IP aliasing]("https://help.ubuntu.com/community/KVM/Networking#IP_Aliases") (to give VMs static IPs on the network) and [forwarding ports]("https://help.ubuntu.com/community/KVM/Networking#Redirecting_selected_ports_to_virtual_machines") to make services running on the VM accessible to other machines on the network.

[This page]("http://support.apple.com/kb/TS1629") lists common ports used by Apple devices. TCP 3689 is listed for iTunes music sharing.

It still doesn't answer the question of course of why the VM can't access services running on the host, but if the bridging is not quite right then it could be as a result of that.

---

### Post by tomearp on 2014-01-13
Have just come across [this recent post]("http://ubuntuforums.org/showthread.php?t=2199150") about KVM in 12.04. It appears to have a set of steps to follow in order to use bridging.

---

### Post by Casey_Friday on 2014-01-13
I'll give this a try and see if it works.

---

### Post by Casey_Friday on 2014-01-13
Hmmm, those /etc/network/interfaces settings are identical to the ones I have already.  I guess the question is, how is the Windows VM getting its IP of 192.168.0.25 when the host has a static IP of 192.168.0.100, and that's what the bridge states in my /etc/network/interfaces?  Does the bridging in KVM take care of giving the VM a unique IP?

---

### Post by Casey_Friday on 2014-01-13
I also just added a firewall rule to allow incoming and outgoing traffic for TCP port 3689.  Still no joy. :(

---

### Post by Casey_Friday on 2014-01-16
I think I'm beginning to see why this is not working.  The vibr0 device I listed previously is indeed what KVM is using as a network device, and it's on a different subnet than the rest of my network devices.  So it seems as if KVM is using 192.168.122.x as a bridge, then assigning 192.168.0.x IP's to virtual machines, but they are all on what equates to a private bridge - not public.  So now I'm trying to figure out how to change the 'virtual network' to be on the same network as everything else in the house.

[IMG]https://lh4.googleusercontent.com/-yXXtmmOded0/Uthej53ctdI/AAAAAAAAGS8/TbpYp-jEIww/s800/Screen%2520Shot%25202014-01-16%2520at%25204.20.49%2520PM.png[/IMG]

Setting up this new virtual network on the correct subnet.

[IMG]https://lh5.googleusercontent.com/-DGqSs-4H05U/Uthej-FVtVI/AAAAAAAAGS4/J6wspeHnNMY/s800/Screen%2520Shot%25202014-01-16%2520at%25204.21.57%2520PM.png[/IMG]

---

### Post by Casey_Friday on 2014-01-20
Well that didn't work.  Any other ideas how I can get this bridge to work properly?

---

### Post by Casey_Friday on 2014-01-20
Okay, I tried to remove some complexity by setting the Time Warner Arris modem to bridge-mode, so it passes the full connection through to the AirPort Extreme.  I still set the subnet as 192.168.0.x, to keep things simple.

I installed Firefox on the Windows 7 VM, and it turns out I can actually see the Plex Media Server on the host, as well as the host's other services.  So it's just iTunes that's not sharing now.  I'm going to post in the Apple Support forums to see if anyone can help me there, as they might have more extensive iTunes knowledge.

---

### Post by Casey_Friday on 2014-03-01
Figured it out - there was too much network complexity.  I joined the WD MyNet network - the same one the Ubuntu Server is on - and the library showed right up.  I'll be moving into a new house soon, and there will only be one wireless router, and the NAS will be connected via ethernet, so this won't be an issue then.

But fortunately, I've figured it out now!

---

