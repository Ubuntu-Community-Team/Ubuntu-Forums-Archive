---
title: "Home Network Problem"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by Ogonzz on 2008-06-04
I've posted individual problems I've had with my setup, but I thought maybe a complete explination would perhaps make it easier for someone to point me in the right direction.

I have an old desktop running ubuntu 8.04.  I have a sprint usb evdo modem connected to it, and have that working fine. The computer has a wireless desktop card, a netgear wpn311. I have two laptops that I would like to share the connection with, and that is where I'm having the problem. I tried firestarter and that didn't work, and I've through various other howto's and such to no avail ;(

I've spent every evening for the last two weeks trying to get this working, and I'm at my wits end...short of using a router or loading windows I'm not sure what else to try.

on a side note, regarding the wireless card, I previously had the netgear wg311v3, but after being unsuccessful with that one, I read that the wpn 311 was compatible with linux out of the box, so I purchased that one. However, I still cant get my network up.

---

### Post by SpaceTeddy on 2008-06-04
ok, slowly... how is your network "wired" (wired in this case, who is connected where - i know that wifi has no wires :) )

can you please draw that for me ?

also, if you want to do what i *think* you want to do, i've written a [[COLOR="Blue"]howto[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=713874")for that. Now you said that you've been through about a million and one, but with this one i am offering to help you out if you get stuck at any point while doing this.

hope it helps :)

---

### Post by Ogonzz on 2008-06-04
I have the usb evdo modem plugged into the desktop, and I want to used the desktop's wireless card to share internet to laptops,

so....usb modem---desktop---clients(laptops).


as for your Howto, yes I did try it ;-) and got compeletly lost once I got the ip tables part...thats when I went looking for something simpler with a gui...but alas, I'll try anything.

---

### Post by SpaceTeddy on 2008-06-04
right-o. so i take it you have configured everything up to there ?

can you please verify that for me by restarting your computer and pasting the output of the following commands:
```
ifconfig
sysctl net.ipv4.ip_forward
sudo iptables -L -vnx
sudo iptables -L -vnx --table nat
```

the first command will show your network connection after bootup, the second will display if ip_forwarding is turned on. The others will print your iptables configuration so i can see if there is anything in there and what still needs to be added :)

cheers

---

### Post by Ogonzz on 2008-06-04
Very well, will do...

Do I still need to configure eth0, even though I'm not using the ethernet port?  (since the usb evdo is ppp0)

---

### Post by Ogonzz on 2008-06-04
Alright, here is the info you requested earlier:


ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0f:1f:5f:3d:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52500 (51.2 KB)  TX bytes:52500 (51.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:72.57.136.26  P-t-P:68.28.185.69  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1120412 (1.0 MB)  TX bytes:121577 (118.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:2a:ad:5d:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fe9f0000-fea00000 

IP Forwarding:

sysctl net.ipv4.ip_forward
net.ipv4.ip_forward = 1

sudo iptables -L -vnx:

Chain INPUT (policy ACCEPT 2193 packets, 1173349 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 2144 packets, 175180 bytes)
    pkts      bytes target     prot opt in     out     source               destination  

       
sudo iptables -L -vnx --table nat:

Chain INPUT (policy ACCEPT 2193 packets, 1173349 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 2144 packets, 175180 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
ogonzz@ogonzz-home:~$ sudo iptables -L -vnx --table nat
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination

---

### Post by Ogonzz on 2008-06-06
Found a "Router" setup document under ubuntu community; unfortunetly it says it requires "Master Mode" on the wireless card, which in my case returns an error....

Maybe I'll give it a shot anyway and cross my fingers...

---

### Post by SpaceTeddy on 2008-06-06
sorry for the laste reply, i was busy last night. 

Your iptables output shows no rule for masquerading the traffic from the internal network. This means - if your machine sends out pakets to the internet, they will not be able to come back, since the internet does not know your internal ip addresses. You definetly will have to enable masquerading. 

The command you are missing for masquerading is:
> sudo iptables -A POSTROUTING --table nat -o ppp0 -j MASQUEARDE
this will only be a temporary rule which will disappear upon a reboot. If you want it permanent (after you have tested it) you can put this command (some one with absolut pasth and run by root) int the /etc/rc.local file so it gets executed upon every boot:
> /sbin/iptables -A POSTROUTING --table nat -o ppp0 -j MASQUEARDE

That said, the rest look pretty good. Your ip_forwarding is enabled, and your ip's seem to be configured correctly. The last think that i am wondering is if your clients are configured correctly. How do they obtain their ip configuration ? via dhcp ? static config ? of you could answer that we can probably wrap this up fairly soon.

again, sorry for the last answer :)

---

### Post by Ogonzz on 2008-06-06
I would use static ips, along the lines of 192.168.0.3 for one and 192.168.0.4 for the other. I would put 255.255.255.0 for the mask, and 192.168.0.1 for the gateway.

I was trying to edit the /etc/network/interfaces file, but when I would try to edit it it would say I don't have permission.  I was doing this by going to the file through the file manager and double clicking it...I imagine there is a "sudo" terminal command that will open it with necessary permissions??

SpaceTeddy, do I need to download the ipmasq add-on for the masquarading to work?

---

### Post by utsuprainfra on 2008-06-06
sudo gedit
or 
sudo pico

---

### Post by Ogonzz on 2008-06-06
If you can show me how to make it work with dhcp, that would be better, as I wouldn't have to worry about setups when friends come over and want to connect to my network.

will try your earlier advice as soon as I get home...

---

### Post by Ogonzz on 2008-06-06
SpaceTeddy, I tried the command you mentioned, and I got the following error:

sudo iptables -A POSTROUTING --table nat -o ppp0 -j MASQUEARDE 
iptables v1.3.8: Couldn't load target `MASQUEARDE':/lib/iptables/libipt_MASQUEARDE.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.

---

### Post by SpaceTeddy on 2008-06-06
typo... it's MASQUERADE... sorry, my bad

command should be
```
sudo iptables -A POSTROUTING --table nat -o ppp0 -j MASQUERADE
```

sorry again :)

---

### Post by Ogonzz on 2008-06-06
I've got a major issue now...

When I boot up my computer, it hangs on network manager or ip masquerading....

I'm stuck :(

---

### Post by Ogonzz on 2008-06-07
Well I decided it best to just reinstall Ubuntu, as I didn't really have any important info on the comp.

Anyway, I'm back to where I was, I did the ip masquerade, it now shows info passing when I do the ip-tables command.

However, my laptops can't detect the network I've set up ;/

---

### Post by Ogonzz on 2008-06-07
Regarding my current problem, I noticed that if I do "iwconfig", none of the info that is in the etc/network/ interfaces file shows up; by that I mean it doesn't show the essid, or channel, etc.

Maybe that helps...

---

