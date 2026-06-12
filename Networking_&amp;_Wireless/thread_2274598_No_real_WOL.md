---
title: "No real WOL?"
date: 2015-04-21
forum: Networking &amp; Wireless
---

### Post by pingaan on 2015-04-21
Hi,

Please move this topic if you don't think it should be under Networking..

I'm guessing this is hardware related but I'll give it a go anyway!

This is the line I'm using for WOL: 
```
ethtool -s eth0 wol g
```

This works fine when suspending/hibernating the computer but not when shutting down..
Anyone who can think of any reasons why?

Regards.

---

### Post by user_of_gnomes on 2015-04-21
You're having trouble starting the computer up when it has been shut down? Does it work under another operating system?

The technology is pretty finicky, it depends on a lot of factors to work right.

---

### Post by pingaan on 2015-04-21
I have only one copy of Ubuntu installed. The bios WOL options looks like this: [img]http://lh3.ggpht.com/_AKAirBqiu8U/SqoW69BNPcI/AAAAAAAAAHg/NCr3nLtIwIU/s800/P6T-NIC-WOL4.JPG[/img]

---

### Post by matt_symes on 2015-04-21
Hi

I'm using WOL on one of my backup PC's. I run a script on this laptop and it automatically wakes the backup computer when this laptop is on my local network, rsyncs over ssh and shuts the backup computer down when it is finished.

Here's the steps i used to get it working.

Enable WOL in the BIOS.

On the server to be woken.

```
sudo apt-get install ethtool
```

See if a WOL magic packet can be sent to the servers network card. Below eth0 is the name of the network card.

```
sudo ethtool eth0
```

Below is an example for my laptop and not my backup server.

```

matthew-laptop:/home/matthew:1 % sudo ethtool eth2 | grep Wake
        **Supports Wake-on: puag**
        **Wake-on: g**
matthew-laptop:/home/matthew:1 %
```

You're looking for a **g** or a **d** where i have emboldened above.

If that all looks good, ensure WOL magic packet is configured for the card.

```
sudo ethtool -s eth0 wol g
```

Again change eth0 for your network card.

Now make a note of the MAC address for the network adapter on the server.

```
ifconfig eth0
```

You're looking for something like **HWaddr 00:40:45:2g:a0:f5.**

Now shutdown the server.

On the client machine install wakeonlan

```
sudo apt-get install wakeonlan
```

Then send the magic packet to the server using the MAC address obtained earlier.

```
wakeonlan 00:40:45:2g:a0:f5
```

Change the MAC address above as required.

That was how i got it working between this laptop and my backup server.

Kind regards

---

### Post by chili555 on 2015-04-21
Thanks, Matt! IMO, an excellent explanation. Bookmarked for future plagiarism!

---

### Post by pingaan on 2015-04-21
@matt_symes: Thanks, but it's of no help. The tutorial is great and all but that's basicly how I came up with the ethtool line and of course I know the macadress. 
My issue is that when I'm trying to wake it nothing happens unless it's on hibernate/suspend.

---

### Post by matt_symes on 2015-04-21
Hi

> This works fine when suspending/hibernating the computer but not when shutting down..
Anyone who can think of any reasons why?

Is your Ethernet card a PCI or PCIe card ?

If it's PCI and not PCIe then enable Power on by PCI in your BIOS.

Also does the BIOS battery still have charge ? When you power off, is it a full power off or a soft power off ?

BTW: Can you wake the machine using rtcwake if you enable Power on by RTC in the BIOS ? It's not the same as WOL but it that does not work as well then that may point to something.

After enabling Power on by RTC in the BIOS, boot into Ubuntu, open a terminal and type

```
sudo rtcwake -m off -s 180
```

Then go and get a drink for 3 minutes then see if it wakes up as well.

Kind regards

---

### Post by pingaan on 2015-04-21
I found the issue myself.. For some reason the app I use on my mobile device decided capital letters in the mac address was a good idea! 

........how ever, this actually brings up more irrelevant questions; how in hell does it wake up the comp when being in hibernate when the mac is wrong? Maybe it goes for the ip number in that case?

Thanks for taking your time to help me out! <3

Best regards.

---

### Post by matt_symes on 2015-04-21
Hi

> **chili555 said:**
> Thanks, Matt! IMO, an excellent explanation. Bookmarked for future plagiarism!

Thanks Chili. I'm sure I plagiarised it from elsewhere :)

> **pingaan said:**
> I found the issue myself.. For some reason the app I use on my mobile device decided capital letters in the mac address was a good idea! 

........how ever, this actually brings up more irrelevant questions; how in hell does it wake up the comp when being in hibernate when the mac is wrong? Maybe it goes for the ip number in that case?

Thanks for taking your time to help me out! <3

Best regards.

So you got it working ? Excellent !

If you fancy marking this thread as [SOLVED] that would be great.

Kind regards

---

### Post by pingaan on 2015-04-22
Yea, sorry.. Done!

---

