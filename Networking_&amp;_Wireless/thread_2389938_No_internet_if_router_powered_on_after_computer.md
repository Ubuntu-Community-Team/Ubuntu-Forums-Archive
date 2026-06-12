---
title: "No internet if router powered on after computer"
date: 2018-04-23
forum: Networking &amp; Wireless
---

### Post by oygle on 2018-04-23
I usually turn on the router first and then the computer and have no problems with networking. However, if I turn on the computer first (no router on ), there is no internet.

No amount of deactivating and activating the network via the network icon on the desktop will start the network correctly. Even a reboot does nothing. In this situation, I have to shutdown and then after a reboot, the network is fine.

Are there some command level (terminal) instructions to restart the network in this situation please ?

---

### Post by TheFu on 2018-04-24
If the router provides the network settings to the system, which is common through DHCP, then the computer doesn't get any network configuration.

Over the different releases of Ubuntu, the methods to start and stop networking have changed.  If you can tell use which release version you are running, someone can probably provide the CLI commands to start/restart the networking subsystem.   For trivial network setups, this should work, but for non-trivial networking, I've had issues where the whole system network restart doesn't work unless I manually bring each component down in the correct order, then bring it back up in the reverse order, correctly.

But you can bypass all of this by setting up a static IP on your LAN. How that is properly accomplished depends on the release. 12.04, 14.04, 16.04 and 18.04 each have different config file options/methods.

---

### Post by oygle on 2018-04-24
Thanks for your reply. yes, the router provides the network to the system.

I'm using Kubuntu 16.04.4 LTS. I'd assume my setup is trivial. I think I can also setup a static IP from the router, not totally sure though. But if it all works better by setting up on Kubuntu, all the better. :)

---

### Post by SeijiSensei on 2018-04-24
Have you tried logging out after turning on the router, then logging back in? Usually Ubuntu tries to establish the network connection during login.

---

### Post by TheFu on 2018-04-24
> **SeijiSensei said:**
> Have you tried logging out after turning on the router, then logging back in? Usually Ubuntu tries to establish the network connection during login.

Is that really true?  All my systems handle network connections at boot, not login.  It would be a huge bug if a running Unix system didn't have networking without a user logged in on the console. After all, how would they ssh in?

Could it be a KDE thing?

Setting a static IP can be done on the system in the /etc/network/interfaces file or using a DHCP reservation from the router.  But if you do it in the router, obviously, it will only work if the router is on FIRST.  

[https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html) explains how.  Best to do it on the Ubuntu side.
About 3/4 of the way down is an example. Yours will need to be a little different, but it is just 6 lines that need to be added. Don't touch the "lo"  lines.  Use **sudoedit** to edit the file safely.  Be certain NOT to use an IP that it in the router managed DHCP range.

---

### Post by SeijiSensei on 2018-04-25
On client systems that use NetworkManager and wifi, I'm pretty sure there is no network connection until the user logs in and selects one of the available SSIDs, either manually or by default.  From looking at /var/log/syslog on an Ethernet-connected machine, those connections may happen before login.  

I have a machine that is primarily a workstation that displays on my TV and uses wifi.  I can't see it from other places on the network until I've logged in to it and let NetworkManager connect to my default SSID.

I've seen other symptoms of this problem.  For instance, using /etc/rc.local to run scripts on wifi-connected machines fails because the network is not available.  The machine I mentioned acts as a masquerading router via its Ethernet port for other Internet devices like the TV itself and a PS3 console.  I can only run the script that sets up the interfaces and the iptables rules after logging in and starting the wifi connection since the wifi interface is undefined before then.

I'm sure I could script dhclient, iwlwifi, and whatever else is needed to make the network connection happen during boot.  It doesn't bother me enough to invest the effort

---

### Post by oygle on 2018-04-26
> **SeijiSensei said:**
> Have you tried logging out after turning on the router, then logging back in? Usually Ubuntu tries to establish the network connection during login.

I tried this today, but it didn't work.

> **TheFu said:**
> Setting a static IP can be done on the system in the /etc/network/interfaces file or using a DHCP reservation from the router.  But if you do it in the router, obviously, it will only work if the router is on FIRST.  

