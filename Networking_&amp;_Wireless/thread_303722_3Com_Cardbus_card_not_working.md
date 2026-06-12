---
title: "3Com Cardbus card not working"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by nkessler2000 on 2006-11-20
Hello

I just installed Ubuntu 6.10 and cannot get the wireless card to work. It is a marginally old IBM Thinkpad T20 laptop with a 3Com 3CRWE62092B Cardbus 802.11b wireless card. 

I've visited the WirlessTroubleshootingGuide on the Ubuntu Wiki

Following the advice there, I did a   
```
sudo lshw -C network
```
and got the following
```

*-network
      description: 3Com
      physical id: 0
      version: 3CRWE62092B Wireless PC Card
      Slot: Socket 1
      resources: irq:3
*-network
      description: Wireless interface
      physical id: 1
      logical name: eth0
      serial: 00:04:75:eb:cc:b3
      capabilities: ethernet physical wireless
      configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

```

The troubleshooting guide says the driver should be listed in the configuration line, but it isn't. The module, however, is loaded. This card uses the atmel chipset. 

I'm kinda at a loss. The troubleshooting guide is a little unclear as to how to address this issue. Any advice?

---

### Post by FrodoB on 2006-11-20
Was the card not recognized at all? Not seen in iwconifg?

---

### Post by nkessler2000 on 2006-11-20
It is seen in iwconfig, but if I do a "iwlist eth0 scan", I get an error that says "Resource temporarily unavailable"

---

### Post by FrodoB on 2006-11-20
Take a look at the references to this card in this forum. Surely some of these folk's post may be useful:

