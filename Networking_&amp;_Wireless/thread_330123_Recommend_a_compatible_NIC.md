---
title: "Recommend a compatible NIC"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by andreasbygdell on 2007-01-02
Hi,

I'm a long time and fairly proficient computer user that's in dire need of assistance. A brief recap...

I've been using OsX(/9/8...) and Dos/Windows (cirka 1990 up to the latest server versions) both personally and professionally for most of my 25 year long life. While I'm forced to use both branches in my profession I just can't stand Windows at home anymore. I've been playing about with various Linux-distros on some leftover hardware at home and has really grown to like Ubuntu which, imho, is an excellent and well excecuted idea.

My parents' computer was turning into a spyware-ridden, WGA-damaged XP-mess (a legit copy, mind you) and after a chat about their needs (basically OpenOffice, printer support, camera support and IM) we decided to backup all documents and install Ubuntu on it. All goes well (and they love the new system - it even comes with Solitaire!) except for one major thing...

Their Davicom NIC doesn't work. I've tried jumping through all the hoops described in the millions of forum threads dedicated to this particular piece of hardware and come to the conclusion that it's just not worth the hassle. I'm going to buy them a new NIC but I need to find one that is 100% compatible and easy for them to install. Unfortunately I live 1200 kms away from them and won't be able to attend the installation so it's imperative that they can just plug it in, insert whatever CD came with the card and follow the printed instructions. "sudo gedit whatever" is unfortunately not an option.

So... is there a NIC out there that I should buy or do I have to tell them to order Vista? (Please, don't...) Any help is much appreciated! If I can work this one out I'll feel more confident in recommending Ubuntu to other people.

---

### Post by wireddad on 2007-01-02
I may have missed it but if you are installing on a PC, a Dlink works.  Dlink works for both PC and laptops.  If you need specific I can try to get that for you.  I have Ubuntu on both PC and laptop.

---

### Post by hoosemon61 on 2007-01-02
*My parents' computer was turning into a spyware-ridden, WGA-damaged XP-mess (a legit copy, mind you) and after a chat about their needs (basically OpenOffice, printer support, camera support and IM) we decided to backup all documents and install Ubuntu on it.* ......
[B]
Good for you!  I too support my 75+ yr old parents and have been tempted to do the same.  My dad is particularly adept at picking up various malware and installing apps he doesn't need.[/B]



*So... is there a NIC out there that I should buy or do I have to tell them to order Vista? (Please, don't...) Any help is much appreciated! If I can work this one out I'll feel more confident in recommending Ubuntu to other people.*[/QUOTE]

[B]I'm certainly no guru, but I believe you can run almost anything using Win drivers if you load a Linux package called NDisWrapper.  

I haven't done that successfully though, so I've chosen hardware from the list of compatible stuff: [/B]

  [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)

I hope that helps.

---

### Post by yota on 2007-01-02
Hi, you can pick one here (plenty of choice):

[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)

It's likely that realtek based cards are easy to be found and cheap:

[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek)

Hope this helps!

---EDIT: i really hate simulposting! ;-)

---

### Post by RRS on 2007-01-02
I have a Linksys "10/100 EtherFast PCI Adapter" installed in one of my machines. It was detected and the connection set automatically during various installations of Breezy, Dapper and Edgy without any issues.

The barcode sticker on the box shows "Model No.; LNE100TX"

Don't know if it's easily available to your parents, "1200 km" implies you're not in the U.S. but even without a good(well stocked) retailer in their area, should be available for shipping.

There's probably several others equally good but this one worked for me.

---

### Post by andreasbygdell on 2007-01-08
Thank you very much everyone! I've decided to order [this one]("https://www.datorbutiken.com/home/Navigation/Details.aspx?Product=DFE-530TXR") for them, which was listed in the compatibility list. If it doesn't auto configure at once I'll just guide them through backing up their documents and reinstalling from scratch. (Unless there is a surefire easy way to reset and rescan all network devices?)

I like the OS and I'm really starting to like the community. I'll spread the gospel!

---

### Post by wireddad on 2007-01-09
That one should work.  I have a D-link something too.  Have not had any problems with the card in any distro.

If anyone knows how to rescan when installing new hardware please tell us.

---

### Post by bsalt on 2007-02-15
bump

---

### Post by chili555 on 2007-02-15
> If anyone knows how to rescan when installing new hardware please tell us.

I believe if you shut down the computer, disconnect the power cable (mains?), install the card, reconnect the mains and ethernet cable, it will just work. 

You may need to check in System ->  Administration -> Networking to be sure that the ethernet connection is enabled and using DHCP.

---

