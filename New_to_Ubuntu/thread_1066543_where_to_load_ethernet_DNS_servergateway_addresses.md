---
title: "where to load ethernet DNS server\gateway addresses ??"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-02-11
Where do you enter your server addressing for a wired ethernet connection?

somewhere my ip address, gateway, and DNS server information needs to be added.

when ubuntu boots up the os starts looking for addressing (?) to the wired connection but never finds it and disconnects the network connection.

ed

---

### Post by ozark_hillbilly on 2009-02-11
under network connections i found IPv4 settings...
i went with method: manual
in this area i can enter all the addressing, gateway, etc.

BUt when I fill in all the data fields the OK block is at half intensity and will not let me select it. 

am i in the right area to configure this ethernet connection?

Dazed and More Confused,

Ed

---

### Post by ozark_hillbilly on 2009-02-11
more progress made:

by configuring auto eth0 i can now ping to my gateway but neither DNS server. For some reason the netmask value reverts to 24 even though i enter 255.255.255.0 in the data field. My address and gateway values remain unchanged.

Is this causing my inability to ping the DNS servers?

Ed

---

### Post by ozark_hillbilly on 2009-02-11
googled netmask 24

says 255.255.255.0 = 24

still don't know why ping is unsuccessful to DNS servers.....

---

### Post by highowl on 2009-02-12
Okay hopefully I can help you out a bit.

First off I think I had the same problem as you and it took me damn near half an hour to figure out exactly what was wrong.  (Not new to linux or networking - but rather new to Ubuntu) 

As soon as I stopped trying to use the graphic network configuration tool and decided to use the good ol' terminal, I figured out what the issue was in no time.  

So you're going to want to open up the terminal and type:

```

sudo gedit /etc/network/interfaces

```

This should open up a text editor with your basic network info in it. 

Make sure it reads something like this (and remember to use your own network settings)

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1

```

address - will be the IP address you want statically assigned to your computer

netmask - will be 255.255.255.0 unless you're doing something fancy (but i'm guessing your not based on your post - correct me if i'm wrong)

gateway - would be the IP address of your router (usually 192.168.1.1 or 192.168.0.1 on home networks)

Once you make sure all of that is correct - save it and close the text editor.  You should now be back at the terminal.

Now you're going to want to set up your DNS - at the prompt type:

```
sudo gedit /etc/resolv.conf
```

This will open another text editor with your dns servers listed.

If you would like to use the DNS servers your router is using change resolve.conf to something like this:

```
nameserver 192.168.1.1
```

(that's assuming your router's IP is 192.168.1.1)

If you would like to use your own DNS servers or some other DNS server not provided by your ISP just replace the "192.168.1.1" with the IP of the DNS server.

Once you have your resolv.conf how you want it - save it and exit - you should now be back at the prompt again.

Now in the terminal type: 

```
sudo gedit /etc/hosts
```

make sure the IP address next to your hostname matches the IP you set in /etc/network/interfaces

It should look something like this:

```

127.0.0.1 loopback
192.168.1.50 YourHostName

```

(The above is assuming your computer's name is "YourHostName" and your IP address assigned in /etc/network/interfaces is "192.168.1.50")

It will probably have a bunch of extra stuff at the end for IPv6 networking but that can be ignored.  

Once you have /etc/hosts configured to your liking - save it and close it.  This should land you back at the prompt.  

Now to finish it off type:

```

sudo ifconfig eth0 down
sudo ifconfig eth0 up

```

This will take the ethernet card offline and bring it back up again using the new information provided in the files you edited.  

Now, hopefully everything should be working smoothly for you.  

--------------------------------



P.S.  The netmask 255.255.255.0 is the same as 24 

The netmask separates the network bits from the host bits.  

255 being 11111111 in binary. 

11111111 is 8 bits.   

255.255.255.0 in binary is 11111111.11111111.11111111.00000000 - meaning 24 bits for the network and 8 bits for the address. (That's where the 24 comes from)  

Basically a netmask of 255.255.255.0 means that all IP addresses starting with the first 3 #'s (eg. 192.168.1.X) are on the same network and the last number (X) is the number unique to each machine.  

This is just a quick explanation - hope it helped - though it probably just confused you more lol.

---

