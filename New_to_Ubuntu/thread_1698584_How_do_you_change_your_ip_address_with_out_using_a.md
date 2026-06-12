---
title: "How do you change your ip address with out using a proxy?"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by robro on 2011-03-02
Hi everyone,
I was wondering if there was a way to change your IP address in kubuntu,
right now I can disconnect and reconnect to change it, but I hate to have to do that...
specs:

verizon usb760 modem
dynamic IP
uses ppp0

I have googled this and found the command: "ipconfig ppp0 (new IP) up" although that does successfully change it, I cant access the web anymore...

any help is appreciated :)

---

### Post by vivek.pandey on 2011-03-02
well there is a way though to hide your ip try torK... well though i am extra nosy and curious but why do you need to change your ip so often?

---

### Post by robro on 2011-03-02
I just got thru installing tor/tork, and i cant get tork running but i can run tor although it just runs a browser with a proxy and dosn't "change" my ip address :|

is there a step to step guide for this?

and to your question about why i want to change it, I just like to get a fresh ip every now and then lol

---

### Post by ironic.demise on 2011-03-02
```
gedit /etc/network/interfaces
```

add the lines
```

auto eth0
iface inet loopback
iface eth0 inet static
address xxx.xxx.xxx.xxx(enter your ip here)
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx(enter gateway ip here)
```
```
source:http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html
```

Just change the ip everynow and then in the file?

---

### Post by robro on 2011-03-02
can you please explain what i have to exacly write

---

### Post by ironic.demise on 2011-03-02
> **robro said:**
> can you please explain what i have to exacly write
Save this text to a file called "ipchanger.sh"
open terminal and go to the directory that the file is and type ```
chmod +x ipchanger.sh
```
Text to go into the file:
```

echo "Enter number requested for new ip"
echo "example: 13 will give you the ip address 192.168.0.13"
read NEWIP
echo "auto lo" >> /etc/network/interfaces
echo "iface lo inet loopback" >> /etc/network/interfaces
echo "" >> /etc/network/interfaces
echo "iface eth0 inet static" >> /etc/network/interfaces
echo "address 192.168.0.$NEWIP" >> /etc/network/interfaces
echo "netmask 255.255.255.0" >> /etc/network/interfaces
echo "network 192.168.0.0" >> /etc/network/interfaces
echo "broadcast 192.168.0.255" >> /etc/network/interfaces
echo "gateway 192.168.0.1" >> /etc/network/interfaces

```

Then at terminal type
```
sudo bash ./ipchanger.sh
```

This changes only LOCAL ip, that which is within your network, not external.
It's not really reasonably possible to force your external ip to change...
this may not be specific to your network, though it will be close.

---

### Post by NCLI on 2011-03-02
If you want to change your external IP, the easiest way to do that without using a proxy is to install xforwardedfor-spoofer, a Firefox plugin.

It won't really hide your identity through, but will let you watch many US-only videos.

---

### Post by JKyleOKC on 2011-03-02
> **robro said:**
> Hi everyone,
I was wondering if there was a way to change your IP address in kubuntu,
right now I can disconnect and reconnect to change it, but I hate to have to do that...The address is assigned to you by your ISP, and only the ISP can change it so that it will still work. You've discovered the only practical way to force the change, already!

As you've discovered, changing it at your end of the wire by using ifconfig or editing the interfaces file may appear to work, but your ISP isn't going to know your new address and will continue sending packets to (and listening from) your old address. Thus you've effectively disconnected from the network (although you might start getting packets meant for someone else, if you happened to pick a currently active set of numbers!).

Since you get a changed address when connecting anew, there's really not much of a privacy issue there. Think of the IP address as being like a street address or snail mail box; the party at the other end of the wire has to know the address to send anything to you. Your ISP handles the details of relating your mail address to the current IP address, but any attempt by you to change things fouls up that process.

---

### Post by robro on 2011-03-03
> **JKyleOKC said:**
> -snip-

Thank you for explaining that :)
well so much for that idea... thanks for your help everyone :D

---

