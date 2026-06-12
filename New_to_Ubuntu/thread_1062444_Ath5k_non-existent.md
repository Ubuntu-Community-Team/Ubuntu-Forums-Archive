---
title: "Ath5k non-existent?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Chazbot on 2009-02-06
I just (today) purchased a Compaq laptop, and immediately set to installing ubuntu. Now I'm still very much an ubuntu newbie, but this is the first time this particular problem has happened to me. I installed it and the network manager didn't seem to beleive I had a wireless card. My hardware drivers clearly indicated special driver support for an Atheron 802.11 Wireless card. So I go about looking for support and all the fingers eventually lead to one palm in the community documentation, [Located Here]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros"). The first step in this process is locating ath5k and installing it. The article tells me it can be found at the package repository, super good. Except... it can't. Not for Ibis anyway. I'd really like to use my new laptop as a linux system, can anyone guide me where to go from here?

---

### Post by 2hot6ft2 on 2009-02-06
Are you using Hardy or Intrepid. That link was for Intrepid and it uses ath9k, at least mine does. Maybe this will help.
[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k)

If you have the AR5009 wifi card it works out of the box with Intrepid using ath9k and blacklisting ath5k and hal_pci in /etc/modprobe.d/madwifi

---

### Post by Chazbot on 2009-02-06
um... complete newbie... can you break that down into a list of steps or something? I can't begin to follow you

and yes, Ibis went on the laptop (my desktop still has hardy, but it has wireless problems too)

---

### Post by 2hot6ft2 on 2009-02-06
How about some specs on the laptop with Ibex? In a terminal use
Applications>Accessories>Terminal
```
lspci
```
and post the output.

Looking for wifi card info, might be AR242 or AR928x

---

### Post by Chazbot on 2009-02-06
Output follows

> chazbot@chazbot-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation Device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation Device 0845 (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


Windows Device Manager (I'm keeping windows installed for games) lists the card as Atheros AR5007

---

### Post by lkraemer on 2009-02-07
Chasbot,
Here is your Guide.

1.  What is the model number of your Compaq?
    Most likely someone else has already installed
    the same software on the same model computer
    and will answer your post.  
2.  What Version of Ubuntu did you install?
    (I installed it......means nothing to us
    and neither does Ibis!)
    7.04, 7.10, 8.04.1, 8.04.2, 8.10,.......
3.  Are you familiar with Google & search?
    If not, they are very useful.....
4.  Search for either bmartin (user) or AR242x
    in this forum and look for a post with answer
    to #2 above to help you install the Atheros wireless.
5.  Save this guide along with information from
    #4 for later installs in your Documents folder.

Happy searching.

[http://ubuntuforums.org/showthread.php?t=792158&highlight=bmartin](http://ubuntuforums.org/showthread.php?t=792158&highlight=bmartin)

lk

---

### Post by Chazbot on 2009-02-07
yes, I suppose it is Ibex, not Ibis. I keep thinking bird themes, my mistake! :D 
The fix found at [URL="http://ubuntuforums.org/showthread.php?t=1054629"]This Link
[/URL] solved the problem admirably. Thank you both so much for your effort, I know it's not always so easy to deal with people who don't have the first foggiest idea what they're doing

(P.S. I went to google before posting anything, I don't want to spam requests for help anymore than you want to see them. I just found all the answers incomprehensible so I figured it was beyond me at this point in my linux usage)

(P.P.S. Isn't there some official way to give kudos on the forums? I know when I was trying to fix my desktop there was a button to click on the individual posts but I don't see it anymore)

---

### Post by kdreimiller on 2009-02-07
i think thats the same wireless card i have in my toshiba satellite.  and it's similar problems.  im on intrepid ibex.  anyways, i used this fix.  this was the only one i could get working for me.  give it a look see?

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

very easy to use instructions.

---

