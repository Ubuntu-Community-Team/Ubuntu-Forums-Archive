---
title: "[SOLVED] Ibex Static IP (how do I configure /etc/network/interfaces manually?)"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Gathalimay on 2008-10-31
I know the network manager has a problem, but I want to know if I can just configure the /etc/network/interfaces file so I don't have to bother with them at all.

In windows, I fill in the following:

IP address 192.168.1.120
Subnet mask 255.255.255.0
Default Gateway 192.168.1.1


Preferred DNS server 67.75.160.63
Alternate DNS server 67.75.160.64

Now, how would I translate that over to the interfaces file and do I need any more information to do that (if so, how can I get it?)

I have seen these things for the interfaces:
address (Desired IP address?)
netmask (Subnetmask I'm assuming?)
network (No clue) UPDATE: Ignorable
broadcast (No Clue) UPDATE: Ignorable
gateway (Default Gateway?) 
dns-nameservers (The two things I posted up above?) UPDATE: Ignorable

Would filling that in be sufficient to get it going?

Thanks in advance!
(if someone could post up an example file with the proper info based on what I put up, that'd be awesome. Also this is a wired connection)

UPDATE: Solved, see my 2nd post below.

---

### Post by vitorgatti on 2008-10-31
Those you have No Clue, you really don't have to put something. Just don't add the line :)

---

### Post by jynyl on 2008-10-31
These threads might help ...
[http://ubuntuforums.org/showthread.php?p=6077550]("http://ubuntuforums.org/showthread.php?p=6077550")
[http://ubuntuforums.org/showthread.php?t=965416]("http://ubuntuforums.org/showthread.php?t=965416")

---

### Post by kevdog on 2008-11-01
There was a nice sticky written by Weiman01 on this exact topic, but the moderators in their infinite wisdom chose to remove this sticky -- although it was the most accessed sticky on the forums!!  I would suggest you look in tutorials and tips under weiman01 for this sticky.

---

### Post by Gathalimay on 2008-11-01
So I set up my interfaces file with just the address gateway and netmask, then I tried this:

/etc/init.d/networking restart

and it says I have no /etc/resolv.conf

Also, I don't see anything by the user you mentioned above, and don't I still need to work out the DNS stuff?

EDIT: Found the guy, Wieman01 (it is "ie" not "ei"). His post was about wireless, but it was still similar. However, I think the problem is with the lack of resolv.conf file. I don't see how you allow a distro to come out when something so basic is not functioning. How are you supposed to fix it if you only have 1 computer? You can't look online. . .

---

### Post by Gathalimay on 2008-11-01
I fixed my problem!! I am typing this from kubuntu now.

First off, I configured /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.100 [the LAN IP address you want]
gateway 192.168.1.1 [the IP address of the router]
netmask 255.255.255.0
```

Then I created /etc/resolv.conf (There was none on my installation)
To do this: 
```
sudo kate /etc/resolv.conf
```
-It gave me an error saying it could not be loaded due to some error 
--I looked for the file in /etc/ but I saw nothing. I'm guessing the file was "there" but it was either corrupt or inaccessible, which is why the internet wasn't working. 
---Ignore that error and add the following lines but with your own data for the 3 fields:

```
search socal.rr.com (it actually works without this line)
nameserver 66.75.160.63 [DNS server]
nameserver 66.75.160.64 [DNS server]
```

Kill network manager, and restart the networking module (or w/e) with:
```
sudo /etc/init.d/networking restart
```

And then it should work.

The DNS servers I actually got off of windows. If you have a windows installation, type the following into the command line:
```
ipconfig /all
```

and it should give you some LAN configurations, such as IP, gateway, netmask, etc.
Below that stuff, you should see something that looks like a website name (your isp.com for example, like what I have above). That is what I put for the search field but I'm not entirely sure it is correct. Either way, it works without that line. Omit it if you want.

It should also give you some DNS servers which look like IP addresses below.
Plug that info into the /etc/resolv.conf file. Put ONLY ONE DNS for each nameserver line. Say it gives you 3, then make 3 separate nameserver fields and plug each one in.

---

