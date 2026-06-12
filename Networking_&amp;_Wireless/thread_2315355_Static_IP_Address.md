---
title: "Static IP Address"
date: 2016-02-27
forum: Networking &amp; Wireless
---

### Post by seal308 on 2016-02-27
Hello,

I know nothing about networking but would like to port forward my router for ssh.
On this page there is info on my router: [http://portforward.com/english/routers/port_forwarding/Cisco/DPC3825/SSH.htm](http://portforward.com/english/routers/port_forwarding/Cisco/DPC3825/SSH.htm)
It says I first need to have a static ip address.
I'm just not sure if I have it already or not, how can I tell?
I'm running a computer using lubuntu and it's connected via ethernet.
When I turn off my computer and turn it back on it has the same ip address.
Does this mean the ip address is already static?

Thanks.

---

### Post by Bucky Ball on 2016-02-28
Not necessarily, unless you've set one manually.

When you booted to a desktop and online, click the network icon and 'edit connections'. Go to the IPv4 tab. Is that set to 'Automatic' or 'Manual'? My guess is automatic. 

Set it to manual and set up your IP address. You will need the IP of your router/access point (which is the 'gateway' address), 'netmask' is generally '255.255.255.0' and you will need the DNS IPs that are normally provided by your ISP (internet provider). 

If you need/want your router to still serve IP addresses to other devices via DHCP you are going to need to set up a range for it to serve them in and set your static IP outside that range. 

If you set up the router to serve IPs between, say, 192.168.0.100-110, then you would want to set your static IP outside that range, say 192.168.0.111 and above or 192.168.0.99 or below. Follow? Lot of info to absorb perhaps so if you hit a brickwall, just ask. 

Once you have this set up, reboot and check you are connected with the static IP you set. Good luck.

---

### Post by seal308 on 2016-03-05
My IPv4 tab is automatic.
To get info on my router I just went and right clicked network icon in tray and selected "Connection Information".
Is "Default route" the gateway? It gives a "subnet mask" which I think is the netmask. 
It also gives a primary and secondary DNS. 
I don't know how to  set up the range to serve ip addresses or how to set the static ip address outside the range.
This is a pic from my router admin page, is this where I'm supposed to set a range?
[IMG]http://i927.photobucket.com/albums/ad111/seal308/Screen%20Shot%202016-03-04%20at%2011.30.58%20PM_zpsegbuivuk.png[/IMG]


> **Bucky Ball said:**
> Not necessarily, unless you've set one manually.

When you booted to a desktop and online, click the network icon and 'edit connections'. Go to the IPv4 tab. Is that set to 'Automatic' or 'Manual'? My guess is automatic. 

Set it to manual and set up your IP address. You will need the IP of your router/access point (which is the 'gateway' address), 'netmask' is generally '255.255.255.0' and you will need the DNS IPs that are normally provided by your ISP (internet provider). 

If you need/want your router to still serve IP addresses to other devices via DHCP you are going to need to set up a range for it to serve them in and set your static IP outside that range. 

If you set up the router to serve IPs between, say, 192.168.0.100-110, then you would want to set your static IP outside that range, say 192.168.0.111 and above or 192.168.0.99 or below. Follow? Lot of info to absorb perhaps so if you hit a brickwall, just ask. 

Once you have this set up, reboot and check you are connected with the static IP you set. Good luck.

---

### Post by SeijiSensei on 2016-03-05
That warning may also concern the address that your router gets from your ISP.  ISPs use the same "DHCP" protocol to give your router an address in their networks as your router uses to give addresses to the machines in your home.  There's no guarantee that the router's public address will remain fixed.  So even if you set up portforwarding correctly, when you're outside your home, the address to which you would need to connect may not remain the same.  You might discover that the address the router had yesterday isn't the same as the one it has today.  There are services like [noip.com](http://www.noip.com/) you can use to tie the router's address to a "hostname." They provide software to update the name=>address mapping whenever it changes.

---

### Post by Bucky Ball on 2016-03-05
Hmm. That might be it.

Stick 192.168.0.100 as 'Start Address' and 192.168.0.103 in 'End Address', enable, save and get out of the router. Log out of your machine and back in then click network icon> Connection Information. What's the IP?

The subnet is generally 255.255.255.0 and your router is probably something like 192.168.0.1

Make a note of these two AND the two DNS addresses. They are probably being supplied by your ISP and you may need them to set up the static.

---

### Post by seal308 on 2016-03-07
> **Bucky Ball said:**
> Hmm. That might be it.

Stick 192.168.0.100 as 'Start Address' and 192.168.0.103 in 'End Address', enable, save and get out of the router. Log out of your machine and back in then click network icon> Connection Information. What's the IP?

The subnet is generally 255.255.255.0 and your router is probably something like 192.168.0.1

Make a note of these two AND the two DNS addresses. They are probably being supplied by your ISP and you may need them to set up the static.

I was able to get a static ip address and I port forwarded port 22.
I just wanted to be able to ssh to my home computer from school using a tablet.
I tried it out today and got it to work.
My only issue now is the whole setting up the ip range for dhcp.
I tried calling my ISP and they told me that IP filtering are IP addresses I want to block. (I don't really get it)
They gave me the number of Cisco my router brand. 
Cisco told me that they don't give tech support to end users and that I would have ask my ISP to ask for me.
My ISP said that I would need to upgrade to a business account if I want to do this.
In the worst case if I don't set up a range and my router gives my static ip to a different computer will that really mess my network?
Or can I just change the static ip address to automatic and everything will be fine?
There is a lot of information on Cisco routers a lot of it was over my head, the best info I could find is this:
[IMG]http://i927.photobucket.com/albums/ad111/seal308/Screen%20Shot%202016-03-07%20at%205.06.17%20PM_zpseqa4t5bt.png[/IMG]
It seems like I might have to somehow use terminal to get into my router and enter some commands.
Since I don't really know what I am doing I worry using the terminal my screw up my router/network also I have no idea how to connect to the router via terminal.

---

### Post by Bucky Ball on 2016-03-07
If your router is already serving your IP address to another device, no, it won't mess up your network, only your machine. You won't be able to get online with your static IP. How could you? It is already in use ...

PS: The example you posted tells you exactly how to exclude a range for the IP to NOT serve in. I've never seen it done with commands, though. This is generally very easily done through the router config page on a web browser.

---

