---
title: "I &quot;networkly bricked&quot; my remote server via VPN bridging (can't access it anymore)"
date: 2018-08-28
forum: Networking &amp; Wireless
---

### Post by bobis on 2018-08-28
Hello , I own an Ubuntu Desktop 18.04.1 LTS that I run it as a server (hereafter referred as "pc-server" in the whole post. Ubuntu Server was not enough for me since I wanted some graphical programs to run at it too).

I am currently in vacation so I access this pc-server only  via ssh,sftp , vnc over ssh , as well as I have set up an OpenVPN server, (all the ways mentioned before have their respective ports forwarded in the router, since I access my pc-server from the Internet, outside my LAN) just to have easy access to my LAN devices like routers and access points from the internet via the pc-server. I also use it as file storage , like a network NAS , so I access my files via sftp or smb (smb or samba is always over OpenVPN connection only). 

Now to the point of my post: As you know,  OpenVPN (hereafter referred to as "VPN"), uses tap0 (and tun0 , but in my case , I only used tap0) interface in the pc-server to create tunneled connections. These connections come in a special subnet like 10.6.0.0/24 , where 10.6.0.1 is the IP of pc-server itself (the "router" of the VPN). At the same time , pc-server is connected via ethernet cable, providing the physical network interface eth0 , with static ip of 192.168.135.2. So,  when I connect to my VPN from my remote location (vacation) as I am now, I obtain an IP like 10.6.0.6 which is then routable via VPN to the next hop , which is the 192.168.135.1 router, the router of my pc-server that connects to the Internet and also the "creator" of the 192.168.135.0/24 LAN which the pc-server physically is a part of.

Now, in order for a specific app to work in my side , I had to make these two networks bridged ( the eth0 and tap0 interfaces) . In other words, instead of 10.6.0.6 , I wanted to obtain an IP of 192.168.135.6 (the meaning of the bridge here is to bypass the 10.6.0.0/24 subnet and its NAT , so bypass a hop at traceroute, right? ) So , I went and read some tutorials in the OpenVPN site of interface bridging and after that I concluded editing my /etc/network/interface like this:

```

...................................................
auto br0
iface br0 inet static
address 192.168.135.2
netmask 255.255.255.0
gateway 192.168.135.1
network 192.168.135.0
broadcast 192.168.135.255
dns-nameservers XXX.XXX.XXX.XXX
bridge_ports eth0

auto eth0
iface eth0 inet static
address 192.168.135.2
netmask 255.255.255.0
gateway 192.168.135.1
network 192.168.135.0
broadcast 192.168.135.255
dns-nameservers XXX.XXX.XXX.XXX
...................................................
```


the tap0 interface was set up in a way that it would be connected to the above bridge while the openvpn server service was starting (up.sh script)

Then, I rebooted my pc-server and guess what! I lost the connection! Since I am not physically close to pc-server , I have to wait for my return home in order to plug a monitor and keyboard and fix it.

So , my question here is since I passed the same IP settings from eth0 to br0 interface , why on earth the connections were all disabled, like the interfaces are dead or the ethernet cable was disconnected? 

Thank you

---

### Post by TheFu on 2018-08-29
You can't have 2 network devices using the same IP.  eth0 and br0 can't both be on .2.
```
network 192.168.1.0
broadcast 192.168.1.255

```settings are unnecessary.  I think you are missing some bridge options too. For lurkers, never use wifi for bridges. 

You shouldn't use a commonly used local subnet if you want to use VPNs.  192.168.1.x is a poor choice.  Use something like 192.168.46.x/24 to prevent lots of dumb issues.  Routing from a local network using  192.168.1.x  to your home network using  192.168.1.x  just doesn't work.

I don't use tap interfaces with openvpn and never use CIFS over openvpn. Aren't there some big performance problems doing that?

To get the best help, post output from commands, not config files.
ifconfig
route -n
and brctl show
are what I'd use.

You might need to also look at firewalls and some tcpdump packets to see how far packets are actually getting.

BTW, I've been there - 14K miles from home and my ISP back home dropped the connection. It is a pain.

---

### Post by bobis on 2018-08-29
Hello, well I used 192.168.1.x as an example to define the local network  subnet, I am surely concerned about the conflict of when you are for example in a friend's home with 192.168.1.x as the LAN IP'S and your home which the VPN server is located, also uses 192.168.1.x internal network...you want to observe a host @ 192.168.1.10 at your home but it is also the ip of your buddy' laptop! 

I have edited the IP's on my main post as the correct value.

---------------------------------------------------------------

To the point: I managed to "re-create" the accident. Since I have access to my router  from outside my LAN  , I managed to  send wake on lan packet via the router to my gaming pc (this is my main pc desktop rig with windows 10), which is in the same network as pc-server. Interesting the fact that on my router, the pc-server "appears" online reporting its MAC but it is not pingable. Thus, wake on lan of course had no effect on pc-server!

So, after I woke my pc, I used teamviewer to access it and managed to install virtualbox on it and created a guest ubuntu machine, exactly like the pc-server.  (I now regret how idiot I am that I didn't think about it at first, you should always test such network things in a VIRTUAL MACHINE before applying them in  a real machine, when both of them are out of physical reach! At least, if you make a serious mistake on the virtual machine and it stopped appearing online or stuck,  you can always access its screen at home machine's vm software and restore it as if it was a physical machine and you connected a monitor and keyboard on it).

So, I installed OpenVPN server on the vm and set the /etc/network/interface exactly like what I pasted in my first post. As it was expected, the vm either was not able to boot (recovery mode from grub showed that it stucked on a line related to "network") , or booted but with connectivity to zero, no Internet, no pings, nothing.

But , I was able to fix this by just deleting the eth0 lines and only mention it as "iface eth0 inet manual" at the interfaces file and eventually, by using a proper tutorial, I managed to complete my tap vpn setup, working it 100%.

In the tutorial I followed, it was mentioned about static dhcp of br0 interface. In other words, static ip don't work at br0 and you need to set it as "iface br0 inet dhcp" in order for tap vpn to work but for keeping the ip constant, you need to go to the router and set a static dhcp ip of a given MAC address.

And then , an idea was came up with me  , to set static dhcp to my missing pc-server...let's see if it will take it when it will boot up the next morning! (pc-server is always shutting down via cron at 3 am and opens at 9 am)

---

### Post by TheFu on 2018-08-29
br0 that isn't static will cause issues, but you can use DHCP or DHCP reservations, if you like. It is your network. The tutorial you are following is incorrect.   Using the "manual" for eth0 is what I do. No other settings.

**Also, with 18.04, everything changed.  You get to learn netplan.** The older  "interfaces" file isn't used.

I don't bother shutting down anything, but I'm running email servers and hosting public websites.

---

