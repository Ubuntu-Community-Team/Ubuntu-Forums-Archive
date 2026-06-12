---
title: "Static IP Settings.....how do i get them"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-18
I've been having issues with staying connected via my wired connect to my wireless modem.  It's been suggested to set a Static IP through Network Manager.  My question is, how do I find the following settings, so I can set this up.

MAC Address
Address
Netmask
Gateway
DNS Servers

I hope this solves my problem with dropping my connection.

Thanks,

JS

---

### Post by mkvnmtr on 2009-03-18
I believe I set my static IP through my router. I logged on to the page of my router and there set my address and opened ports for the applications that I wanted open. I found  the page for my router by googleing "port fowarding". There is a page with that name that will tell you hw to do each router. Each router is a little different.

---

### Post by pdoma on 2009-03-18
If you're using a wireless router you can most likely create a reservation on it for your PC. You can also set your PC to use a static IP by modifying the /etc/network/interfaces file but if you are using a laptop that may not be a good idea cuz you most likely would not be able to connect to any other network without modyfying it again. 

To answer your question... you can find most of this information by typing in ifconfig in the console this will show you the information that your PC is using when obtaining IP through DHCP.

---

### Post by unutbu on 2009-03-18
With your current DHCP connection working, run the following commands:


To find your MAC address, your IP address, and netmask, open a terminal (Applications>Accessories>Terminal) and type
```

ifconfig
```
A wired network interface is usually called [COLOR="Teal"]"eth0"[/COLOR].
The output will look something like this:
```

...
[COLOR="Teal"]eth0[/COLOR]     Link encap:Ethernet  HWaddr **20:22:ae:30:b0:20**  <-- **MAC Address**
          inet addr:[COLOR="Red"]192.168.1.81[/COLOR]  Bcast:192.168.1.255  Mask:[COLOR="Lime"]255.255.255.0[/COLOR]  <-- [COLOR="Red"]IP Address[/COLOR], [COLOR="Lime"]Net Mask[/COLOR]
...

```

Next type
```

route -n
``` 
The output will look something like this:
Look for the numbers in the Gateway column. 
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         **192.168.1.1**     0.0.0.0         UG    100    0        0 wlan0 <-- **Gateway**
```

Next type
```
dig

```
Near the bottom of the output you will see
```

;; Query time: 31 msec
;; SERVER: **192.168.1.1**#53(192.168.1.1)  <-- DNS Server
;; WHEN: Wed Mar 18 08:46:51 2009
;; MSG SIZE  rcvd: 512

```
(In this example the DNS server is also the gateway. Your case may be different.)

Also, /etc/resolv.conf should contain a list of DNS Servers if you are setup with more than one. For example, 
```

search myhome.westell.com
nameserver 192.168.1.1
nameserver 81.151.10.55

```

Thus in the above example, 
```

MAC = 20:22:ae:30:b0:20
IP address = 192.168.1.81
Netmask = 255.255.255.0
Gateway = 192.168.1.1
DNS servers = 192.168.1.1 and 81.151.10.55

```

Finally, if you type the gateway IP address into the URL bar of firefox (or other web browser), you should be able to access your router. All this information may be on one of the router's configuration or status pages.

---

### Post by js@lloyd on 2009-03-18
> **unutbu said:**
> With your current DHCP connection working, run the following commands:


To find your MAC address, your IP address, and netmask, open a terminal (Applications>Accessories>Terminal) and type
```

ifconfig
```
The output will look something like this:
Your wireless interface is usually called "[COLOR="Teal"]wlan0[/COLOR]", or "ath0" or maybe even "eth0" depending on your hardware.
```

...
[COLOR="Blue"]wlan0[/COLOR]     Link encap:Ethernet  HWaddr **20:22:ae:30:b0:20**  <-- **MAC Address**
          inet addr:[COLOR="Red"]192.168.1.81[/COLOR]  Bcast:192.168.1.255  Mask:[COLOR="Lime"]255.255.255.0[/COLOR]  <-- [COLOR="Red"]IP Address[/COLOR], [COLOR="Lime"]Net Mask[/COLOR]
...

```

Next type
```

route -n
``` 
The output will look something like this:
Look for the numbers in the Gateway column. 
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         **192.168.1.1**     0.0.0.0         UG    100    0        0 wlan0 <-- **Gateway**
```

Next type
```
dig

```
Near the bottom of the output you will see
```

;; Query time: 31 msec
;; SERVER: **192.168.1.1**#53(192.168.1.1)  <-- DNS Server
;; WHEN: Wed Mar 18 08:46:51 2009
;; MSG SIZE  rcvd: 512

```
(In this example the DNS server is also the gateway. Your case may be different.)

Also, /etc/resolve.conf should contain a list of DNS Servers if you are setup with more than one. For example, 
```

search myhome.westell.com
nameserver 192.168.1.1
nameserver 81.151.10.55

```

Thus in the above example, 
```

MAC = 20:22:ae:30:b0:20
IP address = 192.168.1.81
Netmask = 255.255.255.0
Gateway = 192.168.1.1
DNS servers = 192.168.1.1 and 81.151.10.55

```

