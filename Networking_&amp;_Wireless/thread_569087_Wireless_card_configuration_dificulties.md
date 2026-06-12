---
title: "Wireless card configuration dificulties"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by oli2562 on 2007-10-06
Hi, I've been having some difficulty recently with the Dynamode wireless pci card (WL-GI-600XA with Marvell Technology Ltd Libertas 88w8335 chipset) that i bought for my computer. My computer runs 7.04 Fiesty, with nearly all updates downloaded.

When i got the wireless card, i initially went looking on the internet for Linux drivers for the beast. After several days of trawling however i realised i would have not luck, and therefore i downloaded and installed Ndiswrapper. This solution worked - the card is recognised and my network is seen. One problem however, i cant connect to the internet.

I've spent a lot of time as well looking on forums etc... for a solution to this problem but decided after nearly burning my retinas out from a monitor, that maybe addressing a forum might be better. So here i am, with my semi working wireless card in my nice computer.

Could anyone please help me with this problem.:KS

Please realise that i'm no linux expert, just an enthusiast - having only been converted to the wonderful world of linux around a month or two ago, i've not had much time to aquire knowledge.

Thanks in advance!!!

---

### Post by Lambert on 2007-10-07
> **oli2562 said:**
> Hi, I've been having some difficulty recently with the Dynamode wireless pci card (WL-GI-600XA with Marvell Technology Ltd Libertas 88w8335 chipset) that i bought for my computer. My computer runs 7.04 Fiesty, with nearly all updates downloaded.

When i got the wireless card, i initially went looking on the internet for Linux drivers for the beast. After several days of trawling however i realised i would have not luck, and therefore i downloaded and installed Ndiswrapper. This solution worked - the card is recognised and my network is seen. One problem however, i cant connect to the internet.

I've spent a lot of time as well looking on forums etc... for a solution to this problem but decided after nearly burning my retinas out from a monitor, that maybe addressing a forum might be better. So here i am, with my semi working wireless card in my nice computer.

Could anyone please help me with this problem.:KS

Please realise that i'm no linux expert, just an enthusiast - having only been converted to the wonderful world of linux around a month or two ago, i've not had much time to aquire knowledge.

Thanks in advance!!!

Are you using any encryption? If so which method?
Have you tried connecting from the command line?
If you are using encryption, have you tried to turn it off just to rule out possibilities and know the card/driver is working.

I might be missing something, long day. Post details on what you have tried.

---

### Post by oli2562 on 2007-10-07
Thanks for the reply:KS

I've not tried connecting via the command line, as i'm not sure how. In the *network-admin* window, i'm shown the 'Wireless connection' Option which i wasn't before i carried through the ndiswrapper solution, and in the properties of this wireless connection it shows the name of my BT Home Hub, the percentage signal level (usually ~20/25%), my password type (WEP Hex), and my network key.

*iwconfig* returns the results
```
oli@Quiberon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Is there anything wrong with these results

---

### Post by Lambert on 2007-10-07
Try this

Open up a terminal and type the following commands

```

sudo iwconfig wlan0 essid _____ key open _____ mode managed

sudo dhclient wlan0

```

enter information in blanks

---

### Post by oli2562 on 2007-10-08
Thanks for the reply, I actually found the solution by simply moving the computer closer to the router to check whether it was signal strength that was lacking. It seems this was the case. With the computer closer to the router and the signal level above 60%, the  computer wasn't complaining. I've just now bought another router identical to my current t sort the problem.

Sorry for having wasted your time on such a simple matter!

Thanks:KS

---

### Post by Jonagon on 2008-04-29
I'm also having some problems with this card, I can't even get the driver installed! I used linux a few years ago, but never dealt with wireless at the time, and have only just come back to it with release 8.0.4, so I'm fairly rusty.

I downloaded the driver from the dynamode website, but when I install it with ndiswrapper it doesn't work.. if I do 

ndiswrapper -l

I just get..

tnet1130 : driver installed

and I've tried sudo modprobe ndiswrapper 
and:

ifup wlan0

with no success.. this is a bit of a pain, I dont' know what to try next, i've experimented with various drivers from the dynamode website and have tried forcing ndiswrapper to use that device with the driver to no success.. any ideas?

---

