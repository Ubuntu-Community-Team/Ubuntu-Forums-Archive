---
title: "connect two computers for data transfer"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by DavidFourer on 2010-11-04
Is there a simple way to connect two Ubuntu computers with a wire and see/copy data?  To anyone with networking experience I guess this would be a dumb question, but that is an area I have never had to deal with.  Currently I would copy to a usb-flash drive if I wanted to move some large files, or I would use some cloud service if I planned to collaborate or synchronize something.

---

### Post by irv on 2010-11-04
I believe the easiest way is to create a small network and connect them via a network cable. Here is a small article on connecting computer.
[http://www.associatedcontent.com/article/316437/how_to_transfer_data_between_two_computers.html]("http://www.associatedcontent.com/article/316437/how_to_transfer_data_between_two_computers.html")
Here is a howto transfer data via a USB cable:
[http://www.wikihow.com/Connect-Two-Computers-Using-Usb]("http://www.wikihow.com/Connect-Two-Computers-Using-Usb")

---

### Post by lkraemer on 2010-11-04
See:
[http://ubuntuforums.org/showthread.php?t=1346673&highlight=crossover](http://ubuntuforums.org/showthread.php?t=1346673&highlight=crossover)
Posting #6.

[http://ubuntuforums.org/showthread.php?t=1031300&page=2](http://ubuntuforums.org/showthread.php?t=1031300&page=2)
Posting #15

lk

---

### Post by DavidFourer on 2010-11-04
So I gather I can make my desktop computer a network host and my notebook computer a network remote, using some software that comes with Ubuntu or is easily installed.  Then I would disconnect my my internet Ethernet cable and connect the network adapters in the two computers by Ethernet cable.  Once set up, it should be easy to use.  

I might set this up as a learning exercise, since I want to learn something about networking.

(I see we crossed posts--I will read the above.)

---

### Post by Zzl1xndd on 2010-11-04
You might need a different cable. Normally Direct PC to PC connections require a Cross-Over Cable. 

[http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

The one connected to your Modem may or may not be one (probably not).

That being said long term you would probably be better served to get a Router. This would allow you to share your internet connection as while as network the two PC's to share files.

---

### Post by irv on 2010-11-04
> **DavidFourer said:**
> So I gather I can make my desktop computer a network host and my notebook computer a network remote, using some software that comes with Ubuntu or is easily installed.  Then I would disconnect my my internet Ethernet cable and connect the network adapters in the two computers by Ethernet cable.  Once set up, it should be easy to use.  

I might set this up as a learning exercise, since I want to learn something about networking.

(I see we crossed posts--I will read the above.)
Let me ask some questions. How do you have these computers hooked up to the Internet now? Do you have them on cable or wifi? If on a wire, do you have them plugged into a hub or router or maybe a switch? If you do, you might have them networked already.

---

### Post by DavidFourer on 2010-11-04
> **irv said:**
> How do you have these computers hooked up to the Internet now? ... you might have them networked already.
Good point.  They are on a router and one is cable and the other is wifi.  I didn't set it up, but I think these home routers provide some kind of networking. I will have to get the owners manual and read about the router.

---

### Post by CharlesA on 2010-11-04
> **tweakedenigma said:**
> You might need a different cable. Normally Direct PC to PC connections require a Cross-Over Cable. 

That's true with 10/100 Network cards, but Gigabit NICs have [Auto MDIX]("http://en.wikipedia.org/wiki/Medium_dependent_interface"), so you can use a regular cable to hook up two hosts.

> **DavidFourer said:**
> Good point.  They are on a router and one is cable and the other is wifi.  I didn't set it up, but I think these home routers provide some kind of networking. I will have to get the owners manual and read about the router.

They are already on a network.

Depending on what host OS in on the machines, you could use NFS (*nix), Samba (Windows) or even ssh (sftp)

I'd suggest NFS myself.

---

### Post by uRock on 2010-11-04
Take the HDD out of one and throw it in the other as a slave drive then just drag-n-drop files to or from the drive. A cross over cable will get it done as well, provided that the cards aren't Gigabit/MDIX compatible.

---

### Post by CharlesA on 2010-11-04
> **uRock said:**
> Take the HDD out of one and throw it in the other as a slave drive then just drag-n-drop files to or from the drive. A cross over cable will get it done as well, provided that the cards aren't Gigabit/MDIX compatible.

Good idea.

I was going on the assumption that one was a laptop, since they mentioned wifi. :P

---

### Post by uRock on 2010-11-04
> **CharlesA said:**
> Good idea.

I was going on the assumption that one was a laptop, since they mentioned wifi. :P
I see that now, oops.[IMG]http://www.mikesplanet.net/forums/images/smilies/cool.png[/IMG] It is still possible, but I would only do it if the drive on the lappy was easily removed. Sounds like the best bet would be utilizing a networking strategy.

---

### Post by irv on 2010-11-04
> **DavidFourer said:**
> Good point.  They are on a router and one is cable and the other is wifi.  I didn't set it up, but I think these home routers provide some kind of networking. I will have to get the owners manual and read about the router.
goto place>network and see if you can see the other computer. If you have a problem go to the file manager and set up a share directory. You can do this by right mouse clicking on the directory and select share and set it my putting a check mark in the little box next to share.

---

