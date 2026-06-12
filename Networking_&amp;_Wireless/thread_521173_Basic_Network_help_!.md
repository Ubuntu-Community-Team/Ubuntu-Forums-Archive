---
title: "Basic Network help !"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by jrgibb on 2007-08-09
Hi,

I've previously been able to seen the two other windows machine on my network but now I can't seem them when I go Places, Network and click on Windows Network icon? Nor cam I seen my Ubuntu machine from either of the WIndows machines which I could do before. 

The only thing I've done is turn everything off (was on vacation),restarted all machines and installed  32 system updates for the Ubuntu machine.

Any and all help welcome, ta ! 

J

---

### Post by callan79 on 2007-08-09
> **jrgibb said:**
> I've previously been able to seen the two other windows machine on my network but now I can't seem them when I go Places, Network and click on Windows Network icon? Nor cam I seen my Ubuntu machine from either of the WIndows machines which I could do before.

First thing I'd do is make sure each computer has its Network IP Address statically set, instead of auto, that way you know exactly what's going on. Set them to 192.168.1.1, 192.168.1.2, or similar. IF you need help with that, please ask :)

Then make sure none of the machines are running any firewalls - even if they are disabled they can still be a problem, remove them totally!

Then make sure your Windows machines have shared folders

Then in Ubuntu, go to Places >> Computer, and in the address bar type in   smb://192.168.1.1  or whatever the IP Address of one of your Windows machines. This way it should find it.

I've always found the automatic network icon search things in Windows and Ubuntu to be pretty unreliable!

Cheers
Callan

---

### Post by jrgibb on 2007-08-09
Thanks m8 !! :biggrin:

---

### Post by oldmanriver28 on 2007-08-15
> **callan79 said:**
> First thing I'd do is make sure each computer has its Network IP Address statically set, instead of auto, that way you know exactly what's going on. Set them to 192.168.1.1, 192.168.1.2, or similar. IF you need help with that, please ask :)

Then make sure none of the machines are running any firewalls - even if they are disabled they can still be a problem, remove them totally!

Then make sure your Windows machines have shared folders

Then in Ubuntu, go to Places >> Computer, and in the address bar type in   smb://192.168.1.1  or whatever the IP Address of one of your Windows machines. This way it should find it.

I've always found the automatic network icon search things in Windows and Ubuntu to be pretty unreliable!

Cheers
Callan

I am trying to do the same thing, except I am a newbie to Ubuntu and am not as technically inclined.  Can you explain how to make the Network IP statically set.  

Currently my desktop computer is directly connect to the router with an ethernet cable and my windows laptop is wirelessly connected.  I would like to simply transfer files to and from each computer.

Also when I got to Places>>Computer, I do not see an address bar to type anything in.  Am I missing something?

I was able to go to places>network>shared folder

However when I try to access the shared folder, it asks for a password even though I have not set one up on the laptop.

---

### Post by callan79 on 2007-08-16
> **oldmanriver28 said:**
> Can you explain how to make the Network IP statically set.  
Also when I got to Places>>Computer, I do not see an address bar to type anything in.  Am I missing something?
However when I try to access the shared folder, it asks for a password even though I have not set one up on the laptop.


Hi there,

Are both your machines running Ubuntu?

Also, I assume your router is the device that connects you to the Internet. This means you need to know the IP Address of your router, and the DNS settings for your ISP. If you start a terminal (Applications >> Accessories >> Terminal) then you can use these commands to find out more :

  -  ifconfig  [enter] ........... this will show your current IP Address
  -  route  [enter].............this will show your router's IP address, listed as the 'default'

I'll paste my details at the bottom so you can see an example.

Once you know those settings, plus your ISP's DNS settings, go to System >> Administration >> Network. Choose WIRED NETWORK and click PROPERTIES. Change 'DHCP' to "Static IP Address' and fill in the blanks.

  -  IP Address should be same as your router, except last number is different. So if router is 192.168.1.1, then your computer can be 192.168.1.2 or 192.168.1.3, it has to be unique on the network.
  -  Subnet mask same as what IFCONFIG shows you
  -  Default Gateway same as what ROUTE shows as default
  -  On the DNS tab, enter your ISPs DNS settings

That's all done - repeat for other machines on the network.


Regarding not having an address bar, you might see some buttons at the top that show you the folders you've been looking at. To the left of that is an icon with a paper and pencil. Click that and the buttons change into an address bar where you can type.

Hear from you soon with good news!

My ifconfig and route details to follow, as an example

Cheers
Callan




```

callan@brutis:~$ ifconfig -v eth0
eth0      Link encap:Ethernet  HWaddr 00:00:21:2B:6E:9D  
          inet addr:192.168.7.22  Bcast:192.168.7.255  Mask:255.255.255.0

```


```

callan@brutis:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.7.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.7.254   0.0.0.0         UG    0      0        0 eth0

```

---

### Post by oldmanriver28 on 2007-08-20
> **callan79 said:**
> Hi there,

Are both your machines running Ubuntu?

Also, I assume your router is the device that connects you to the Internet. This means you need to know the IP Address of your router, and the DNS settings for your ISP. If you start a terminal (Applications >> Accessories >> Terminal) then you can use these commands to find out more :

  -  ifconfig  [enter] ........... this will show your current IP Address
  -  route  [enter].............this will show your router's IP address, listed as the 'default'

I'll paste my details at the bottom so you can see an example.

Once you know those settings, plus your ISP's DNS settings, go to System >> Administration >> Network. Choose WIRED NETWORK and click PROPERTIES. Change 'DHCP' to "Static IP Address' and fill in the blanks.

  -  IP Address should be same as your router, except last number is different. So if router is 192.168.1.1, then your computer can be 192.168.1.2 or 192.168.1.3, it has to be unique on the network.
  -  Subnet mask same as what IFCONFIG shows you
  -  Default Gateway same as what ROUTE shows as default
  -  On the DNS tab, enter your ISPs DNS settings

That's all done - repeat for other machines on the network.


Regarding not having an address bar, you might see some buttons at the top that show you the folders you've been looking at. To the left of that is an icon with a paper and pencil. Click that and the buttons change into an address bar where you can type.

Hear from you soon with good news!

My ifconfig and route details to follow, as an example

Cheers
Callan




```

callan@brutis:~$ ifconfig -v eth0
eth0      Link encap:Ethernet  HWaddr 00:00:21:2B:6E:9D  
          inet addr:192.168.7.22  Bcast:192.168.7.255  Mask:255.255.255.0

```


```

callan@brutis:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.7.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.7.254   0.0.0.0         UG    0      0        0 eth0

```

Callan thanks a bunch, sorry for the delay in getting back to you I have been on vacation.  Everything seems to be working great.

Best regards,

Jason

---

