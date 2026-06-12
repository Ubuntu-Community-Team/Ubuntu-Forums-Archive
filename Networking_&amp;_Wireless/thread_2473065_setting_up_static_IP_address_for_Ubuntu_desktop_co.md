---
title: "setting up static IP address for Ubuntu desktop computers"
date: 2022-03-22
forum: Networking &amp; Wireless
---

### Post by Old Jimma on 2022-03-22
Hello Ubuntu Community:

I have several Ubuntu computers that communicate with each other.

I want to make static IP addresses for each of them.

Here is my plan for computers with an Ubuntu desktop:

For computers with the Ubuntu desktop:

[LIST=1]
[*]issue the ifconfig command to get the inet address (IP) and mask, and  
[*]issue the ip route command to get the default route (gateway).
[/LIST]


 For my computer the output for ifconfig is:

> 
enp5s0f1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        **inet 192.168.1.180  netmask 255.255.255.0**  broadcast 192.168.1.255
        inet6 2600:1700:9f70:2590:80c9:aec9:2151:1ee0  prefixlen 64  scopeid 0x0


**that shows the inet (IP) address is 192.168.1.180  and the netmask is 255.255.255.0 **


and the output for ip route is

> 
default via **192.168.1.254** dev enp5s0f1 proto dhcp metric 100 
169.254.0.0/16 dev enp5s0f1 scope link metric 1000 
192.168.1.0/24 dev enp5s0f1 proto kernel scope link src 192.168.1.180 metric 100


**that shows that the default route (gateway) is  192.168.1.254**

Finally, for each ubuntu desktop computer I&#8217;ll 

1. click on Settings > Network (for computers connected to my network with a cable) or Wi Fi (for computers connected to my network via Wi Fi), 

2. click on the &#8220;gear&#8221; icon next to the &#8220;wired&#8221; label (for computers connected to my network with a cable) or the &#8220;gear&#8221; icon next to the &#8220;Visible Network&#8221; (for computers connected to my network via Wi Fi). This will open a gui dialog box.

3. When the gui dialog box opens, I&#8217;ll click on IPV4 and then the &#8220;manual&#8221; button and **enter the computer&#8217;s IP address in the &#8220;Address&#8221; box, the netmask number in the &#8220;Netmask&#8221; box, and the default route number in the &#8220;Gatway&#8221; box.**

4. Then, I&#8217;lll click on &#8220;Apply&#8221; in the upper right corner of the gui dialog box.

And then, I think the job is done, right?

Thanks,
Old Jimma from the Old Country

---

### Post by HermanAB on 2022-03-22
Howdy,

The easiest solution is to configure your home router DHCP server to hand out fixed IP addresses based on the MAC addresses of the PCs.  

If you log into the router, you can usually see the MAC addresses in a log, then you just copy them from there to another spot.  I cannot describe it in detail, since every router is different.

---

### Post by slickymaster on 2022-03-22
*Thread moved to **Networking & Wireless**.*

---

### Post by Old Jimma on 2022-03-22
Hello HermanAB:

Thank you for your reply.

I don't know how to do what you've suggested, and you have not provided specific details on how to do what you've proposed.

The purpose of my post was to learn if the method I described works.

Do you think the method works?

I'm grateful for your reply.

THanks,
Old

---

### Post by Old Jimma on 2022-03-22
HI Slickymaster:

Thank you for your email.

I'm still waiting on a reply that either confirms what I proposed will be successful at assigning static IPs to my ubuntu desktop computers, or another proposal that  has suffcient detail to achieve that (not just general remarks that something else will work).

Old

---

### Post by Morbius1 on 2022-03-22
This falls under the "not just general remarks that something else will work" category so feal free to ignore.

Your process will work as long as you promise to never shut down or reboot your computers.

If your computer exits the network and another enters it the new computer may very will be assigned that very same ip address by DHCP on the router. In order to avoid that you would need to find the "scope" or range of the the DHCP server on the router. Some routers have a range of 50 for example something like 192.168.0.1 to 192.168.0.50. You would have to assign your static ip address to be outside that range like 192.168.0.52 for example so that your desired ip address isn't assigned to somebody else.

That means accessing the admin pages of the router to find out what the DHCP range is. But since you are there anyway you might want to do what HermanAB suggested which in the long run is the easiest most efficient way. What he descibed has many names like "DHCP IP Reservation", "DHCP Reservation", I even had a router call it "Static DHCP".

Anywho, Here's an example of how that works: [https://www.linksys.com/us/support-article?articleNum=137180](https://www.linksys.com/us/support-article?articleNum=137180)

---

### Post by TheFu on 2022-03-22
It is very important that any static IPs never be in the same range as the DHCP range handed out by the DHCP server (usually the router).

So, if the DHCP range is .100 - .254, then any static IPs should be in the .1 - .99 range, but the router will probably take either the .1 IP or the .254 IP, so it is best to avoid those for static IPs.  What happens if there is a collision between the static and dynamic IPs?  Neither computer will work on the network.

Most routers have a menu to setup 'dhcp reservations'.  There are good reasons to use that method and some bad things can happen. Suppose the DHCP server isn't working? Now all your computers cannot get those static IPs.  This might happen once every few years, but it will really suck.  Also, router DHCP servers have known bugs where outsiders can use that protocol to gain access.  Google it a bit, to see the issue.  It is fairly specific and only a few popular routers were hit. By now, they should all be patched, assuming patching the router is something done every month.

---

### Post by him610 on 2022-03-22
You can assign static IP addresses on each machine followed by reserving each individual machine IP address in your router setup. 
Check your router manual as to how. If your gateway/router is provided by your internet service provider then they will probably have web-pages describing how to change settings in the provided device.

Provides a listing of local IP addresses and MAC addresses
```
 arp -e 
```

---

### Post by Old Jimma on 2022-03-23
Thanks, TheFu,

I appreciate and trust yuour guidance.

... especially previous guidance about using a pi to back up my ubuntu computers. It has paid off several times, already.

Best regards and thanks,
Oldest of Days Old Jimma

---

### Post by Old Jimma on 2022-03-23
Thank you for your reply him610:

I vaguely recall that assigning permaent IP addresses using my router will require mac addresses. Your suggestion helps me to find them!

Have a great day!

Old JImma

---

### Post by SeijiSensei on 2022-03-23
In my Archer C7, you can display a table of the MAC addresses and assigned IPs like this:
```

1	OBi200	9C-AD-EF-67-CE-1B	192.168.100.59
2	LRTV	C8-3A-6B-F7-17-2D	192.168.100.57	
[etc.]

```
Pretty much any router has this feature.

---