[http://www.ubuntuforums.org/search.php?searchid=9970887](http://www.ubuntuforums.org/search.php?searchid=9970887)

Yes, the search includes this thread as well.

---

### Post by nkessler2000 on 2006-11-20
Nope, none of those threads are really relevant. 

"3Com 3CRWE62092B PCMCIA WiFi Card Not Working Under 6.06 (Worked Fine under 5.10)" is a bunch of people complaining about how their wireless cards have a variety of issues in Ubuntu 6.06, with no advice on how to fix any of the problems. 

"atmel pcmcia wifi card" recommends a firmware upgrade, but it seems to apply to 6.06. The package it recommends is not part of 6.10. Also, it says Atmel card. Although my card has an atmel chipset, it's a 3com. Same difference?

In "Wireless Woes" he says he put a 3CRWE62092B and that fixed his problem

"3COM or Netgear wireless card - please help", the response was to recompile the kernel to fix a Netgear card, not a 3Com. 

So my problem with this card has never been addressed in these forums. 

The module loads, the interface shows up in iwconfig and ifconfig. What else can I check?

---

### Post by FrodoB on 2006-11-20
Refer to:

[http://linux-wless.passys.nl/query_part.php?brandname=3Com](http://linux-wless.passys.nl/query_part.php?brandname=3Com)

Your card is sold by 3Com, but the wireless chipset is Atmel. So any information regarding another card using Atmel is going to provide clues that you need to solve this. Unless 3COM also sold the same model with another chipset.

---

### Post by nkessler2000 on 2006-11-20
Well... the page you linked to suggests my card should work. The page that page links to, the driver homepage, says the latest version of the driver came out in 2005. I would hope 6.10 would have the latest version. 

I could try the firmware upgrade. Unfortunately, the wireless card is the only network card that works :( The wired card was causing crashes so I had to take it out. 

Anyway, I'll burn a CD or something and give it a try, but I'm not getting my hopes up. I think something else is going on.

---

### Post by FrodoB on 2006-11-20
How did you accomplish your Ubuntu install? Regular 6.10 CD or Alternative CD?

---

### Post by nkessler2000 on 2006-11-20
Regular install CD.

---

### Post by FrodoB on 2006-11-20
Can you find and publish the section of dmesg that shows the loading of this device, so we can see if there is a firmware issue or somesuch? I am not familiar with this device:

$ dmesg |more

Thanks.

---

### Post by FrodoB on 2006-11-20
OK, I have an Atmel device in my bonepile and it works out of the box with Dapper, I will check Edgy in a few minutes.  Are you sure that your setup in /etc/network/interfaces is correct?

---

### Post by nkessler2000 on 2006-11-20
I found this by doing dmesg | grep eth0

```

[   63.023752] eth0: Atmel at76c50x. Version 0.98 MAC 00:04:75:eb:cc:b3
[  133.354460] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

There is also one error that caught my attention

```

[  58.661549] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module! 

```

What is piix4_smbus? Related to PCMCIA in any way?

---

### Post by FrodoB on 2006-11-20
OK, my Atmel device is a WUSB11V2.6 USB wireless controller and yours is cardbus, that could make a difference. This one does work with Edgy as well straight out of the box.

Can you give us the output of cardctl ident. You probably need to get it with:

$ sudo apt-get update
$ sudo apt-get pcmcia-cs

$ cardctl ident

With this ID we should be able to make sure that we are looking for the correct drivers.

---

### Post by nkessler2000 on 2006-11-20
> **FrodoB said:**
> OK, I have an Atmel device in my bonepile and it works out of the box with Dapper, I will check Edgy in a few minutes.  Are you sure that your setup in /etc/network/interfaces is correct?

AFAIK /etc/network/interfaces is okay:
```

auto eth0
iface eth0 inet dhcp
wireless-essid xxxxxxxx
address 192.168.0.11
netmask 255.255.255.0
gateway 192.168.0.1
wireless-key s:

```

(I temporarily turned security off on my router thinking that might be the problem. No go. Like I said, it can't even scan for networks.)

---

### Post by nkessler2000 on 2006-11-20
> **FrodoB said:**
> OK, my Atmel device is a WUSB11V2.6 USB wireless controller and yours is cardbus, that could make a difference. This one does work with Edgy as well straight out of the box.

Can you give us the output of cardctl ident. You probably need to get it with:

$ sudo apt-get update
$ sudo apt-get pcmcia-cs

$ cardctl ident

With this ID we should be able to make sure that we are looking for the correct drivers.

Looks like cardctl isn't installed, and since I can't get a network connection, I'll have to burn a CD to get the pcmcia-cs onto the machine. Do you have a direct link to the package? If not, I'll scour around for it.

---

### Post by FrodoB on 2006-11-20
I did check and mine can use iwlist wlan0 scanning. Well let's look at the dmesg output and see what is loading.

---

### Post by FrodoB on 2006-11-20
Take a look in your firmware directory and make sure that all of the firmware for atmel devices is there:

$ ls /lib/firmware/`uname -r`

Also, dont' forget the output of cardctl ident and the dmesg output.

I have to retire for the night and I will take a look in the morning. Hopefully someone can chime in with the answer.

Another possibility is that you are having device driver contention. Is this a clean install or has ndiswrapper been involved perhaps? If so blacklist it.

---

### Post by nkessler2000 on 2006-11-20
I'm not going to be able to post the whole dmesg output, since I'd have to manually transcribe it. I posted the parts about eth0 and it seems to be loading the driver. If I take the card out and put it back in and do another dmesg, it again says 

```
eth0: Atmel at76c50x. Version 0.98
ADDRCONF(NETDEV_UP: eth0: link is not ready
```

---

### Post by nkessler2000 on 2006-11-20
The firmware files to appear to be there. I'll try and get pcmcia-cs installed on the machine and do a cardctl. 
It is a clean install, and to my knowledge there is no involvement of the ndiswrapper. 

Thanks for your help. Good night!

---

### Post by FrodoB on 2006-11-20
OK, one more think before I leave the keyboard.  Have you tried ifup and ifdown in a terminal window?

$ sudo ifup wlan0

$ sudo ifdown wlan0

Maybe this will give useful output?

---

### Post by nkessler2000 on 2006-11-20
I did an ifdown and ifup like you requested. Absolutely no messages appear for either command.

---

### Post by FrodoB on 2006-11-21
I see a post on the web contending that this think likes the router to be in shared rather than open authentication mode. This would be strange as most everything else is just the opposite.

See:

[B][http://www.fedoraforum.org/forum/archive/index.php/t-60249.html](http://www.fedoraforum.org/forum/archive/index.php/t-60249.html)


That seems to be the only useful suggestion. I see folks contending that it should work on Edgy and others saying that it won't. Perhaps a different version of Ubuntu, if nothing else works? We need to find someone with specific experience with this device I think.
[/B]

---

### Post by FrodoB on 2006-11-21
Do have a symptom like can be seen in this thread? It works on the live CD mode, but not after install. A solution for this is given, maybe it would help in your circumstance?

[http://www.ubuntuforums.org/showthread.php?t=256782&highlight=Atmel](http://www.ubuntuforums.org/showthread.php?t=256782&highlight=Atmel)

---

### Post by nkessler2000 on 2006-11-21
No, I'm afraid not. dmesg seems to indicate that the driver is loading. 

I'm totally at a loss. Maybe I will try a different version. This card used to work perfectly with 5.10, but that's kind of old.

---

### Post by gravyface on 2007-09-21
Did anyone ever resolve this?  I'm in the same boat with Feisty with the same card.

---

### Post by Propwash on 2008-02-10
I have a 3CRWE62092B card and I'm running 7.04 (from 5.10 to 6.06 to 6.10) and it works fine.  I'm running WEP on a D-Link 625.

---

