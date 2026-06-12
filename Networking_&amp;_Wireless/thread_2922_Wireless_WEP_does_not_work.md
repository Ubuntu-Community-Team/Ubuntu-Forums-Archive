---
title: "Wireless WEP does not work"
date: 2004-11-01
forum: Networking &amp; Wireless
---

### Post by maxdeo on 2004-11-01
I can't get my wireless to work with WEP key.  If I disable encryption at the router I get an IP and everything works fine.  I've tried configuring using the GUI and ifconfig/IWconfig conbination, also editing /etc/network/interfaces.  I also tried using a static IP versus DHCP.    The wireless card sees the router because the signal appears on network connection GUI as a strong signal.  Any ideas?

---

### Post by FLeiXiuS on 2004-11-01
[QUOTE=maxdeo]I can't get my wireless to work with WEP key.  If I disable encryption at the router I get an IP and everything works fine.  I've tried configuring using the GUI and ifconfig/IWconfig conbination, also editing /etc/network/interfaces.  I also tried using a static IP versus DHCP.    The wireless card sees the router because the signal appears on network connection GUI as a strong signal.  Any ideas?[/QUOTE]
 

Just a thought, did you insert the WEP key when you did it via GUI?

**Enabling a WEP Key On an Interface**
Enter the WEP key in the following format: xxxx-xxxx-xx For example:
```

iwconfig $INTERFACE key xxxx-xxxx-xx

```

Replace '$INTERFACE' with the Wi-Fi interface. (IE: eth0)

---

### Post by maxdeo on 2004-11-03
Yes I entered the wep key using the GUI and also tried it with the IWCONFIG command.   Using either method when I enter iwconfig ath0 the configuration display is correct.  I think that it's ignoring the key somehow.

---

### Post by mduduzi on 2004-11-03
[QUOTE=maxdeo]Yes I entered the wep key using the GUI and also tried it with the IWCONFIG command.   Using either method when I enter iwconfig ath0 the configuration display is correct.  I think that it's ignoring the key somehow.[/QUOTE]


Try setting your AP WEP mode to Open key instead of Shared Key. I don't know if your AP has that setting but others do. What AP are you connecting to?

---

### Post by chard on 2004-11-04
[QUOTE=mduduzi]Try setting your AP WEP mode to Open key instead of Shared Key. I don't know if your AP has that setting but others do. What AP are you connecting to?[/QUOTE]
 I had the same issue during install.  Now the card isn't even recognized. No matter how I entered the WEP key, it wouldn't connect.  How can I get the NIC recognized now?

---

### Post by mduduzi on 2004-11-04
[QUOTE=chard]I had the same issue during install.  Now the card isn't even recognized. No matter how I entered the WEP key, it wouldn't connect.  How can I get the NIC recognized now?[/QUOTE]


It's fairly difficult to try to share thoughts on problem resolution withour some info on the hardware you're using.

---

### Post by maxdeo on 2004-11-04
I tried OPEN instead of SHARED and it works.  The router is a DI-624 and the wireless card is aDWL-G650 both dlink products.   Thanks for your help

---

### Post by dave_euser on 2004-11-04
Just in my own experience (in case someone searches for this in the future), the Atheros chipset drivers seem to work with WEP a little better if you give the key as an alpha string instead of a hex string.....had similar problems until I did this, then everything worked fine.

never had time to figure out what was actually going on....

---

### Post by mrinferno on 2005-02-16
i have a netgear wg511 pc card and a netgear wgr614 router...

i couldn't get my wireless to work with a fresh install of ubuntu.  i have WEP 128bit enabled and it's hex, not just alpha.

i just wanted to say thanks for the info in this thread  :grin: .  i was having trouble, so i googled it up and this thread was the first link i tried.

my router was set to "automatic" for the WEP authentication type.  based on this thread i changed the setting to "open system" and everything started working fine.  using using static ip and dhcp.

---

