---
title: "Static IP"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by Pyraine on 2007-11-11
I am an absolute newbie to networking on Linux, the problem I am having is setting a static IP so I can forward my ports, so far I have 3 boxes connected to my router (that's if the separate partitions of Windows and Linux are counted separately, I don't know) so I would like a more permanent solution that simply reconfiguring the virtual servers each time I am assigned a new IP.

I originally tried using System > Administration > Network as on first glance, I assumed it was the equivalent of the Windows TCP/IP settings, but after configuring that how I usually would, my connection dropped. 

Then I went to google for help, but that kept mentioning "eth0", but when I open /etc/network/interfaces my setting do not mention eth0, it is currently:

```
auto lo
iface lo inet loopback
```

so now I am just absolutely lost as to what I should do next, so any help would be appreciated. Cheers.

---

### Post by trak87 on 2007-11-11
You don't need to do anything to Ubuntu. This is handled entirely at the router. Just keep the Ubuntu defaults, like DHCP. 

Just use Firefox and surf right in to your router. The address is numeric and should be posted in your router manual. It will look something like 192.168.1.100. The last two sets of numbers will be different but the first two will be 192.168. If you don't have your manual handy, you might find the address online at the router manufacturer's website.

Once you access your router with Firefox (it's just like surfing into any website), look for the option to specify a fixed ip address. On my router it's in the "LAN IP Setup" and it's called "Address Reservation". You associate your computer's MAC address with a particular IP address for your computer (like 192.168.1.200). Then, every time you boot up, the router recognizes your computer via it's MAC address and always gives it the 192.168.1.200 address.

---

### Post by Pyraine on 2007-11-11
Well the only page within my router I could find about allocating IP's with DHCP was this page in this [screenshot]("http://img102.imageshack.us/img102/9075/screenshotwx9.png")

But I'm just used to setting the static IP on the actual box itself so I have no idea how to work this page, is there anyway you could help me?

---

### Post by trak87 on 2007-11-11
In the case that you don't have the ability to set your IP at the router, you can do it at Ubuntu:

I haven't done this but I think this is how you do it:

System, Administration, Network Settings

Uncheck "Enable roaming mode"
Configuration: "Static IP address"
IP address: (choose one) 192.168.5.125 (or whatever you want. Just keep the 192.168)
Subnet mask: 255.255.255.0
Gateway address: the address of your router (192.168.x.x)

That should do it. Though you still might be able to at the router. Did you look though all the options?

---

### Post by Pyraine on 2007-11-11
as i said in my initial post that was the way I tried to do it first but it just downed my connection.

---

### Post by trak87 on 2007-11-11
Don't forget to restart your computer when you make a change. (Or at least do "sudo /etc/init.d/networking restart"). Might even help to restart the router.

I'm no expert at networking. I would read everything possible on this router and look to Google if you don't find the info here. Chances are the question has been asked by somebody somewhere.

How many computers do you have attached to this router? You might try disabling DHCP at the router and then set your static IP in Ubuntu as suggested above. If that works you'd have to do the same to the other attached computers and network devices. This seems like the most inflexible way though. 

Best bet is to study your router's settings. There may be something there.

---

