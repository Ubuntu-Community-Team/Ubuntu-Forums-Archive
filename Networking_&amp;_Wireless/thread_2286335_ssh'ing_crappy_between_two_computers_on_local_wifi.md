---
title: "ssh'ing crappy between two computers on local wifi network"
date: 2015-07-11
forum: Networking &amp; Wireless
---

### Post by motrek on 2015-07-11
Hi guys,


I have a Mac in my apartment with excellent connection to my wifi router in the same room. Ping times to google are ~10ms.


I have a PC in my storage room running Ubuntu desktop 15.04 right below my apartment, also with excellent wifi connection. Ping times to google are the same, ~10ms.


The problem is that when I ssh from my Mac to my PC, it's crap. Pings from the Mac to the PC are usually in the 400 to 800ms range, plus every few minutes the connection will fall apart and give me a bunch of random/alternating error messages: "Operation timeout" and "Connection refused" and "No route to host". That usually lasts for a minute or two, then it's back to my 500ms pings and everything is working again (as well as ssh can work with 500ms pings).


I would expect that if both machines have excellent connection to the internet (and thus the router), then the connection between the computers should be rock solid.


I've tried for hours to search for this problem on the web but everything I've found is about sorting out ssh access that doesn't work at all, whereas my access is crappy and intermittent.


Does anybody have any idea what's going on? Thank you in advance!

---

### Post by TheFu on 2015-07-12
Let's get the over - wifi sucks. There is no way to control interference from all sorts of devices. From second to second, the interference changes. A trivial ping doesn't show that.  When surfing, humans don't see it either, but the computers do - BIG TIME.

So, if you care about a stable connection, use wired ethernet, period.  You probably don't want to.

Not all wifi chips are created equal.  You'll need to become an expert on yours to know exactly which protocols they support. 
Plus the wifi router will need to be configured to support the fastest connection that both these systems support, but no lower.  Inside the same room, I'd try to use 5Ghz bandwidth, but that doesn't like walls. If direct line-of-sight isn't possible, then 2.4Ghz will be necessary. 2.4Ghz is full of crap and all your neighbors crap.  You'll want to select a channel that nobody else uses. This all happens on the router config.  Pick from channels 1, 6, 11 - unless those are already used (which is common in dense people areas). Those are the only 2.4Ghz channels that don't overlap.  All other channels cause interference - which sucks, but sometimes you don't have any choice.

Lastly, every extra wifi device on a channel cuts the available bandwidth 50%, so turn off the wifi-smartphone when you want to transfer files.  If the connection speed (not the speed on the router box) to the router is 150Mbps, then 1 device makes that 75Mbps, 2 devices makes that 37Mbps, 3 = 18Mbps ....

Did I mention that wifi sucks?

So - you have to find the channel with the least interference first.  AFTER you do all of that, then you probably want to turn down the cipher level for the file transfers if your computers aren't Core i3 or better. Encryption takes processing power. **man ssh_config** has a list of ciphers. I think arcfour is the cheapest on CPU.

Lastly, some wifi cards need specific driver settings to perform well. I would assume the Mac has been tuned with Linux drivers already, so start with the other machine. You'll need to know the chips used, driver used and look for tuning params online.

---

### Post by motrek on 2015-07-12
> **TheFu said:**
> Let's get the over - wifi sucks. There is no way to control interference from all sorts of devices. From second to second, the interference changes. A trivial ping doesn't show that.  When surfing, humans don't see it either, but the computers do - BIG TIME.
... 

Thank you for taking the time to reply but I think you've missed the part where both of the computers have excellent wifi connections. I can't believe that the problem is with the wifi connection.

I can ssh into my downstairs computer, ping google, and get 10ms ping times. I assume this wouldn't be possible if it didn't have a good wifi connection.

Meanwhile, I can ping the downstairs computer from my Mac at literally exactly the same time and get typical ping times of over 500ms.

Unfortunately it's impractical for me to run ethernet from my apartment to my storage room but again, I can't imagine the wifi connection to my router is a problem.

---

### Post by TheFu on 2015-07-12
I did provide other alternatives.  Some settings in one card will interfere with the settings in another.   Post the output from **sudo lshw -C network** to get help. **Code tags** would be appreciated.

There isn't any "*check this box and everything will be fine*" setting, at least not yet. We need some data from you first.

