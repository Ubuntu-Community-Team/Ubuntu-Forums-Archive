---
title: "File and Print Sharing"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by arbulus on 2007-02-13
I am in desperate need of help.  I have googled and googled and googled and searched these forums but I cannot seem to find a straight answer. 

I have an HP Netserver E60 running Ubuntu Edgy, an iMac G5 PPC running Mac OS X 10.4 and Ubuntu Edgy dual boot and a MacBook Pro running Mac OS X 10.4.  The HP box is set up as a server for my LAN.  I am a home user.

I set up the HP box with Samba to share files with the Macs.  They work beautifully.  But I cannot get file sharing to work with Ubuntu on the iMac.  It sees the file server, but won't connect to it.  I have set up Samba on the Ubuntu iMac, but it doesn't seem to have any effect.

Also, I want to use the HP box as a print server.  

Here is my dilemma:  most everthing i can find says that I should use NFS to share between the Ubuntu server and Ubuntu iMac.  Most everything also says that I have to configure cups to use for printer sharing.  But the problem is that every single thing I find assumes that I have a static IP address for my server.  I DO NOT HAVE A STATIC IP ADDRESS.  I am a home user and cannot have a static IP address.  It is part of my ISPs terms of service that only business customers can have static IP addresses.  

I do not need the server to be open to the outside world.  I am not hosting a web site or mail.  I am just trying to set up a file and print server.  

I have tried the NFS and cups setups as everything has led me, and i have substituted my subnet addresses for the IP addresses.  I use an Airport Extreme as my router with the address of 10.0.1.1 and it assigns the addresses to the other computers, 10.0.1.2, 10.0.1.3, etc.  But these do not work in the place of the IP address that all the tutorials suggest.  

I'm really at my wit's end here.  Can anyone guide me to a clear and concise tutorial on how to set up Ubuntu to Ubuntu file sharing and printer sharing from Ubuntu to Ubuntu and Mac OS X?  I need good step by step instructions that do not rely on static IP addresses.  

Please help!

---

### Post by gradedcheese on 2007-02-14
Your ISP has nothing to do with your IP address in this case.  Here's a very sloppy diagram:

(isp)<------->router<--------->(your lan)

Where (your lan) is one or more PCs.  Your one "not static" IP, is what the router gets.  That's the WAN IP.  Your router then runs a DHCP server, handing IP addresses to your LAN, and those addresses are only good on the LAN... outside, you just have the router's ISP-assigned IP.

For this reason, you can do anything you want on your LAN: static IPs are fine, just configure your router.  For example, you should be able to tell it "10.0.1.2 though 10.0.1.20 are static, don't assign anything via DCHP there" and "10.0.1.11 and up are up for grabs to DHCP users" ...check the router settings.  If there aren't settings for this, go to the store and for $60 or so buy a better router :)  Even the cheapo Linksys WiFi routers you see on every store shelf happily do this.

That said, some routers can also do 'fake' static IPs: they will assign certain MAC addresses a certain IP each time.  Yours may or may not have that feature.

Finally, you can look at Avahi... this is the Linux implimentation of Apple's Zeroconf, it will allow your server to advertise the Samba or NFS services and other PCs will know about them even without a static IP address.  I can help you set that up if you want to use it, but a static IP makes more sense, I think.

Oh, also printer sharing is indeed quiet doable.  I can post some suggested samba settings if you need them.  Lets get your static IP assignment working first.

---

### Post by gradedcheese on 2007-02-14
oops, double post

---

### Post by scrooge_74 on 2007-02-14
You need to start by configuring your lan properly.  It would be better if you had a router that could assign ip address for your lan different from the outside IPs.  

If you configure CUPS properly the PCs with linux will detect each other in the LAN even if the IPs are dynamic.

What you are trying to set up using NFS is to mount folders or drives from the other PC using Linux.  Did you try from the menu bar the option connect to server and give options.  I for myself have done it by way of using ssh (I installed openssh server on the machines) that way I could log into the PC and browse the files.

