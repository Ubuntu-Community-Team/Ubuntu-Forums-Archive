---
title: "Fresh blood"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by NZMatt on 2009-05-26
Hey everyone

I'm completely new to Ubuntu and have so far been very impressed. I only installed it yesterday but it seems very user friendly.

My issue at the moment is that I'm unable to connect using wireless.

[IMG]file:///tmp/moz-screenshot-2.jpg[/IMG]If I go to System / Preferences / Network Connections, and then click on Wireless, nothing appear in my connections Window - it doesn't seem to be detecting the router.

[IMG]http://i40.tinypic.com/28s4y9l.png[/IMG]

I'm on an nc4400 laptop with an Intel 

Can anyone help?

Thanks very much.

Matt

---

### Post by bruno9779 on 2009-05-26
have a look here:

[http://www.linlap.com/wiki/hewlett-packard+nc4400](http://www.linlap.com/wiki/hewlett-packard+nc4400)

it is a compatibility checklist for your box with linux.

"Use the ipw3945 module" is what is said under "wifi"

post back if you need help setting ipw3945 up

---

### Post by reg4c on 2009-05-26
In the Network Connections dialog you will only see the setup connections, such as ones with a WEP where you have succesfully connected

To actually connect to a network you should click on the network icon in the status area on your panel. It will either be an icon like the one on the phone showing you the signal with a little red X in the corner or two computers. There will be a list of all the networks that the wireless card has detected.

Try that, and if you cannot find it, or there are no networks then post back...

---

### Post by NZMatt on 2009-05-26
Thanks for the info guys.

I'm really very new to this. I did actually already find the stuff on the Intel  PRO/Wireless 3945ABG adapter, but got a bit lost trying to find it.

As for the network icon in the status area - I don't have one. Here's a screen shot of my whole screen to show you what I do have:

[IMG]http://i40.tinypic.com/2liy8uu.png[/IMG]

Again, thanks for help - it is truly appreciated.

---

### Post by 3rdalbum on 2009-05-26
Isn't it those two screens next to the Bluetooth logo? Click that and you should see what networks are available.

---

### Post by NZMatt on 2009-05-26
Oops! Sorry!

That just shows me "Wired connection 1", which is what I;m using now, and a menu for VPN connections. Nothing about wireless.

---

### Post by NZMatt on 2009-05-26
Incidentally, this is the only info I can find on installing the ipw3945abg driver:

[http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL)

I've got to say - it looks like a total nightmare for a beginner! There must be an easier way!

[-o<

---

### Post by tom56 on 2009-05-26
Try System->Administration->Hardware Drivers

---

### Post by NZMatt on 2009-05-26
That brings up the following, but nothing about wireless device drivers.

[IMG]http://i39.tinypic.com/npm1l3.png[/IMG]

I suspect I need to install a driver, but I haven't a clue how to go about it. I've downloaded the driver but there doesn't appear to be an option anywhere to install it. Can anyone help with this?

Cheers

Matt

---

### Post by NZMatt on 2009-05-27
Hi again guys. Just a bump to see if anyone else can lend a hand. I've got to say, this is immensely frustrating. It seems the only way to install the driver is to type a bucketload of commands that I don't understand into a command prompt.
 
I've tried the ndiswrapper and it doesn't work. I;ve also tried downloading the package mentioned int he beginner's guide, but that hasn't worked either.
 
Any takers?

---

### Post by cariboo on 2009-05-27
Your network device should be supported out of the box, could you open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

The above command will print out a listing of your network devices, including whether a driver si loaded. Please paste the output in your next post.

---

### Post by zeroseven0183 on 2009-05-27
Switch on the wireless device?

I believe it's on the left side.

Oh, sorry but that really sound stupid. How about you give us another shot of what's in the list when you click the network icon.

---

### Post by NZMatt on 2009-05-28
> **cariboo907 said:**
> Your network device should be supported out of the box, could you open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```The above command will print out a listing of your network devices, including whether a driver si loaded. Please paste the output in your next post.

Sure. Thanks for the help! I got the following:

  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d4:42:f8:bb
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5753m-v3.56 ip=10.1.1.3 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:4e:f0:33:52:03
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Make any sense?

---

### Post by NZMatt on 2009-05-28
> **zeroseven0183 said:**
> Switch on the wireless device?
 
I believe it's on the left side.
 
Oh, sorry but that really sound stupid. How about you give us another shot of what's in the list when you click the network icon.
 
Nah - I tried that. I wish it were that simple!
 
All I see when I click the network icon is:
 
Wired network (greyed out)
Wired connection 1 (checked)
VPN connections menu

---

### Post by NZMatt on 2009-05-28
Well, I'm online, wirelessly.
 
I thought I'd try the last LTS Ubuntu release - 8.04 - and straight after install I'm online. Looks like the 9.04 release is not too great for this particular piece of hardware. I'm gonna stick with Hardy Heron for awhile, just so I have a chance to get used to Linux.
 
Cheers for the help, guys.

---

### Post by Chalfont on 2009-05-28
Isn't that a bit retrograde?

Maybe it's my Windows upbringing, but I would expect the newer version to be better and work with more current hardware (and it doesn't sound like our NZ friend there has awfully old hardware).

Currently the jury's still out for me definitely on this whole Linux thing - I was advised to go for Ubuntu because it was more user friendly and had all the sophisticated security etc that Windows didn't have, and yet my experience (and NZ's) so far seems to point to something much less.

---

### Post by NZMatt on 2009-05-28
> **Chalfont said:**
> Isn't that a bit retrograde?

Maybe it's my Windows upbringing, but I would expect the newer version to be better and work with more current hardware (and it doesn't sound like our NZ friend there has awfully old hardware).

Currently the jury's still out for me definitely on this whole Linux thing - I was advised to go for Ubuntu because it was more user friendly and had all the sophisticated security etc that Windows didn't have, and yet my experience (and NZ's) so far seems to point to something much less.

I can see what you're saying. It's taken me two days to deal with an issue that would be dealt with relatively quickly in Windows XP and the only solution in the end was to downgrade to an older OS.

However, I also experienced terrible problems when I first installed Vista and ended up jacking it in and going back to XP. The difference between Ubuntu and Windows is that Ubuntu is free! Microsoft actually had the gall to charge for that piece of crap!

Also, Ubuntu make no bones out of the fact that their 8.04 is a more reliable long term release and 9.04 is an interim release - it's obvious which one will be more reliable.

---

