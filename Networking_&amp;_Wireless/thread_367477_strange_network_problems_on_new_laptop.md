---
title: "strange network problems on new laptop"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by killerdrone on 2007-02-22
Hi!
I have some serious problems with my brand new lenovo T60. Got it 2 weeks ago, installed Ubuntu 6.10 and everything worked great, except that network transfers were very slow (<700k/s using sftp, network is 100mbit and both computers should be able to do many times that). A few days ago i decided to retire my old workstation as a server/router, and throw the old server out. When i started the new server everything worked great on all clients - except my new laptop! I use dynamically assigned ip:s on the local network, range 192.168.1.10 - 192.168.1.254, but when running dhclient on the laptop i got assigned 192.168.1.255, and pinging the server returned "no route to host" (i think it was). I got the advice to assign a static ip in dhcpd.conf like this: 

```
host aurora {
   hardware ethernet 00:15:58:7D:5F:6C;
   fixed-address 192.168.1.2;
}
```

but it did no good. Now i tried with an old 16bit PCMCIA NIC i had lying around, and i got assigned the ip 192.168.1.253. All other clients get ip:s in the range 192.168.1.10-30, why this odd one?! Two days ago things got even worse, now i get no contact at all with the dhcp server, regardless of which NIC i use! Won't even get assigned a (non-working) ip. The cables are ok, they work with other clients, and i've tried connecting from several different places. 

Just tried another approach, and i got really worried: i started with ubuntu:s live-cd, and the problem is the same! Network worked out of the box two weeks ago, and now it's completely dead! Any ideas at all, anyone?

edit: the last part about no connection at all with server is solved, unknown temporary problem with the server, went away with a reboot. I still get assigned 192.168.1.255, and can't ping the server. When the network cable is attached, it takes like 2 minutes to open an xterm window!!! I've been told that this is because the network is out of order...It's sure annoying as HELL!!

---

### Post by Strider on 2007-02-22
192.168.1.255 seems like a broadcast address if you're using 192.168.1.0/24 (255.255.255.0).  If this is the case then the laptop is not getting back the correct response from the DHCP server.

Not sure how familiar you are with "tcpdump" (packet capturing command line tool) but take a look at tcpdump and run it ("tcpdump -i eth0", if "eth0" is your NIC).  Monitor what happens during the DHCP request/exchange.

Also, on your DHCP server, run a packet capture (I'm assuming the DHCP server is running Linux) using tcpdump.  Maybe you can pin-point the issue there.

Silly question but do you have more than one DHCP server on the network?  Can you verify this?

Another suggestion would be to cross connect the server with the laptop directly (using a cross-over cable or if the laptop or server supports auto negotiation on cable type use a regular patch cable).  By doing this you bypass the network.  Once you connect the cable run "ifdown eth0" and "ifup eth0".  If that doesn't work, run "/etc/init.d/networking restart".

Another suggestion: assign a static IP to your laptop - "ifconfig eth0 192.168.1.5 netmask 255.255.255.0".  Make sure the interface is up and then try to ping other hosts on your network.  You will not be able to ping with 192.168.1.255 as this is the broadcast address.

Hope some of that helps or at least point you in the right direction.  If you can, post the printout of "ifconfig".

-Mike

---

### Post by killerdrone on 2007-02-22
About tcpdump, i know how it works, but i'm no expert at interpreting the results. And as i can be a bit of a GUI victim sometimes i use wireshark instead of tcpdump. When running dhclient two packets are collected: first from 0.0.0.0 (laptops MAC) to 255.255.255.255, DHCP request. Hey, there's one line here saying "requested ip address: 192.168.1.255". It looks like the laptop is asking for that address? But it's not in the range specified in dhcpd.conf on the server... Anyways, my dhclient.conf says nothing about requesting a specific IP. Where else can such a request be specified? 

Now we're getting somewhere: after manually setting IP to 192.168.1.99 i was able to ping the server! However, pinging one of my isp:s nameservers returned "network is unreachable". Could be something strange going on with the server again..i will look into this tomorrow, too tired now. 

Thanks a bunch for helping me, it's no fun to have a new laptop and not being able to use it!!

---

### Post by Strider on 2007-02-23
-- double post -- ignore.

---

### Post by Strider on 2007-02-23
You can't get to the DNS servers or anywhere on the NET because you don't have a default route to the Internet.  To use static configuration you can use the GUI to set the IP address, DNS, Default Gateway to manual and this will make the changes to the system.  If not, you can do this manually but it requires changing two files from the console.  Give the GUI a shot to change the IP settings to manual and input the necessary information.  That should at least get you going with Internet access until you can resolve the DHCP issue.

-Mike

---

