---
title: "ZyAIR B-120 Wireless PCMCIA Recognized, but doesn't work"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by Noxilenticus on 2007-02-03
P.S. I forgot to say that I am running Ubuntu kernal 2.6.15-26-386 and yes I installed all the kernal headers needed with synaptic.

I usually avoid posting on forums at all costs, but I have no idea where else to go in this situation. I have tried every tutorial possible on the web that I can find to try to and get my ZyAIR B-120 Wireless PCMCIA card to work in my HP Omnibook Xe2 laptop, and I have had no luck. 

To start off, the Device Manager identifies this card as "B120 802.11b Wireless LAN", leading me to believe there should be a driver for it loaded, however an ifconfig -a shows no devices to be found. No wlan0, no eth0, no nothing.

The first thing I did was go to the ZyXEL website ([http://www.us.zyxel.com](http://www.us.zyxel.com)) to see if they made a driver for linux. No such luck there and from the forums I have been reading people have said they will not support linux.

The second thing someone suggested I try was ndiswrapper. I downloaded the correct driver off the ZyXEL website and ran the following commands from other tutorials I have found:

ndiswrapper -i ZD1201COBM.INF

When I did a ndiswrapper -l here is what I got:

Installed ndis drivers:
zd120lcobm        Invalid diver!

of course when I tried to do a

"ndiswrapper -m"

and then a

"modprobe ndiswrapper"

"ifconfig -a" still showed no devices.

The third step I found someone with a similar card and tried to manually insert an entry into my /etc/pcmcia/config file.

This was done by doing a "cardctl ident", which displays the information:

Socket 0:
  product info: "ZyAIR", "B120 802.11b Wireless LAN", "Version 1.00", ""
  manfid: 0x0308, 0x3401
  function: 6 (network)

I edited the config file and added an entry for my card:

card "B120 802.11b Wireless LAN"
manfid 0x0308, 0x3401
bind "orinoco_cs"

and uncommented a line as the tutorial I was following said:

device "orinoco_cs"
  #class "network" module "hermes", "orinoco", "orinoco_cs"
  class "network" module "orinoco_cs"

became

device "orinoco_cs"
  class "network" module "hermes", "orinoco", "orinoco_cs"
  #class "network" module "orinoco_cs"

after I restarted my PCMCIA card "/etc/init.d/pcmciautils restart" I still got nothing from "ifconfig -a".

I tried "modprobe orinoco_cs" manually. I tried "modprobe orinoco" manually. No luck.

I have heard that the ZyAIR B-120 has a Prism 2.5 chipset. I am unsure if this is true or not, so the fourth step I have tried is downloading the latest wlan-ng drivers.

I tried to "modprobe pcmcia2_plx" driver for Prism 2.5 chipsets. I have still had no luck and since I lack experiance with playing around with linux drivers and knowing commands I have no idea where to go from here.

Another thing to note is that yes I did do a dmesg after each of these steps to check if the drivers actually did load. Yes they all loaded correctly. 

I would appreciate it if anyone could give me any help in getting this Wireless card to work. 

Thank you,
Noxilenticus
[email]noxilenticus@gmail.com[/email]

---

### Post by amike on 2007-04-08
Any one have any solution for it?

I have exactly the same card and exactly the same problem ... :(

Any help will be much appreciated!!

Mike

---

### Post by amike on 2007-04-11
Why nobody answers this post?

I think Noxilenticus has done a lot of work and described the problem quite clearly.

Please help !!

---

### Post by chili555 on 2007-04-11
amike-
I guess the original poster has given up. I hope not.

Posts usually go unanswered because no one knows the answer, or the person that has one of these and has it working is not looking at the forum any longer, they are busy downloading mp3's, instant messaging Mum, etc.

According to this site; [http://linux-wless.passys.nl/query_hostif.php?hostif=PCMCIA](http://linux-wless.passys.nl/query_hostif.php?hostif=PCMCIA) which is highly reliable, the card uses the zd1201 module, which is present in the 2.6.17-x kernels. I would try ```
sudo modprobe zd1201
iwconfig
```See if an interface, possibly eth1 shows up ready to be configured and connected. 

Ndiswrapper with an invalid driver is futile. Forcing the card to bind to orinoco, if it does not use a Prism2/2.5 chipset is likewise.

This site, as well, confirms the zydas driver and not Prism2/2.5: [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

---

### Post by amike on 2007-04-21
Hello chili555,

Thanks for the reply.

I checked the page [http://linux-wless.passys.nl/query_hostif.php?hostif=PCMCIA](http://linux-wless.passys.nl/query_hostif.php?hostif=PCMCIA)

and found b-120 at the last row. Following its "comment" link ([http://linux-lc100020.sourceforge.net/)](http://linux-lc100020.sourceforge.net/)), I got to the ZyDAS zd1201 Driver page. But I could not find b-120 there(all devices with ZyDAS zd1201 are USB dongles accroding to that page).

Also I tried the solutions on "Howto: setup Zydas (zd1201) based adapters"([http://ubuntuforums.org/showthread.php?t=49070&highlight=zyxel+b-120)](http://ubuntuforums.org/showthread.php?t=49070&highlight=zyxel+b-120)), but it still didn't work for me.

My iwconfig output is still like this:

lo        no wireless extensions.

eth0      no wireless extensions.

Can you see where could the problem be?

Thanks a lot.

Mike

---

### Post by chili555 on 2007-04-21
Are you, by chance, trying to get this going with the ethernet cable attached. I read a post somewhere that suggested with the cable attached and holding an IP address, the B-120 will not be detected. If this is the case, please detach the cable and do:```
sudo ifdown eth0
sudo tail -f /var/log/messages
```Watch the terminal as you remove and re-insert the card. See if it is detected and, most importantly, the firmware is loaded. Let us know.

---

### Post by cump on 2007-06-23
:(  I have a same card and a same question

---

