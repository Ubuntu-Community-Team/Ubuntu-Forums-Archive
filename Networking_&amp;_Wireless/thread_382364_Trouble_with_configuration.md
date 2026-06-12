---
title: "Trouble with configuration"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by richardsonh on 2007-03-12
This could totally be beyond me. And I might just be misunderstanding and it is a divers issue, but I believe its just an ID10T error.


Alright so I have experience with Linux. But never with wireless, so I wanted to figure out how to get my card working. I'll go into details about it in a second. I can scan just fine, but I'm not connecting, and I am getting strange conflicts in configuration.

What I have.
**Linksys WMP54G Wireless 802.11g PCI card using the RaLink chipset.**
**Linksys WRT54G Wireless Router using 64bit WEP encryption**

a *lspci* returns
**RaLink RT2561/RT61 802.11g PCI**

I get into Ubuntu, and sudo iwconfig returns several things to me 
**wlan0**
**wmaster0**

I havent a clue what wmaster0 is, I was told in the #Ubuntu channel that, sometimes Ralink chipsets will do that (no biggie, i've seen weirder stuff)

Alright so I decide to do an *iwlist wlan0 scan* i'm returned a list containing several cells. I see mine on there. I am figuring that since I can preform a scan just fine, that I can probably connect just fine. But again I may just be wrong.

When I try to configure the wlan0 connection using *sudo iwconfig wlan0 essid chesney key 0000000000 mode managed* I'm not given an error, unless under the System > Administration > Networking interface the device is enabled. then I get a resource busy. If I disable it and use the terminal to set the information it doesn't give me an error. 

If I do a **sudo iwconfig wlan0** It says "ESSID: Chesney" which is correct. but under access point I see "Not-Associated" and Encryption Key: off.

After I set this information using sudo in the terminal if I check **/etc/network/interfaces** It doesnt have the updated information.

So basically i'm at a loss of what to do.

I've read all the man pages for iwconfig, ifconfig, and such.
I've tried [LIST]
[*]**key open 0000000000**
[*]**key restricted 0000000000**
[*]**key open 0000-0000-00**
[*]**key restricted 0000-0000-00**
[/LIST]

I've tried a good bit of the forms of
**iwconfig wlan0 essid *siteid*  key *{number of the forms stated above}* mode managed **

---

### Post by adam.tropics on 2007-03-12
I am no expert on wireless stuff, but can offer a few links which you may or may not find helpful.

As far as drivers are concerned, with your card, [this is worth a look]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?action=show&redirect=Rt61WirelessCardsHowTo"), it looks a heap scarier than it is, but it fairly clear.

Also, network manager is not the only option, and apparently still doesn't play great with some cards. If you think that could be it, then check out alternatives, [Wicd,]("http://compwiz18.blackhole.cx/wicd/wb/") and [Wifi radar.]("http://linuxappfinder.com/package/wifi-radar") Failing all that there is a good [troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") at the [Ubuntu Docs project]("https://help.ubuntu.com/community/") which you might find useful.
 
Sorry I couldn't be more help, but that should get you started if nobody else pipes up!.

---

### Post by richardsonh on 2007-03-12
adam.tropics

Thanks for the tutorial. It's up and working!

---