### Post by mduduzi on 2005-04-29
[QUOTE=mrinferno]i have a netgear wg511 pc card and a netgear wgr614 router...

i couldn't get my wireless to work with a fresh install of ubuntu.  i have WEP 128bit enabled and it's hex, not just alpha.

i just wanted to say thanks for the info in this thread  :grin: .  i was having trouble, so i googled it up and this thread was the first link i tried.

my router was set to "automatic" for the WEP authentication type.  based on this thread i changed the setting to "open system" and everything started working fine.  using using static ip and dhcp.[/QUOTE]


Thanks for your feedback. Now I need yours...
The last time I tried NetGear's Wi-Fi PCMCIA card (I think it was the 511 series) I had to return it because it had a soft MAC. I found out that not all their card were the same -though sold under the same model number. I'm curious to know whether that has changed or not as I would love to match both AP and cards for my clients (I love their DG834G).
Please  look behind your card and tell me whether it was made in China or no. And also approximately when and in which Country you bought it.

Thanks,

---

### Post by mrinferno on 2005-04-29
i bought mine in early 2004.  i live in the US.  the card was made in Taiwan.

if you go to netgear's site, they are up to WG511v2 now.  i just have the straight up WG511.

hope that helps.

---

### Post by mduduzi on 2005-05-01
I thought so... The WG511 cards from Taiwan have a good reputation. It's the ones from China that raise my ire. OK, thanks.

---

### Post by F4lc0n on 2005-05-25
[QUOTE=maxdeo]I tried OPEN instead of SHARED and it works.  The router is a DI-624 and the wireless card is aDWL-G650 both dlink products.   Thanks for your help[/QUOTE]

So anyone had luck getting it to work with Shared auth? I have the same problem with the dlink DWl 520+ nic and a netgear AP with shared auth.. i cant change the the auth method. so i have to try and get it working with shared. suggestions?

 ](*,) 

Thanks guys

---

### Post by lonetree on 2005-06-04
guys,

don't know if I'm right about this. I have problem with WEP settings too. 

I'm using Dlink DI-724, and orinoco pcmcia wireless adapter. My WEP default key is set at key 3 (HEX type), no luck while trying to obtain IP address from my router. However, if WEP is disabled, connection (wireless) is established. Can't find anything about open mode or shared mode in my router, so I tried to set the WEP to key 1 instead, and re-activate the wireless connection again. 

Bingo! 

My wireless connection is established. Well this work for me, but I still feel that this is not the ideal case. I wish to use other key instead of only key 1.

One other issue, I saw from some other posting that the WEP key must follow with a "-" after every 4 character, well for my case here, I do not need any.

I hope this would help some of you.

Thanks.

Regards.

Ubuntu Rocks (best linux desktop I ever see so far) :grin:

---

### Post by lonetree on 2005-06-04
Guys,
Sorry for the last post, some mistake here, I did issue a command " iwconfig eth1 key xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx " and also the command, iwconfig eth1 key on


just in case, my previous post don't work. Try this. :-)

Regards

---

### Post by misterhung on 2005-06-22
I thought I may be able to add something that will help.

When one is using a shared key, simply enter the key under "WEP key" in the wireless interface config window (in Ubuntu's Networking configuration app) **PREFIXED** by the word "[FONT=Courier New]restricted[/FONT]" (that's "restricted" followed by a space, then the shared WEP key).  You'll not be able to see what you are typing, so you'll have to trust your fingers.  :)

[IMG]http://warmachine.3cx.org/misc/wireless-config.jpg[/IMG] 

See the iwconfig man page for more.

---

### Post by lonetree on 2005-07-21
Assuming this works, (at the point of time when replying to this, I have not try it yet). How do I specify which key I wanna use. For instance, I am using key #4. And if I'm not wrong, the WEP key that is entered in the WEP field is always pointing to key #1.

Hope you understand what I'm talking aout.

:-)

regards.

---