[http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)
[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)
[http://ubuntuforums.org/showthread.php?&t=202605](http://ubuntuforums.org/showthread.php?&t=202605)

Maybe some of this threads can be helpfull for you.

Once again first setup your network properly, nobody can force you to use the IPs the way the provider wants to. You can setup your own router to assign IP address in your LAN anyway you please, besides it is better for you to have your own router with a firewall as your first line of defense

---

### Post by arbulus on 2007-02-14
First I want to apologize.  I hope that my first post didn't sound terribly mean.  I've been incredibly frustrated with trying to sort this all out.  I didn't mean to come across so harshly.  So if that was the case, I sincerely apologize.

It's so confusing when trying to find information on how the IP addresses work in a LAN like this.   But I hadn't thought about trying to modify the IP assignment settings on the router.  I'm going to check out the setting on the router and see what I am able to do and then I'll update everyone.

---

### Post by arbulus on 2007-02-14
ok, so I took a look at my AirPort settings.  It assigns IP addresses via DHCP from 10.0.1.2 to 10.0.1.200.  I can tell it to specifiy a certain range manually, but if I do, then I have no way of telling it "don't use 10.0.1.2, only use 10.0.1.3 and up"  On the server, I went to the Network preferences and gave it a static IP of 10.0.1.201, but then my Macs could no longer see it.  So I don't know if maybe I'm not doing it right or if the AirProt doesn't allow assigning a specific IP.

---

### Post by gradedcheese on 2007-02-14
> 
10.0.1.2 to 10.0.1.200


Ok, but what about 10.0.1.201 through 10.0.1.254?  :) Those are available as static IPs.

Some background: an IP address is a 32-bit number.  For readiblity they are written as four bytes, separated by dots.  In a byte (8 bits), you can represent the numbers 0 through 255 (unsigned), and that's why 10.0.1.0 through 10.0.1.255 are the true range...

As far as the Macs no longer seeing it: perhaps you need to refresh something on them?  Can you tell them to look at that specific address?

---

### Post by arbulus on 2007-02-15
Yeah, I tried using nubmers above 10.0.1.200 as a static address for the server, but then the server disappeard from the LAN.  I also tried turning off IP assignment in the AirPort settings and just manually giving addresses to each of my computers, but then none of them could communicate with each other or get on the internet.  There is a setting on the AirPort where you can tell it to look for a particular server at a particular address, but it doesn't seem to work.  It asked for a Public Port, and IP Address, and a Private Port.  In the public and private port I put the router ports used for Windows Sharing and for Personal File Sharing, and I enetered the static address I assigned to the server, but it still didn't recognize it. Whenever I made any changes I rebooted the AirPort and even rebooted the computers, but they still wouldn't work.

---

### Post by arbulus on 2007-03-08
Ok, so this is a completely freak thing. I had previously tried assigning an addres to the server, but it wouldn't accept it. But I decided to have one more try at it and it worked.  I have absolutely no idea why it didn't work previously.

I assigned 10.0.1.201 to my server and just left everything else alone.  I didn't make any changes to the Airport's config, and it works like a charm.

Having figured that out, I was able to configure NFS properly on the server so share files and set up those shares in Ubuntu on the iMac.  As well, I was able to configure CUPS to share my printers.  That however was another freak thing.  I did everything that it seemed like I should, and it wouldn't work.  Then, the next day, I tried setting it up again and everything worked just fine.  I have no idea why that was.  But everything is running like a dream now. Files and printers are sharing and everything works.

I want to thank you all for your patience with me.  You offered some greatly helpful suggestions.  And I want to apologize again for my frustration in my original post. 

Thanks everyone!

---

### Post by Mr. C. on 2007-03-08
arbulus,

Slow down a bit - from our end, this feels like drinking from a firehose ! ;-)

Quite frankly, I'm not entirely sure exactly what the state of your environment is now.  If you want help, here's what I'll need:

a) a simple overview of your systems, routers, and the OS each will run (I don't care about dual boot, because you're only using one at a time).  For example:

```

Broadband modem
                   \
  PCu1 <--> Router <-> PCu2 <-- PrinterHP
                      \ 
                       -> MacOS1

```

b) a simple description of your requirements.  For example:

  1) share files from PCu1 to PCu2
  2) print from all systems to PrinterHP
  3) ...

c) give network addresses, netmasks, broadcasts, etc. for your network(s).

More facts, less story.  If you can do that, I think we'll make some progress.

MrC

---

