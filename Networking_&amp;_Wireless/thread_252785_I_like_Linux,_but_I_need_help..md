---
title: "I like Linux, but I need help."
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by keiyoushi on 2006-09-07
I recently installed Ubuntu 6.[whatever] on my Compaq Presario V3000.  The thing is, I'm not exactly computer savvy, but I follow instructions very well.

So.

I guess I can't connect to any networks, and since I'm not very good with internet support, be it wireless or LAN in general, I need some help.

If anyone could give me some really BASIC instructions that don't require much more than simple file searching in folders and such, that could help me connect to wireless networks and/or the LAN, that would be really great.

If not, that's cool too, but still, I'm in need of some help here.  And as I really like Ubuntu, for all the neat programs and the cool layout, I'd really like to keep using it more.

Anyone have any ideas?  Or rather, anyone wanna share?

Thanks.

---

### Post by jrb114 on 2006-09-07
Hi there,

It's easier for us all if you could give more info. But based on a quick google, you've got a newish (new?) laptop.

It's /far/ easier to start with the wired LAN. So that's what I'll set out here for now.

Assuming your laptop has the LAN cable plugged in, and the LEDs are up flashing (i.e. everything looks good), then getting an IP address should be quite simple (I'm hoping DHCP is enabled on whatever box your laptop is connected too).

Firstly, you need to open a terminal and type commands.

Go to Applications -> Accessories -> Terminal

Now, we need to check that your network card has been detected.

```

ifconfig

```

If you get something like 
```

eth0      Link encap:Ethernet  HWaddr 00:0C:6E:E4:44:97  
          inet addr:XXX.XXX.XXX.XXX  Bcast:XXX.XXX.XXX.XXX Mask:255.255.254.0
          inet6 addr: XXX:XXX::XXX::XX  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9172870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5521413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1609515440 (1.4 GiB)  TX bytes:2884865319 (2.6 GiB)
          Interrupt:201 Base address:0x9800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2457843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2457843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:818465798 (780.5 MiB)  TX bytes:818465798 (780.5 MiB)

```

Then we're in business. NB, there might also be something like wlan0 or ath0, that will be your wireless card, which we can deal with later.

There are two methods as I understand it, to get network cards and wireless cards up and running.

The simplest, if you've had success so far, if to type:

```

sudo dhclient eth0
[CODE]

Or whatever ethX appeared as output from the above command. This is asking your network card to get an IP address from the DHCP configured server/router/whatever. Hopefully this will work, and you will get and IP. 

If DHCP is not enabled, then this will be more complicated. You need to know your own IP settings and gateway etc, without more info you can't go any further. If this is the case, you will need to look inside /etc/network/interfaces, which is where all of the network cards are listed.

=======

I mentioned that there is another way to manage network interfaces without using the terminal.

To do this you need to use network manager.

From a terminal:

[CODE]
sudo apt-get install network-manager network-manager-gnome
[CODE]
(Substitute network-manager-kde for n-m-gnome if you're using kubuntu.)

You now need to disable control of your network interfaces by the system (at least I think this is what it this does).

Just to be sure, do an 

[CODE]
sudo ifdown --all

```

We have just stopped all network interfaces.

Now, comment (add a # to the beginning of each line) all of the interfaces in /etc/network/interfaces

*WARNING*. DO *NOT* comment the loopback interface, that is the one that begins lo.

```

sudo gedit /etc/network/interfaces

```

*WARNING*. DO *NOT* comment the loopback interface, that is the one that begins lo.

Now we want to enable network manager's applet on log in to gnome.

From the System menu -> Preferences -> Sessions

Choose the "Startup Programs" tab

And check that 

```

nm-applet --sm-disable

```
Is listed.

If not, add it.

Now, log out of gnome and back in.

There should now be an information widget in the top right (or in your notification area) of your toolbar.

You can then configure your wired LAN (and your wireless one) through this.

Hope this helps, let me know if you need anymore.

James

---

### Post by twade on 2006-09-08
I am also a newbie with that same laptop, which I'm currently trying to get to run smoothly.  Search for posts by reedatschool.  He has a similar set up and claims to have most of the components working, with somewhat cryptic how to info.  I'll post more info as I get more to work.

For the LAN, in windows (while successfully linked to the internet) go to start -> run and type in cmd.  Make note of the output from
code:
ipconfig /all

in particular, note the the DNS servers.

In linux, you may have to do some menu browsing.  I think you want System -> Administration -> Networking, but it may be one of the other Networking modules in these menus. (I don't have linux in front of me at the moment) In any case, try to find where to enter these DNS addresses.  After doing this, my LAN and internet worked.

---

