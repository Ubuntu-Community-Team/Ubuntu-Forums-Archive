---
title: "Can connect to internet, but not other devices on network"
date: 2023-11-28
forum: Networking &amp; Wireless
---

### Post by symbiant on 2023-11-28
So I recently upgraded to Ubuntu 23.10 and can no longer communicate between my ubuntu machine and other devices on the network.

I can access the internet from my ubuntu machine (via wifi), but for instance 192.168.0.1 does not bring me to my router config page, as it does on other devices, and I can't access my ubuntu machine via SSH or any of the docker instances it's running via local IP address from another machine (though I can access it via local ip address from the same machine).

Any idea what i need to be looking at?

EDIT: I've tried rebooting both the machine and the router multiple times

---

### Post by TheFu on 2023-11-28
I'm guessing you screwed up the routing on your Linux system in trying to get docker working.  

Wifi should be avoided. Use wired ethernet.  Work with 1 or the other, don't mix until you have stronger network skills.  Use the different options for the 'ip' command to gather information.

IPs, routing, metric values and exactly which interface is used for each connection.

---

### Post by symbiant on 2023-11-28
> **TheFu said:**
> I'm guessing you screwed up the routing on your Linux system in trying to get docker working.  

Wifi should be avoided. Use wired ethernet.  Work with 1 or the other, don't mix until you have stronger network skills.  Use the different options for the 'ip' command to gather information.

IPs, routing, metric values and exactly which interface is used for each connection.

I actually had everything working fine for a few months, always connected via wired connection. I had to move the table the computer was on like 4 feet, and think I damaged the Ethernet port somehow in the process, hence the wifi.

Edit: Ethernet doesn't show up at all, and lights don't blink. Tried it with multiple cables and router ports confirmed working with other devices. If it turned out there was some driver issue that could cause this behavior and I got that fixed and could move back to Ethernet, all the better.

---

### Post by symbiant on 2023-11-28
One weird thing is a tried assigning the reserves internal ip from the prior Ethernet ports Mac address to the wifi chips Mac address but it didn't fix things. The u assigning it seems to have no affect, it still holds to that same IP.

---

### Post by symbiant on 2023-11-28
> **TheFu said:**
> I'm guessing you screwed up the routing on your Linux system in trying to get docker working.  

Wifi should be avoided. Use wired ethernet.  Work with 1 or the other, don't mix until you have stronger network skills.  Use the different options for the 'ip' command to gather information.

IPs, routing, metric values and exactly which interface is used for each connection.

Is there any specific information from the IP command you think would be helpful?

---

### Post by TheFu on 2023-11-28
> **symbiant said:**
> Is there any specific information from the IP command you think would be helpful?

Uh ... 
> IPs, routing, metric values and exactly which interface is used for each connection.
That's why I wrote it.

---

### Post by symbiant on 2023-12-06
I figured I'd ask since there are a bunch of options, but now that I look at it I see it's probably just the five or so "query" options, and it wouldn't have been *that* much to just run each one and post everything. Next time I ask for help I'll just assume full data dump is best. No need to waste time of someone willing to offer free help. I really do appreciate it even if I didn't make the best use of it.

For what it's worth, I just gave up on the problem, and waited for a more permanent solution. I bought a USB ethernet adapter and moved it back off wifi, taking the opportunity to do a fresh install and switch to a more sensible division of services across multiple devices. If I had to guess at the problem, I think it has something to do with my router. When trying to figure out a couple other things I've realized that it's internal dhcp system is a little wonky, or maybe my understanding of it is. It can sometimes display the wrong internal IP (checked against the IP address of the device locally), and reserving an IP address that was previously allocated to a different MAC address causes all sorts of weirdness, even if that mac address is no longer in use and the allocation should already be expired. I'll have to dive in and become better versed in networking at some point, as right now the only area where services aren't seamlessly moved between devices/restored from backups has to do with the local IPs - needing to update where different services look for each other, where docker tunnels point, local home assistant ui address, etc. Hopefully I won't need to be doing any fresh installs/machine migrations any time soon though.

---

### Post by TheFu on 2023-12-06
Everything you wrote is why we use static IPs everywhere we can, configured on each device.  We only use DHCP reservations when it isn't possible to get a device to have the same IP forever some other method.   So, guest devices get dynamic DHCP IPs, network TV turners get static reservations, same for all wifi-only devices ... which get put into a firewalled off network segment from everything else along with IoT (really IoSh) devices.  I don't trust wifi and definitely don't trust IoT stuff.

Nobody starts out knowing this stuff.  Learn as you go, as you need to understand things.  IP networking is getting more and more confusing thanks to IPv6, which is either really easy or exponentially harder. Just depends on what you need and how strong your firewalls are (both computer and router) if IPv6 is good for you are not.

If the router really is the issue, nobody here was going to discover that magically.  

My rule of thumb for routers is that if a new firmware hasn't been provided and installed in the last 3 months, that router is out of support and needs to be replaced.  It is common for most consumer router brands to drop support in less than 2 yrs, with very few exceptions.  I know that the two largest ISPs in my country, if they provide the router for the connection, will also patch them when required.  That assumes you use their equipment.  I also know that Asus follows the best practices for patching, especially security patching, their routers due to an FTC mandate that lasts 20 yrs (it was signed in 2015-ish). We have some time left on that.

Then there are the small business router people - MikroTik and ubiquiti. Both of them have provided patches for significantly longer than any others in their list of competitors.  They have a higher learning curve than typical consumer routers, however and it is important to really know what you are buying, since it is possible to think you are getting 1 thing when you are getting something 10x slower by accident.

Then there are the "BYOD" router distros like openwrt and pfsense and opnsense.  These will run on x86-64 computers with 2 NIC ports and new hardware will probably last 10+ yrs, perhaps longer.  pfSense changed their licensing recently, so it is off my suggested list, but opnsense is a fork of it and works well. It is what I use on my APU2 router hardware (12W power, fan-less, silent) that was purchased in 2015 and I don't have any plans to replace it today.  If I get a network connection 50x faster than I currently have, then I'll need faster hardware to handle that throughput, but today, the router easily handles even 10x faster connectivity than I have.

I learned most of these things the hard way.  I've been burned by router makers dropping support far too fast for my needs, so I never plan to have any type of router hardware than an x86-64 based system.  Also, I'm happy to have switched to BSD-based router software to make it just a bit more difficult for attackers to break in.

BTW, a hint about asking for help - if you want someone to tell you the exact commands, ask for the exact commands.  I don't have them memorized - generally I have an alias for the different options I find useful, but since I don't know if you know what an alias is, it wouldn't be helpful to provide that list. I have perhaps 50 aliases for common things to make my CLI stuff faster and I don't need to memorize lots of options.   For example, I know that **ipr** is the alias I use to get routing information. Doubt that helps you at all. ;(

---