Also - so we know how bad it is, please test the transfers using **time rsync --stats --progress** command + options when sending files so we have some real data.  "it is crappy" doesn't actually tell us anything concrete. We need fact and data. Please.

---

### Post by motrek on 2015-07-12
> **TheFu said:**
> I did provide other alternatives.  Some settings in one card will interfere with the settings in another.   Post the output from **sudo lshw -C network** to get help. **Code tags** would be appreciated.

There isn't any "*check this box and everything will be fine*" setting, at least not yet. We need some data from you first.

Also - so we know how bad it is, please test the transfers using **time rsync --stats --progress** command + options when sending files so we have some real data.  "it is crappy" doesn't actually tell us anything concrete. We need fact and data. Please.

Unfortunately I'm out of town but I will be able to do the lshw command later tonight and I'll post the results.

Bandwidth to/from the Ubuntu machine is as expected. When the machine is ping'able, I can ftp files to/from it at several MB per second.

Latency is the problem. As I've said, ping times are 500+ ms. When I type a character in ssh or sftp, it takes that long to appear. Everything is as sluggish as a 500+ ms ping would suggest. When the connection "drops" and the machine becomes un-pingable, the ssh connection doesn't actually break. Whatever I type eventually appears, delayed by a few minutes.

---

### Post by motrek on 2015-07-13
> **TheFu said:**
> I did provide other alternatives.  Some settings in one card will interfere with the settings in another.   Post the output from **sudo lshw -C network** to get help. **Code tags** would be appreciated.

There isn't any "*check this box and everything will be fine*" setting, at least not yet. We need some data from you first.

Also - so we know how bad it is, please test the transfers using **time rsync --stats --progress** command + options when sending files so we have some real data.  "it is crappy" doesn't actually tell us anything concrete. We need fact and data. Please.

Here is the relevant output from lshw:

  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 7c:dd:90:76:31:4e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.19.0-21-generic firmware=0.29 ip=192.168.254.42 link=yes multicast=yes wireless=IEEE 802.11bgn

I do not know what you mean by "code tags" but if you can provide the command to get those I'll be happy to supply them.

As I've said 3 times now, I don't think the wifi connection from the Ubuntu machine to my router or the internet is the problem. I can ping google from that machine and get rock solid reliable ping times in the low-two-digit range.

So if we assume that my wifi hardware and my wifi connection are good (and I see no reason not to assume that), that leaves the mechanism that my Mac is using to find and communicate with the Ubuntu machine.

I think we can also assume that nothing is wrong with ssh keys or encryption or anything, since my ssh crappyness basically just reflects what ping is telling me (crap ping times and frequent dropouts).

So I'm not sure what that leaves us with... maybe the Ubuntu machine is communicating its availability to the local network incorrectly or inconsistently? Something to do with DNS? I admit that I don't know much about networks.

---

### Post by weatherman2 on 2015-07-13
Ping doesn't really mean anything in terms of the reliability of the connection - I think that's what TheFu is trying to get across to you.

Still, to eliminate WiFi from equation, I encourage you to try temporarily wiring them both together, then seeing how well ssh works.  If you have the same lousy connection, then you can confirm WiFI has nothing to do with it.

I will say that I disagree with TheFu about the feasibility of reliable WiFi connections.  I have a couple of servers on my home network connected via WIFi and I access them all the time via my wireless laptop.  I can get excellent transfer times when copying files from one place to another.  But, I have spent a lot of time over the years understanding how to setup my wireless network reliably.  It is not necessarily as easy as it seems.  I have no idea at all how your wireless connections are setup, what kind of router you use, how it is configured, etc.  But if you wire everything together and connections are still slow, then WiFi is irrelevant to your issue.  This is how I tend to debug things: eliminate variables, one at a time.

---

### Post by weatherman2 on 2015-07-13
Another thought regarding WiFi: in my experience, those little USB wireless cards (you seem to have one) are not very reliable.  I have one on one of my servers that is sometimes super solidly connected; at other times I get a terrible connection to it and sometimes it goes back and forth like that within a few minutes.  I have found using a stand-alone wireless router configured as a wireless ethernet bridge works much, much better.  5GHZ works better too if you have a lot of neighbors with WiFi networks, most of which are 2.4GHZ.

---

