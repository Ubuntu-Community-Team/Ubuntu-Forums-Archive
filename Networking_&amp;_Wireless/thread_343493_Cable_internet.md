---
title: "Cable internet"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by gfroce78 on 2007-01-21
I am new to Linux and I am trying to connect to the internet but, I am having difficulties doing so. I see there is a section for dial up and DSL but I have Cable internet that is always on and does not require a password or username so where could I find directions to setup that internet.:mad:

---

### Post by iver2435 on 2007-01-21
Well, there are a lot of variables in getting something connected, but I'll at least try to help.  With having cable internet, most likely you're just getting a DHCP address from your ISP, so you don't need to delve into the section for Dial-up and DSL (PPPoE).

The way that I have done it in the past is to simply configure your network card for DHCP and then let the network pretty much do the rest...

If you are running your cable internet into a router first, then that changes things a little bit, but not too much.

If you are not having any luck with the "plug and pray" method, then I would suggest just re-posting with more information about your setup (makes, models, etc..) and what you've done so far.  I think that after you do that you'll have a lot more luck in getting help from the community.

---

### Post by gfroce78 on 2007-01-21
I am not sure exactly what specfics what everyone needs but, I am running my internet from the wall into a modem then my computer. When I bring up firfox and try to got to the internet a message saying webpage cannot be found comes up.

---

### Post by bladerun on 2007-01-23
I am  having the same problem

---

### Post by RandomJoe on 2007-01-23
Have you had this setup working before, perhaps with Windows or on another computer?

The first thing - are you getting a link between the cablemodem and your Ethernet card?  Link lights on, probably data flashing (cable networks ALWAYS have traffic...).  Are you sure you have the _right_ cable?  I can't remember if mine needs a straight-thru or crossover cable...

If the physical connection is good, Ubuntu _should_ get an IP by DHCP when booting by default.  If the connection was originally set up using a different computer, there are two other possibilities - a few ISPs require you register the computer's MAC address before they give an IP.  Or, if they don't, if you are only allowed one IP you have to power-cycle the modem when switching it between computers.  The modem holds the first MAC address it sees and only gives an IP to that one.  (Unless told to allow more by the cable company.)

Do you possibly have a cablemodem with built-in router?  I've seen DSL modems that way, but not cable.  Perhaps there are some, though.  Maybe there is some setup required for the router?

On the Ubuntu side, what are your connection properties for the ethernet connection?  The checkbox for Enable should (obviously) be checked.  Mine just has DHCP for configuration, that's it.

That reminds me - there are apparently a few ISPs around who require you send a particular hostname with the DHCP request, perhaps your account's username or something.  If you need to do that, you can edit the /etc/dhcp3/dhclient.conf and add a line at the top like:
```
send host-name "yournamehere"
```

Beyond that, for a standard DHCP setup you shouldn't need to do anything special on the Ubuntu end...

---

### Post by chili555 on 2007-01-23
It should be pretty easy! First, let's see if your ethernet card is working. Open a terminal and type: sudo ifconfig -a

You should get something like this: eth0      Link encap:Ethernet  HWaddr 00xxxxxxxxxxx:FB  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
You should get a lot of other lines, too, but we want to see eth0.

If so, simply go to System->Administration->Networking and configure eth0. Highlight the wired connection and click Properties. Select DHCP, check "Enable this connection" and close. It should start right up. Check by pinging a site; ping -c3 [www.google.com](www.google.com). If you get a reply, you're all set.

Good luck and have fun!

---

