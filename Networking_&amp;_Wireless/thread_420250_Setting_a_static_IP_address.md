---
title: "Setting a static IP address"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Ozor Mox on 2007-04-23
How do I set a static IP address for my wireless network? I've done some searches on this and the result seems to be that I need to go to System > Administration > Network and disable "roaming mode" to set an IP address. However, I can't select WPA from the password type, only WEP (hex or ASCII) are available as choices.

The other conclusion I can see is that I have to edit my etc/network/interfaces file in some way. Originally I commented this all out (except loopback) so that Network Manager could handle all my connections; must I uncomment this for a static IP or is there an easier way to do it using an interface?

---

### Post by A*p on 2007-04-23
A quick "temp" way to set a static ip is to use ifconfig, for example.. 

**sudo ifconfig eth0 192.168.0.10 netmask 255.255.255.0 up**

For a more permanent solution you will need to edit your etc/network/interfaces file  

for example...
[B]
# Static address for eth0
auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1[/B]

Just change the details to suite your card and network settings.

---

### Post by Ozor Mox on 2007-04-24
Thanks for that! A couple of questions:

Will this affect Network Manager's handling of wireless network connections? Will I need to comment this section back out to allow Network Manager to manage the connections again?

---

### Post by Ozor Mox on 2007-05-01
I tried the temporary solution using eth1 instead of eth0 because eth1 is my wireless network interface. I could see from ifconfig that the IP address was now correct, but all internet services went down. Do I need to disable Network Manager to do this? Should I try the permanent solution instead?

---

### Post by seamus7 on 2007-05-03
I have two profiles saved in Networking ... one is called Roaming and one is called Static. Network Manager will work with both. In order to switch between them I usually need to turn off the wifi radio signal and disconnect/disable from wireless and networking under the network manager applet, change to the other profile in Networking and click the check mark to apply the new profile, then restart the wifi signal and re-enable networking and wireless under the applet. I also restart networking via the terminal using:

```
sudo /etc/init.d/networking restart
```

Note that the Network Manager applet will show the signal bars under the roaming profile but will show two connected computers under the static profile.

---

### Post by mas99 on 2007-05-03
I would have a look at your router and see if you can tie a mac address to a specific IP via the routers dhcp server - I can do that on my netgear.

I know it isnt what you are asking but feisty seems so problematic with wireless that it might at least give you a working solution in the short term.

---

### Post by 5h4rk on 2007-05-04
> **Ozor Mox said:**
> 
Will this affect Network Manager's handling of wireless network connections? Will I need to comment this section back out to allow Network Manager to manage the connections again?

I'm looking forward to the answer.

:) 

thanks.

---

### Post by marcantonio on 2007-07-19
seamus7, are you using wireless or wired at home?

---

### Post by seamus7 on 2007-07-21
wireless at home.. i have a dsl modem/router connected to a belkin wireless router configured as an access point.

---

### Post by diablo75 on 2007-07-21
> **mas99 said:**
> I would have a look at your router and see if you can tie a mac address to a specific IP via the routers dhcp server - I can do that on my netgear.

I know it isnt what you are asking but feisty seems so problematic with wireless that it might at least give you a working solution in the short term.

This worked PERFECTLY for me.  That was a very easy solution.  Thank you!!:guitar:

---