Finally, if you type the gateway IP address into the URL bar of firefox (or other web browser), you should be able to access your router. All this information may be on one of the router's configuration or status pages.

The machine I'm using is my Desktop that is wired to my wireless modem.  Here's the output:

jsinlloyd@JS-Desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:87:28:db:33  
          inet addr:192.168.15.3  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:fe28:db33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6388273 (6.3 MB)  TX bytes:708700 (708.7 KB)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3711 (3.7 KB)  TX bytes:3711 (3.7 KB)

jsinlloyd@JS-Desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.15.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
0.0.0.0         192.168.15.1    0.0.0.0         UG    0      0        0 eth0
jsinlloyd@JS-Desktop:~$ dig

; <<>> DiG 9.5.0-P2 <<>>
;; global options:  printcmd
;; connection timed out; no servers could be reached
jsinlloyd@JS-Desktop:~$ 



I'm going to make the 1st attempt.

---

### Post by Kareeser on 2009-03-18
It is preferable to set static IPs through the router's web interface, as pre-determining IP addresses on the end user's machine might result in conflicts down the road, especially if the router doesn't realize you're using that IP address (i.e. if you run out of the lease, and the address gets re-assigned, then you log back in)

---

### Post by unutbu on 2009-03-18
js@lloyd, Kareeser is making a good point. If your router assigned you 192.168.15.3
while using DHCP, then you should not use that same address for your static IP.

Your router most likely has a configuration page which allows you to set a range of valid IP addresses to be used by DHCP. You should choose a static IP which is outside this range.

@Kareeser: How is it possible to set static IPs through a router's web interface? Wouldn't you still have to edit /etc/network/interface on the computer?

In my case, I managed to set up a static IP on the local network simply by editing /etc/network/interface and doing nothing on the router side except avoiding the DHCP pool of IP addresses.

---

### Post by DGortze380 on 2009-03-18
Just a nit-picking side note ... 

A static IP is set on the host (users computer), period.

If you're setting it on the router it's a Static DHCP Lease, typically determined by your MAC address.

There is a difference.

---

### Post by js@lloyd on 2009-03-18
> **DGortze380 said:**
> Just a nit-picking side note ... 

A static IP is set on the host (users computer), period.

If you're setting it on the router it's a Static DHCP Lease, typically determined by your MAC address.

There is a difference.


Should I choose another IP address to set Static?

---

### Post by Kareeser on 2009-03-18
> **unutbu said:**
> @Kareeser: How is it possible to set static IPs through a router's web interface? Wouldn't you still have to edit /etc/network/interface on the computer?

The router can be configured to recognize an incoming DHCP request based on the MAC address of your ethernet card. It will then give you whichever IP you set, and not give it to anyone else unless their MAC address is identical (which, for all intents and purposes, is nearly impossible)

The entire process is completely transparent for the end-user computer. It sends a DHCP request to the router, and the router sends back the same IP time after time. No further configuration is needed.

---

### Post by dustman on 2009-03-18
You can change you MAC Address like this:

```
dustman@ubuntu>sudo ifconfig $NETWORK_INTERFACE down hw ether $00:11:22:33:44:55
dustman@ubuntu>sudo ifconfig $NETWORK_INTERFACE up
dustman@ubuntu>sudo /etc/init.d/networking reload



- where -> $NETWORK_INTERFACE is eth0, eth1, eth2, ...
        -> $00:11:22:33:44:55 is the desired MAC address. 
        -> "sudo /etc/init.d/networking reload" might be with   "restart" instead of "reload" :)

```

Take note that if you change the MAC address of your laptop, don't set the same MAC address for the router (or viceversa).

The thing is that you have to do this every time you reboot, unless you create a script to run at startup and executing the commands from above:

1. Create a file that will contain the commands:
```
sudo gedit /etc/init.d/network_script
```

- add the commands there and Save.

2. Make sure the script runs at startup:
```
sudo update-rc.d defaults network_script
```

3. Change the permissions for the file so that it can run at startup:
```
sudo chmod +x /etc/init.d/network_script
```


P.S I wrote these commands from memory, so if something doesn't work, post a reply!

Best regards, 
Radu

---

### Post by unutbu on 2009-03-18
Thank you Kareeser and DGortze380 for the information regarding Static DHCP Leases. :)

---

### Post by stchman on 2009-03-18
> **js@lloyd said:**
> I've been having issues with staying connected via my wired connect to my wireless modem.  It's been suggested to set a Static IP through Network Manager.  My question is, how do I find the following settings, so I can set this up.

MAC Address
Address
Netmask
Gateway
DNS Servers

I hope this solves my problem with dropping my connection.

Thanks,

JS

Some routers will bind an IP to a certain MAC address.  If your router has this function then you are golden.

My router does not.

I went to System--->Administration--->Network.

There I changed from DHCP to Static IP.

I recommend specifying an IP outside your router's DHCP.

---

