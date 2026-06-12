---
title: "Internet Connection Problem (DHCP)"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by darshshinde on 2006-10-18
hello guys ,
i am a ubuntu newbie and m slowly learning to learn things n ubuntu .. but the gr8test hindrance is that i am not able to connect to internet on ubuntu ..the day i do that, i m gonna dump xp for gud ..

i am using a pentium 4 1.6 ghz pc, with 80 gb hard disk, 384 mb ram, 845 chipset motherboard, tnt2 riva 16 mb graphics card. I have dlink ethernet network card installed.

I have dual boot system, running windows xp sp2 & ubuntu 6.06 LTS version. I connect to internet via a boardband provider, who provides connectivity via a dhcp server (that's what he said he me when i tried to get his help on starting net on ubuntu - he could not though !) well in xp all i need is to make a connection for the first time was via a wizard which prompts me to make a choice of type of connection. i made a choice of a connection in which i have to enter a username and password (which my isp gave me)after which i get connected to net via the network. ubuntu shows windows netwrk in network place,(that means it detects my ethernet card) but i dont know the step by step method by which i can connect to net. the isp has provided 2 ip addresses, which are of the server which gives me the connectivity. now what should i do which the settings in netwrk tools menu in ubuntu or somewhere else to get connected.. ? also a thing i forgot to mention .. i use a static ip adress for my pc everytime i log on .

plz help , or i'll will have to ](*,) 
darshu:) 

PS_ is there small patch which would load my ntfs partitions into ubuntu just by click - without typing those commands which i fear might ruin my installation ?

---

### Post by kidders on 2006-10-18
Hi there,

> **darshshinde said:**
> I connect to internet via a boardband provider, who provides connectivity via a dhcp server

...
...

in xp all i need is to make a connection for the first time was via a wizard which prompts me to make a choice of type of connection. i made a choice of a connection in which i have to enter a username and password

DHCP isn't capable of this kind of authentication. You must be using something else, like PPPoE.


> **darshshinde said:**
> PS_ is there small patch which would load my ntfs partitions into ubuntu just by click - without typing those commands which i fear might ruin my installation ?
Which commands?

The most convenient solution might be to have your NTFS partition mounted in *no* clicks ... add a line to your /etc/fstab to have it mounted at boot :-)

---

### Post by mips on 2006-10-18
Who is your ISP, weblink please ?
What brand/model router/modem do you have ?
post output of:
ifconfig -a
cat /etc/network/interfaces

---

