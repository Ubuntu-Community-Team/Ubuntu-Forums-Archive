---
title: "NDISWrapper catch-22"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by Runiko on 2008-01-05
Alright, lets start with this:

I'm trying to get wireless working on my Everex Stepnote NC1510, which has a Marvell Libertas 88w8335 mrv8k card. To do so I need NDISwrapper.

[FRUSTRATION] When I look for places to get NDISwrapper, everyone says "use apt-get". How the @#$% am I supposed to use apt-get if I need ndiswrapper to connect to the internet?! :mad: I'm using the windows side of the dual-boot right now. [/FRUSTRATION]

Does anyone know where I can get a .deb or other ready-to-go package of ndiswrapper for 7.04?

Many thanks! :)
   -Runiko

---

### Post by macaholic on 2008-01-05
When I first started using linux I had the same exact problem, no wireless, and couldn't get ethernet access. If i remember correctly, you can just download [this package]("http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9") and [this package]("http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common") from another computer put it on a usb disk and then install it under ubuntu, and I think the dependencies are installed off the cd. Hope this helps.

---

### Post by kevdog on 2008-01-05
Perhaps this will clear some things up for you:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by Runiko on 2008-01-06
Alright, that really pushed me in the right direction! Thanks a lot!

BUT!

I still have a problem... :(

What I have right now: a working wireless card, with the correct driver and ndiswrapper functioning without any complaint.

I can ping my wireless router. I can access it's HTML config menu. I thought I was good to go. But then I tried to surf over to google.com. The page was unavailable. I am unable to ping anything "outside" of my local area network. Not even the DNS servers that show up under the network-manager respond to pings. What can I do??

Thanks in advance!

---

### Post by kevdog on 2008-01-06
Its either a problem with routing the default gateway or your dns servers.

Can you post 
route -n

Also can you connect to a website by IP address rather than name?
Googles IP address is: 64.233.167.99

So can you
[http://64.233.167.99](http://64.233.167.99)

---

### Post by Runiko on 2008-01-06
This... is very odd.

I am posting now from inside ubuntu (rock on! :guitar:)

But I am very confused about how I did it. At first, I was following someone's advice that it might be a bug some people experience when using network-manager in 7.04, so I uninstalled network-manager and replaced it with Wicd. THAT didn't work at all (broke even the pinging of the router), so I uninstalled Wicd too. So here I am right now without network-manager or Wicd, and the computer is connecting just fine. :confused:

Well, I'm here now. Welcome to the tubes, me!

Thanks for your help!
-Runiko

---

### Post by kevdog on 2008-01-06
Something tells me you will be back!

---

### Post by Nrbelex on 2008-01-07
> **Runiko said:**
> So here I am right now without network-manager or Wicd, and the computer is connecting just fine. :confused:

hehe, just don't ever restart! Seriously though, you'll probably have to experiment to figure out which one works best for you - wicd or the standard manager.

~ Brett

---

