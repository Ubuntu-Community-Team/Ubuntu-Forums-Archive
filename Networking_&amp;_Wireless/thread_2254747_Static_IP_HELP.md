---
title: "Static IP HELP"
date: 2014-11-29
forum: Networking &amp; Wireless
---

### Post by charlesdugger on 2014-11-29
Hello everyone and thank you in advance. I am pulling my hair out. I am setting up a backup server for work, I would like to keep the operating system the same. I have a dell poweredge 1950 and I am setting it up with server 12.04. I need a static IP, I have tried everything and nothing works. I have started over and reinstalled Ubuntu, I have tried putting desktop so far nothing works. The other server I set up last year I don't remember having this problem. Everything works fine until I set the ip static. I have tried removing the DCHP client. I have tried installing network manager. I have tried to enter the Mac address in router to set ip.

Im at a total loss this should not be a big deal but on this server it is

I cant print the if config when it is static but it looks correct. I have used the dns from google, the dns from my windows laptop the /etc/network/interfaces file that works on my server at work. The box hes eth0 and eth1 both work on dhcp neither static. I can not ssh to it or ping it when set to static. I lost nothing works
contents of /etc/network/interfaces
```

cardinal@cardinalserver2:~$
  GNU nano 2.2.6         File: /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#       address 192.168.1.199
#       netmask 255.255.255.0
#       gateway 192.168.1.1
#       dns-nameserver 8.8.8.8

```

yes I have it back on dhcp to talk to it at this point but I see no errors when it is not commented out.  


i have tried this after sitting static
```

sudo rm /run/resolvconf/interface/eth0.dhclient
 sudo rm /run/resolvconf/interface/original.resolvconf\
 
 
```
 I really dont want a desktop on this but will install it if needed but I have tried that already also.
 
 I keep reading how this is a known bug but no answer.
 
 and before the last install i tried this 
 sudo apt-get remove isc-dhcp-client
 
 if config using dhcp
 ```

 
sudo] password for cardinal:
eth0      Link encap:Ethernet  HWaddr 00:15:17:ac:7f:e4
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:17ff:feac:7fe4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:927 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:80796 (80.7 KB)  TX bytes:20400 (20.4 KB)
          Interrupt:18 Memory:98820000-98840000
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
cardinal@cardinalserver2:~$

 
```

---

### Post by papibe on 2014-11-29
Hi charlesdugger.

The easiest way to set an static for a machine would be to let the machine 'as is' and set a DHCP reservation on the DHCP server.

In a regular home network, the DHCP server is the router. I'd start by getting into your router admin pages to see if that is possible.

If your router doesn't have that functionality, you have to set the static IP on the server itself as you tried to do. First, you need to use the same network and general IP range of your current network. Since your DHCP server is serving 192.168.0, I'd select an address in that range instead of 192.168.1

Then, you need to select an IP address that is outside the router's DHCP range. The used range should be available on the router's admin pages, or manuals.

After you set the address, you have to either restart the network:
```
sudo service networking restart
```
or reboot the machine.

In some cases, the server won't be available by 'name' to the rest of the network, but only using its IP address.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by charlesdugger on 2014-11-29
I have already tried that it still goes to 192.168.0.6 . I have already put 14.04 on it once and I could set it static, I really really would like to keep the same os on both servers. This will be going to work and leaving the house once it's finished. I'm just stumped. I know it is something I need to do but what??

---

### Post by charlesdugger on 2014-11-29
I would be fine with ripping everything auto out of the install it is a server and once I get it on LAN it will not be moved moved. How can I use the old resolve.conf?

---

### Post by untrustytahr on 2014-11-29
```
...aces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#       address 192.168.1.199

```
```
sudo] password for cardinal:
eth0      Link encap:Ethernet  HWaddr 00:15:17:ac:7f:e4
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
```

Different subnets (192.168.1.x & 192.168.0.x)

Oops... looks like papibe already mentioned it... sorry papibe.

---

### Post by charlesdugger on 2014-11-29
I noticed that why is it going to different subnet?

---

### Post by charlesdugger on 2014-11-29
My router is set to assign dhcp between 192.168.1.100 - 192.168.1.150, t I went to my router and reserved the dhcp for the MAC address to 192.168.1.150 then rebooted bat the address was 192.168.0.6 :-(

---

### Post by untrustytahr on 2014-11-29
> **charlesdugger said:**
> I noticed that why is it going to different subnet?

Your DHCP server is serving 192.168.0.0/24 but you are trying to assign 192.168.1.0/24 manually.

---

### Post by untrustytahr on 2014-11-29
> **charlesdugger said:**
> My router is set to assign dhcp between 192.168.1.100 - 192.168.1.150, t I went to my router and reserved the dhcp for the MAC address to 192.168.1.150 then rebooted bat the address was 192.168.0.6 :-(

Rogue DHCP server :-k

---

### Post by charlesdugger on 2014-11-29
Hmm my cable modem has a built in wifi which I disabled to use my router? This server has no wireless card, I don't think that would do it.  The rouge server is the linux box??? ](*,)](*,)](*,)

---

### Post by papibe on 2014-11-29
> **untrustytahr said:**
> Rogue DHCP server :-k
Interesting idea...

To detect your DHCP servers, install nmap:
```
sudo apt-get install nmap
```
Then run this:
```
sudo nmap --script broadcast-dhcp-discover 192.168.1.0/24
```
Let it run for a minute or so. Then stop it with Ctrl+C.

Then, do the same for the other subnet:
```
sudo nmap --script broadcast-dhcp-discover 192.168.0.0/24
```
Post back  the results of both commands.

Regards.

---

### Post by charlesdugger on 2014-11-29
Rouge dhcp I brought the server in the other day and grabbed a cat 5 cable not checking what it was hooked to. One of my kids had been putting linux on a old laptop I brought home from work and it was plugged into the cable modem not the router. I spent much time wasted because of this it could never work. 

Thank you all!!!!!!!!

---

### Post by charlesdugger on 2014-11-29
Recharging my brains and laptop will see if all is well later this has to be it.

---

### Post by charlesdugger on 2014-11-29
Amazing how well it works when you are on the correct router. 

Thanks everyone.

---

