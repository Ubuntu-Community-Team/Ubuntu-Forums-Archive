---
title: "Adding high-speed dedicated LAN link between two devices"
date: 2022-05-11
forum: Networking &amp; Wireless
---

### Post by bernard2 on 2022-05-11
I have a standard (!) Gb ethernet running around my house - a few switches, a WiFi mesh, lots of assorted devices, and it's all working fine. The speed is generally quite adequate for my purposes.

However, there are two devices where I often wish I had a bit more speed between them: my Ubuntu (20.04) server and a Mac Mini (Monterey) which I use for regular desktop work. These devices sit right next to each other, plugged into the same Gb switch.

One day I hope to upgrade to 2.5Gb ... so one option right now would be to get a small 2.5Gb switch to replace the one in this area, get a 2.5Gb interface for both Ubuntu and Mac, and I would be off - I'd have 2.5Gb between those devices only, 1Gb everywhere else.

However, I'm feeling mean, and I'm pretty sure that 2.5Gb (or more) switches are going to get cheaper before I'm ready to roll out 2.5Gb across the whole house, if indeed I ever do. Really, looking at how I use this stuff, it's only the link between Mac and Ubuntu where speed matters. Most file transfer is via Samba, in case that matters (Samba because there are also Windows machines accessing the same info). Ubuntu currently has a fixed IP address, Mac is using DHCP from my router.

I know I can add an additional 2.5Gb interface to each device for not too much money. But can I then easily link those two together directly, without impacting either device's ability to connect to everything else on the network? 

I have a feeling it ought to be easy but my knowledge is a bit sketchy so I'd really appreciate some pointers. TIA !

---

### Post by TheFu on 2022-05-11
Yes, you can, but you'll want to put those new interfaces onto a different subnet, give them different names and NOT use DHCP.

But I have real doubts that the network is the bottleneck for file transfers.  Storage is almost always the true bottleneck for HDDs, not the network.  At some point the bytes have to be read and written somewhere. If either side doesn't use SSD storage, then the network ain't the problem.  Fix the storage first.

Also, some 2.5Gbps NICs have poor Linux support. The forums are full of issues.

And, NFS is usually faster than CIFS/Samba, so using that between all the Unix systems in the house (wired ethernet!, not wifi) makes sense.  If your Mac is running that other OS, you'll likely need to change the uid for the humans users to map 1-for-1 to what Ubuntu uses.  The uid/gid numbers need to match on all systems sharing NFS storage.  Typically, we don't need to worry about daemon accounts, just humans and the few groups those humans are in that also get used between the NFS server and client systems.

---

### Post by bernard2 on 2022-05-11
Thanks for the response. Your warning about HDD speed is entirely fair, though in this case the Mac is entirely SSD - and so is a lot of the storage in the server, particularly the "scratch" area where I do a lot of reading/writing - I use HDD for data that has settled, as it were.

I'll have a look for clues for a NIC that might work in Linux, and can look into adding NFS.

Let's say I sort that ... and I now need to configure a new interface in Ubuntu. I know how to add that, and specify a different subnet, and make sure I'm not using DHCP.

So now if I'm at one of these machines I now have two routes to get to the other one: the original route through the current NICs and switch, and the new route through the new NICs and direct cable. How do I encourage the transfer to take place through the new motorway rather than the old back road?

---

### Post by TheFu on 2022-05-11
The interface will show up in a list next to where ever the existing interfaces are of this is a desktop.  Click to edit, add a new IP, netmask, and don't put in any gateway.
Connect the cable directly between the two computers. No need for a special cable for 1Gbps and faster NICs.
Put the 2 new IPs in the /etc/hosts on the Linux and Mac computers AND **USE DIFFERENT NAMES**. The different names are important. Those should be the same lines for each. Make certain the "files" is listed in /etc/nsswitch.conf for dns. Here's the line for my systems.  Just be certain that "files" is first. It is ok if mdns is there too.
```
hosts:          files dns 
```

The IP and netmask are what tell the computers which interface to connect through.  So, if your main LAN is 192.168.1.x/24, make the special LAN something like 10.11.12.x/24.  Then all traffic on that subnet will automatically traverse on the NIC with IP in that subnet.

You can setup **metrics** in the network configs to place 1 for 10.11.12.x/24 and 100 for 192.168.1.x/24 and 1000 for all others (i.e. the default route.  Easy Peasey.

Now, you just need to remember to use the different names. There are all sorts of ways that people standardize names for having lots of different interfaces.  Some people use different colors for the different networks.
[LIST]
[*]Red = Internet(danger)
[*]Green = save desktop with NAT access to the internet
[*]Black = administrative
[*]Yellow = Storage ... I get the feeling this is what you'd like for your NFS/CIFS/SAN.  
[/LIST]

Don't get too hung up on the colors, just use what makes use to you.  If you like, you can buy different color cables, but that brings all sorts of other maintenance issues.  See attached.  I have a better image with all yellow cables - perhaps 10,000 down a row of different network equipment.

---

### Post by bernard2 on 2022-05-12
Thank you! I think the "different names" is the key message that makes this makes sense.

I think my next step is to try NFS to see what improvements that gives me, do some measurements with different copies to see what my potential speed-up will be, and then if all looks good to give it a go. Your assistance is much appreciated.

---

### Post by bernard2 on 2022-05-23
Update in case anyone else finds this ... after a short delay, partly because of other stuff happening and partly because the first NIC I bought turned out to be faulty, I now have it working! I'm using a Comfast 2.5Gb PCIe card in Ubuntu, and an RSHTech USB-C to Ethernet adapter in my Mac, connected directly with a Cat6 cable.

Speed comparison for a use case which is important to me: copying a video file from SSD on my Mac to SSD on Ubuntu was running at about 0.9Gb/s on the 1Gb link, which is fair enough.

Having implemented the new high speed link, the same copy is running at just over 2Gb/s ... that's still using Samba. Whether further speed up is possible by shifting to NFS I don't know.

The new network is set up as 10.0.0.1 or 2, fixed addresses. The main thing I had to do was configure Ubuntu Samba (smb.conf) to use both old and new interfaces and allow connections from both. At the moment I have just configured the Mac to connect to the specific ip address (10.0.0.1). I could of course add a new hostname to the Mac /etc/hosts file to make that a little cleaner.

---

