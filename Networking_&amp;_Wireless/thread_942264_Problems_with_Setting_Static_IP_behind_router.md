---
title: "Problems with Setting Static IP behind router"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by Nir Friedman on 2008-10-09
Hello,
my goal is to set up a static (local) IP address for my computer on the wireless network so that I can forward ports to my computer consistently. Now, I know this is a common thing to set up and I have googled numerous approaches and tried many of them. These include using the GUI in KDE, editing /etc/network/interfaces, and putting in commands such as:
ifconfig wlan0 192.168.1.150 
(or whatever I wanted to set it to). Some guides specifically discuss changing router settings and others do not (my router is currently set to DHCP, I have played around with the settings on it as well). Basically, any attempt I have made to make any changes instantly results in my internet connection ceasing to work. I have been at this for 3 hours and it's getting quite frustrating. I would provide more details, but to be honest I'm not sure exactly which are relevant so I'll hold off on posting all my router specs until I get a better idea of what is relevant. Help with this would be terrific, I'm clueless on where to even start trying to fix this.

---

### Post by FrostyFlames on 2008-10-09
[http://codesnippets.joyent.com/posts/show/319]("http://codesnippets.joyent.com/posts/show/319")

First, backup your "/etc/network/interfaces" file. I'll be doing everything in the command line interface (CLI) AKA the Terminal.
This copies and renames the interfaces file so that you have a backup:
```
sudo cp /etc/network/interfaces /etc/network/interfaces_old
```
If you screw up the new interfaces file you can replace it with the backup with the following code:
```
sudo cp /etc/network/interfaces_old /etc/network/interfaces
```

This opens up a basic text editor. When you're done editing code press "Control + X". That should bring up if you want to save it, press Y, then press ENTER (we don't want to change the name), and nano should exit.
```
sudo nano /etc/network/interfaces
```

You will probably have this at the end of the interfaces file.
```
# The primary network interface
auto eth0
iface eth0 inet dhcp

```

Basically this means that eth0 (Your first ethernet port) is setup as DHCP. You want to change from your DHCP address to a static IP. To do that you will need to change a few things. Below is an **_example_**. (Do not use this example because your setup is probably different). 

```
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```

On the 3rd line we changed "dhcp" to "static" and then added some other information. The "address" is the IP you want for your machine. The next line has "netmask", this should be if you're on a local LAN "255.255.255.0", just like in the example. The "network" is a little tricky. In you post you said "192.168.1.150", here for the network you would want "192.168.1.0". This has to deal with the netmask (go look up subnetting ](*,) if you want more info on that, it's beyond the scope of this post). The "broadcast" for your "192.168.1.150" IP would be "192.168.1.255", again another subnetting thing. The "gateway" is your router. You MUST know this or you won't get any internet at all. Your gateway should be "192.168.1.1".

If you do not know your gateway, install "traceroute" and do a trace on a website.

Traceroute install:
```
sudo apt-get install traceroute
```
Then run traceroute. You will get something that looks like this:
```
user@ubuntu:~$ traceroute google.com
traceroute to google.com (209.85.171.99), 30 hops max, 40 byte packets
 1  MyHomeNetworkSSID (192.168.1.1)  1.425 ms  1.835 ms  2.317 ms

```
This tells me that my first hop hits a router. That router happens to be my gateway. It also displays the IP address of your gateway. In my case that is "192.168.1.1".

All in all, if you want your 192.168.1.150 IP, your config should look like this:
```
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.150
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

If this does not answer your question, we probably will need to know your gateway's IP and the IP you want to use. And if you really screwed up we will need to see your interfaces file.

I probably wrote way too much.:lolflag:

---

### Post by Nir Friedman on 2008-10-09
I tried to make the recommended changes, and once again my internet immediately stopped working. I typed in exactly what you had in the last box, except that I replaced eth0 with wlan0 because I need this to work over wireless. I installed traceroute and verified that my router is 192.168.1.1 (well I suppose I already knew that from entering my router set up before, but whatever). Here is what my interfaces file looks like now (I restored the original)

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

and that's all. Thanks a lot for your detailed post. Is there perhaps something I need to change on the router to help make this happen?

---

### Post by FrostyFlames on 2008-10-09
It appears that the networking app that controls the wireless connection does not support manual static IP addresses after doing some more research.

Your router should have some kind of "Static DHCP" setting in your router settings perhaps. Router Model/Make information would help a lot.

---

### Post by theDaveTheRave on 2008-10-10
Hi all,

I'm hoping the information in this post will help me solve a couple of problems.

hers is my situation.

At work all the pc's and laptops have a static IP address, mostly they are either Windoze or Mac.



I recently joined the team and attempted to join my ubuntu powered laptop to the network and everything went fine.

They have a "redundant" machine that is going to ultimately be a file / MySQL server (with a raid device), and if I can get my way will run on either Ubuntu or Deb.

I'm currently sorting out the setup on my laptop to make sure I know what all the settings are going to need to be for the server.

Others in the group, who have tried to run linux on said "server", have problems setting a statip IP on said machine. so I decided that I would test this out and should have a "staticIP" on my laptop, but just like my colleagues I found that this immediately broke the network connection.

The details entered into Network Manager are exacly the same as a pc next to mine, both connected through the same router (obviously I changed my IP address to the one obtained from the output of <ifconfig> for the eth0 device on my laptop.

At the moment I am located at the research centre liked to my job and won't be back ay "my office" for a week or so, but I'm hoping the information supplied by Frosty Flames will solve my problems, and if s/he is correct and static IP settings in "Network Manager" break networking I'm going to be seriously surprised that they even have the option available!

I have one other question...

is it possible to set up "locations" within the /etc/network/interfaces file?? I only ask as when I am at home I'm certain that my ***WIRELESS*** device will have a different IP address to the ***WIRED*** one, and when I am downloading update etc I link in directly to the back of the wireless router (for faster dowloads), will having a predetermined statip IP bugger this up for me??

I've also recently had a look at the [wicd]("http://wicd.sourceforge.net/") site and may try multiple locations with that, but I would like to be able to make this work by editing the various config files.

I've hunted all over for a solution, and I realy hope that this one will work for me!

dave

---

### Post by Seantiago on 2008-10-18
> **FrostyFlames said:**
> It appears that the networking app that controls the wireless connection does not support manual static IP addresses after doing some more research.

Your router should have some kind of "Static DHCP" setting in your router settings perhaps. Router Model/Make information would help a lot.

Will static ips over wireless connections be supported in ibex, or is ubuntu completely broken in this regard? It seems pretty silly to leave somehthing like this out.

My router (a linksys wrt54g) does not support static dhcp.

Thank you.

---

