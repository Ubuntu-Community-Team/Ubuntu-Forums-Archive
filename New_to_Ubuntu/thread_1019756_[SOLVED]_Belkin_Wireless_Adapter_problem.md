---
title: "[SOLVED] Belkin Wireless Adapter problem"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by newmans on 2008-12-23
Belkin wireless usb wont connect to network until 10 minutes after start-up.
Any advice on a wireless interface or any driver solutions?

Info: Belkin High-speed mode wireless G USB network adapter,
Model number: F5D7051

Thanks if anyone can help!

---

### Post by sanderella on 2008-12-23
What computer are you using? Have you had this problem previous to using a Belkin?

---

### Post by newmans on 2008-12-23
Hi, yea i'm using a dell dimension 4600, and no i havent had this problem with a belkin before with the delay.

---

### Post by negev on 2008-12-23
maybe the packets get scrambled?

---

### Post by anewguy on 2008-12-23
A few questions:

- what version of ubuntu are you running?

- did this same adapter work okay before, or is it a new adapter for you?

- did you have/do any updates recently?

- what driver are you using?

- do you have any special apps, etc., starting when you log on?


I have a Belkin F5D7050 (as best as my eyes can make out the little tiny print on it).  It has always run in 7.10, 8.04 and now 8.10 just fine with a driver that is automatically installed for it.  

Dave :)

---

### Post by newmans on 2008-12-23
Hi dave, here are some answers to your questions
-I'm running 8.10 at the moment
-The same adapter worked fine using windows XP (I am using a BT router, which are not the best things ever)
-I have only installed ubuntu in the last couple of days, and even though it does work eventually it takes atleast 10 minutes to see the usb adapter. I updated the system as soon as I installed it.
-I'm not sure what driver I am using, is there a easy way to find out?
-I'm pretty sure I don't have any network apps, or any special apps when I start up.

I thought it was the driver, but it seems weird that the problem just takes time, but I would like to sort this problem out before I get used to waiting every day, cheers

---

### Post by anewguy on 2008-12-23
try lshw -C network in a terminal window and post that back here as well.

It may be that the driver it apparently found isn't working the best for you.  If you have or can download the Windows XP driver for it, I can walk you through ndiswrapper and that driver to see if it helps any.

Not sure why it doesn't work for 10 minutes and then works.  Does it work fine after 10 minutes, or does it seem slow, etc.?

Dave :)

---

### Post by newmans on 2008-12-23
alrite dave, heres the info you asked for:

*-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:59:dd:bf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:c6:47:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device ip=192.168.1.64 multicast=yes wireless=IEEE802.11bg

I'm completely new to this, but 2005? seems pretty old ha, Yeah getting of the windows driver should be no problem, so if there seems to be nothing out of place in the above I can easily get it, if you can guide me through the process, cheers tim

---

### Post by anewguy on 2008-12-23
> **newmans said:**
> alrite dave, heres the info you asked for:

*-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:59:dd:bf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:c6:47:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device ip=192.168.1.64 multicast=yes wireless=IEEE802.11bg

I'm completely new to this, but 2005? seems pretty old ha, Yeah getting of the windows driver should be no problem, so if there seems to be nothing out of place in the above I can easily get it, if you can guide me through the process, cheers tim

Hummmm, my adapter doesn't even show a driver, so I'm curious yet it works great.  There must be a difference between your model and mine.

To try working with ndiswrapper, look at the wireless section in this how-to I did for a laptop, but keep in mind a couple of things:

- you aren't working with anything bcm*, so for now don't blacklist anything

- remember to substitute you driver file name wherever you see bcmxxxx

- you may also need to edit (as sudo) the /etc/modules file:

sudo gedit /etc/modules

go to end of file

add a new line that says:

ndiswrapper

click save, then exit the editor.  When you've done everything, reboot and see if your wireless works or not.

If you need any help along the way, just post back.  I'll be off/on occaisionally tonight so I'll check to see how you're doing.

Dave :)

---

### Post by abn91c on 2008-12-23
check you network settings and firewall if you have firestarter in case you setup some type of custom configuration, I also have the same belkin adapter on a dimension gx240 and kubuntu 8.10, it worked out of the box for me also on this one also with ubuntu on another old PC that I had.

---

