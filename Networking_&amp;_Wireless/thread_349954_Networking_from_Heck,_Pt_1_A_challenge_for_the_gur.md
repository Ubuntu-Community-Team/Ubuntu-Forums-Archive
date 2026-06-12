---
title: "Networking from Heck, Pt 1: A challenge for the gurus!"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by spasticteapot on 2007-01-30
First, I should mention that I volunteered to be  sysadmin of a small network with very little experience with either linux or networking because nobody else wanted to do it, and the little I know is still more than everyone else. 

Anyway, continue to read the Network from Heck.

I have a network of computers, all of which have static IP addresses: 192.168.5.x, with X being the number of the computer in the lab. I set them up this way mostly because I have not the foggiest clue of how to set up DHCP.

However, we have no internet.

Next door is a coffeeshop with wifi; we have permission to use their network. One of the PCs has a functional wireless card (after trying four others that would'nt #@$@#$ connect!), and I'd like the other PCs to be able to connect through it.

And here are the problems:

1. I have no information on the access point other than that it uses DHCP. No static IPs allowed. 2. There are a mix of windows and linux PCs on the network.
3. I have no idea of what I'm doing.

A guru I know suggested using a NAT function - perhaps Masquerade? - on the wireless connected machine (which will be used for nothing but internet serving), and simply pointing the other PCs to the NAT-box as the gateway. 

How do I work masquerade? Should I use DHCP instead? Am I doomed?

---

### Post by Jimmey on 2007-01-31
I don't think you are.

What you're going to have to do is make the computer that's capable of connecting to the wireless network the main computer in the network. You've got to ensure that this computer is pingable by all the other computers. 

Figure out the this computer's LAN address (in Windows, Start>>Run>>cmd[enter]>>"ipconfig", in Ubuntu, open a terminal, and type "ifconfig"). It'll be, like you say, 192.168.5.X.

Once you know this, go to another computer, and try pinging the main computer. You can do this by typing "ping 192.168.5.X" into either the command prompt, or a terminal.

For now, I'll assume that that'll work (you'll get responses from that IP address). 

The next step would be to make sure that the computer with the wireless card in it has access to the internet. What you'll need to do is ask the network administrator of the coffee shop for the following:

The address of the wireless hub (the default gateway);
The subnet mask to use;
The essid (network ID) to use; 
And if any secrity measures are in place on the network (WPA, etc).

Let me know how that goes.

---

### Post by Vashu on 2007-01-31
I think with the DHCP tutorial @ [www.ubuntuguide.org](www.ubuntuguide.org) you can easily set dhcp up on the pc with the internet connection. And with the firestarter's wizard mode you can easily make it share the internet with the inner lan while keeping you safe from internet attacks.

I think those two are all you need. (for now).

---

### Post by chili555 on 2007-01-31
Well, I must admit, that from a learning experience standpoint, getting a DHCP server going and working out NAT on the computer with the wireless card would be a challenge. It's quite do-able but takes some research and head-scratching. A feeling of pride and accomplishment will wash over you when it's done!

Another approach is to buy a tiny box with all those problems worked out and built in! Take a look at a wireless ethernet bridge: [http://cgi.ebay.com/Linksys-WET11-Wireless-Ethernet-Bridge-802-11b_W0QQitemZ110084587949QQihZ001QQcategoryZ61817QQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Linksys-WET11-Wireless-Ethernet-Bridge-802-11b_W0QQitemZ110084587949QQihZ001QQcategoryZ61817QQrdZ1QQcmdZViewItem)

The fact that you use 192.168.x.xxx IP addresses implies you are all plugged into a router. Plug a bridge into the router and tell *it* to get an address from the wireless network, the bridge will share the connection with everyone on the router and you are all set!

---

### Post by spasticteapot on 2007-01-31
> **Jimmey said:**
> I don't think you are.

What you're going to have to do is make the computer that's capable of connecting to the wireless network the main computer in the network. You've got to ensure that this computer is pingable by all the other computers. 

Figure out the this computer's LAN address (in Windows, Start>>Run>>cmd[enter]>>"ipconfig", in Ubuntu, open a terminal, and type "ifconfig"). It'll be, like you say, 192.168.5.X.

Once you know this, go to another computer, and try pinging the main computer. You can do this by typing "ping 192.168.5.X" into either the command prompt, or a terminal.

For now, I'll assume that that'll work (you'll get responses from that IP address). 

The next step would be to make sure that the computer with the wireless card in it has access to the internet. What you'll need to do is ask the network administrator of the coffee shop for the following:

The address of the wireless hub (the default gateway);
The subnet mask to use;
The essid (network ID) to use; 
And if any secrity measures are in place on the network (WPA, etc).

Let me know how that goes.

Already done - all the PCs can ping each other, if nothing else. The wireless bridge/NAT PC connects just fine. However, a bridge might not work so well - the wireless source is unencrypted and set up for plain DHCP.


> **chili555 said:**
> Well, I must admit, that from a learning experience standpoint, getting a DHCP server going and working out NAT on the computer with the wireless card would be a challenge. It's quite do-able but takes some research and head-scratching. A feeling of pride and accomplishment will wash over you when it's done!

Another approach is to buy a tiny box with all those problems worked out and built in! Take a look at a wireless ethernet bridge: [http://cgi.ebay.com/Linksys-WET11-Wireless-Ethernet-Bridge-802-11b_W0QQitemZ110084587949QQihZ001QQcategoryZ61817QQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Linksys-WET11-Wireless-Ethernet-Bridge-802-11b_W0QQitemZ110084587949QQihZ001QQcategoryZ61817QQrdZ1QQcmdZViewItem)

The fact that you use 192.168.x.xxx IP addresses implies you are all plugged into a router. Plug a bridge into the router and tell *it* to get an address from the wireless network, the bridge will share the connection with everyone on the router and you are all set!

We have no money. None. Zero. Zip. 

(The wireless card is mine.)

The computers are 192.168.5.x because that's what I set them to; no other reason. I'm personally fond of static IPs because they're easy, but I suppose that I could give DHCP a shot. 

Of course, someone would have to explain how.

---

### Post by RandomJoe on 2007-01-31
You do NOT need to set up a DHCP server.  Keep your static IPs, they are fine!

The ONLY DHCP you need is a _client_ - run on the PC with the wireless card - to fetch an IP from the wireless system next door.  

Does this PC have Inet connectivity already?  As in, you have the wireless card set up and connected, can browse?  If so, then all you need to do is set up IP forwarding and NAT/masquerade on that PC and the others should suddenly, magically have access.  (You will also have to tell them to use that PC's IP as the Gateway.)

By default, Ubuntu will use DHCP on a network interface so if you don't yet have the wireless card set up yet, just get the drivers configured and point it to their AP.  Once it's associated, the system should run dhclient and grab an IP.  You can double-check that by going to System -> Administration -> Networking, then looking at the properties for the wireless card.

When they say you can't use static IPs, that just means a static IP won't work when connecting directly to their wireless system.  Since you are hiding all your other machines behind the NAT, their system will never see those static IPs.

Edit:
Okay, it might help to say how to set up the forwarding bit.  [This]("https://help.ubuntu.com/community/InternetConnectionSharing") is the first Ubuntu Howto I found in a quick search - it's rather terse, and doesn't completely apply to your situation since you already have most of what you want/need set up.  The really short version is you need the two lines under 'configure NAT on iptables', something like:
```
sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```
This assumes wlan0 is the name of the wireless interface you want everything to go out of.

While this should work, you can also go to great lengths to configure iptables for all knids of things - such as allowing certain ports in for things like servers or bittorrent - but that gets complex quick. although there are some GUI programs to make it easier.

If the two lines above do what you want, you could just add them to /etc/rc.local (quick and dirty way - and don't put the 'sudo' part in there) although I'm sure there are more proper ways of doing that... :rolleyes:  I haven't set this up in Ubuntu yet - still have Slackware on the firewall.

---

### Post by spasticteapot on 2007-01-31
> **RandomJoe said:**
> You do NOT need to set up a DHCP server.  Keep your static IPs, they are fine!


Whew!

(I've had about twelve people tell me twelve different ways to do this, all of which, other than this one, were headache-inducing.)

> **RandomJoe said:**
> 
Does this PC have Inet connectivity already?  As in, you have the wireless card set up and connected, can browse?  If so, then all you need to do is set up IP forwarding and NAT/masquerade on that PC and the others should suddenly, magically have access.  (You will also have to tell them to use that PC's IP as the Gateway.)

When they say you can't use static IPs, that just means a static IP won't work when connecting directly to their wireless system.  Since you are hiding all your other machines behind the NAT, their system will never see those static IPs.


That's what I was going for. The wifi card in the "server" works 100%. 

> **RandomJoe said:**
> 
Okay, it might help to say how to set up the forwarding bit.  [This]("https://help.ubuntu.com/community/InternetConnectionSharing") is the first Ubuntu Howto I found in a quick search - it's rather terse, and doesn't completely apply to your situation since you already have most of what you want/need set up.  The really short version is you need the two lines under 'configure NAT on iptables', something like:
```
sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```
This assumes wlan0 is the name of the wireless interface you want everything to go out of.


All righty then! I think that this should work fine - I'm not sure if the wifi card is eth1 or wlan0 (Edgy seems a bit odd that way), but I should'nt have any trouble.


And now, for an unrelated question:

Would I have any trouble if I were to also use this machine for a Samba file server?

---

### Post by RandomJoe on 2007-01-31
No, you shouldn't have any trouble.  It would be set up in the normal way.  The only thing is, as you start adding other services on that machine you will want to make sure you get the iptables firewall set up correctly, otherwise, other people on the wireless system next door could access your services.

That's why I said that he masquerade rule is really the quickie-easy way to get it going, but not really the full story.  If you search for 'iptables' you will find all kinds of howtos and other pages discussing setting up a proper firewall.  Some will make your head spin! ;)

I believe the program I've heard people here suggest for making iptables a little easier to work with is 'firestarter' in the Universe repository.  But I also read a thread that mentions it only works after you have logged in.  My preference is to have an iptables script that runs on bootup, so it's present from the get-go.  I would attach mine as an example, but it's unnecessarily complex for your application...

However you do it, at least to start with what you want is to deny any connections coming in on the wireless connection.  That will keep outsiders from seeing / accessing anything on your system.

---

### Post by spasticteapot on 2007-02-01
> **RandomJoe said:**
> No, you shouldn't have any trouble.  It would be set up in the normal way.  The only thing is, as you start adding other services on that machine you will want to make sure you get the iptables firewall set up correctly, otherwise, other people on the wireless system next door could access your services.

That's why I said that he masquerade rule is really the quickie-easy way to get it going, but not really the full story.  If you search for 'iptables' you will find all kinds of howtos and other pages discussing setting up a proper firewall.  Some will make your head spin! ;)

I believe the program I've heard people here suggest for making iptables a little easier to work with is 'firestarter' in the Universe repository.  But I also read a thread that mentions it only works after you have logged in.  My preference is to have an iptables script that runs on bootup, so it's present from the get-go.  I would attach mine as an example, but it's unnecessarily complex for your application...

However you do it, at least to start with what you want is to deny any connections coming in on the wireless connection.  That will keep outsiders from seeing / accessing anything on your system.

Woah...thanks for warning me! That could have been a disaster!

I think I'll try turning a PC into a combination firewall/NAT, and make the file server seperate. I have a junky old P1 machine that should do the job - Ubuntu runs very well on a 486 if you turn off X-windows, I've found.

---

### Post by RandomJoe on 2007-02-01
That would be my recommendation.  I have an old PC as my firewall/router as well.  It does nothing but that function, and a few related - DHCP for my internal LANs (I have two - wired and wireless are physically separate), VPN access from outside, proxying and DNS.

I did think of one other thing you will need - the internal computers will need a DNS server.  You have a couple of choices.  

If you have just a few non-changing computers internally, you can just put those IPs and their hostnames in /etc/hosts for internal resolution (or just use IP addresses) and put whatever DNS server the wireless provider gives you into /etc/resolv.conf on each machine.  (Check the resolv.conf file on the gateway machine once it is connected.)

If you would like to have a little more flexibility in internal naming, perhaps want to wind up using DHCP, or would just like to have a bit more control over DNS queries you can set up 'dnsmasq'.  I use that on my system.  It's much easier to set up than the more full-blown systems, and works very well for a small network.

---

### Post by chili555 on 2007-02-01
> However, a bridge might not work so well - the wireless source is unencrypted and set up for plain DHCP.

A bridge will work static or DHCP and encrypted or not. This is posted for others who may be following this saga and considering a bridge.

---

### Post by spasticteapot on 2007-02-02
The network is now working. Marvellously - I get 130KB/s download speeds, just as good as I get from my laptop. (I'd donate some money to Ubuntu if I actually had any to spend.)

Anyway, I now need to do the following:
1. Shared linux/Windows file server. Samba won't actually run, or I'm running it wrong. All IPs are static, at least.
2. Shared Linux/Windows printer. It's an ethernet-connected HP LaserJet, so this should not be  too hard. 
3. I'm moving the wireless card to its own machine soon. I was thinking of using multiple wireless cards - one for each AP - and sharing the load if possible.

Also, I would be very happy if someone could explain how I could use Telenet to access the servers over the network, if only at the command-line.

---

### Post by Jimmey on 2007-02-02
For Samba, I can suggest going to [http://help.ubuntu.com/community](http://help.ubuntu.com/community) and searching for Samba.

For telnet, I think your best best in ssh. You can install an SSH server really quite easily (> sudo apt-get install open-ssh), and then once that's installed (provided the computer's firewall permits it), you can connect to that machine using the command > ssh 192.168.5.X.

You might want to try searching for "SSH" while you're at that website, too, you'll want to make sure that your network is totally secured before you install it.

---

### Post by chili555 on 2007-02-02
You may find it a bit easier to specify the user you want to log in as, just in case you are not a user on all these machines. 

```
chili@LAPTOP:~$ ssh -l sarah 192.168.5.5
```

---

### Post by dsegarra on 2007-02-02
spasticteapot

I have your same setup and cant get it to work. I am using a router in between. Just two computers. Would you mind sharing how you get it to work?. I found RandomJoe post the most useful, straight to the point but still cant get the connection to work. I can ping from/to both computers.


Thanks

dan

---

### Post by dsegarra on 2007-02-02
which DNS server should I use for the clients? the one provided automatically in the wlan0 card? or the IP of that wlan0 card?..Kinda confused here.


thanks

D.

---

### Post by RandomJoe on 2007-02-03
dsegarra, if you don't need DNS for your internal LAN (you are just going to use IPs between them) then you can just use whatever IP the ISP provides you for a DNS server.  If you have a machine connecting successfully to the Internet directly, while it is connected check what is in /etc/resolv.conf - it should list one or more 'nameserver' lines.  Put those into the /etc/resolv.conf on the other internal machines and they will all go to that/those IPs for DNS requests.

This does _not_ work if you are using DHCP, as the DHCP client on each computer will overwrite /etc/resolv.conf every time it gets an IP.  It will replace the nameserver lines with whatever the DHCP server tells it is the "proper" DNS server.  I'm not sure how to turn this behavior off - on Slackware, there's a commandline switch for dhcpcd but dhclient (what Ubuntu uses) doesn't appear to have that option.

If you want/need DNS services for your own LAN, and set up something like dnsmasq, then the internal machines would get the internal IP address of the machine running dnsmasq as a DNS server.  They would send queries there, and dnsmasq would either answer back or forward them out to the "real" DNS server for the Internet (based on settings in the dnsmasq.conf file).

---

### Post by dsegarra on 2007-02-03
thanks RandomJoe, will try that. Thanks for the insights!..


Dan.

---

### Post by RandomJoe on 2007-02-03
> **spasticteapot said:**
> 1. Shared linux/Windows file server. Samba won't actually run, or I'm running it wrong. All IPs are static, at least.
I've not run Samba here, I "don't do Windows"... :D  But if you've installed it correctly (through Synaptic, search for 'samba') then System -> Administration -> Shared Folders ought to let you set things up.  If neither Samba or NFS is installed, going there should prompt you to install one or the other.  Check the boxes and hit Apply.

> 2. Shared Linux/Windows printer. It's an ethernet-connected HP LaserJet, so this should not be  too hard.
This depends on what exactly you have in mind.  The easy way - and with just a few computers probably fine - would be to set up each machine to print directly to the printer.  This is how I do things here.  On Ubuntu, I just went System -> Administration -> Printing and added a new printer.  You will need to know some info about how the printer presents itself.

On mine (actually using a "print server" to which the printer is connected) I select UNIX printer (LPD), plug in the IP of the printer for host, and select the appropriate driver.  Some can be a little more involved.

The other option is to have one machine act as the print spooler, so that everyone dumps print jobs there and it queues them up to send to the printer as it becomes available.  In that case, set up printing on that machine as above, then (depending on how you do it) use either Samba or CUPS printer on each client to send the jobs to that server.  If you are also printing from Windows, I suspect setting up a Samba printer would be best.  I can't give a lot more info on this, as it's been a LONG time since I last did it...
 
> 3. I'm moving the wireless card to its own machine soon. I was thinking of using multiple wireless cards - one for each AP - and sharing the load if possible.
Do you have multiple providers, or are all these APs connected to the same network on the other end?  While it's possible to distribute load across multiple providers, I think the best ways of doing that generally require support on both ends.  If they are all connected to the same network segment on the other end anyway, you probably won't see much improvement.

How fast is the coffee shop's connection?  Most places aren't going to have a huge pipe - you are probably getting about as much as you can get anyway.

> Also, I would be very happy if someone could explain how I could use Telenet to access the servers over the network, if only at the command-line.
As others have said, don't use telnet use SSH.  It's more secure and is easy to set up!  It also allows you to do port forwarding and a host of other more advanced things that can allow you - among other things - to run GUI apps/utils on the server, with the display appearing on your system.  But that's a fair bit more involved, and I don't do it enough to remember the commands right off... ;)

---

### Post by dsegarra on 2007-02-03
I dont know if this has happened to any of you but I was able to ping from/to both machines so I was suspicious as to why it was not working. After a few hours, I found out the last detail to my connection. It was dumb. Under firefox connection settings, I had to enable automatically detect proxy and it worked!!..thanks guys for such big help. 



Dan

---

### Post by Lil_Eagle on 2007-02-05
> This does not work if you are using DHCP, as the DHCP client on each computer will overwrite /etc/resolv.conf every time it gets an IP. It will replace the nameserver lines with whatever the DHCP server tells it is the "proper" DNS server. I'm not sure how to turn this behavior off - on Slackware, there's a commandline switch for dhcpcd but dhclient (what Ubuntu uses) doesn't appear to have that option.

You can override the dchp settings two ways.  In /etc/dhcp3/dhclient.conf you'll see an example for the prepend-name-servers parameter, which will put the server defined there BEFORE the information obtained from the DHCP server.  You can also modify the request itself and not request DNS information from from the server.  Look at that file, it's well commented.

---