[https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html) explains how.  Best to do it on the Ubuntu side.
About 3/4 of the way down is an example. Yours will need to be a little different, but it is just 6 lines that need to be added. Don't touch the "lo"  lines.  Use **sudoedit** to edit the file safely.  Be certain NOT to use an IP that it in the router managed DHCP range.

I found the section "Static IP Address Assignment" from that link, but what I saw was 5 lines, not 6, so I didn't proceed any further.

Some info ....

```
$ ifconfig -a
```

> enp7s0    Link encap:Ethernet  HWaddr **:**:**:**:**:**  
          inet addr:192.168.20.2  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: ****::****:****:****:****/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64669 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113554673 (113.5 MB)  TX bytes:7868339 (7.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:385351 (385.3 KB)  TX bytes:385351 (385.3 KB)

wlp6s0    Link encap:Ethernet  HWaddr **:**:**:**:**:**  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
$ cat  /etc/network/interfaces
```

> # interfaces(5) file used by ifup(8) and ifdown(8)                                                                                                                                              
auto lo                                                                                                                                                                                         
iface lo inet loopback

```
$ ifconfig lo
```

> lo        Link encap:Local Loopback                                                                                                                                                             
          inet addr:127.0.0.1  Mask:255.0.0.0                                                                                                                                                   
          inet6 addr: ::1/128 Scope:Host                                                                                                                                                        
          UP LOOPBACK RUNNING  MTU:65536  Metric:1                                                                                                                                              
          RX packets:3205 errors:0 dropped:0 overruns:0 frame:0                                                                                                                                 
          TX packets:3205 errors:0 dropped:0 overruns:0 carrier:0                                                                                                                               
          collisions:0 txqueuelen:1                                                                                                                                                             
          RX bytes:385351 (385.3 KB)  TX bytes:385351 (385.3 KB)
          
> **SeijiSensei said:**
> On client systems that use NetworkManager and wifi, I'm pretty sure there is no network connection until the user logs in and selects one of the available SSIDs, either manually or by default. 

Whilst this router does have wifi, I only use cat5 (cable) to the computer. I found these notes in a file that was 9 years old, so not sure if it is still appropriate

```
sudo /etc/init.d/networking restart
sudo /etc/init.d/NetworkManager restart
```

But I'd assume that the 'disconnect/connect' that I'm trying from the gui/desktop is the same ??

---

### Post by TheFu on 2018-04-26
The init.d/ commands have been deprecated since 12.04. You should be using systemctl now that systemd is used as the init system. 16.04 and later need to use this.
```
sudo systemctl restart networking.service
```

Thanks for the information. Add these lines to the bottom of the /etc/network/interfaces file using **sudoedit /etc/network/interfaces**
```
auto enp7s0
iface enp7s0  inet static
  address 192.168.20.250
  gateway 192.168.20.1
  netmask 255.255.255.0
  dns-nameservers 1.1.1.1 1.0.0.1 8.8.8.8 8.8.4.4
```
Before doing this, check your **route -n** to see the router IP.  The .1 IP above is just an educated guess. It could be wrong and really bad things will happen if it is wrong. CHECK FIRST.

I made up the .250 IP. The main thing is it has to be in the CIDR for the subnet, but not inside the router DHCP managed space.  The DNS choices are up to you. Order matters.  I put in the cloudflare privacy dns service followed by google's DNS.  Normally, only 2 are used, but it shouldn't hurt. Google claims they don't track DNS queries, cloudflare has made some very difficult decisions and ALWAYS goes towards providing privacy and freedom of speech.

The interfaces file is not used from 17.10 and later, "*they*" decided that something called "NetPlan" is better than doing what we've been doing for 30+ yrs. Perhaps that is true. IDK. 

Anyways, hope this helps.

---

### Post by oygle on 2018-05-13
> **TheFu said:**
> The init.d/ commands have been deprecated since 12.04. You should be using systemctl now that systemd is used as the init system. 16.04 and later need to use this.
```
sudo systemctl restart networking.service
```


Thanks. I had occasion this morning to try that command. The first time, nothing at all happened (no difference to network), but I tried it a minute or 2 later and the network was going okay. Whether the network would have restored okay without doing it the second time, .. who knows  ??

Thanks for the other info re setting up the static IP. I hope to get to that soon.

---

