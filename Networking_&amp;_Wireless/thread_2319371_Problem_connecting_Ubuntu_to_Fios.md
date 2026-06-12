---
title: "Problem connecting Ubuntu to Fios"
date: 2016-04-03
forum: Networking &amp; Wireless
---

### Post by Robert_E._Kilpatri on 2016-04-03
I love my Surface Pro 2 but it is getting old, so about 4 months ago I installed Ubuntu.  It has been ten year since I used Red Hat and SuSE so it has been a ruff ride, but I'm  going to go ahead and get rid of my other OS completely if all goes well with installing the software I have to have for school in VM.  I sat down at my computer today and the Internet did not work so I ran some test and all of the devices in the house are working great and I have very fast upload and download speeds.

Now the Internet has always been slow on my Surface Pro up until I had to take a business trip a few weeks ago.  When I got to my barracks I realized that my wireless only worked for a few minutes.  After a lot of trial and error I finally figured it out and I was up and running again.  

Now I can connect to the Internet by connecting an Apple device or threw WiFi other than what is running in my house.  I have Fios and I can connect to the router threw Ethernet cable and WiFi but I can't connect to the Internet.  At first I thought it was my computer so I spent several hours looking for answers but I can't find a step-by-step that gets me up and running yet.  I know that this is a common problem because I found a lot of post asking for the same help.  Some older post that deal with the same problem have been solved but I couldn't figure out how to apply them to Ubuntu 15.10.  I am also starting to think that I might be gong at this in the wrong way.  When I go into the router and look at the firewall I see a long list of events from today that have been blocked, so I know that the router's firewall is blocking my Unbutu.  I have never messed with a router firewall before so I googled this too and I still could not figure out how to get threw to the Internet.  

I never use the wireless in my house on this device, so if someone could help with the Ethernet that would be great.

---

### Post by SeijiSensei on 2016-04-03
Are you using the standard Verizon router?  When you connect by either means, run the command "route -n" from a terminal prompt and see if you have a gateway specified.  It should be provided automatically by the router.  You'll see something like this:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```
The top line tells the machine to send any packets not intended for the local network to the router at 192.168.1.1 to be forwarded out to the Internet.  You may have different addresses specified, but you should have a gateway.

If you don't have a gateway specified, my first suggestion would be to reboot the router by disconnecting it from power, waiting thirty seconds, and reconnecting it.  See if that fixes the problem.  If not, we'll try some other methods.

---

### Post by Robert_E._Kilpatri on 2016-04-03
I get 

Destination       Gateway       Genmask         Flags Metric Ref Use Iface
0.0.0.0             192.168.1.1  0.0.0.0            UG    600    0       0  wlx501ac507c3c4
169.254.0.0      0.0.0.0         255.255.0.0     U      1000  0       0  virbr0
192.168.1.0      0.0.0.0         255.255.255.0 U      600    0       0  wlx501ac507c3c4
192.168.122.0  0.0.0.0         255.255.255.0  U      0       0       0  virbr0

so... I don't know what this means.  

When I ran test from my son's laptop (Windows OS) gets download speeds avg.@ 87 mps, upload speeds avg.@ 72 mps.  I am concted to the router with Ubuntu right now in Firefox, but when I try to get even Verizon Support website threw the router home page it will not connect.  I am using the gnome interface and in the upper right side of the top bar the device does show that it is sending and receiving packages every now and then but they are very small.

I am going to go and **** off my kids again and unplug the router this time 30 sec.

---

### Post by Robert_E._Kilpatri on 2016-04-03
That stinks, typing on an iPad is a real pain, Sorry it didn't keep the spacing I added a pic.

---

### Post by Robert_E._Kilpatri on 2016-04-03
Nope it is still the same, I can connect to the router but not the Internet. Even thought I get the same results on wifi or Ethernet, I just realized the there is a deference in the computer name.  When I am on Ethernet the router sees the right name of my computer but on WiFi it calls my computer "new-host-3"

I also rebooted into Window and the Internet still works fine there.

Ok, run a some commands I found on line and I have found a problem, eth0 has no IP adres, but only when I am trying to connect to Fios (as I type this I know it makes no since.) but here is a pic of what I got.

---

### Post by matt44 on 2016-04-06
In your case, it looks like you are connecting over wireless. If that is the case, then you are not using eth0. It looks like you are getting an IP address on your wireless adapter (wlx501ac507c3c4) of 192.168.1.254 and your route -n is showing that your gateway is 192.168.1.1 via your wireless adapter. Assuming that that is a legitimate network, everything appears fine. You can try to ping your router (192.168.1.1) to see if that works. 

Can you post the result of the following commands;
# nmcli dev list | grep DNS

# ping [www.google.com]("http://www.google.com")

# ls -al /etc/resolv.conf

If you do not have DNS configured then it would appear that your internet is not working.

---