### Post by newmans on 2008-12-24
hi Dave, is there a link for the how-to for the ndiswrapper? I'm new to terminal commands, so I cant figure it out from just what you say. I've downloaded ndiswrapper but still unsure on how to use it in conjunction with the windows driver(or even if I've installed it!ha), thanks for the continuing help!!

---

### Post by newmans on 2008-12-24
just remembered, I'm running ubuntu through the wubi software, I'm not sure if this makes a difference or not, tried running lsusb and so far nothing has come up, even though I have several usb attachments...?

---

### Post by anewguy on 2008-12-24
I haven't used wubi, so I can't really comment on what it can or cannot do or what it will or will not allow.  I suspect that since you see none of your devices with lsusb (have you tried "sudo lsusb" ?) that this may mean you won't be able to do it.  If you intend to keep using wubi, I would suggest you mark this thread as "solved" and open a new one with a title like "wubi - USB wireless not working" and go from there - it would get a little more attention from those more familiar with wubi.

Dave :)

---

### Post by abn91c on 2008-12-24
if you used the network tools set up that may mess up you belkin detection
here is what my /etc/network/interfaces file contains
auto lo
iface lo inet loopback
and for comparison here is what i get with lshw -C network

 *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:b2:4c:97
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:5a:bf:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192xxx.xxx.xxx multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ee:a1:6c:69:77:a7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
                            [COLOR="Red"]Note I Erased my IP on purpose for the posting[/COLOR]

---

### Post by abn91c on 2008-12-24
I would recommend removing anything ndiswrapper you installed, clear any setting you used on the system tools and edit as root you [COLOR="Blue"]/etc/network interface [/COLOR] file to look like mine. reboot and check if ubuntu autodetects then since it did for me on an old PC100 motherboard and when I upgraded to a (new for me) dell GX240 from the flea market :)
One more thing if it has a PCI networkcard installed try removing it also.

---

### Post by anewguy on 2008-12-24
> **abn91c said:**
> I would recommend removing anything ndiswrapper you installed, clear any setting you used on the system tools and edit as root you [COLOR="Blue"]/etc/network interface [/COLOR] file to look like mine. reboot and check if ubuntu autodetects then since it did for me on an old PC100 motherboard and when I upgraded to a (new for me) dell GX240 from the flea market :)
One more thing if it has a PCI networkcard installed try removing it also.


Just curious - are you running wubi like the poster?

dave :)

---

### Post by abn91c on 2008-12-24
> **anewguy said:**
> Just curious - are you running wubi like the poster?

dave :)
not on my gx240 but my inspiron 1000 has wubi and it works there as well.

---

### Post by anewguy on 2008-12-25
> **abn91c said:**
> not on my gx240 but my inspiron 1000 has wubi and it works there as well.

Is your Inspiron using the same wireless USB adapter as the poster?

The reason I'm asking is that if you have a different wireless adapter than the poster, you could be using "native" drivers in Linux.  It appears the poster is not that lucky - hence why I recommended he try ndiswrapper.  Ndiswrapper is not a no-no, but rather a very important tool used to help get wireless working for countless people.  My concern is that since he is using wubi and not seeing his usb devices that it may be another problem causing the lack of visibility of the usb devices and hence his wireless wouldn't be found since it's usb.

I'm going to do searches on yahoo and google for ubuntu and his wireless adapter to see how others have gotten it to work.  As I mentioned, mine is a slightly different model number, so I may be using a completely different chipset (and hence driver) than the poster.

If you are using wubi and have the exact same model of usb wireless adapter, then perhaps we can work together to solve the posters problem - and I get to learn in the process to boot.

BTW - the poster should look at these threads and more:

[http://ubuntuforums.org/showthread.php?t=540942]("http://ubuntuforums.org/showthread.php?t=540942")

[http://thehardsell.wordpress.com/2007/11/08/kubuntu-and-the-belkin-f5d7051-a-saga/]("http://thehardsell.wordpress.com/2007/11/08/kubuntu-and-the-belkin-f5d7051-a-saga/")

[http://linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded]("http://linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded")

And many others.  The point is the default driver either doesn't work well or doesn't work at all depending on the version (and hence chipset) of the Belkin F5D7051 - it may be the broadcom chipset, in which case sometimes the default driver DOES cause problems for some people.  The solution in this case is to blacklist the current driver (bcm43xx), then install ndiswrapper and use the Windows driver.  This is pretty standard on the bcm43xx chipsets.

So, newmans - I need to know the 3 packages you installed - I assume ndisgtk, ndiswrapper and the ndiswrapper utils?  What version number of Ubuntu are you running (7.10, 8.04, 8.10, etc.)?  From there I can guide you through some things to try to see if we can get it working better for you.  Be sure to have the Windows driver (not Vista though) for your adapter available.  It may not work on the first try or 2, but we can sure try.  I've used ndiswrapper countless times with some ralink and lots f broadcom chipsets to get wireless working.

Dave :)

---

