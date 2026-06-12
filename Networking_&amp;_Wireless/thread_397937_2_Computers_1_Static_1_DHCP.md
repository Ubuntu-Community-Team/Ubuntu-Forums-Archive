---
title: "2 Computers 1 Static 1 DHCP"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by mindstate on 2007-03-31
Having some trouble figuring this out, For a few days now ive been trying to setup my DSL modem/router combo to assign a Static IP for Computer 1 and a Dynamic IP for  Computer 2. I want to run postfix but i want both computers to have a seperate public IP address.I've tried various different method of doing this .. Logging into my Gateway @ 192.168.1.1 and assigning Computer 1 to a static address, this does nothing though both IP's still say their Assigned Statically..

Ive tried to go into the /etc/network/interfaces file and adding the neccessary options for static ip assignment ..

At one point my DSL did it automatically 1 Address was assigned dynamically and the other static and i had 2 public IP address for each computer. Is there a way to manually configure this? 

Any help would be so appreciated thanks guys

---

### Post by diablo75 on 2007-03-31
Did you pay for two public IP addresses with your Internet Service Provider?  And is the device that connects you to the internet (the modem) able to do static network address translation?

My understanding is, if you are connecting to a router, which is connected to a modem, NAT (Network Address Translation, specifically, Port Address Translation) is already taking effect, converting your 192.168.1.X addresses, into (likely) a Class A public IP address, which is divvied to your modem by the ISP, and can only have one IP address assigned to it at once, I believe.

Why do you need these two computers to be represented to the internet with different IP addresses?  What is it you need them to do that port triggering in the router can't take care of to solve your dilemma?

---

### Post by mindstate on 2007-04-01
> **diablo75 said:**
> Did you pay for two public IP addresses with your Internet Service Provider?  And is the device that connects you to the internet (the modem) able to do static network address translation?

My understanding is, if you are connecting to a router, which is connected to a modem, NAT (Network Address Translation, specifically, Port Address Translation) is already taking effect, converting your 192.168.1.X addresses, into (likely) a Class A public IP address, which is divvied to your modem by the ISP, and can only have one IP address assigned to it at once, I believe.

Why do you need these two computers to be represented to the internet with different IP addresses?  What is it you need them to do that port triggering in the router can't take care of to solve your dilemma?

sorry for the delay, but youre absolutely right. Im running postfix on one of my computers and i thought maybe having the same public IP would conflict with this, but youre absolutely right port fowarding works just fine. I thought by doing this i would open up ports on both machines but i can port foward seperate sub ips . 

Thanks for the replay though ..appreciate it

---

